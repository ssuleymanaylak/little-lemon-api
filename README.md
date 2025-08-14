# 🍋 Little Lemon Restaurant API

## 📌 Introduction
This project is a fully functional REST API for the **Little Lemon Restaurant**, allowing client developers to build web and mobile applications for menu management, order processing, and user role management.

Built with **Django** and **Django REST Framework**, using **Pipenv** for dependency management.

---

## 📂 Project Structure
- **Single Django App**: `LittleLemonAPI`
- All API endpoints are implemented within this app.
- Dependencies managed with **Pipenv** (`Pipfile` & `Pipfile.lock`).
- Supports both **function-based** and **class-based** views.
- Proper **naming conventions** and **status codes** are used.

---

## 👥 User Roles
- **Manager** – Full control over menu items, orders, and group assignments.
- **Delivery Crew** – Assigned to deliver orders and update delivery status.
- **Customer** (default) – Can browse the menu, manage their cart, and place orders.

---

## 🔑 Authentication & Authorization
- Implemented using **Djoser** for user registration, login, and token generation.
- Permissions enforced according to user roles.
- Secure endpoints with proper HTTP status codes for errors.

---

## 📜 HTTP Status Codes
| Code | Meaning |
|------|---------|
| 200 | OK – Successful GET, PUT, PATCH, DELETE |
| 201 | Created – Successful POST |
| 401 | Forbidden – Authentication failed |
| 403 | Unauthorized – Authorization failed |
| 400 | Bad Request – Validation errors |
| 404 | Not Found – Resource does not exist |

---

## 🚀 API Endpoints

### **1. User Registration & Token**
| Endpoint | Role | Method | Purpose |
|----------|------|--------|---------|
| `/api/users` | None | POST | Register a new user |
| `/api/users/me/` | Authenticated | GET | Get current user |
| `/token/login/` | None | POST | Generate auth token |

---

### **2. Menu Items**
| Endpoint | Role | Method | Purpose |
|----------|------|--------|---------|
| `/api/menu-items` | Customer, Delivery Crew | GET | List menu items |
| `/api/menu-items/{id}` | Customer, Delivery Crew | GET | View single item |
| `/api/menu-items` | Manager | POST | Add new menu item |
| `/api/menu-items/{id}` | Manager | PUT/PATCH | Update menu item |
| `/api/menu-items/{id}` | Manager | DELETE | Delete menu item |

---

### **3. User Group Management**
| Endpoint | Role | Method | Purpose |
|----------|------|--------|---------|
| `/api/groups/manager/users` | Manager | GET | List managers |
| `/api/groups/manager/users` | Manager | POST | Add user to manager group |
| `/api/groups/manager/users/{userId}` | Manager | DELETE | Remove user from manager group |
| `/api/groups/delivery-crew/users` | Manager | GET | List delivery crew |
| `/api/groups/delivery-crew/users` | Manager | POST | Add user to delivery crew group |
| `/api/groups/delivery-crew/users/{userId}` | Manager | DELETE | Remove user from delivery crew group |

---

### **4. Cart Management**
| Endpoint | Role | Method | Purpose |
|----------|------|--------|---------|
| `/api/cart/menu-items` | Customer | GET | View cart |
| `/api/cart/menu-items` | Customer | POST | Add item to cart |
| `/api/cart/menu-items` | Customer | DELETE | Clear cart |

---

### **5. Orders**
| Endpoint | Role | Method | Purpose |
|----------|------|--------|---------|
| `/api/orders` | Customer | GET | List user’s orders |
| `/api/orders` | Customer | POST | Create new order from cart |
| `/api/orders/{id}` | Customer | GET | View order details |
| `/api/orders` | Manager | GET | List all orders |
| `/api/orders/{id}` | Manager | PUT/PATCH | Assign delivery crew / update status |
| `/api/orders/{id}` | Manager | DELETE | Delete order |
| `/api/orders` | Delivery Crew | GET | List assigned orders |
| `/api/orders/{id}` | Delivery Crew | PATCH | Update delivery status |

---

## 🔍 Additional Features
- **Filtering, Pagination, Sorting** for `/api/menu-items` and `/api/orders`
- **Throttling** for authenticated and anonymous users
- Proper **error handling** with descriptive messages

---

## 🛠️ Installation & Setup

### 1. Clone the repository
```bash
git clone https://github.com/USERNAME/little-lemon-api.git
cd little-lemon-api
pipenv install
pipenv run python manage.py migrate
pipenv run python manage.py createsuperuser
pipenv run python manage.py runserver
