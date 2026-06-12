---
title: "Java project to a deb file"
date: 2006-05-18
forum: Programming Talk
---

### Post by EjeCt on 2006-05-18
Hey..
I am currently working on my main project to get my bachlor degree in software development. We are creating a program in java called EdSys. Object of the program is to let kids get better grip on reading. Soo I am going to create deb files for the project and i need som help... 

Do anybody how you can easily make a deb files from a java project..

EjeCt

---

### Post by binks on 2006-05-20
hey dude i no nothing of rogramming in linux but my boy is only 5 and would love to beta test the app if its aimed at his age group that is,
cheers if you want to get in touch pm me for my email cheers [QUOTE=EjeCt]Hey..
I am currently working on my main project to get my bachlor degree in software development. We are creating a program in java called EdSys. Object of the program is to let kids get better grip on reading. Soo I am going to create deb files for the project and i need som help... 

Do anybody how you can easily make a deb files from a java project..

EjeCt[/QUOTE]

---

### Post by daneel_olivaw on 2006-05-22
Anyway I never heard about putting a java program into a deb file O_o but I don't know that much about deb files..

I always thought that the only way to deploy a java program was to just put it into a jar file and that's it.. maybe even attaching an installation class to it.

---

### Post by mtinman on 2008-11-30
I am having the same kind of issue, while attempting to package the Vuze 4 program to a deb file. If anybody knows how to package a working Java program to a deb file, please post an answer... Thanks in advance!

---

### Post by NathanB on 2008-11-30
This wiki does a decent job of explaining the packaging process:

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

When you run into trouble, please ask for help in the
'Development & Programming > Packaging & Compiling Programs'
subforum.

---

### Post by drubin on 2008-11-30
> **daneel_olivaw said:**
> Anyway I never heard about putting a java program into a deb file O_o but I don't know that much about deb files..

I always thought that the only way to deploy a java program was to just put it into a jar file and that's it.. maybe even attaching an installation class to it.

Eclipse, Netbeans all all package in .deb files and are java based :)

---

### Post by janiver on 2011-08-19
solved: 1. cd projectdir 2. sudo checkinstall -D sunjavac *.java

---

### Post by akoskm on 2011-08-19
Nearly all required information in included in the guide what NathanB linked in [his post]("http://ubuntuforums.org/showpost.php?p=6282400&postcount=5"). However if you run into any problem I could help you based on my experience (I'm also creating deb installers for Ubuntu from the framework in my sign below).

---

### Post by janiver on 2011-08-19
:popcorn:    1. create Java Makefile: [http://www.cs.swarthmore.edu/~newhall/unixhelp/javamakefiles.html]("http://www.cs.swarthmore.edu/%7Enewhall/unixhelp/javamakefiles.html")
                 2. run sudo checkinstall -D make install

---

### Post by janiver on 2011-08-19
[http://thedarkmaster.wordpress.com/2008/05/24/how-to-create-manipulate-a-deb-file-of-a-compiled-application/](http://thedarkmaster.wordpress.com/2008/05/24/how-to-create-manipulate-a-deb-file-of-a-compiled-application/)

---

### Post by janiver on 2011-08-19
[http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/](http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/)

---

### Post by jamessnell on 2013-02-05
> **NathanB said:**
> This wiki does a decent job of explaining the packaging process:

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

When you run into trouble, please ask for help in the
'Development & Programming > Packaging & Compiling Programs'
subforum.

Not anymore. That page has been nuked it would seem. :(

---

### Post by slickymaster on 2013-02-05
There is a great tutorial [here]("http://www.debian.org/doc/maint-guide/") and another one [here]("http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html").

---

### Post by r-senior on 2013-02-05
New Ubuntu packaging guide is here:

[http://developer.ubuntu.com/packaging/html/](http://developer.ubuntu.com/packaging/html/)

---

### Post by jamessnell on 2013-02-05
For my case, I'm using ant to coordinate my builds as it is.

I found jdeb, which seems like a decent means to add an ant build target that'll actually generate your deb for you. Not sure how well it'll work. But looks promising

[https://github.com/tcurdt/jdeb/blob/master/docs/ant.md](https://github.com/tcurdt/jdeb/blob/master/docs/ant.md)

[http://repo1.maven.org/maven2/org/vafer/jdeb/1.0/](http://repo1.maven.org/maven2/org/vafer/jdeb/1.0/)

---

### Post by knahrvorn on 2013-03-01
Also a guide here:
[http://blog.pryds.eu/2013/02/package-java-apps-for-ubuntu-and-debian.html](http://blog.pryds.eu/2013/02/package-java-apps-for-ubuntu-and-debian.html)
This one doesn't expect you to have a source tarball, just a bunch of .class files that you'd like to package to a deb archive.

---

