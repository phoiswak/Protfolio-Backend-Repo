# MyPortfolio — Backend API

A personal portfolio backend built with **ASP.NET Core (.NET)** following Clean Architecture principles. Designed to serve portfolio data (projects, skills, experience) via a RESTful API to a React frontend.

## Tech Stack

| Layer | Technology |
|---|---|
| API | ASP.NET Core, .NET |
| Architecture | Clean Architecture, CQRS |
| Messaging | MediatR |
| Validation | FluentValidation |
| Database | PostgreSQL |
| ORM / Query | LinqToDB |
| Migrations | FluentMigrator |

## Project Structure

```
src/
├── Portfolio.API/           # Entry point — controllers, middleware, DI setup
├── Portfolio.Application/   # Use cases — commands, queries, DTOs (MediatR handlers)
├── Portfolio.Domain/        # Core entities and domain logic (no dependencies)
└── Portfolio.Infrastructure/ # Database access, external services
```

This structure follows Clean Architecture — domain and application layers have no dependency on infrastructure or frameworks.

## Getting Started

### Prerequisites

- [.NET SDK](https://dotnet.microsoft.com/download) (version 8+)
- [PostgreSQL](https://www.postgresql.org/) running locally (default port 5433)

### 1. Clone the repository

```bash
git clone https://github.com/phoiswak/MyPortfolioWebsite.git
cd MyPortfolioWebsite
```

### 2. Configure the database

Update `src/Portfolio.API/appsettings.json` with your local PostgreSQL credentials:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Host=localhost;Port=5433;Database=portfolio_db;Username=your_user;Password=your_password"
  }
}
```

> **Note:** Never commit real credentials. Use `appsettings.Development.json` locally (it is gitignored).

### 3. Run database migrations

```bash
cd src/Portfolio.API
dotnet run --migrate
```

### 4. Start the API

```bash
dotnet run
```

API runs at `https://localhost:7000` by default. Swagger UI is available at `/swagger`.

## Architecture Notes

- **CQRS with MediatR** — all business operations are expressed as commands or queries, keeping handlers focused and testable.
- **Clean Architecture** — the domain layer has zero external dependencies; infrastructure concerns (DB, HTTP) are injected at the API layer.
- **FluentMigrator** — database schema changes are versioned and applied on startup.

## Contact

- Email: phosiwak@gmail.com
- LinkedIn: [Khorommbi Irvin Phosiwa](https://www.linkedin.com/in/khorommbi-irvin-phosiwa-605691119/)
