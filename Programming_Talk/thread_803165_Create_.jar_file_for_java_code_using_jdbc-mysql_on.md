---
title: "Create .jar file for java code using jdbc-mysql on eclipse"
date: 2008-05-22
forum: Programming Talk
---

### Post by Mokhta on 2008-05-22
All right....I'm working on this project which involves programming in JDBC and MySQL..now everything is running smoothly on Eclipse but once I try exporting my project as a .jar file and running it I get SQL errors that I didn't usually get as I've already told.

I have looked around and read a huge number of threads but none of them actually answered my question which finally would be about how to prevent getting error while I run the .jar file? In other words how can I include my sql library in the .jar folder as I personally think of it as the only possible source of the problem.
Just for the record all my programming is based on the default library and the imported library mysql.jar that I got while installing some weird stuff which I was told to be important for JDBC and that currently resides in my \usr\share\java folder.

Can anyone give me a good hint better would be a tutorial helping me resolving this problem.

Thanks a bunch!

---

### Post by Zugzwang on 2008-05-22
Please state *which* SQL error you get when running the .jar file.

I don't know much about Eclipse, but here's some simple way to include the MySQL classes: Rename your application .jar file to bla.zip, do the same with the MySQL stuff jar file. Then copy all of the contents of the MySQL jar/zip file into the application .zip file and rename it to .jar again.

That's the simplest way to do so but please keep in mind that you might run into problems w.r.t the licence of the MySQL JDBC stuff (only important if you distribute your program). In that case, you can modify the Manifest file of your application .jar file to point to some relative location of the MySQL  .jar file. Google is your friend here.

---

### Post by Mokhta on 2008-05-22
Thanks for the reply.
Actually the error that I get is java.lang.ClassNotFoundException: com.mysql.jdbc.Driver

---

### Post by Mokhta on 2008-05-22
Well I guess I pretty much solved the problem I had to include the classes in my jar file as you said.
Thanks a lot buddy!

---

### Post by NormR2 on 2008-05-22
You don't need to copy the class files from another jar file into your applications jar file. You can reference the other jar file by putting an entry in the manifest file for your jar file. For example here is a contents of a manifest file:
```

Main-Class: GetURLText
Class-Path: DocumentViewerWParser.jar

```


I have both jar files in the same folder when I execute my app:
java -jar <jarfile>

Another way is to use a script to start the app with both jar files specified on the classpath:
```

java -cp <yourjarile>:<otherjarfile> <classname>

```

---

### Post by Mokhta on 2008-05-22
Right on! worked for me.

---

