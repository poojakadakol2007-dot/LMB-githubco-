# LMB-githubco-
<img width="1533" height="787" alt="WhatsApp Image 2026-05-18 at 10 48 09 AM" src="https://github.com/user-attachments/assets/6a567f97-8105-4744-a785-9737d8c869c1" />
<img width="286" height="176" alt="download" src="https://github.com/user-attachments/assets/d92d3c73-d0bf-43c6-9a23-bce6ede0de86" />


# 📚 Library Management System - Full Stack Django Project

A comprehensive full-stack library management system built with Django and Django REST Framework. This application provides both REST APIs and professional web interfaces for managing books, authors, categories, and book issuance.

## 🎯 Features

### API Endpoints (REST Framework)
- **Books API** - Full CRUD operations with advanced search and filtering
- **Authors API** - Manage authors with book count tracking
- **Categories API** - Organize books by categories
- **Book Issues API** - Track book borrowing and returns

### HTTP Methods Supported
- ✅ **GET** - Retrieve data (list and detail views)
- ✅ **POST** - Create new records
- ✅ **PUT** - Update entire records
- ✅ **PATCH** - Partial updates
- ✅ **DELETE** - Delete records
- ✅ **Custom Actions** - Available, borrow, return, overdue tracking

### Web Interface
- 🏠 **Home Page** - Featured books showcase with modern gradient design
- 📖 **Books Browse Page** - Advanced filtering and search with sidebar
- 🎨 **Professional UI** - Beautiful gradient design with responsive layout
- 📱 **Mobile Responsive** - Works perfectly on all devices

### Database Models
1. **Author** - Author information with email and biography
2. **Category** - Book categories for organization
3. **Book** - Complete book information with status tracking
4. **BookIssue** - Track book borrowing, due dates, and fines

---

## 🚀 Installation & Setup

### Prerequisites
- Python 3.8+
- pip (Python package manager)

### Virtual Environment Setup

```bash
# Create virtual environment
python -m venv ds

# Activate virtual environment
# On Windows (PowerShell):
.\ds\Scripts\Activate.ps1

# On Windows (Command Prompt):
ds\Scripts\activate.bat

# On Mac/Linux:
source ds/bin/activate
```

### Install Dependencies

```bash
pip install django==6.0.5
pip install djangorestframework==3.17.1
```

### Database Migrations

```bash
# Create migrations
python manage.py makemigrations

# Apply migrations
python manage.py migrate
```

### Create Superuser (Admin)

```bash
python manage.py createsuperuser
# Username: admin
# Email: admin@library.com
# Password: Admin@123
```

Or use the pre-created admin (if using populate_data.py):
- **Username:** admin
- **Email:** admin@library.com
- **Password:** Admin@123

### Populate Sample Data

```bash
python manage.py shell
exec(open('populate_data.py').read())
```

Or directly:
```bash
python populate_data.py
```

This will create:
- 10 Sample Authors (J.K. Rowling, George R.R. Martin, Stephen King, etc.)
- 6 Categories (Fiction, Science, History, Technology, Self-Help, Mystery)
- 12 Sample Books with complete details

---

## ⚡ Running the Application

```bash
# Activate virtual environment
.\ds\Scripts\Activate.ps1

# Start development server
python manage.py runserver
```

The application will be available at: **http://127.0.0.1:8000/**

---

## 🔗 API Endpoints

### Books API
```
GET    /api/books/                    - List all books (paginated)
GET    /api/books/{id}/               - Get book details
POST   /api/books/                    - Create new book
PUT    /api/books/{id}/               - Update entire book
PATCH  /api/books/{id}/               - Partial update book
DELETE /api/books/{id}/               - Delete book

GET    /api/books/available/          - List available books only
POST   /api/books/{id}/borrow/        - Borrow a book
POST   /api/books/{id}/return_book/   - Return a book
GET    /api/books/search/             - Advanced search (q=query)
```

### Authors API
```
GET    /api/authors/                  - List all authors
GET    /api/authors/{id}/             - Get author details
POST   /api/authors/                  - Create new author
PUT    /api/authors/{id}/             - Update entire author
PATCH  /api/authors/{id}/             - Partial update author
DELETE /api/authors/{id}/             - Delete author
GET    /api/authors/{id}/books/       - Get all books by author
```

### Categories API
```
GET    /api/categories/               - List all categories
GET    /api/categories/{id}/          - Get category details
POST   /api/categories/               - Create new category
PUT    /api/categories/{id}/          - Update entire category
PATCH  /api/categories/{id}/          - Partial update category
DELETE /api/categories/{id}/          - Delete category
GET    /api/categories/{id}/books/    - Get all books in category
```

### Book Issues API
```
GET    /api/issues/                   - List all book issues
GET    /api/issues/{id}/              - Get issue details
POST   /api/issues/                   - Create new issue
PUT    /api/issues/{id}/              - Update entire issue
PATCH  /api/issues/{id}/              - Partial update issue
DELETE /api/issues/{id}/              - Delete issue
GET    /api/issues/overdue/           - Get all overdue books
POST   /api/issues/{id}/return_issue/ - Return a book with fine calculation
```

---

## 🌐 Web Pages

### Home Page
- **URL:** `/` or `/admin/`
- **Features:**
  - Featured books carousel
  - Modern gradient background
  - Quick search functionality
  - Navigation to all books

### Books Browse Page
- **URL:** `/library/`
- **Features:**
  - Advanced search by title, ISBN, author
  - Filter by category and status
  - Sort functionality
  - Pagination (10 books per page)
  - Book cards with full details
  - Borrow and view details buttons

### Admin Dashboard
- **URL:** `/admin/`
- **Features:**
  - Manage Authors, Categories, Books, Issues
  - Advanced search and filtering
  - Bulk actions
  - Organized fieldsets

---

## 📝 API Request Examples

### Create a Book
```bash
curl -X POST http://127.0.0.1:8000/api/books/ \
  -H "Content-Type: application/json" \
  -d '{
    "title": "The Great Gatsby",
    "isbn": "9780743273565",
    "author_id": 1,
    "category_id": 1,
    "publication_date": "1925-04-10",
    "pages": 180,
    "price": 12.99,
    "quantity": 5
  }'
```

### Search Books
```bash
curl "http://127.0.0.1:8000/api/books/search/?q=Harry"
```

### Get Available Books
```bash
curl "http://127.0.0.1:8000/api/books/available/?page_size=20"
```

### Borrow a Book
```bash
curl -X POST http://127.0.0.1:8000/api/books/1/borrow/
```

### Return a Book
```bash
curl -X POST http://127.0.0.1:8000/api/books/1/return_book/
```

---

## 🗂️ Project Structure

```
library_project/
├── manage.py                 # Django management script
├── populate_data.py          # Script to populate sample data
├── library_project/          # Project settings
│   ├── settings.py          # Django settings (REST framework config)
│   ├── urls.py              # Main URL configuration
│   ├── wsgi.py              # WSGI application
│   └── asgi.py              # ASGI application
├── books/                    # Main app
│   ├── models.py            # Database models (Author, Category, Book, BookIssue)
│   ├── serializers.py       # DRF serializers
│   ├── views.py             # ViewSets and web views
│   ├── urls.py              # App URL routes
│   ├── admin.py             # Admin configuration
│   ├── apps.py              # App configuration
│   ├── migrations/          # Database migrations
│   ├── static/              # Static files (CSS, JS)
│   └── templates/
│       └── books/
│           ├── index.html          # Home page with featured books
│           └── books_list.html     # Books browse page
├── ds/                       # Virtual environment
└── db.sqlite3               # SQLite database
```

---

## 🎨 Design Features

### UI/UX
- **Gradient Design** - Modern purple-to-blue gradient aesthetic
- **Responsive Layout** - Works on desktop, tablet, and mobile
- **Smooth Animations** - Hover effects and transitions
- **Professional Cards** - Well-organized book information display
- **Advanced Filters** - Sidebar with multiple filter options
- **Search & Sort** - Real-time search and sorting capabilities

### Frontend Technologies
- **HTML5** - Semantic markup
- **CSS3** - Advanced styling with gradients, flexbox, grid
- **Vanilla JavaScript** - Async/await for API calls
- **Fetch API** - Modern client-side HTTP requests

### Backend Technologies
- **Django 6.0.5** - Web framework
- **Django REST Framework 3.17.1** - API development
- **SQLite** - Database (can upgrade to PostgreSQL)
- **Python 3.8+** - Programming language

---

## 📊 Database Schema

### Author Model
- `id` - Primary key
- `name` - Author name (unique)
- `email` - Email address
- `bio` - Biography
- `birth_date` - Date of birth
- `created_at` - Creation timestamp
- `updated_at` - Last update timestamp

### Category Model
- `id` - Primary key
- `name` - Category name (unique)
- `description` - Category description
- `created_at` - Creation timestamp
- `updated_at` - Last update timestamp

### Book Model
- `id` - Primary key
- `title` - Book title
- `author` - Foreign key to Author
- `category` - Foreign key to Category
- `isbn` - ISBN (unique)
- `description` - Book description
- `publication_date` - Publication date
- `pages` - Number of pages
- `language` - Language of the book
- `status` - Book status (available, borrowed, reserved, damaged)
- `quantity` - Total copies
- `available_quantity` - Available copies
- `price` - Book price
- `created_at` - Creation timestamp
- `updated_at` - Last update timestamp

### BookIssue Model
- `id` - Primary key
- `book` - Foreign key to Book
- `member_name` - Borrower name
- `member_email` - Borrower email
- `issue_date` - When book was borrowed
- `due_date` - Return due date
- `return_date` - Actual return date
- `fine` - Late return fine

---

## 🔐 Admin Credentials

- **URL:** http://127.0.0.1:8000/admin/
- **Username:** admin
- **Email:** admin@library.com
- **Password:** Admin@123

---

## 🛠️ Configuration

### REST Framework Settings
The project includes DRF configuration in `settings.py`:

```python
REST_FRAMEWORK = {
    'DEFAULT_PAGINATION_CLASS': 'rest_framework.pagination.PageNumberPagination',
    'PAGE_SIZE': 10,
    'DEFAULT_FILTER_BACKENDS': [
        'rest_framework.filters.SearchFilter',
        'rest_framework.filters.OrderingFilter',
    ],
}
```

### Installed Apps
- `rest_framework` - API framework
- `books` - Main application

---

## 📱 Pagination

All list endpoints support pagination:
- **Default:** 10 items per page
- **Parameter:** `?page_size=20` to change size
- **Navigation:** Use `?page=2` to go to page 2

---

## 🔍 Filtering & Search

### Search Parameters
- Books: Search by title, ISBN, author name, category
- Authors: Search by name or email
- Issues: Search by member name, email, book title

Example:
```
GET /api/books/?search=harry&ordering=-created_at&page_size=20
```

---

## 🚧 Future Enhancements

- User authentication and permissions
- Book reservations system
- Member management
- Fine calculation and payment tracking
- Book recommendations
- Review and rating system
- Email notifications for due dates
- Advanced reporting and analytics
- Mobile app
- Barcode/QR code scanning

---

## 📞 Support

For issues or questions:
1. Check the API documentation above
2. Review the admin panel at `/admin/`
3. Examine the code in the `books/` directory

---

## 📄 License

This project is open source and available for educational purposes.

---

## ✨ Summary of Implementation

✅ **All HTTP Methods Implemented**
- GET, POST, PUT, PATCH, DELETE for all resources

✅ **REST API with Django REST Framework**
- Serializers with nested relationships
- ViewSets for automatic CRUD operations
- Custom actions for advanced operations

✅ **Professional Web Interface**
- Home page with featured books
- Books listing with advanced search and filtering
- Internal CSS and JavaScript (no external frameworks)
- Beautiful gradient design
- Responsive layout

✅ **Database with Models**
- Author model with relationships
- Category model for organization
- Book model with status tracking
- BookIssue model for tracking borrowing

✅ **Admin Interface**
- Full Django admin integration
- Organized fieldsets for each model
- Search and filtering capabilities
- Custom display fields

✅ **Sample Data**
- 10 authors
- 6 categories
- 12 books with complete information

✅ **Superuser Creation**
- Admin account: admin / Admin@123
- Full access to all operations

Enjoy your Library Management System! 📚
