---
title: "How do i compile Java"
date: 2006-09-25
forum: Programming Talk
---

### Post by L2wis on 2006-09-25
Hi all, This morning i've installed jdk1.5.0_08, I can run java programs with the command Java, but when i go to compile my program using:

```
javac -d bin -classpath bin src/numericOnly.java
```

It doesn't recognise javac?! Please help me get compiling.

Regards

Lewis

---

### Post by arkangel on 2006-09-25
javac is not in the PATH, in a console type  
# export PATH=$PATH:[dir/where/yourjavac/is]

this will work in the current console, you can add that line in the .bashrc
in your home directory (for you ) or as su in /etc/enviroment  for all user

---

### Post by L2wis on 2006-09-25
```
 export PATH=$PATH:[jdk1.5.0_08/bin/javac]
```

Is that the command i need to type into a terminal. How do i open that bashrc file?

---

### Post by arkangel on 2006-09-25
1. how did you install java  and JRE ? when I  meant [jdk1.5.0_08/bin/javac]
i was trying to say in the directory where the compiler is  (in my case i have installed in another directory  and not in the normal installatiion dir , if you have isntalled  using synaptic   ) 

I have java in /opt/jdk1.5/  so the  export command is for me :
# export PATH=$PATH:/opt/jdk1.5/bin

in your case , if i remember well,  the bin directory (where all executables of java are )of java must be /usr/lib/j2sdk1.5-sun/bin ( try looking for it in  /usr/lib/java or /usr/local/java... or  something similar , if your installation is ok  the direcotry is stored in a  enviroment variable  called JAVA_HOME, so type in a terminal 
# $JAVA_HOME
and it will prompt where java is installed, sotry this first

assuming that the binaries (javac) are in the directory i just mentioned , you have to type in a console 
# export PATH=$PATH:/usr/lib/j2sdk1.5-sun/bin/
if not you have to change it accordingly

2.  if the last command works  for you ,and you were able to find the dir of java   open .basrc and copy that command, in a terminal type 
#gedit ~/.bashrc
and paste at the end of the file  the line  
**export PATH=$PATH:/usr/lib/j2sdk1.5-sun/bin/ ** or  the one that works for you 

once again ,you  have to find the right direcotry  where java is ,

---

### Post by L2wis on 2006-09-26
Hello m8, It's sorted now :) i looked at ur example and typed:
```
export PATH=$PATH:jdk1.5.0_08/bin/
```

And it all worked :D

Regards!!!

---

