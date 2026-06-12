---
title: "No suitable driver found for jdbc:mysq"
date: 2008-02-20
forum: Programming Talk
---

### Post by arobert74 on 2008-02-20
I am using Netbeans 6.0 and have followed "Using Java Persistence API Within a Visual Web JSF Application" document.
When trying to run the TestWebApp project, the page comes up but says "No Items found".
Looking at the Glassfish tab inside Netbeans, I see following error:
Caused by: java.sql.SQLException: No suitable driver found for jdbc:mysql://localhost:3306/sample

Here is what I verified:
1. Connection to database is correct
I have gone to Services > Databases > Drivers > Right click on MySQL and tried a connection with above URL.
It is successful so URL is correct

2. I do have the connector jar file as a librairie in my project

3. Here is my persistence.xml

<?xml version="1.0" encoding="UTF-8"?>
<persistence version="1.0" xmlns="http://java.sun.com/xml/ns/persistence" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://java.sun.com/xml/ns/persistence http://java.sun.com/xml/ns/persistence/persistence_1_0.xsd">
  <persistence-unit name="samplePU" transaction-type="RESOURCE_LOCAL">
    <provider>oracle.toplink.essentials.PersistenceProvider</provider>
    <class>com.samples.model.Users</class>
    <properties>
      <property name="toplink.jdbc.user" value="root"/>
      <property name="toplink.jdbc.password" value="oracle"/>
      <property name="toplink.jdbc.url" value="jdbc:mysql://localhost:3306/sample"/>
       <property name="toplink.jdbc.driver" value="com.mysql.jdbc.Driver"/>
  </properties>
  </persistence-unit>
</persistence>

What else am I missing?

Thanks a lot

---

### Post by MobiusNZ on 2008-02-21
You need the jdbc driver for mysql.

```
sudo apt-get install libmysql-java
```

---

### Post by arobert74 on 2008-02-23
Thanks for the reply !
How do I do that?

---

### Post by MobiusNZ on 2008-02-24
open up a terminal window and copy/type

```
sudo apt-get install libmysql-java
```

Then press enter. You'll need to put in your password to continue. After that you should be all good.

If you really don't want to use the terminal, use your favourite package manager (like synaptic) and search for libmysql-java

---

### Post by zdw208 on 2008-05-28
> **arobert74 said:**
> I am using Netbeans 6.0 and have followed "Using Java Persistence API Within a Visual Web JSF Application" document.
When trying to run the TestWebApp project, the page comes up but says "No Items found".
Looking at the Glassfish tab inside Netbeans, I see following error:
Caused by: java.sql.SQLException: No suitable driver found for jdbc:mysql://localhost:3306/sample

Here is what I verified:
1. Connection to database is correct
I have gone to Services > Databases > Drivers > Right click on MySQL and tried a connection with above URL.
It is successful so URL is correct

2. I do have the connector jar file as a librairie in my project

3. Here is my persistence.xml

<?xml version="1.0" encoding="UTF-8"?>
<persistence version="1.0" xmlns="http://java.sun.com/xml/ns/persistence" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://java.sun.com/xml/ns/persistence http://java.sun.com/xml/ns/persistence/persistence_1_0.xsd">
  <persistence-unit name="samplePU" transaction-type="RESOURCE_LOCAL">
    <provider>oracle.toplink.essentials.PersistenceProvider</provider>
    <class>com.samples.model.Users</class>
    <properties>
      <property name="toplink.jdbc.user" value="root"/>
      <property name="toplink.jdbc.password" value="oracle"/>
      <property name="toplink.jdbc.url" value="jdbc:mysql://localhost:3306/sample"/>
       <property name="toplink.jdbc.driver" value="com.mysql.jdbc.Driver"/>
  </properties>
  </persistence-unit>
</persistence>

What else am I missing?

Thanks a lot

 My application throws an SQLException 'No Suitable Driver'. Why is this happening?

There are three possible causes for this error:

    *

      The Connector/J driver is not in your CLASSPATH, see Chapter 2, Connector/J Installation.
    *

      The format of your connection URL is incorrect, or you are referencing the wrong JDBC driver.
    *

      When using DriverManager, the jdbc.drivers system property has not been populated with the location of the Connector/J driver.

---

### Post by HSada on 2008-10-08
I had the same problem and I was finally able to make it work by copying MySQL Connector/J jar file into the lib directory of glassfish server.  I believe zdw is correct about the classpath.  The glassfish server could not find mysql driver because its not in it's classpath so the easiest thing to do is just to include it in the lib directory where I know it is in the classpath or actually modify the classpath itself to point to the driver on some other directory.

---

