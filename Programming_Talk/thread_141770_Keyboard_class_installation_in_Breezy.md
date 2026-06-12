---
title: "Keyboard class installation in Breezy"
date: 2006-03-09
forum: Programming Talk
---

### Post by encompass on 2006-03-09
I have the fallowing instructions for windows...
> Possible modification to an environment variable

To be able to use some common class (like Keyboard.class,
Database.class or JDBC database driver for some database), you can tell
the Java Compiler and Runtime Environment where to find these classes.
This is done by adding folder paths to the CLASSPATH environment
variable. Example:

CLASSPATH=.;c:\myjava\keyboard\;c:\solid\jdbc\SolidDriver2.0.jar;

The first two characters in the beginning, ".;" have to be there. It
means that classes will be searched first from the current working
directory (folder).

In Windows environment variables can be set in
Control Panel > System > Advanced > Environmental variables.
The text editor has to be closed and opened again so the new CLASSPATH
will be used.

In network you might be able to modify only the user setting CLASSPATH.
how would I do that same thing so that my eclipse will compile the programs with that kyboard class?  I need it for my first semester of assignments at school.  Java I think is sucks, but I have to start somewhere.

---

