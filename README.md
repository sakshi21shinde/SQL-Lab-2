# SQL Lab – Foreign Key and ADD CONSTRAINT

## 1. Overview

This lab demonstrates how to establish a relationship between tables in a Bank Database using a Foreign Key constraint in MySQL. It focuses on using the `ALTER TABLE` and `ADD CONSTRAINT` statements to add a Foreign Key to an existing table.

## 2. Objective

- Understand the concept of a Foreign Key.
- Learn how to add a Foreign Key to an existing table.
- Establish a relationship between the Customer and Loan tables.
- Maintain referential integrity in the database.

## 3. Tools Used

- MySQL
- MySQL Workbench
- SQL

## 4. Tables Used

- **customer:** Stores customer details such as customer ID, name, email, and phone number.
- **Loan:** Stores loan details such as loan ID, loan amount, interest rate, start date, and end date.

## 5. SQL Implementation

### Step 1: Add Customer ID to the Loan Table

```sql
ALTER TABLE Loan
ADD COLUMN Customer_id INT;
```

This column stores the ID of the customer associated with each loan.

### Step 2: Add a Foreign Key Constraint

```sql
ALTER TABLE Loan
ADD CONSTRAINT fk_loan_customer
FOREIGN KEY (Customer_id)
REFERENCES customer(Customer_id);
```

**Explanation:**
- `ALTER TABLE Loan` specifies the table to modify.
- `ADD CONSTRAINT fk_loan_customer` assigns a name to the Foreign Key constraint.
- `FOREIGN KEY (Customer_id)` specifies the column that references another table.
- `REFERENCES customer(Customer_id)` identifies the referenced column in the customer table.

### Step 3: Verify the Foreign Key

```sql
SHOW CREATE TABLE Loan;
```

This command displays the Loan table definition, including the Foreign Key constraint.

## 6. How the Foreign Key Works

The Foreign Key connects the `Loan` table with the `customer` table through `Customer_id`.

For example, if customer ID `1` exists in the customer table, a loan can reference customer ID `1`.

If a loan references a customer ID that does not exist in the customer table, MySQL rejects the insertion.

This helps maintain referential integrity and prevents invalid customer references.

## 7. Key Learnings

- A Foreign Key creates a relationship between two tables.
- `ALTER TABLE` modifies an existing table.
- `ADD CONSTRAINT` adds a Foreign Key rule.
- The referenced column must be a Primary Key or a suitable Unique Key.
- Foreign Keys help maintain referential integrity.

## 8. Conclusion

This lab provides practical experience in adding a Foreign Key constraint to an existing table using MySQL. It demonstrates how the Customer and Loan tables can be linked to maintain valid relationships between customer records and their loans.

## Author

Sakshi Shinde
