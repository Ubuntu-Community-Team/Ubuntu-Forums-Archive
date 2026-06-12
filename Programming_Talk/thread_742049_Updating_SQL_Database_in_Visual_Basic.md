---
title: "Updating SQL Database in Visual Basic"
date: 2008-04-01
forum: Programming Talk
---

### Post by prismpirate on 2008-04-01
I'm currently using Microsoft Visual Basic Express 2008, and want to create a high score table vial MySQL.

If I am to update, lets say the first entry in the database, how would I go around doing it in code?

Take name as the name &
Take cheesesize as the score.

The table has two columns, the first is named, "Name", while the second is named "Score".

All this is done locally.

---

### Post by pedro_orange on 2008-04-01
Presumably you'd do the same as you do in any .NET 

Include the SQL libraries.

```

Imports System.Data.SqlClient

```

Make yourself a connection string:

```

Public Const constDSN As String = "Password=pw;Persist Security Info=True;User ID=usr;Data Source=dsn"

```

Then create your objects to interact with the database

```

Dim myConnection As New SqlClient.SqlConnection
Dim myCommand As New SqlClient.SqlCommand
Dim dr As SqlClient.SqlDataReader
Dim sConnect As String
Dim sSQL As String

```

Open your connection, build your query, run it. Easy.

(This looks so cool in Orange.)

---

