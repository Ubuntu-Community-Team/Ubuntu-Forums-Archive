---
title: "mysql jdbc connector problem"
date: 2011-03-14
forum: Programming Talk
---

### Post by Segaman on 2011-03-14
hi
I have a question during writing a simple app which is connecting to mysql database and work with it.
So...
```

try { // load the driver
         Class.forName("com.mysql.jdbc");
    }
    catch( Exception e ) { // problem loading driver,
                             // class not exist?
         e.printStackTrace(); 
         //return;
    }

```here I`m loading driver...
and it crashes as "java.lang.ClassNotFoundException: com.mysql.jdbc"
I know its been alot of threads about it but after reading I dont know why but I`m confused..
But first of all,I`ve loaded Connector/J from mysql.com
I`ve tried to open /etc/bash.bashrc and to add this strings:
```

JAVA_HOME="/usr/lib/jvm/java-1.5.0-gcj-4.4/jre/lib/"
export JAVA_HOME

```Perhaps I set a wrong direction here..?

Then I tried by typying in terminal this:
```

export set CLASSPATH=/home/sega/Downloads/mysql-connector-java-5.1.15.tar.gz:$CLASSPATH"

```And its still doesnt work..
Please advise

---

### Post by Some Penguin on 2011-03-14
".tar.gz" != ".jar"

Unpack the .tar.gz and read any instructions within it.

---

### Post by Segaman on 2011-03-14
unpack, then
```

export set CLASSPATH=/home/sega/mysql-connector-java-5.1.15-bin.jar:$CLASSPATH

```
And still not working
:(

---

### Post by Some Penguin on 2011-03-14
One more bit:  "com.mysql.jdbc" sounds like a *package* name, not a class name -- by convention, classes begin with capital letters.  You want the /class/.

[http://www.docjar.com/docs/api/com/mysql/jdbc/Driver.html]("http://www.docjar.com/docs/api/com/mysql/jdbc/Driver.html")

---

### Post by Segaman on 2011-03-14
changed to
```

try { // load the driver
         Class.forName("com.mysql.jdbc.Driver");
    }

```

same...

---

### Post by Segaman on 2011-03-14
oh wait! its working now!!!
thankss!! :D

---

### Post by Segaman on 2011-03-14
UPDATE:
its not working.
Project`s runnig as Application but if I activate non-visual class and press "Run" I am still have 
```
 java.lang.ClassNotFoundException: com.mysql.jdbc.Driver 
``` 
any thoughts guys?

---

### Post by PaulM1985 on 2011-03-14
You say you are doing this in Eclipse (from the tag).  Are you able to just add the Jar as a library for the project?

[http://www.wikihow.com/Add-JARs-to-Project-Build-Paths-in-Eclipse-(Java](http://www.wikihow.com/Add-JARs-to-Project-Build-Paths-in-Eclipse-(Java))

This would remove the need to be adding it to your classpath.

Paul

---

### Post by Segaman on 2011-03-14
Oh thanks! I`ll try it.

---

### Post by Segaman on 2011-03-24
well...its not working.
I`ve created folder 'lib' in project`s dir,put an unjared Connector/J jar file...and still have that error.

---

