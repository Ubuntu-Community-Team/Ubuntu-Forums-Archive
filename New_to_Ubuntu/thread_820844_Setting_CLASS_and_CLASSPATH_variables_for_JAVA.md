---
title: "Setting CLASS and CLASSPATH variables for JAVA"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by bmcase on 2008-06-06
I'm getting compiler errors that lead me to believe that one or both of these variables is set incorrectly. I'm not sure where I need to configure these or the syntax to use.

I assume that etc/environment is the file that needs to be edited. It has one line of code:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

I assume that this is correct because a simple "Hello World" prog compiles and runs. If I try to import any other packages I get alot of DOES NOT EXIST or CANNOT FIND SYMBOL errors consistent with the ClassPath variable not correctly referring to the java lib/tools.jar file. Is /etc/environment where I need to be editing this? What syntax do I need to use to make a ClassPath variable and have it point to the tools.jar file? Do I need to also specify the current directory as with the ".;" in Windows?

---

### Post by bmcase on 2008-06-06
*bump*

---

### Post by _graham_ on 2009-06-27
Run Terminal and type "echo $CLASSPATH" to see what it is set to already (it might be empty).

Edit /home/user/.bashrc with any text editor

If you had something in your CLASSPATH you might find it being set inside this file.  If you can't find it you might want to try looking elsewhere.

If there was nothing in your CLASSPATH then add this on to the end of your .bashrc file

#set the java classpath
export CLASSPATH=/usr/share/java/saxonb-9.0.jar:.

I'm putting a jar file for SaxonB in there, but you should put whatever you need.  Multiple files should be separated by a colon.  I've put the current directory "." in there too, but I suppose that is just for preference.

---

