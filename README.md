# Projeto-DIO-Criando-Board-Tarefas-Java

:spiral_calendar: Atualizado em 26 de Junho de 2025 :heart:

<img align="right" alt="GIF" height="160px" src="https://github.com/rdeconti/rdeconti-resources/blob/main/Digital%20Innovation%20One%20-%20Logotipo.png" />

Este projeto foi proposto pela Digital Innovation One
- Link do código original: https://github.com/digitalinnovationone/board
- Professor: José Luiz Abreu Cardoso Junior
- Aulas: [DIO](https://web.dio.me/lab/proejto-board-de-tarefas/learning/20a6039c-3f63-43c8-9812-ef7aa35bc2f3?back=/track/tonnie-java-and-ai-europe)

## Descrição
- Aprenda a criar um board de tarefas em Java, passando por todas as etapas do desenvolvimento, desde o planejamento e estruturação até a implementação de funcionalidades como gerenciamento de dados e integração entre camadas, seguindo boas práticas de programação.

## Estrutura do Projeto

```
├── build.gradle.kts                # Configuração do Gradle
├── gradlew / gradlew.bat           # Scripts para executar o Gradle
├── settings.gradle.kts             # Configuração de módulos do Gradle
├── README.md                       # Este arquivo de documentação
├── LICENSE                         # Licença do projeto
├── .gitignore                      # Arquivos e pastas ignorados pelo Git
├── src/
│   └── main/
│       ├── java/
│       │   └── br/com/dio/
│       │       ├── Main.java                       # Classe principal
│       │       ├── dto/                            # Data Transfer Objects
│       │       ├── exception/                      # Exceções customizadas
│       │       ├── persistence/
│       │       │   ├── config/                     # Configuração de conexão
│       │       │   ├── converter/                  # Conversores de tipos
│       │       │   ├── dao/                        # DAOs para acesso ao banco
│       │       │   ├── entity/                     # Entidades do banco
│       │       │   └── migration/                  # Estratégia de migração (Liquibase)
│       │       ├── service/                        # Serviços de negócio
│       │       └── ui/                             # Interface de linha de comando
│       └── resources/
│           ├── liquibase.properties                # Configuração do Liquibase
│           └── db/
│               └── changelog/
│                   ├── db.changelog-master.yml     # Master changelog do Liquibase
│                   └── migrations/                 # Scripts de migração SQL
```

### Principais arquivos Java

- [`Main.java`](src/main/java/br/com/dio/Main.java): Ponto de entrada da aplicação.
- [`MigrationStrategy.java`](src/main/java/br/com/dio/persistence/migration/MigrationStrategy.java): Executa as migrações do banco de dados via Liquibase.
- [`MainMenu.java`](src/main/java/br/com/dio/ui/MainMenu.java): Menu principal da aplicação.
- [`BoardMenu.java`](src/main/java/br/com/dio/ui/BoardMenu.java): Menu de operações do board.
- [`BoardService.java`](src/main/java/br/com/dio/service/BoardService.java): Lógica de criação e exclusão de boards.
- [`CardService.java`](src/main/java/br/com/dio/service/CardService.java): Lógica de manipulação dos cards.
- [`BoardDAO.java`](src/main/java/br/com/dio/persistence/dao/BoardDAO.java): Acesso ao banco para boards.
- [`CardDAO.java`](src/main/java/br/com/dio/persistence/dao/CardDAO.java): Acesso ao banco para cards.

### Migrações e Configuração

- [`liquibase.properties`](src/main/resources/liquibase.properties): Configuração do Liquibase.
- [`db.changelog-master.yml`](src/main/resources/db/changelog/db.changelog-master.yml): Arquivo mestre de changelogs.
- Scripts SQL em [`migrations/`](src/main/resources/db/changelog/migrations/): Scripts de criação e alteração de tabelas.

## Como Executar

1. **Pré-requisitos**:
   - Java 17 ou superior
   - MySQL rodando em `localhost` com banco `board`, usuário `board` e senha `board`
   - Gradle (ou use o wrapper `./gradlew`)

2. **Configuração do Banco de Dados**:
   - Crie o banco de dados e usuário:
     ```sql
     CREATE DATABASE board;
     CREATE USER 'board'@'localhost' IDENTIFIED BY 'board';
     GRANT ALL PRIVILEGES ON board.* TO 'board'@'localhost';
     FLUSH PRIVILEGES;
     ```

3. **Executando o Projeto**:
   - No terminal, execute:
     ```sh
     ./gradlew build
     java -cp build/libs/Board-1.0-SNAPSHOT.jar br.com.dio.Main
     ```
   - Ou rode diretamente pela sua IDE, executando a classe [`br.com.dio.Main`](src/main/java/br/com/dio/Main.java).

4. **Liquibase**:
   - As migrações são executadas automaticamente ao iniciar a aplicação.

## Licença
    - MIT License