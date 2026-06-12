---
title: "Setting Java Classpath?"
date: 2006-11-10
forum: Programming Talk
---

### Post by austinwilde on 2006-11-10
I am a swichee from Windows :( to ubuntu Linux :). Can anyone tell me how to set my path to run Java apps that I am writing, to learn Java? I can do it Windows, but....now to do on Lin. Thanks! ;):confused:

---

### Post by depu on 2006-11-11
This link shows how to set up the classpath and the java home path

[http://ubuntuforums.org/showthread.php?t=217936&highlight=classpath](http://ubuntuforums.org/showthread.php?t=217936&highlight=classpath)

or you sould also set up the same in your .bashrc file

---

### Post by hod139 on 2006-11-11
If you install Java from Ubuntu's repository, most of the classpath settings are automagically set up for you.  Just see this howto: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378), ignoring the eclipse steps (unless of course you decide you want to install eclipse).

---

### Post by pschulam on 2009-11-30
Hi All,

I've looked through the posts above and have not been able to locate where my CLASSPATH variable is defined.

I tried to export CLASSPATH in .profile but that didn't work.

All I need to do is make sure that java knows were to find a .jar that I'm working with currently. How do I do this? I've searched through the forums but nothing has done the trick.

Thank you for any help.

Best,
Peter

---

### Post by Axos on 2009-11-30
How are you running the program? From a terminal or an IDE like NetBeans? If you are running it from a terminal, type this before you run the java command:

export CLASSPATH=/path/to/wherever:/another/path:/blah/blah/blah

Note that you use colons on Linux, not semicolons.

If you are running it from an IDE, there is probably a project setting which lets you specify the class path. Alternatively, you can set the class path globally by putting the above export command into the file ~/.gnomerc, assuming you are using the Gnome desktop. Once you edit .gnomerc, log off and back on for it to take effect. To verify that it worked, open a terminal and type:

echo $CLASSPATH

---

### Post by Axos on 2009-11-30
You can also specify the class path on the java command line using either the -cp or -classpath option:

-cp <class search path of directories and zip/jar files>
-classpath <class search path of directories and zip/jar files>
   A : separated list of directories, JAR archives,
   and ZIP archives to search for class files.

You can run java -help to see all the command line options you can feed to java.

---

