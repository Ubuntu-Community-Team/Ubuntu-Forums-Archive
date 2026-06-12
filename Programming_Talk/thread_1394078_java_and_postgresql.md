---
title: "java and postgresql"
date: 2010-01-30
forum: Programming Talk
---

### Post by luftadler on 2010-01-30
Hi, 

I'm an absolute beginner in programing languages. I need to do a project for the school in java.

Problem: 

select from a list with students 

- the best student
- list students by the notes
- list students by the age

so, I've created a postgres database called students with this fields: name|age|notes
I also added JDBC driver to project (I'm using Netbeans)
using an example code i've write this code:

```

package Student;

import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;

public class Student {
    private static Object con;
    private static Object Connection;

    public static void main(String[] args)throws Exception{
        Class.forName("org.postgresql.Driver");
        Connection = con;
        DriverManager.getConnection(
                "jdbc:postgresql://127.0.0.1:5432/studenti","gisdata", "*****");
        PreparedStatement statetment = con.prepareStatement (
                "select * from studenti");
        ResultSet result = statetment.executeQuery();
        while (result.next()){
            System.out.println(result.getString(1)+" "+result.getString(2));
        }



    }

}

```first problem netBeans say that is something wrong with this row

```
  PreparedStatement statetment = con.prepareStatement (
```con.prepareStatement (cannot find symbol)

second problem is that i don't now how to go forward


Any help is appreciated.
Thank you in advance,

---

### Post by CptPicard on 2010-01-30
You seem to be a bit at loss with basic Java.

I don't understand why you have those two "Objects" con and Connection there. They are both null to begin with, and you're just setting Connection to con, which doesn't do anything.

Then you get a connection from DriverManager that you just throw away, and don't keep a reference to it anywhere.

Then you try to use prepareStatement on "con" which is an "Object", therefore, it doesn't have the method. That's where you get the compiler complaint...

I guess what you're wanting is con object of class Connection... that is "Connection con". Then, you'll want "con = DriverManager.getConnection..." and so on.

---

### Post by Some Penguin on 2010-01-31
You should probably search for a basic Java tutorial, plus one for JDBC.

JDBC, incidentally, is NOT where I would suggest that you start if you're not quite familiar with Java.  It's useful, but can provide the occasional nasty surprise (like cheerfully loading a million rows all into memory even though you were only doing forward, non-updating iteration; or leaking resources because you're not careful about closing Statements and ResultSets because you're used to finalizers taking care of it for you).

---

### Post by luftadler on 2010-01-31
So, i've made this code:


```

package Student;

import java.sql.Connection;
import java.sql.DatabaseMetaData;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.ResultSetMetaData;
import java.sql.Statement;

public class Student {

public static void main(String args[])
{
  try
  {
        Class.forName("org.postgresql.Driver");
        Connection connection = DriverManager.getConnection("jdbc:postgresql://127.0.0.1:5432/studenti","gisdata", "vasile");
        // Create a result set
        Statement stmt = connection.createStatement();
        ResultSet rs = stmt.executeQuery("SELECT * FROM studenti");


        DatabaseMetaData meta = connection.getMetaData();

        System.out.println("We are using " + meta.getDatabaseProductName());
        System.out.println("Version is " + meta.getDatabaseProductVersion() );
        // Get result set meta data
        ResultSetMetaData rsmd = rs.getMetaData();
        System.out.println("--- Structure of tables: ---");

        int numColumns = rsmd.getColumnCount();

        // Get the column names; column indices start from 1
        for (int i=1; i<numColumns+1; i++)
        {
            String columnName = rsmd.getColumnName(i);

        // Get the name of the columns table name
            String tableName = rsmd.getTableName(i);
            System.out.println("columnName "+columnName);
        }
        ResultSet srs = stmt.executeQuery(
        "SELECT name, age FROM students");
        while (srs.next()) {
        String name = srs.getString("name");
        float age = srs.getFloat("age");
        System.out.println(name + "     " + varsta);
        }
        connection.close();
    }

    catch (Exception e)
    {
    System.out.println(e);
    }
}
}

```this code works, it list the students and the age
now i must list students by age, starting from the oldest to the youngest

how i can make this possible? any ideas?

Thanks,

---

### Post by Some Penguin on 2010-01-31
Use the database to do the ordering for you.  Specifically, look up 'ORDER BY'.

---

