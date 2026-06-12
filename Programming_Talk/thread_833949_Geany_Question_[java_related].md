---
title: "Geany Question [java related]"
date: 2008-06-19
forum: Programming Talk
---

### Post by brandon89 on 2008-06-19
how do i go about telling Geany where my third-party .jar packages are located so that when i compile my class files i dont get hundreds of errors saying that xxx package doesnt exist?

---

### Post by NormR2 on 2008-06-19
Is there a menu/option to set the commandline for compiling?
Add the classpath to your jar files to that javac command.

---

### Post by brandon89 on 2008-06-19
under the build options there's this thing:

[IMG]http://img237.imageshack.us/img237/3082/optionpb5.png[/IMG]
so fill in the first one?

---

### Post by NormR2 on 2008-06-19
I'm not on Ubuntu right now to check, but I think that's right.

You'll also have to add those jar files to the classpath in the second commandline for when you try to execute the program.

---

### Post by brandon89 on 2008-06-19
um im having some issues getting the syntax right when trying to fill in the classpath...any help on what it should look like?

---

### Post by NormR2 on 2008-06-19
The doc for java should help with options etc.  For Linux it would be something like this:

javac -classpath <fn1>.jar:<fn2>.jar:. <other options> %f

Not sure about the %f - it requires the full filename here.

Try using the Search on this forum for: -classpath

Open a terminal window and try some combinations of the commandline there. Then if you get some error message you can't figure out, copy the whole of the command and error message and paste it back here.

---

