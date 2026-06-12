---
title: "Need help installing Connector/J"
date: 2011-10-25
forum: Programming Talk
---

### Post by Smyril on 2011-10-25
I recently just started using Ubuntu and now started developing in Java. I've started a database project, where I need to connect to a MySQL database, by which I need Connector J but I'm not quite sure how to install Connector J, and the documentation isn't really any help to me...

Please, think of me as I know nothing of Ubuntu, any assistance would be highly appreciated.

Thanks in advance.
-Smyril


EDIT: Solution: [http://ubuntuforums.org/showpost.php?p=11394722&postcount=5](http://ubuntuforums.org/showpost.php?p=11394722&postcount=5)

---

### Post by lisati on 2011-10-25
*Thread moved to **Programming Talk**.*

---

### Post by nimbrant on 2011-10-25
You can get the Connector/J driver from the mysql website, and add the jar to you classpath

[http://dev.mysql.com/downloads/connector/j/](http://dev.mysql.com/downloads/connector/j/)

Here are a couple lines which are important to get started, you can find more examples with google.
```

Class.forName("com.mysql.jdbc.Driver");
Connection conn = DriverManager.getConnection(url);

```

the format of the url is something like
jdbc:mysql://host/dbname?user=dbuser&password=dbpassword

---

### Post by Smyril on 2011-10-25
> **lisati said:**
> *Thread moved to **Programming Talk**.*

Thank you.

> **nimbrant said:**
> You can get the Connector/J driver from the mysql website, and add the jar to you classpath

[http://dev.mysql.com/downloads/connector/j/](http://dev.mysql.com/downloads/connector/j/)

Here are a couple lines which are important to get started, you can find more examples with google.
```

Class.forName("com.mysql.jdbc.Driver");
Connection conn = DriverManager.getConnection(url);

```

the format of the url is something like
jdbc:mysql://host/dbname?user=dbuser&password=dbpassword

Thanks for the reply, I had an application running successfully on windows, the problem I have, is getting the connector installed. I'm not quite sure where to place the connector jar file and how to add it to classpath.

---

### Post by Smyril on 2011-10-26
I'm not quite sure what I did different to fix this, but I reinstalled Ubuntu and now it works. 

What I did:

I downloaded [mysql-connector-java]("http://dev.mysql.com/downloads/connector/j/").

in terminal I wrote:

```
sudo apt-get install libmysql-java
```

then I moved mysql-connector-java-5.1.18-bin.jar to /usr/lib/jvm/java-6-openjdk/jre/lib/ext/ using

```
sudo nautilus
```

Then in terminal I wrote:

```

CLASSPATH=$CLASSPATH:/usr/lib/jvm/java-6-openjdk/jre/lib/ext/
export CLASSPATH

```

and now it successfully runs the Java file.

Hopefully, this will help anyone else with similar problems as I had, thanks for the replies.

---

