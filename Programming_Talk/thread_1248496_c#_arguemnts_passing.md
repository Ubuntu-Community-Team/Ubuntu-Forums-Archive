---
title: "c# arguemnts passing?"
date: 2009-08-24
forum: Programming Talk
---

### Post by abhilashm86 on 2009-08-24
in c# or in general any language,
if we initialize variables in main function and pass arguements to a method( pass by reference), what is benefit and advantage?

what is difference between the above method and genral way where in fuction we initialize parameters, like this
```

class pass {
void initialize(double a1,double a2) {
a1=12.334;
a2=34.233;
//
//
}

```

---

### Post by WitchCraft on 2009-08-24
> **abhilashm86 said:**
> in c# or in general any language,
if we initialize variables in main function and pass arguements to a method( pass by reference), what is benefit and advantage?

what is difference between the above method and genral way where in fuction we initialize parameters, like this
```

class pass {
void initialize(double a1,double a2) {
a1=12.334;
a2=34.233;
//
//
}

```

We? Is this homework ?

The difference is that by passing by reference the values of the variables passed to a function will also be altered in your main program if the function alters their value.



consider

```

sub add(byref x as integer, byval y as integer)
x +=2
y +=2
end sub

```

If you call them from your main program:
```

sub main()
dim x as integer = 5
dim y as integer = 5
add(x,y)
console.writeline("X = {0}, Y = {1}", x,y)
end sub

```

Then the output will be:

X = 7, y = 5

---

### Post by abhilashm86 on 2009-08-25
> **WitchCraft said:**
> We? Is this homework ?

The difference is that by passing by reference the values of the variables passed to a function will also be altered in your main program if the function alters their value.



consider

```

sub add(byref x as integer, byval y as integer)
x +=2
y +=2
end sub

```

If you call them from your main program:
```

sub main()
dim x as integer = 5
dim y as integer = 5
add(x,y)
console.writeline("X = {0}, Y = {1}", x,y)
end sub

```

Then the output will be:

X = 7, y = 5

yup, it was asked in class, i know the concept, i wanted to know what is advantage on initializing data members in main function, then send it to methods, this is actually with reference to c#, keywords out and ref i think............

---

### Post by WitchCraft on 2009-08-25
> **abhilashm86 said:**
> yup, it was asked in class, i know the concept, i wanted to know what is advantage on initializing data members in main function, then send it to methods, this is actually with reference to c#, keywords out and ref i think............

Simple: The advantage is you can have a value back, but don't have to have all the code in your main function.

For example in an asp.net application:
Consider Gridview1_Sorting the main method.
```

    Protected Sub Gridview1_Sorting(ByVal sender As Object, ByVal e As GridViewSortEventArgs)
        MyName.DBcmds.GetDataSet("SELECT * FROM T_DMS_Process ORDER BY " + e.SortExpression.ToString + " ASC", dsPendingProcesses)
        If dsPendingProcesses.Tables.Count > 0 Then
            GridView1.DataSource = dsPendingProcesses.Tables(0)
            ' Need to rebind or page does not change 
            GridView1.DataBind()
            GridView1.Visible = True
            dsPendingProcesses.Dispose()
            dsPendingProcesses = Nothing
        Else
            MyName.Debug.MsgBox("Fehler beim Sortieren von T_DMS_Process nach " + e.SortExpression.ToString + ".")
        End If

    End Sub

```

```

        Public Shared Sub GetDataSet(ByRef strSQL As String, ByRef dsDataFromTable As Data.DataSet, Optional ByRef strTableName As String = "ThisTable")
            Dim sqlConnection As Data.SqlClient.SqlConnection = Nothing
            Dim daQueryTable As Data.SqlClient.SqlDataAdapter = Nothing
            Try
                sqlConnection = New Data.SqlClient.SqlConnection(GetConnectionString())
                daQueryTable = New Data.SqlClient.SqlDataAdapter(strSQL, sqlConnection)
                dsDataFromTable = New Data.DataSet(strTableName)

                System.Threading.Monitor.Enter(sqlConnection)
                sqlConnection.Open()
                daQueryTable.Fill(dsDataFromTable)
                daQueryTable.Dispose()
            Catch ex As Exception
                MyName.Debug.MsgBox(String.Format("Exception executing GetDataSet: {0}", ex.Message.ToString() + vbCrLf + "strSQL=" + strSQL))
            Finally
                sqlConnection.Close()
                System.Threading.Monitor.Exit(sqlConnection)
                daQueryTable.Dispose()
                daQueryTable = Nothing
                sqlConnection.Dispose()
                sqlConnection = Nothing
            End Try
        End Sub ' GetDataSet

```

Now, you can simply query a SQL database from the main method, don't have to have the code in the main routine, and get the dataset back.

Now you could do that in a function, but then you can only return one return value. Byref allows for several returnable values.

Also, if you pass a variable (for example a custom class) byref, then the application doesn't have to copy all the contents of that class, it just passes a pointer to the class in the main method. That's a lot faster (depending on your class).

If you need the C# sourcecode, then use the codeconverter at [http://www.developerfusion.com/tools/convert/csharp-to-vb/](http://www.developerfusion.com/tools/convert/csharp-to-vb/)
which converts C# to VB.net and vice-versa

```

protected void Gridview1_Sorting(object sender, GridViewSortEventArgs e)
{
    MyName.DBcmds.GetDataSet("SELECT * FROM T_DMS_Process ORDER BY " + e.SortExpression.ToString + " ASC", dsPendingProcesses);
    if (dsPendingProcesses.Tables.Count > 0) {
        GridView1.DataSource = dsPendingProcesses.Tables(0);
        // Need to rebind or page does not change 
        GridView1.DataBind();
        GridView1.Visible = true;
        dsPendingProcesses.Dispose();
        dsPendingProcesses = null;
    }
    else {
        MyName.Debug.MsgBox("Fehler beim Sortieren von T_DMS_Process nach " + e.SortExpression.ToString + ".");
        
    }
}

```

```

public static void GetDataSet(ref string strSQL, ref Data.DataSet dsDataFromTable, [System.Runtime.InteropServices.OptionalAttribute, System.Runtime.InteropServices.DefaultParameterValueAttribute("ThisTable")] ref // ERROR: Optional parameters aren't supported in C# string strTableName)
{
    Data.SqlClient.SqlConnection sqlConnection = null;
    Data.SqlClient.SqlDataAdapter daQueryTable = null;
    try {
        sqlConnection = new Data.SqlClient.SqlConnection(GetConnectionString());
        daQueryTable = new Data.SqlClient.SqlDataAdapter(strSQL, sqlConnection);
        dsDataFromTable = new Data.DataSet(strTableName);
        
        System.Threading.Monitor.Enter(sqlConnection);
        sqlConnection.Open();
        daQueryTable.Fill(dsDataFromTable);
        daQueryTable.Dispose();
    }
    catch (Exception ex) {
        MyName.Debug.MsgBox(string.Format("Exception executing GetDataSet: {0}", ex.Message.ToString() + Constants.vbCrLf + "strSQL=" + strSQL));
    }
    finally {
        sqlConnection.Close();
        System.Threading.Monitor.Exit(sqlConnection);
        daQueryTable.Dispose();
        daQueryTable = null;
        sqlConnection.Dispose();
        sqlConnection = null;
    }
}
// GetDataSet

```

---

