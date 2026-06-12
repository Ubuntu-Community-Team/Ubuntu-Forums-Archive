---
title: "Java jdbc MySQL database connection"
date: 2010-11-24
forum: Programming Talk
---

### Post by Uubnewb on 2010-11-24
Hi everyone,

I know this forum does not specialize in Java, but so far this forum seems to have the answer to "life, the universe and everything," so here goes:

I'm using Netbeans 6.9.1 on (at least at the moment) Windows 7.  I've set my environment "Path" variable to:
```
%SystemRoot%\system32;%SystemRoot%;%SystemRoot%\System32\Wbem;%SYSTEMROOT%\System32\WindowsPowerShell\v1.0\;C:\Program Files\Dell\Dell Wireless WLAN Card;c:\Program Files\WIDCOMM\Bluetooth Software\;c:\Program Files\WIDCOMM\Bluetooth Software\syswow64;C:\Program Files (x86)\Common Files\Roxio Shared\DLLShared\;C:\Program Files (x86)\Microsoft SQL Server\100\Tools\Binn\;C:\Program Files\Microsoft SQL Server\100\Tools\Binn\;C:\Program Files\Microsoft SQL Server\100\DTS\Binn\;C:\Program Files (x86)\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE\;C:\Program Files (x86)\Microsoft SQL Server\100\DTS\Binn\;C:\Program Files (x86)\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies\;C:\Program Files\MySQL\MySQL Server 5.1\bin;C:\Program Files (x86)\Java\jdk1.6.0_05\bin;C:\Program Files\Java\jre6\lib\ext
```

I'm using the following class to check my connectivity with the MySQL database:
```
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class JdbcExample2 {

  public static void main(String args[]) {
    Connection con = null;

    try {
        System.out.println("1");
      Class.forName("com.mysql.jdbc.Driver").newInstance();
      System.out.println("2");
      con = DriverManager.getConnection("jdbc:mysql:///test",
        "root", "secret");
      System.out.println("3");

      if(!con.isClosed())
        System.out.println("Successfully connected to " +
          "MySQL server using TCP/IP...");

    } catch(Exception e) {
      System.err.println("Exception: " + e);
    } finally {
      try {
        if(con != null)
          con.close();
      } catch(SQLException e) {}
    }
  }
}
```

Unfortunately, I keep getting the following output:
```
1
Exception: java.lang.ClassNotFoundException: com.mysql.jdbc.Driver
BUILD SUCCESSFUL (total time: 0 seconds)
```

I've tried the following:
[INDENT]1. Download the JDBC driver for MySQL at [http://dev.mysql.com/downloads/connector/j/](http://dev.mysql.com/downloads/connector/j/)[/INDENT]
[INDENT][INDENT]Although I must admit that I didn't exactly know what to do with it (I thought the .jar file should be executed).[/INDENT][/INDENT]
[INDENT]2. I then found out that I had to place the .jar file in my java\jre\lib\ directory as well as the java\jre\lib\ext directory.  So I did that.[/INDENT]
[INDENT]3. I've also tried yelling at the computer as well as giving it the ol' evil-eye, none of wich seemed to work.[/INDENT]

Sooo, I'm fresh out of ideas.  I've seen some mention of "add[ing the] .jar file to your controller," but I don't know what they mean by that.

If and when you answer, please keep in mind that I am fairly new to Java (and programming as a whole, actually).  I've done it at college, but at the moment I know some of the theory and very little of the practical application thereof.

Thanks for any possible help.

---

### Post by Uubnewb on 2010-11-24
Oh wait, don't worry.  Someone just showed me how to add the .jar file to the library in Netbeans.

For future reference, as well as anyone else having trouble with this, do the following in Netbeans:
[INDENT]1. In the left-hand pane, right-click on the "Libraries" directory and click "Add JAR/Folder..."  Then just browse to your JDBC driver (the .jar file) and click add.[/INDENT]

Hope this helps someone.  :)

PS: This forum is awsome, as soon as I posted my question, I got my answer ;)

---

### Post by Some Penguin on 2010-11-24
For reference, should you want to work directly with a Java compiler, extra jars are normally specified in the CLASSPATH variable --

```

export CLASSPATH=/some/extra/library.jar:/another/extra/library.jar

```

or directly as a command-line option

```

java[c] -cp /same/path.jar:/same/path.jar 

```

for both compiling and running.


Also, as a general practice,
```

catch (Exception e) {
 only-log-here
}

```

is pretty dangerous.  For instance, there are exceptions for which the proper response might be to terminate as gracefully as possible, because the programmer has probably done something wrong to the point where recovery is not possible (e.g. an UnsupportedOperationException or ConcurrentModificationException is usually indicative of a logic error -- you're coding badly...).  If you're going to catch generic runtime exceptions only for logging, *rethrow them* so that whomever calls you might handle them sanely or die if appropriate.

---

### Post by Uubnewb on 2010-11-24
Some Penguin,

Thanks for the reply.  

If you don't mind, would you please explain what you mean by "*rethrow them* so that whomever calls you might handle them sanely or die if appropriate?"  I know about throwing exceptions, and that all thrown exceptions must be caught at some time, but I have never thrown an exeption more than once.

---

