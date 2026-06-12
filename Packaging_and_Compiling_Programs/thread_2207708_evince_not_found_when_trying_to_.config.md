---
title: "evince not found when trying to ./config??"
date: 2014-02-24
forum: Packaging and Compiling Programs
---

### Post by antman2 on 2014-02-24
Hello.
Recently I've been learning the ropes in extracting and compiling in ubuntu thanks to my determination to install Denemo(music transcript software)

 (instructions) [http://linuxg.net/how-to-install-denemo-1-0-4-on-ubuntu-linux-mint-and-debian/](http://linuxg.net/how-to-install-denemo-1-0-4-on-ubuntu-linux-mint-and-debian/)

The instructions were helpful and I'm trying to run ./configure and been through a couple hurdles in installing libxml and whatnot and I installed evince, but when I ran ./configure again, I get this!

checking for EVINCE_2_0... no
checking for EVINCE_2_30... no
checking for EVINCE_2_32... no
configure: error: Package requirements (evince-view-2.32 >= 2.0) were not met:

No package 'evince-view-2.32' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EVINCE_2_32_CFLAGS
and EVINCE_2_32_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.




Now what am I supposed to do?  It would be really helpful if you guys can provide me with something to paste onto my terminal that would fix this. 

Thank you

---

### Post by zvacet on 2014-02-25
Try to install **libevince-dev** package.Maybe that will help.

 Did you tried second method on that link?

---

### Post by oldos2er on 2014-02-25
Moved to Packaging & Compiling Programs.

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by epikvision on 2014-02-25
I second that, since it seems that your computer probably doesn't have evince in your computer. It's as easy as:

```
 sudo apt-get install libevince-dev 
```

What Ubuntu version are you running? I can find out the latest supported package for your system and see if you can install it.

---

### Post by zvacet on 2014-02-26
You can do this (I tried just to be sure)

```
wget -c denemo.org/downloads/denemo-1.1.0-0.linux-x86
chmod +x denemo-1.1.0-0.linux-x86
./denemo-1.1.0-0.linux-x86
```

You will run it with 

```
/home/user_name/bin/denemo
```

Of course **user_name** is your username.You can even make launcher if you want to. ;)

---

