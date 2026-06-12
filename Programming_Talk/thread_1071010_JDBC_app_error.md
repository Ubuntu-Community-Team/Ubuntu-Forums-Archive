---
title: "JDBC app error"
date: 2009-02-15
forum: Programming Talk
---

### Post by andrew222 on 2009-02-15
I just installer Oracle and put this program on Eclipse and got an error  at this line (stating "oracle can not be resolved to a type"):

```
DriverManager.registerDriver (new oracle.jdbc.driver.OracleDriver());
```



Here is the entire program....


```
import java.sql.*;
class Conn {
  public static void main (String args []) throws SQLException
  {
        DriverManager.registerDriver (new oracle.jdbc.driver.OracleDriver());

        Connection conn = DriverManager.getConnection
            ("jdbc:oracle:thin:@localhost:1521:orcl", "scott", "tiger");
                            // @machineName:port:SID,   userid,  password

        Statement stmt = conn.createStatement();
        ResultSet rset = stmt.executeQuery("select BANNER from SYS.V_$VERSION");
        while (rset.next())
              System.out.println (rset.getString(1));   // Print col 1
        stmt.close();
  }
}
```

I would like to write a JDBC program using Oracle but I am getting errors on every program that I take from a tutorial and put onto Eclipse.  Any advice is welcome....

---

### Post by cl333r on 2009-02-15
Perhaps instead of DriverManager.register.. you should use 
> Class.forName("oracle.jdbc.driver.OracleDriver");

[http://www.eecs.umich.edu/~ppadala/pubs/oracle/jdbc.htm](http://www.eecs.umich.edu/~ppadala/pubs/oracle/jdbc.htm)

PS: Make sure you got the driver library in the right place and if not, pointing the class path to it.

---

