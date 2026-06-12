---
title: "java enviromental variables"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Maha1980 on 2008-04-27
i installed java on my machine
i use ubuntu 8.04
machine is dell inspiron 1525

i'm a complete newbie

i successfully installed java
i opened the terminal and entered
vi ~/.profile
and also tried 
vi ~/.bash_profile

some lines come up and don't know how and when to start typing these commands:
export JAVA_HOME ...etc

this is so weird :(

---

### Post by txcrackers on 2008-04-27
Firstly, *vi* is a screen-based text editor. Since you don't seem to have used it before, I would recommend **not** using it - try *gedit* instead.

Secondly, once you have Java installed, you generally will not need to set **JAVA_HOME** except in some very rare instances. If you do need to set it (according to some specific software requirements), again I would recommend using *gedit* in place of *vi*.

---

### Post by Maha1980 on 2008-04-27
i'm trying to test an example
so i type in the terminal
ATM
the example name
and it didn't work

---

### Post by RealPSL on 2008-04-27
I agree with the previous poster that gedit is a lot simpler to use than vi/vim. If you really want to use vi then you can find many tutorials online e.g.

[http://www.eng.hawaii.edu/Tutor/vi.html]("http://www.eng.hawaii.edu/Tutor/vi.html")

If you give us a little more details on the variables you are trying to set at the terminal we may be able to help more.

---

### Post by Maha1980 on 2008-04-28
JAVA_HOME
PATH

aren't they the variables that i need to set, in order to make
j2se works!?

---

### Post by RealPSL on 2008-04-28
You can add to your local environment by using ```
gedit ~/.profile
``` while logged in as the user you want to make the modifications for.

You can add the lines below to your .profile so they are set each time you login to the system

```
JAVA_HOME=/path_jdk_installation; export JAVA_HOME
PATH=$PATH:$JAVA_HOME/jre/bin; export JAVA_HOME
```


You can also type the 2 lines above at the terminal for testing purposes.

---

