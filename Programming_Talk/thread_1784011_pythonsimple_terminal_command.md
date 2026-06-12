---
title: "python:simple terminal command"
date: 2011-06-16
forum: Programming Talk
---

### Post by deadpieface on 2011-06-16
I have searched and cannot find exactly the right info to do this.  While I know this is extremely simple....anyway. I know this is probably pretty lame but I am okay with that.

I want to open a terminal and preform this command via a python script.

java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame

the code i have is this and it does not work:

> 
import subprocess

pid = subprocess.Popen(args=[
    "gnome-terminal", "--command=java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame"]).pid
print pid


---

### Post by cgroza on 2011-06-16
An error message would be very helpful.

---

### Post by deadpieface on 2011-06-16
There are no errors.  It runs the code.  A terminal window will pop open for a fraction of a second and then it closes. 

If I remove this :

```
, "--command=java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame"
```

a terminal will open just fine.  So the above part is not inputing the command in the terminal and running it.  I need that to happen.  So I will continue to see what I can get going on.

Thanks

---

### Post by geirha on 2011-06-17
In gnome-terminal's settings, set that it should not close the terminal when the command finishes. That way you'll see what error message, if any, the java command outputs.

---

### Post by deadpieface on 2011-06-17
> **geirha said:**
> In gnome-terminal's settings, set that it should not close the terminal when the command finishes. That way you'll see what error message, if any, the java command outputs.

This is what it says, and thanks by the way. I never thought about doing that at all.


```
Exception in thread "main" java.lang.NoClassDefFoundError: net/minecraft/LauncherFrame
Caused by: java.lang.ClassNotFoundException: net.minecraft.LauncherFrame
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
Could not find the main class: net.minecraft.LauncherFrame. Program will exit.


```

I found that when i run that command in /home i get the same result but when i switch to /home/Myusername it works.  So I guess I just need to cd /home/Myusername first.  but I am not sure how to issue that command then the second one properly.

---

### Post by epicoder on 2011-06-17
You could use os.chdir and then call java directly from the Popen call.
```
import os, subprocess
os.chdir("/home/Myusername")
pid = subprocess.Popen(args=[
"/usr/bin/java", "-Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame"]).pid
print pid
```I may or may not be doing the Popen call correctly, I've never used subprocess before.

---

### Post by deadpieface on 2011-06-17
> **sh228 said:**
> You could use os.chdir and then call java directly from the Popen call.


I am not sure what that did, but it did not run it.  There were no errors though.

I have the command to open a terminal. What would the next code be to input a line into the terminal and running it?

---

### Post by geirha on 2011-06-18
Either do a chdir, then run you previous Popen call, or provide the absolute path to that jar-file. E.g.:
```

import os
import subprocess

jarfile = os.path.expanduser("~/minecraft.jar")
proc = subprocess.Popen(
    ["gnome-terminal",
     "--command=java -Xmx1024M -Xms512M -cp %s net.minecraft.LauncherFrame" % (jarfile,)]
)

```
The pid won't be useful to you btw. That gnome-terminal process will find and connect to the main gnome-terminal process, tell it to open a new terminal window to run your java command, and then it dies.

---

### Post by deadpieface on 2011-06-18
> **geirha said:**
> provide the absolute path to that jar-file. E.g.:


You my friend are a genius or something much more resourceful than me.  I appreciate your help.  Now I am going to make an icon for it.

Thanks again.:popcorn:;):P:guitar:

Do you happen to know how I would make the command in the launcher?  I am going to research it but just in case you know and it is easy....

---

### Post by kagov on 2011-06-18
> **deadpieface said:**
> You my friend are a genius or something much more resourceful than me.  I appreciate your help.  Now I am going to make an icon for it.

Thanks again.:popcorn:;):P:guitar:

Do you happen to know how I would make the command in the launcher?  I am going to research it but just in case you know and it is easy....

Are you referring to the class 'Launcher'? If so then you'd need to either decompile, modify, then recompile, or use a bytecode library such as object web's ASM. However this is only if the icon is not held locally, unless there are other ways to override it which I don't know about.

---

### Post by geirha on 2011-06-18
> **deadpieface said:**
> Do you happen to know how I would make the command in the launcher?  I am going to research it but just in case you know and it is easy....

Make sure your python script has a shebang, e.g. the absolute first line should read
```
#!/usr/bin/env python
```
and make the script executable. Then, when you create the launcher, browse to your script and select it as the command.

---

### Post by deadpieface on 2011-06-18
> **geirha said:**
> Make sure your python script has a shebang, 


When I do, that nothing happens.

this is my script:
```
#!/usr/bin/env python

import os
import subprocess

jarfile = os.path.expanduser("~/minecraft.jar")
proc = subprocess.Popen(
    ["gnome-terminal",
     "--command=java -Xmx1024M -Xms512M -cp %s net.minecraft.LauncherFrame" % (jarfile,)]
)
```

I created a launcher and selected the tester.py file.

I used this to make the file executable:

chmod +x tester.py

that correct?

---

### Post by geirha on 2011-06-18
That looks right. Check ~/.xsession-errors for clues as to why it didn't work. ```
tail ~/.xsession-errors
```

BTW. If that's all your python script is supposed to do, you don't really need it. Just run the java command in the launcher, and set the launcher type to "Application in terminal" (or whatever it's called).

---

### Post by deadpieface on 2011-06-18
> **geirha said:**
> 
BTW. If that's all your python script is supposed to do, you don't really need it. Just run the java command in the launcher, and set the launcher type to "Application in terminal" (or whatever it's called).

That did it! Thank you, I really appreciate your time and help!

I am still going to try and figure out the other way just to see....

---

