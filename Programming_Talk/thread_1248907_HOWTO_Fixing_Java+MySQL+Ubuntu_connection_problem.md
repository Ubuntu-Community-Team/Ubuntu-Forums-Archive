---
title: "HOWTO: Fixing Java+MySQL+Ubuntu connection problem"
date: 2009-08-24
forum: Programming Talk
---

### Post by CaptainPanick on 2009-08-24
This particular problem caused me at least 6 hours to resolve and I finally found a particular solution that worked for me. I decided to list all the possible solutions in one place.

**Code:**
```

Class.forName("com.mysql.jdbc.Driver");
dbConnection = DriverManager.getConnection("jdbc:mysql://localhost:3306/dbname", "dbusername", "dbpassword");	

```

**Results in Error:**
com.mysql.jdbc.exceptions.MySQLSyntaxErrorException: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '????????????????????????????????' at line 1

**Reason for error:**
This problem seems to occur because there are incompatibilities between specific versions of MySQL and Java's JDBC MySQL driver. These incompatibilities in turn causes communication problems due to different character sets being used between the JDBC driver and MySQL.

**Version Details:**
Ubuntu: 9.04 Jaunty Jackalope
MySQL: 5.0.75
Java Version: Java(TM) SE Runtime Environment ( build 1.6.0_14-b08 )
MySQL JDBC Connector: mysql-connector-java-5.1.8-bin.jar

**Possible solutions for fixing the problem:**

**Solution A**
First try changing your connection string by adding the useJvmCharsetConverters parameter:
```

"jdbc:mysql://localhost:3306/dbname?useJvmCharsetConverters=true"

```

**Solution B**
If that doesn't work, add the following parameters instead:
```

"jdbc:mysql://localhost:3306/dbname?useUnicode=yes&characterEncoding=UTF-8"

```

Note: You may have to change UTF-8 to a different character set if you are not using it.

**Solution C**
Still no luck? Try adding a combination of the parameters:
```

"jdbc:mysql://localhost:3306/dbname?useJvmCharsetConverters=true&useUnicode=yes&characterEncoding=UTF-8"

```

**Solution D**
If it still doesn't work the amount of effort your going to put in just got more. Try setting the version JRE (Java Runtime Environment) that is currently used to SUN's JRE instead of GNU JRE. Do this by running:
```

sudo update-alternatives --config java

```
Something like the following will be displayed:

```

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/gij-4.3
          3    /usr/lib/jvm/java-gcj/jre/bin/java
*         4    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        5    /usr/lib/jvm/java-6-openjdk/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```

Make sure that yours is set to either /usr/lib/jvm/java-6-sun/jre/bin/java or /usr/lib/jvm/java-6-openjdk/jre/bin/java (You may have to try both)

**Solution E**
Download the latest JDBC MySQL drivers from here:
[http://www.mysql.com/products/connector/](http://www.mysql.com/products/connector/)

Extract the .tar.gz file and follow the installation instructions in the README.txt file.

If none of the above solves your problem then you are out of luck and I can't help you. Sorry. :(

---

