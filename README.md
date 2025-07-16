
# 📚 Library Management System

A Spring Boot RESTful application that handles core library operations such as managing users, issuing library cards, managing authors and their books, and handling book reviews.

---

## 🚀 Features

- 👤 Add a user and automatically issue a library card
- 🔎 Fetch user details and issued library card by email
- ✏️ Update user name using email
- 🗑️ Delete user and their associated library card
- 🧑‍💼 Add an author with a list of books
- 💬 Add reviews for a specific book
- 📚 Fetch a book and its reviews
- ❌ Delete a book and all its associated reviews

---

## 🛠 Tech Stack

| Layer      | Technology                 |
|------------|-----------------------------|
| Backend    | Spring Boot 3.5.0           |
| Language   | Java 17+ / 21+ / 24          |
| ORM        | Spring Data JPA + Hibernate |
| Database   | PostgreSQL                  |
| Validation | Jakarta Bean Validation     |
| API Docs   | Swagger (Springdoc OpenAPI) |

---

## 📂 Entity Relationships

- **User ↔ LibraryCard** → One-to-One
- **Author ↔ Book** → One-to-Many
- **Book ↔ Review** → One-to-Many

---

## 🔗 API Endpoints

| Method | Endpoint                                            | Description                               |
|--------|-----------------------------------------------------|-------------------------------------------|
| POST   | `/LMS/add-user-and-issue-library-card`              | Create user and issue a library card      |
| GET    | `/LMS/fetch-user-and-issued-library-card/{email}`   | Fetch user and card info by email         |
| PUT    | `/LMS/update-name/{email}/{updatedName}`            | Update user name by email                 |
| DELETE | `/LMS/delete-user/{email}`                          | Delete user and their library card        |
| POST   | `/LMS/add-author-and-books`                         | Add an author with multiple books         |
| POST   | `/LMS/add-reviews/{title}`                          | Add review to a book by title             |
| GET    | `/LMS/fetchBookDetailsAndReviews/{title}`           | Get a book’s details along with reviews   |
| DELETE | `/LMS/delete-book/{title}`                          | Delete a book and its reviews             |

---

## 📘 Sample JSON Requests

### 👤 Add User and Issue Library Card

```json
POST /LMS/add-user-and-issue-library-card

{
  "name": "Alice",
  "email": "alice@example.com",
  "libraryCardsDTO": {
    "issueDate": "2025-07-01",
    "expiryDate": "2026-07-01"
  }
}
```

### 🧑‍💼 Add Author and Books
```json
POST /LMS/add-author-and-books

{
  "name": "J.K. Rowling",
  "booksDTOS": [
    { "title": "Harry Potter and the Philosopher's Stone" },
    { "title": "Harry Potter and the Chamber of Secrets" }
  ]
}
```

### 💬 Add Book Review
```json
POST /LMS/add-reviews/Harry Potter and the Philosopher's Stone

{
  "rating": 5,
  "comment": "Fantastic fantasy novel!"
}
```

---

## 🧪 Validation & Exception Handling

- Uses Jakarta Bean Validation for inputs (`@Email`, `@NotBlank`, etc.)
- Custom exception handling via `LibraryManagementSystemException`

---

## 🔄 Database Configuration

Update `src/main/resources/application.properties`:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/librarydb
spring.datasource.username=postgres
spring.datasource.password=your_password
spring.jpa.hibernate.ddl-auto=update
```

---

## 💻 How to Run

```bash
# Clone repo
git clone https://github.com/thimothybabu123/LibraryManagementSystem
cd LibraryManagementSystem

# Build and run
mvn clean install
mvn spring-boot:run
```

---

## 🔍 Swagger UI

To view and test APIs visually via Swagger UI:

[http://localhost:8080/swagger-ui/index.html](http://localhost:8080/swagger-ui/index.html)

Add this dependency to your `pom.xml`:

```xml
<dependency>
  <groupId>org.springdoc</groupId>
  <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
  <version>2.5.0</version>
</dependency>
```

---

## 📌 Future Enhancements

- JWT-based authentication
- Role-based access (Admin / Member)
- Book return tracking with due date reminders
- Pagination and filtering support for books and reviews

---

## 📄 License

This project is licensed under the MIT License.

---

## 👨‍💻 Author

**Thimothi Babu Ramagalla**  
[GitHub Profile](https://github.com/thimothybabu123)
