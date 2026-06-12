---
title: "runtime classes in Java"
date: 2007-05-08
forum: Programming Talk
---

### Post by Bobtheknight on 2007-05-08
My Betters,

When I try to compile/run a java program I found on the web, I found that I have a bunch of classes that I must download and include in my CLASSPATH before I can run the TestClient.class.  This would be a problem because after I'm done compiling, I don't want my users to have to download jar files and set classpath, they won't know how.

What should I do?

Bob

---

### Post by samjh on 2007-05-08
Simply distribute your program with the necessary class files, and write a shell script to execute your program with the necessary classpaths specified.

If you don't want to do that, you can pack your program into a jar file, and then archive that jar file with a directory that contains the dependent class files.  For example, you could have YourProgram.tar.gz which will contain RunMe.jar and a subdirectory /lib with the needed classes.  In your RunMe.jar file, you can specify the classpath in the the manifest.  This way, the user can just unpack the tar.gz archive to a directory of their own choosing and run your RunMe.jar without having to tinker with classpaths themselves.  For more info on jar files, see here: [http://java.sun.com/docs/books/tutorial/deployment/jar/](http://java.sun.com/docs/books/tutorial/deployment/jar/)

---

