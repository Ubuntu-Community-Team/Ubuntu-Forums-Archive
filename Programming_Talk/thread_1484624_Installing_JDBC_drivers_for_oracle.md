---
title: "Installing JDBC drivers for oracle"
date: 2010-05-15
forum: Programming Talk
---

### Post by formaldehyde_spoon on 2010-05-15
For anyone unfortunate enough (like me) to be getting errors like this when compiling a Java program:

```
JDBCDemo.java:2: package oracle.jdbc.pool does not exist
import oracle.jdbc.pool.OracleDataSource;
                       ^
``` This means you need the JDBC drivers for oracle, from oracle.

After scouring the web from top to bottom I realized there just isn't a web page anywhere with a nice, super simple guide to fixing this, so here it is for the next poor guy in my current position:  
(I assume you have Java 1.6. If you have 1.5 substitute ''5'' wherever you see ''6'' below) 

1.) Go here: [http://www.oracle.com/technology/software/tech/java/sqlj_jdbc/htdocs/jdbc_111060.html](http://www.oracle.com/technology/software/tech/java/sqlj_jdbc/htdocs/jdbc_111060.html)  

2.) Download these 4 files under **JDBC Thin for All Platforms** for the latest version:
- libheteroxa11.so
- libocijdbc11.so
- ojdbc6.jar
- orai18n.jar
 Substitute the location you saved them wherever you see ''/your/path/to/files'' below. 

3.) To be completed --- get java to recognize all these libraries and packages.  I'll come back and edit this post shortly when I figure out how, if I haven't already shot myself.  If someone who already knows wants to jump in first, please do.

I just tried the following, but it hasn't worked:
```
 export CLASSPATH=$CLASSPATH:/your/path/to/files/ojdbc6.jar
export CLASSPATH=$CLASSPATH:/your/path/to/files/orai18n.jar
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/your/path/to/files

``` classpath and ld_library_path now include these locations, but still getting the same error on compile

---

### Post by Some Penguin on 2010-05-15
[http://java.sun.com/docs/books/tutorial/essential/environment/paths.html](http://java.sun.com/docs/books/tutorial/essential/environment/paths.html)
[http://stackoverflow.com/questions/219585/setting-multiple-jars-in-java-classpath](http://stackoverflow.com/questions/219585/setting-multiple-jars-in-java-classpath)

---

### Post by formaldehyde_spoon on 2010-05-16
Help, please...
I've read quite a lot of pages today like the ones in the previous post but am still stuck...
I've followed these instructions from Oracle's site, but it hasn't made any difference: [http://www.oracle.com/technology/software/tech/java/sqlj_jdbc/htdocs/111070_readme.html](http://www.oracle.com/technology/software/tech/java/sqlj_jdbc/htdocs/111070_readme.html)
Should I be using LD_LBRARY_PATH?
How do I use the .so files?  The readme doesn't mention them.
CLASSPATH now includes the two .jar files, so is it only the .so files that are the problem?

---

### Post by r-senior on 2010-05-17
Oracle has two types of JDBC driver: 

a. the thin driver

b. the OCI (Oracle Call Interface) driver, which works through SQL*Net (or Oracle*Net or whatever they are calling it this week ;)). 

The OCI driver needs the tnsnames.ora and your .so files (which represent the client side of SQL*Net) on the client and a database listener setup on the server. The thin driver just hits the database direct via a TCP/IP socket. You specify this in your connect string, e.g.:

```
jdbc:oracle:thin:@serverName:1521:dbName
```

All you need for a thin driver to work is the JAR file for the JDBC driver on your classpath. The .so files, LD_LIBRARY_PATH, etc. are not required for the thin driver.

For example, in TestJdbc.java:

```

import oracle.jdbc.pool.OracleDataSource;

public class TestJdbc {

    public static void main(String ... args) {
        System.out.println(OracleDataSource.class.getName());
    }

}

```$ javac -cp ojdbc6.jar TestJdbc.java
$ java -cp ojdbc6.jar:. TestJdbc
oracle.jdbc.pool.OracleDataSource

Hope that helps. I don't have an Oracle database around to show a more complete example. If you are still stuck, maybe post the code that's the problem?

---

### Post by slavik on 2010-05-17
thin driver is what is called a type 4 driver. meaning it is java talking to oracle ... natively (whereas oci is an interface)

---

