---
title: "How to connect Borland InterBase 7.1 and Java"
date: 2009-07-25
forum: Programming Talk
---

### Post by sthiranga on 2009-07-25
I want to connect interbase 7.1 database using java.I found some code from internet
and try run it.But it's not work.My code is like this

```


try{
        Class.forName("org.firebirdsql.jdbc.FBDriver").newInstance();
        Connection connection = DriverManager.getConnection("jdbc:firebirdsql://localhost/C:\\My Documents\\Downloads\\TEST.GDB","SYSDBA","masterkey");
       
       }catch(Exception ex){
            ex.printStackTrace();
       }

```when i run this 
> 
org.firebirdsql.jdbc.FBSQLException: GDS Exception. 335544583. SQLDA missing or incorrect version, or incorrect number/type of variables
Reason: SQLDA missing or incorrect version, or incorrect number/type of variables
        at org.firebirdsql.jdbc.FBDataSource.getConnection(FBDataSource.java:122)
        at org.firebirdsql.jdbc.FBDriver.connect(FBDriver.java:131)

exception thrown.
I used jaybird-full-2.1.6 jar file too.
Can anyone Help me.thanks.

---

### Post by mthalis on 2009-07-30
Try running below program 

```

public class interbase {

    private static Connection getConnections() {
        Connection con = null;
        try {
            Class.forName("org.firebirdsql.jdbc.FBDriver");
        } catch (ClassNotFoundException ex) {
            Logger.getLogger(interbase.class.getName()).log(Level.SEVERE, null, ex);
        }
        try {

            con = DriverManager.getConnection("jdbc:firebirdsql:192.168.101.211/3050:c:/TEMP", "sysdba", "masterkey");


        } catch (Exception ex) {
            System.out.println(ex);
        }
        return con;
    }

    public static void main(String[] args) {

        getConnections();
    }
}

```

In order to run this program **JayBird** library should below 2.0 and must allow port **3050**

---

