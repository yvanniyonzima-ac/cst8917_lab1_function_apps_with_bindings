# Azure Functions with SQL Output Binding – Python Lab

This project demonstrates an Azure Functions written in Python using the **isolated worker model** and an Azure SQL Output Binding.

---

## Tutorials Followed

- [Azure Function Quickstart: HTTP Trigger](https://learn.microsoft.com/en-us/azure/azure-functions/create-first-function-vs-code-csharp)
- [Azure SQL Output Binding Quickstart](https://learn.microsoft.com/en-us/azure/azure-functions/functions-add-output-binding-azure-sql-vs-code?pivots=programming-language-python)

---

## How to setup the app

### Prerequisites

- Visual Studio Code + Azure Extension
- An active Azure subscription

1. **Clone the Repository**
```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
cd YOUR_REPO_NAME
```

2. **Create and Activate a Virtual Environment**
```bash
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
```

3. **Create and deploy the function app**

Follow the instructions on Microsofts Quickstart guide to creating an Azure function for:

- [Creating a Function App in Azure](https://learn.microsoft.com/en-us/azure/azure-functions/create-first-function-vs-code-csharp#publish-the-project-to-azure)
- [Deploy the project to Azure](https://learn.microsoft.com/en-us/azure/azure-functions/create-first-function-vs-code-csharp#deploy-the-project-to-azure)

4. **Set Up an Azure SQL Database and Table**

Follow the [Azure SQL Database create quickstart](https://learn.microsoft.com/en-us/azure/azure-sql/database/single-database-create-quickstart) to create a serverless Azure SQL Database. The database can be empty or created from the sample dataset AdventureWorksLT.

5. **Connect and Create the ToDo Table**

Use the SQL Querry Editor to connect to the database and run:

```sql
CREATE TABLE ToDo (
    Id UNIQUEIDENTIFIER PRIMARY KEY,
    title NVARCHAR(200),
    completed BIT,
    url NVARCHAR(200)
);
```
6. **Update the function app settings**

1. Get the SQL Connection String

- In the Azure Portal, navigate to your Azure SQL Database.

- Under Settings, select Connection strings.

- Copy the ADO.NET connection string for SQL authentication.

- Paste it into a temporary document for editing.

2. Edit the Connection String

- In your temporary document, locate Password=your_password in the connection string.

- Replace your_password with the actual password you used when creating your Azure SQL Database.

- Copy the updated connection string.

3. Add the Connection String to Azure Function App

-  In VS Code Press Ctrl+Shift+P (or Cmd+Shift+P on Mac) to open the Command Palette.

- Search for and run ```Azure Functions: Add New Setting...```

- Select the function app you created.

- When prompted:

  - Enter new app setting name: SqlConnectionString

  - Enter value for "SqlConnectionString": Paste the updated connection string.

---

## Running the Function

1. Press F1 to display the command palette, then search for and run the command Azure Functions:Execute Function Now.... If prompted, select your subscription.

2. Select your new function app resource and HttpExample as your function.

3. In Enter request body type { "name": "Azure" }, then press Enter to send this request message to your function.

4. When the function executes in Azure, the response is displayed in the notification area. Expand the notification to review the full response.

5. In the SQL service in Azure, query the ToDo table to view the new data written to the table via the function app.

---

## 📹 Demo Video

Watch a 5-minute walkthrough and demo here:  
[YouTube Video Link](https://youtu.be/Lv57jBgW7uY)
