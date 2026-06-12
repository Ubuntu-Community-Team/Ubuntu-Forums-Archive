---
title: "Can't connect to Firebird"
date: 2016-04-06
forum: Programming Talk
---

### Post by Bolaum on 2016-04-06
Hi, I'm not sure if this is the right place for this question so if it isn't I'm sorry.

I'm new to Ubuntu and I just installed it on a computer. I installed Samba and shared the folders "/samba" and "/hd". I downloaded and installed Firebird and copied my database that I created on Windows and put it in "/samba". This is my Java code:

```
public static Connection getConnection() throws SQLException {
        Connection connection = null;
        try {
            Class.forName("org.firebirdsql.jdbc.FBDriver");
        } catch (ClassNotFoundException e) {
            throw new RuntimeException(e);
        }
        connection = DriverManager.getConnection("jdbc:firebirdsql://localhost:3050/samba/LNX.FDB", "sysdba",
                "masterkey");
        return connection;
    }
    
    public static void main(String[] args) throws SQLException {
        getConnection();
    }
```

I get this error:

```
Exception in thread "main" org.firebirdsql.jdbc.FBSQLException: GDS Exception. 335544344. I/O error during "open" operation for file "samba/LNX.FDB"
Error while trying to open file
null
    at org.firebirdsql.jdbc.FBDataSource.getConnection(FBDataSource.java:120)
    at org.firebirdsql.jdbc.AbstractDriver.connect(AbstractDriver.java:136)
    at java.sql.DriverManager.getConnection(DriverManager.java:571)
    at java.sql.DriverManager.getConnection(DriverManager.java:215)
    at br.com.ipsnet.jdbc.ConnectionFactory.getConnection(ConnectionFactory.java:16)
    at br.com.ipsnet.jdbc.ConnectionFactory.main(ConnectionFactory.java:22)
Caused by: org.firebirdsql.gds.GDSException: I/O error during "open" operation for file "samba/LNX.FDB"
Error while trying to open file
null
    at org.firebirdsql.gds.impl.wire.AbstractJavaGDSImpl.readStatusVector(AbstractJavaGDSImpl.java:2098)
    at org.firebirdsql.gds.impl.wire.AbstractJavaGDSImpl.receiveResponse(AbstractJavaGDSImpl.java:2048)
    at org.firebirdsql.gds.impl.wire.AbstractJavaGDSImpl.internalAttachDatabase(AbstractJavaGDSImpl.java:463)
    at org.firebirdsql.gds.impl.wire.AbstractJavaGDSImpl.iscAttachDatabase(AbstractJavaGDSImpl.java:411)
    at org.firebirdsql.jca.FBManagedConnection.<init>(FBManagedConnection.java:105)
    at org.firebirdsql.jca.FBManagedConnectionFactory.createManagedConnection(FBManagedConnectionFactory.java:509)
    at org.firebirdsql.jca.FBStandAloneConnectionManager.allocateConnection(FBStandAloneConnectionManager.java:65)
    at org.firebirdsql.jdbc.FBDataSource.getConnection(FBDataSource.java:118)
    ... 5 more
```

If I go to "/samba" and type:

```
isql-fb
connect "localhost:/samba/LNX.FDB" user 'SYSDBA' password 'masterkey';
```

It works perfectly fine, I can select, delete, update, insert,... with no problem at all.

If I use IBExpert on my Windows machine to connect to my database in Ubuntu it says:

```
Unable to complete network request to host "Server-Test".
Failed to estabilish connection.
```

If I use Flamerobin it says:

```
An assertion failed!

../src/common/strconv.cpp(3031): assert "Assert failure" failed in wxCSConv(): invalid encoding value in wxCSConv ctor
```

But it connects, I can select, delete, update,...

---

