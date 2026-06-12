---
title: "J2se"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Maha1980 on 2008-04-27
please please please helpppppppppppppppppppp

machine: Dell inspiron 1525
Distro: ubuntu 8.04

i installed J2SE
throught the terminal using the "sh" command

now, i need to setup my environmental variables
and its been very hard :(

whenever i type in the vi ~/.profile
it loads the file i guess

i don't know how to execute the "export" command!!!

there is no prompt after loading the .profile
and i have no idea how to edit the file
or is this what i'm supposed to do or NOT!

i'm a complete mess :s

please HELPPPPPPPPPPPPPPPPPPPPPPPPP

---

### Post by kai60 on 2008-04-27
If you want to get the JVM or JDK to work, here is a link for that...

[http://java.sun.com/javase/6/webnotes/install/jdk/install-linux.html](http://java.sun.com/javase/6/webnotes/install/jdk/install-linux.html)

Good luck mate.

---

### Post by Maha1980 on 2008-04-27
so using the 
sh 
command is incorrect?
did i mess up the installation?

---

### Post by kai60 on 2008-04-27
I would always follow the instructions for proprietary stuff like this as they seem to work without fail.

Just check to see if you have the jre or jdk installed and then you can use the instructions on the link to make a reference in firefox to be able to access it, or of course you can just redo it quickly. :)

---

### Post by Maha1980 on 2008-04-28
how can i _undo _it first?

---

### Post by howlingmadhowie on 2008-04-28
you can install the jdk through the repositories. this will automatically configure your system to use it. 

if you have got the software from sun instead and installed it (though i thought that the .bin from sun's site was just a tarball with an extractor--it will just unpack itself to the directory where you install it), you will have to edit your $PATH so you can find it. 

to do this, create (if it doesn't exist already) the file '.profile' in your $HOME directory and add the following line to it:

```
PATH=/path/to/java/bin:$PATH
```

and after that (if you were using a terminal to edit the file):

```
source .profile
```

btw, if you're not used to vi, you may find it daunting. try using nano instead :)

---

