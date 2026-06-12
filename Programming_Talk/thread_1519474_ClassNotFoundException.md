---
title: "ClassNotFoundException"
date: 2010-06-28
forum: Programming Talk
---

### Post by MughalShahzad on 2010-06-28
```

    public static void main(String[] args) {      
    System.out.println("Inserting values in Mysql database table!");
    Connection con = null;
    String url = "jdbc:mysql://localhost:3306/";
    String db = "myDB";
    String driver = "com.mysql.jdbc.Driver";
    try{
      Class.forName(driver);
      con = DriverManager.getConnection(url+db,"root","root");
      try{
        Statement st = con.createStatement();
        int val = st.executeUpdate("INSERT INTO employees VALUES("+100+","+"'Shahzad', "+"'Mahmood'"+")");
        System.out.println("1 row affected");
      }
      catch (SQLException s){
        System.out.println("SQL statement is not executed!");
      }
    }
    catch (Exception e){
      e.printStackTrace();
    }
  }
}

```

for the above code following error occurs

```
java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
```

how to solve this kindly suggest me

Regards
Shahzad

---

### Post by Zugzwang on 2010-06-28
You need to put the mysql-connector jar file into the classpath. This is described in the documentation of the MySQL connector, which you are obviously trying to use. Use the forum's search function for finding details (if necessary).

---

