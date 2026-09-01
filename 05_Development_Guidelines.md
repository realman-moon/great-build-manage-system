# Development Guidelines

**Project:** Legacy System Modernization Project

**Version:** 1.0

**Status:** Draft

---

## 1. Purpose

This document defines the development standards, coding conventions,
architecture principles, and best practices that shall be followed
throughout the project.

These guidelines ensure that the new Laravel 12 application is
consistent, maintainable, scalable, secure, and easy to understand.

---

## 2. General Principles

The project shall follow the following software engineering principles.

- SOLID Principles
- DRY (Don't Repeat Yourself)
- KISS (Keep It Simple, Stupid)
- Separation of Concerns
- Clean Code
- Single Responsibility Principle

Business logic shall never be duplicated.

---

## 3. PHP Standards

The project shall follow:

- PHP 8.3+
- PSR-12 Coding Standard
- Strict typing where appropriate
- Meaningful variable names
- Meaningful method names
- Consistent formatting

Example:

```php
public function store(StoreAccountRequest $request)
{
    //
}
```

---

## 4. Laravel Architecture

The application shall follow modern Laravel architecture.

```text
Route
    │
    ▼
Controller
    │
    ▼
Service
    │
    ▼
Repository (Optional)
    │
    ▼
Model
    │
    ▼
Database
```

Controllers should only coordinate requests.

Business logic belongs in Services.

Database access belongs in Models or Repositories.

---

## 5. Folder Structure

```text
app/

├── Http/
│   ├── Controllers/
│   ├── Requests/
│   └── Middleware/
│
├── Models/
│
├── Services/
│
├── Repositories/
│
├── Policies/
│
├── Jobs/
│
├── Events/
│
├── Listeners/
│
├── Notifications/
│
└── Helpers/
```

---

## 6. Controllers

Controllers should:

- Be small
- Be readable
- Validate requests
- Call Services
- Return Responses

Controllers should NOT:

- Contain SQL
- Contain business rules
- Perform calculations
- Handle complex workflows

---

## 7. Services

Services contain business logic.

Example:

```text
AccountController

↓

AccountService

↓

AccountRepository

↓

Account Model
```

Each service should have a single responsibility.

---

## 8. Models

Models should:

- Define relationships
- Define scopes
- Define casts
- Define accessors
- Define mutators

Models should not contain large business workflows.

---

## 9. Validation

All validation shall use Form Requests.

Example:

```text
StoreAccountRequest

UpdateAccountRequest

StoreProjectRequest

UpdateProjectRequest
```

Validation should never be placed inside controllers.

---

## 10. Authorization

Authorization shall use:

- Policies
- Gates
- Middleware

Controllers should not contain authorization logic beyond calling the appropriate policy.

---

## 11. Database

Database changes shall be managed using:

- Migrations
- Seeders
- Factories

Direct SQL should only be used when necessary.

Relationships should use Eloquent.

---

## 12. Routing

Routes should use Resource Controllers whenever possible.

Example:

```php
Route::resource('accounts', AccountController::class);
```

API routes and Web routes should remain separate.

---

## 13. Error Handling

Errors should:

- Be logged
- Return meaningful messages
- Never expose sensitive information

Exceptions should be handled using Laravel's exception handling mechanism.

---

## 14. Logging

Use Laravel logging.

Log:

- System errors
- Failed jobs
- Critical exceptions
- Security events

Avoid logging passwords or confidential information.

---

## 15. Testing

Every major feature should include:

- Unit Tests
- Feature Tests

Critical business workflows should always be tested.

---

## 16. Git Workflow

Branch naming:

```text
feature/account-module

feature/project-module

bugfix/login

hotfix/payment

release/v1.0
```

Commit messages:

```text
feat: Add Account Service

fix: Correct account validation

refactor: Move business logic to service

docs: Update Account documentation

test: Add feature tests for project module
```

---

## 17. Documentation Standards

Every module shall contain documentation covering:

- Business Overview
- Business Rules
- Requirements
- Design
- Database
- API
- UI
- Test Cases

Documentation shall be updated before implementation whenever requirements change.

---

## 18. AI-Assisted Development

Artificial Intelligence may assist with:

- Legacy code analysis
- Documentation
- Refactoring
- Code generation
- Test generation
- Architecture review

AI-generated content must always be reviewed and approved before being merged into the project.

---

## 19. Code Review Checklist

Before merging code, verify:

- Coding standards are followed.
- Business rules are preserved.
- Tests pass successfully.
- Documentation is updated.
- No duplicated logic exists.
- Security considerations have been addressed.
- Performance impacts have been evaluated.

---

## 20. Definition of Done

A task is considered complete when:

- Business requirements are satisfied.
- Code follows project standards.
- Tests pass successfully.
- Documentation is updated.
- Code review has been completed.
- The feature is approved.

---

## 21. Notes

These guidelines apply to every module within the project.

Any deviation from these standards should be documented and approved to maintain consistency throughout the modernization effort.
