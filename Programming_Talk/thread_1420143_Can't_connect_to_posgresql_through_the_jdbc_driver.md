---
title: "Can't connect to posgresql through the jdbc driver"
date: 2010-03-02
forum: Programming Talk
---

### Post by Blu123 on 2010-03-02
Hi
I'm using postgresql 8.3 and the postgresql-8.4-701.jdbc4.jar ( a jar file which is supposed to include the jdbc driver: org.postgresql.Driver) 
I set the CLASSPATH environment variable to the correct place and ran my JAVA code which first tried to call the jdbc driver : "Class.forName("org.postgresql.Driver");"
But to no avail ("java.lang.ClassNotFoundException: org.postgresql.Driver") . At first I thought I set the CLASSPATH wrong (did it thorugh my .bashrc and exported) but after trying a few variations of CLASSPATH I opened the file postgresql-8.4-701.jdbc4.jar with the ZIP tool that came with UBUNTU.
I noticed that the jdbc driver postgresql-8.4-701.jdbc4.jar was not in that bundled jar file...
I did notice that there was another driver in there called "java.sql.Driver"
I put it in my code (just to check the CLASSPATH) : "Class.forName("java.sql.Driver");"
compiled and ran . This time it passed that line correctly (it did get stuck on the actual line that operated  the JDBC URL, but at least it showed me that my CLASSPATH was right...could anyone tell me why org.postgresql.Driver could not  be found in postgresql-8.4-701.jdbc4.jar...? and also if there is an answer to that  , how do I make this one disappear :
java.lang.ClassNotFoundException: org.postgresql.Driver
When I try to call it....

---

