---
title: "Java executables???"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by jeffinhedon on 2008-05-07
Hello again
can someone point me in the right direction please
I 've been reading these threads for ages and just cant find the answer!!!!
The problem.
I have installed a prog which uses java
but I can only run the program by using the terminal and command line
for example
java -jar "prog-name" jar
Can I create an executable link that will either go into the menus
or onto the desktop ...so I can just click to activate and run the prog????:confused:
I think I have java installed and running OK
Any advice will be very much appreciated
Thanks in advance:)

---

### Post by kpkeerthi on 2008-05-07
Does this program has a GUI or is it only command-line oriented?

---

### Post by jeffinhedon on 2008-05-07
> **kpkeerthi said:**
> Does this program has a GUI or is it only command-line oriented?

The jar file contains 2 folders
META-INF  which appears to be a manifest
COM which has the following folders in it
HAMSPHERE (prog name)
RADIO which contains 31 class types files

Cant see any thing that looks like GUI??

Does that help at all???

---

### Post by Xiong Chiamiov on 2008-05-07
You can create a shell file that only has one command, being the one you've been entering.  For example:
```

gksudo gedit /usr/bin/foo

```
In that file, put
```

#!/bin/bash
cd /home/user/wherever_it_is
java -jar "prog-name" jar

```
If it's a GUI, then I think you should add "exit 0" to the end of the file.
Make sure it's executable:
```

sudo chmod +x /usr/bin/foo

```
This will then be accesible simply by typing "foo" into a run dialog.  From there you should be able to create a menu item and tell it to launch "foo".

---

### Post by jeffinhedon on 2008-05-08
Well done 
Thanks for all the Advice
The program is now working perfectly from a menu item as well
Thanks once again

---

