---
title: "err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered"
date: 2008-08-26
forum: Programming Talk
---

### Post by Milind Damle on 2008-08-26
Dear All,
I am trying to run a simple VB6 application on Ubuntu (8.04)
While setting it up, I get an error "ODBC's SQLRemoveDriverManager failed"

While running the program, I get an error :
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered


For your quick reference, the code is here :-
Public con2 As New ADODB.Connection

Public constr As String

Private Sub Form_Load()

Dim adors As New ADODB.Recordset

Dim Adosql As String

constr = "Driver=MySQL ODBC 5.1 Driver;SERVER=192.168.1.6;UID=root;PWD=amit;DATABASE=test;PORT=3306"

con2.ConnectionString = constr

Adosql = "Select * from T02"

adors.ActiveConnection = constr
 ' Code fails here.
adors.Source = Adosql

adors.Open

MsgBox "Result is " & adors(0)

End Sub



Can someone help me figure out how to overcome this problem ?
Thanks & regards,
Milind Damle.

---

### Post by Joeb454 on 2008-08-26
Moved to Programming Talk

---

### Post by Zugzwang on 2008-08-26
So did you install the MySQL ODBC driver in your WINE configuration?

---

