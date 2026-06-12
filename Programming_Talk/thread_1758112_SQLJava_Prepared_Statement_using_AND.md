---
title: "SQL/Java: Prepared Statement using AND?"
date: 2011-05-14
forum: Programming Talk
---

### Post by fallenshadow on 2011-05-14
Does anyone know how to do a prepared statement using AND? (with Java in mind) is it different to a normal SQL statement?

I made an attempt but this error shows up:

> The column position '2' is out of range.  The number of columns for this ResultSet is '1'.

---

### Post by PaulM1985 on 2011-05-14
Could you perhaps provide the code that you are running and the column names of the tables that the code is to be executed on?

Paul

EDIT: Given your error message it sounds like your SQL statement is only returning one column, where you are expecting more.  Does you statement look something like:

```

SELECT a_column
FROM [some statements]

```

in which case only the column "a_column" is being returned.

---

### Post by fallenshadow on 2011-05-14
Ok forget about using AND... I don't think I need it... however I have stripped my code back to basics because all I want to do is get the delete working.

[PHP] String name = procedureNameField.getText();
     
     String query = "SELECT PROCEDURENAME FROM PROCEDURES WHERE PROCEDUREPATIENT = (?)";
        
     String delete = "DELETE FROM PROCEDURES WHERE PROCEDUREPATIENT = (?)";
     
        Connection connection = null; // manages connection
        
        PreparedStatement statement = null; // query statement
        
        ResultSet resultSet = null; // manages results
        
        try
        {
            // establish connection to database
         connection = DriverManager.getConnection(DATABASE_URL);

            infoTextArea2.setText("Connection Established\n");
 
            statement = connection.prepareStatement(query);
            statement.setString(1, name);
  
            String nameSearch = new String();
            
            resultSet = statement.executeQuery();
             while (resultSet.next())
             
             nameSearch=resultSet.getString(1);
            
            statement = connection.prepareStatement(delete);
            statement.setString(1, nameSearch);
            statement.execute();
            
            }
            
            statement.close();
            connection.close();         
        }
            
        catch (SQLException sqlExcept)
        {
            sqlExcept.printStackTrace();
        }
        
         catch ( Exception exception )//for closing
            {
                exception.printStackTrace();
            } // end catch[/PHP]

Does anybody see anything wrong with this?... in particular the delete is the part not working. However the select to search it, is!

---

### Post by r-senior on 2011-05-14
The execute() method is for running stored procedures, executeUpdate() is what you should use for insert/update/delete. Confusing I know, and a common mistake.

The other thing is that your connection.close() is inside your try block, after method calls that could throw exceptions. Your connection will be left open if an exception is thrown. You should use a finally block, e.g.

```

...
finally {
    try {
        statement.close();
        connection.close();  
    }
    catch (Exception e) {}
}

```

Having to use another try block is messy but that's what you get with JDBC and its checked exceptions. (Another good reason for using Spring JDBC templates).

---

### Post by fallenshadow on 2011-05-14
I had hoped changing to executeUpdate would sort this but sadly it has not. I changed my connection.close() but this had no effect either. :(

I think Java just hates me! :mad:

---

### Post by PaulM1985 on 2011-05-14
Are you still getting the same error message from earlier?  Did that problem ever get resolved?

If not, it could be down to your getString method.  Your query gets a result set with one column and you are calling getString on the column which is 1.  Should you be using getString(0) to get from your first column?

Paul

---

### Post by r-senior on 2011-05-14
> **PaulM1985 said:**
> If not, it could be down to your getString method.  Your query gets a result set with one column and you are calling getString on the column which is 1.  Should you be using getString(0) to get from your first column?
The columns on the ResultSet are indexed from 1. That's caught me out a few times in the opposite direction, i.e. putting 0 instead of 1.

Here's another idea though - shouldn't your parameters be in single quotes, given that you are querying for a string in SQL?

---

### Post by fallenshadow on 2011-05-14
No they should not be in single quotes... I have a very similar piece of code doing this but it actually works for the delete. Im not really doing anything different here.

> Are you still getting the same error message from earlier? Did that problem ever get resolved?

Yeah that error has gone away since I removed some things to simplify this code.

---

### Post by Some Penguin on 2011-05-14
> **fallenshadow said:**
> Ok forget about using AND... I don't think I need it... however I have stripped my code back to basics because all I want to do is get the delete working.

[PHP] String name = procedureNameField.getText();
     
     String query = "SELECT PROCEDURENAME FROM PROCEDURES WHERE PROCEDUREPATIENT = (?)";
[/PHP]

Minor note:   not clear that the parenthesis are necessary.

[PHP]    
     String delete = "DELETE FROM PROCEDURES WHERE PROCEDUREPATIENT = (?)";
     
        Connection connection = null; // manages connection
        
        PreparedStatement statement = null; // query statement
[/PHP]

The comment is misleading, because you also reuse the same variable for the delete statement... which does mean that the PS associated with the query doesn't get closed until the connection itself is closed.

[PHP]        
        ResultSet resultSet = null; // manages results
        
        try
        {
            // establish connection to database
         connection = DriverManager.getConnection(DATABASE_URL);

            infoTextArea2.setText("Connection Established\n");
 
            statement = connection.prepareStatement(query);
            statement.setString(1, name);
  
            String nameSearch = new String();
            
            resultSet = statement.executeQuery();
             while (resultSet.next())
             
             nameSearch=resultSet.getString(1);
            
            statement = connection.prepareStatement(delete);
            statement.setString(1, nameSearch);
            statement.execute();
            
            }
            
            statement.close();
            connection.close();         
[/PHP]

Close statements should generally be in a finally() block. What if the statement.execute() throws an SQLException, for instance?  

[PHP]
        }
            
        catch (SQLException sqlExcept)
        {
            sqlExcept.printStackTrace();
        }
        
         catch ( Exception exception )//for closing
[/PHP]

Ewwww.  Generic catches are very, very bad.  What if you receive a NullPointerException or the like?  You throw it away without changing behavior and without propagating it upwards?

As a practical matter, some JDBC drivers will wrap all sorts of exceptions and even errors inside SQLExceptions.  Checking the 'cause' chain can be rather important.  In particular, I've seen InterruptedException and OutOfMemoryError wrapped that way.  

[PHP]
            {
                exception.printStackTrace();
            } // end catch[/PHP]

Does anybody see anything wrong with this?... in particular the delete is the part not working. However the select to search it, is!

Sure.  You're selecting PROCEDURENAME, and then your delete is looking for that PROCEDURENAME in the PROCEDUREPATIENT column.

---

### Post by fallenshadow on 2011-05-14
Sorry... such an idiotic mistake. Im just tired and Java is screwing with my brain. I did too much Java in one day! 

Anyway this is solved now, thanks for the much needed help!

---

