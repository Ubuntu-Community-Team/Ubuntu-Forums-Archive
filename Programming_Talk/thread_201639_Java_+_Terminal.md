---
title: "Java + Terminal"
date: 2006-06-22
forum: Programming Talk
---

### Post by jitesh on 2006-06-22
Does anyone have the source code to execute a command in the linux terminal via a java application.

---

### Post by x64Jimbo on 2006-06-22
it's a java application? Like a jar file? You don't need to run jar files from the command line - you just double click on them. Otherwise, java executables are run by doing "java executablename"

---

### Post by jitesh on 2006-06-22
sorry for the confusion, how do i run a terminal comand from within a java application?

---

### Post by ynef on 2006-06-22
[http://www.google.se/search?q=java+exec+external+program](http://www.google.se/search?q=java+exec+external+program)

Does that cover it?

---

### Post by sphinx on 2006-06-22
Just expanding on ynef's post.

The Class you want to look at is Runtime and the methods you want to look at are the exec() family. I say family because there are several diffrent methods named exec with diffrent arguments, some more useful than others in diffrent situations.

I've actually posted something somewhat related in [this thread]("http://ubuntuforums.org/showthread.php?p=1022306#post1022306"). So you might want to take a look for an example of usage.

The thing to remember is the commands Java executes are not strictly speaking executed on a 'terminal' as is not executed via a shell (such as bash). This has the effect of perhaps not having the correct environment variable set or other things you tend to take for granted in a 'terminal'. Depending on how the original Java app was started. It just an area to look into if you have problems executing a command from within Java.

---

