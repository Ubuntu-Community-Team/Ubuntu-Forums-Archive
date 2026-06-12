---
title: "java vm path"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by PacoCrespo on 2008-04-30
Hello, 

I need to install a .bin package and I always get:

"Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to
running this program."

but I have just install the java virtual machine 1.6 and restart my pc, i think that the environment variable JAVA_HOME is empty cause after
"echo $JAVA_HOME" 
in a terminal I don't get a thing

Please, can anybody give me some help

Thanks a lot

---

### Post by RealPSL on 2008-04-30
In this case the program is looking for the path to java to be specified in the PATH variable. For example if you install the java binary to /opt/java/bin the your PATH variable should be modified to reflect that with 

```
export PATH=$PATH:/opt/java/bin
```

The above is temporary at the terminal. Once you have confirmed it works you can make it permanent by editing your $HOME/.profile with gedit and adding the above line at the end.

The standard java installation with Ubuntu is placed in the path. Where did you install your Java VM.

---

### Post by PacoCrespo on 2008-05-01
I've been searching where my java VM is and I can't find it, perhaps I should reinstall it in the path that /opt/java/bin but I don't know how.

Thanks in advance...

---

