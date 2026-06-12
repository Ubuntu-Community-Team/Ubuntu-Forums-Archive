---
title: "Convert jar file"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by redpower1989 on 2011-11-16
Do you know a tutorial about convert a JAR file to DEB package?

---

### Post by NESFreak on 2011-11-16
That's not something thats easy to do. Even though both .deb files and .jar files are archives, you should actually see the jarfile as an executable. You can even run it with the command "java -jar myjarfile.jar". For your own use a .jar file would therefore not necessarily need to be installed. A .deb file on the other side should be seen as an installer (like an .msi file on windows) for an application. As such it could for instance be used to install the .jar file you have.

So from here on I assume your question is 'how do I create a .deb file (to contain my jar file)' Which is covered here:

Programming Guides and Basics 
[http://ubuntuforums.org/showthread.php?t=1766253](http://ubuntuforums.org/showthread.php?t=1766253)

How to make a "Basic" .deb
[http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717)

See also:
[http://en.wikipedia.org/wiki/JAR_(file_format](http://en.wikipedia.org/wiki/JAR_(file_format))
and
[http://en.wikipedia.org/wiki/.deb](http://en.wikipedia.org/wiki/.deb)

---

### Post by redpower1989 on 2011-11-17
thanks very much !

---

