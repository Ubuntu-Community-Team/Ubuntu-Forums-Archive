---
title: "Java compilation error"
date: 2011-09-09
forum: Programming Talk
---

### Post by Metalbot on 2011-09-09
I've installed the following from the software center:
OpenJDK JAVA 6 runtime
IcedTea Java 6 webstart.
I also installed Geany.

However, I cannot compile my java code. It gives me this message.
 /bin/sh: javac not found.

i found the "javac" file in a computer search.

 It's location is: /media/system/Program Files/Java/jdk1.7.0/bin 

I know it needs to be in bin/sh for my programs to run.
But when i open "bin" in my Filesystem, there is no subfolder called  "sh". There's a "link to exectable" file called "sh". What do i do to  set this right? Please answer.

Thank you.

---

### Post by hyperAura on 2011-09-09
What distribution of linux are you using?

---

### Post by ofnuts on 2011-09-09
/media is where the temporary/external mass storage media are mounted. Having your JDK there is very unusual.

/bin/sh isn't a directory, it's a piece of code (your shell command line interpreter). The "/bin/sh" part of the message isn't tellin you where the problem is, but "who" is emitting the message. It's /bin/sh that doesn't find javac anywhere in the directories in your PATH.

I don't know how your particular Java JDK is installed, but I would expect javac to show up in /usr/bin (likely as a soft link to a piece of code somewhere else).

---

### Post by cgroza on 2011-09-09
You need to install JDK - the Java Development Kit. What you have downloaded, is only the virtual machine that allows you to run the java bytecode.

You can find the JDK on oracle website ( and the repos too??).

---

### Post by WitchCraft on 2011-09-09
> **cgroza said:**
> You need to install JDK - the Java Development Kit. What you have downloaded, is only the virtual machine that allows you to run the java bytecode.

You can find the JDK on oracle website ( and the repos too??).

Yes, sun-java is still on the repos.
However, Oracle, which bought SUN, retracted the free licensing granted by Stanford University Networks (SUN) to all Linux distros, so it shouldn't be.
You should either download it from the Oracle Java homepage, or use the OpenJDK...
In the long term, somebody will probably write a downloader/installer, just like for Flash, which can be put into the repos legally (anybody needs a problem for a bachelor/master thesis ?).

And all those Java people that said mono was a problem / risk...

---

### Post by Bachstelze on 2011-09-09
> **WitchCraft said:**
> .
However, Oracle, which bought SUN, retracted the free licensing granted by Stanford University Networks (SUN) to all Linux distros,

Sun Microsystems and SUN are not, and never were, the same entity.  When former SUN members founded a company, they called it Sun in reference to SUN, but they are not the same thing.

---

