---
title: "E: Couldn't find package pstack"
date: 2013-09-13
forum: New to Ubuntu
---

### Post by Bernhard_Hustomo on 2013-09-13
Hello, this is my first post.

I have problem installing pstack on Lucid 10.04.4 64-bit (TC 2012 x86_64 GNU/Linux | Ubuntu 10.04.4 LTS)

I did sudo apt-get install pstack and the output is:

[COLOR=#ff0000]Reading package lists... Done[/COLOR]
[COLOR=#ff0000]Building dependency tree[/COLOR]
[COLOR=#ff0000]Reading state information... Done[/COLOR]
[COLOR=#ff0000]E: Couldn't find package pstack[/COLOR]

I tried to find the solution on the internet, but I couldn't find one, at least a step-by-step procedure to solve this issue.

So, thanks for any answer or references about the solution. Thank you.

PS: the purpose of this installation is to be able to create zmdiaglog (Zimbra log requested by Zimbra support regarding our company login issue)

---

### Post by ibjsb4 on 2013-09-14
This package is only offered as a 32bit package in 10.04.

[http://packages.ubuntu.com/lucid/pstack](http://packages.ubuntu.com/lucid/pstack)

---

### Post by claracc on 2013-09-14
As 10.04 has reached its EOL support, when you want to install any software package, you have to write the correct address where the repositories have been moved, i.e.: [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

Please, read the following link: [http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release) in order to know how

I recommend you to install a supported ubuntu as 12.04, 12.10 or 13.04 since you are at security risk using lucid lynx, also you cannot expecto to receive any security update

---

### Post by Elfy on 2013-09-14
If this is a server release,  EOL is April 2015

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

As ibjsb4 says - the package is there for 32bit - [http://packages.ubuntu.com/lucid/pstack](http://packages.ubuntu.com/lucid/pstack)

---

### Post by sanderj on 2013-09-14
> **ibjsb4 said:**
> This package is only offered as a 32bit package in 10.04.

[http://packages.ubuntu.com/lucid/pstack](http://packages.ubuntu.com/lucid/pstack)

pstack's man page says it's a 32-bit only program, so independent of the Ubuntu version:

>  RESTRICTIONS
       pstack currently works only on Linux, only on an x86 machine running 32 bit ELF binaries (64 bit not supported).

The weird thing is that I installed and run it on my 64-bit Ubuntu (without any useful output, I must say). So, why make a program installable on a 64-bit system if the man page says it does not work? Or is the man page out of date?


```

sander@flappie:~$ sudo pstack 2623

2623: chromium-browser --type=plugin --plugin-path=/usr/lib/flashplugin-installer/libflashplayer.so --lang=en-US --channel=2339.7....
(No symbols found)
crawl: Input/output error
Error tracing through process 2623
0x7f577ca2f3cd: ????sander@flappie:~$ 
sander@flappie:~$ 
sander@flappie:~$ uname -a
Linux flappie 3.8.0-30-generic #44-Ubuntu SMP Thu Aug 22 20:52:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
sander@flappie:~$

```

---

### Post by ibjsb4 on 2013-09-14
[QUOTE=sanderj;12788325]The weird thing is that I installed and run it on my 64-bit Ubuntu (without any useful output, I must say). So, why make a program installable on a 64-bit system if the man page says it does not work? Or is the man page out of date?

Don't know whats up with the man page, but 12.04 carries the 64bit version.

EDIT: found this

[https://bugs.launchpad.net/ubuntu/+source/pstack/+bug/532000](https://bugs.launchpad.net/ubuntu/+source/pstack/+bug/532000)

---

