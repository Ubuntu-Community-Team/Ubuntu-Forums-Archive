---
title: "How to install Mono Develop 2.2"
date: 2010-02-07
forum: Programming Talk
---

### Post by hoboy on 2010-02-07
I have installed mono from the repository
but is want to install mono from here

[http://monodevelop.com/](http://monodevelop.com/)
can any help me with how to do that ?

---

### Post by Badingo on 2010-02-09
The Ubuntu section of the MonoDevelop website says, "MonoDevelop 2.2 is available in Ubuntu 10.4.", if you can wait a few months.
 
Here is some guidance for some packages out there I haven't tried yet:
 
[http://superuser.com/questions/84697/how-to-install-monodevelop-2-2-on-ubuntu-9-10](http://superuser.com/questions/84697/how-to-install-monodevelop-2-2-on-ubuntu-9-10)
 
[https://launchpad.net/~directhex/+archive/monoxide/+packages](https://launchpad.net/~directhex/+archive/monoxide/+packages)
 
I am also looking into compiling the source code directly, but have never done that before, so any instructions or guidance from others would be appreciated.

---

### Post by Badingo on 2010-02-10
1. From terminal or command prompt type:
```
[FONT=Consolas]sudo add-apt-repository ppa:directhex/monoxide[/FONT]
```
 
2. Then to update the aptitude source list type from terminal or command prompt :
```
sudo aptitude update
```
 
3. From The Sytem menu:
System>Administration>Synaptic Package Manager
 
4. From within Synaptic Package Manager click on the Origin button.
 
5. The list box above should contain at least:
ppa.launchpad.net/main
ppa.launchpad.net/universe
 
We are interested in these two as they contain the Monoxide packages:
monodevelop - 2.2+dfsg-2~dhx1~karmic1 (changes file) 2010-01-19 Published Karmic Devel 
monodevelop-boo - 2.2-1~dhx1~karmic1 (changes file) 2010-01-19 Published Karmic Devel 
monodevelop-database - 2.2+dfsg-1~dhx1~karmic2 (changes file) 2010-01-19 Published Karmic Cli-mono 
monodevelop-debugger-gdb - 2.2-1~dhx1~karmic1 (changes file) 2010-01-19 Published Karmic Cli-mono 
monodevelop-debugger-mdb - 2.2-1~dhx1~karmic1 (changes file) 2010-01-19 Published Karmic Cli-mono 
monodevelop-java - 2.2-1~dhx1~karmic1 (changes file) 2010-01-19 Published Karmic Cli-mono 
monodevelop-python - 2.2-1~dhx1~karmic1 (changes file) 2010-01-19 Published Karmic Devel 
monodevelop-vala - 2.2-1~dhx1~karmic1 
 
from [https://launchpad.net/~directhex/+archive/monoxide](https://launchpad.net/~directhex/+archive/monoxide)
 
6. Select the above packages or the ones you want and mark them for installation and click on the Apply command bar icon (green check I think).
 
7. Open MonoDevelop and note version 2.2. I was able to create and run a simple "Hi" program with requisite label and button...

---

### Post by NikolajSkov on 2010-02-25
Thanks Badingo, it works!

---

### Post by Gouz on 2010-04-14
Badingo thank you

I have been using mono for few months now.

Please told me you can not run C# in Linux install windows but no.. I do not want to :)

thank you all in Mono you are great

the new version is cool :P

---

