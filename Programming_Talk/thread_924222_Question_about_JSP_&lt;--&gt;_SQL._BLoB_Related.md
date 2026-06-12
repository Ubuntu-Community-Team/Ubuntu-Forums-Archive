---
title: "Question about JSP &lt;--&gt; SQL. BLoB Related"
date: 2008-09-19
forum: Programming Talk
---

### Post by balagosa on 2008-09-19
Would there be any other way of storing an Image aside from using **PreparedStatement.setBinaryStream**??

I am wondering because I have no plans of using PreparedStatements as because I am already using SQL->Stored Procedures.

[Example 1]("http://saloon.javaranch.com/cgi-bin/ubb/ultimatebb.cgi?ubb=get_topic&f=3&t=011593")

---

### Post by balagosa on 2008-09-20
*bump*

Sorry for the bump, but this is quite of urgent. The deadline for this school project is by October.

---

### Post by tinny on 2008-09-20
Sorry im confused. Are you saying you dont want to use a PreparedStatement because you are wanting to use a Stored Procedure?

If I was doing this with straight SQL I would do it how this link describes.

[http://www.java2s.com/Code/Java/Database-SQL-JDBC/InsertpicturetoMySQL.htm](http://www.java2s.com/Code/Java/Database-SQL-JDBC/InsertpicturetoMySQL.htm)

For the stored procedure approach have a read up on [CallableStatement]("http://java.sun.com/j2se/1.5.0/docs/api/java/sql/CallableStatement.html").

---

### Post by balagosa on 2008-09-20
> **tinny said:**
> you dont want to use a PreparedStatement because you are wanting to use a Stored Procedure?



yes, that is how i want to do it. All the links I have are about Prepared Statements. I have yet to find one that is using **Statements.**

---

### Post by tinny on 2008-09-21
> **balagosa said:**
> yes, that is how i want to do it. All the links I have are about Prepared Statements. I have yet to find one that is using **Statements.**

Well then [CallableStatement]("http://java.sun.com/j2se/1.5.0/docs/api/java/sql/CallableStatement.html") is what you want for a stored procedure.

---

### Post by balagosa on 2008-09-21
> **tinny said:**
> Well then [CallableStatement]("http://java.sun.com/j2se/1.5.0/docs/api/java/sql/CallableStatement.html") is what you want for a stored procedure.

thanks...but mind giving me a sample website on how to use such?

---

### Post by tinny on 2008-09-21
I haven't used CallableStatement for a while, but from memory...

[PHP]

        try {
            Connection conn = DriverManager.getConnection("jdbc..");
            
            CallableStatement statement = conn.prepareCall("your stored proceedure or SQL statment...");

            //Blob data
            byte[] data = new byte[]{0, 0, 0};

            statement.setObject("parameterNameOfBlob", data);
            
            statement.execute();
            
        } catch (SQLException ex) {
            Logger.getLogger(Main.class.getName()).log(Level.SEVERE, null, ex);
        }
[/PHP]

---

### Post by drubin on 2008-09-21
May I ask why store the Blob directly in the DB as apposed to a link to a file on the file system?

It makes db maintenance so much easier and DB size drops greatly.

---

### Post by tinny on 2008-09-21
> **rubinboy said:**
> May I ask why store the Blob directly in the DB as apposed to a link to a file on the file system?

It makes db maintenance so much easier and DB size drops greatly.

Yeah, id also be interested to know why they are using a stored procedure for this.

---

### Post by balagosa on 2008-09-22
I know you can just use link for picture files, but I wanted more. I never tried storing Pictures in DB, and now I want to learn. If I wanted an easy approach then the latter (links) would be my choice.

I usually do not care about the grades I get from my projects, what concerns me most is the learning I get from making them. This will be one good example of it.

---

