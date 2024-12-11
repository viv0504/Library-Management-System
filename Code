CREATE DATABASE BookstoreDB;
USE BookstoreDB;

-- Table: Books
CREATE TABLE Books (
    BookID INT AUTO_INCREMENT PRIMARY KEY,
    Title VARCHAR(255) NOT NULL,
    Author VARCHAR(255) NOT NULL,
    Genre VARCHAR(100),
    ISBN VARCHAR(20) UNIQUE,
    Price DECIMAL(10, 2) NOT NULL,
    StockQuantity INT NOT NULL,
    PublishedDate DATE
);

-- Table: Users
CREATE TABLE Users (
    UserID INT AUTO_INCREMENT PRIMARY KEY,
    FirstName VARCHAR(100) NOT NULL,
    LastName VARCHAR(100),
    Email VARCHAR(255) UNIQUE NOT NULL,
    PasswordHash VARCHAR(255) NOT NULL,
    PhoneNumber VARCHAR(15),
    Address TEXT,
    DateCreated DATETIME DEFAULT CURRENT_TIMESTAMP
);

-- Table: Orders
CREATE TABLE Orders (
    OrderID INT AUTO_INCREMENT PRIMARY KEY,
    UserID INT NOT NULL,
    OrderDate DATETIME DEFAULT CURRENT_TIMESTAMP,
    OrderStatus ENUM('Pending', 'Shipped', 'Delivered', 'Cancelled') NOT NULL,
    TotalAmount DECIMAL(10, 2) NOT NULL,
    PaymentMethod ENUM('CreditCard', 'DebitCard', 'PayPal', 'CashOnDelivery'),
    FOREIGN KEY (UserID) REFERENCES Users(UserID)
);

-- Table: OrderDetails
CREATE TABLE OrderDetails (
    OrderDetailID INT AUTO_INCREMENT PRIMARY KEY,
    OrderID INT NOT NULL,
    BookID INT NOT NULL,
    Quantity INT NOT NULL,
    UnitPrice DECIMAL(10, 2) NOT NULL,
    Subtotal DECIMAL(10, 2) GENERATED ALWAYS AS (Quantity * UnitPrice) STORED,
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID),
    FOREIGN KEY (BookID) REFERENCES Books(BookID)
);

-- Table: Reviews
CREATE TABLE Reviews (
    ReviewID INT AUTO_INCREMENT PRIMARY KEY,
    BookID INT NOT NULL,
    UserID INT NOT NULL,
    Rating TINYINT CHECK (Rating BETWEEN 1 AND 5),
    ReviewText TEXT,
    ReviewDate DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (BookID) REFERENCES Books(BookID),
    FOREIGN KEY (UserID) REFERENCES Users(UserID)
);
