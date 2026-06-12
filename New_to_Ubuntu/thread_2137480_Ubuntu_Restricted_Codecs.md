---
title: "Ubuntu Restricted Codecs"
date: 2013-04-20
forum: New to Ubuntu
---

### Post by GUZZLR on 2013-04-20
Hello All,
First, I would like to say Hello to the community as this is the first post...hello.  I have heard of Ubuntu for a very long time now, I've just never messed with it before, until now due to Windows 8 and Office 2013 and lets not even go there.  At any rate, my first try was putting Ubuntu 12.04 on an Acer chromebook, which I later upgraded to 12.10 today.  I wish to install Ubuntu Restricted Extras; however when I try and install I'm told to remove: Libav codec library and Libav utility library.  Where do I find these items and how do I remove them?  I can not see them in my app section...I am an absolute beginner with this OS...sorry.  Also, Ubuntu gives me the option to Install Anyway...
Thoughts?
Thanks for the help

---

### Post by monkeybrain2012 on 2013-04-20
If you install restricted-extras these will be automatically removed and be replaced by libavcodecs-extras etc which include more functionalities. You don't need to find and remove them yourself.

For future references if you want to find packages, compare versions etc, you should install the synaptic package manager, it is much better for managing your software packages and faster than the Ubuntu Software Centre. You can either install it from the Software Centre or open a terminal and type

```
sudo apt-get install synaptic 
```

After that you will have no need for the USC. :)

---

### Post by deadflowr on 2013-04-20
+1 to what monkebrain2012 said.

Added, if you wanna try installing them through the terminal just
```
sudo apt-get install ubuntu-restricted-extras
```

Note, during the install, a eula for some fonts will appear, use the tab and/or spacebar left/right keys to check the yes or no and press enter
The installer for the extras won't proceed until this part is done with.

---

### Post by mikewhatever on 2013-04-20
The first is likely **libavcodec53**, and the second **libavutil51**. You can look for them in the software center, or just run:
```
sudo apt-get remove libavcodec53 libavutil51
```.

Also, installing the restricted-extras package in a termina should autoremove the above two.

---

### Post by Sef on 2013-04-21
> [COLOR=#000000] I can not see them in my app section..[/COLOR]

System Settings (gear and wrench (spanner)) then click on software sources, and make sure that restricted and multiverse are enabled.

Next, go to ubuntu software center and type in restricted, and choose ubuntu restricted and click install.

---

### Post by GUZZLR on 2013-04-21
Wow...that was quick responses...I'll try this stuff and see if my cheep Chrome/Ubuntu book throws up.  Thanks for the help

---

### Post by GUZZLR on 2013-04-22
> **mikewhatever said:**
> The first is likely **libavcodec53**, and the second **libavutil51**. You can look for them in the software center, or just run:
```
sudo apt-get remove libavcodec53 libavutil51
```.

Also, installing the restricted-extras package in a termina should autoremove the above two.

Hello,
When I run this, I get two commands I need to fill:
1. user@ChrUbuntu:~$ sudo bash
2. root@ChrUbuntu:~# THIS ONE I DO NOT KNOW WHAT TO INPUT HERE?

---

### Post by Impavidus on 2013-04-22
Forgive my my ignorance, but I can't find where anyone instructed you to run **sudo bash**. You can just install ubuntu-restricted-extras and it will automatically remove the other packages. I've never run **sudo bash** in over six years that Ubuntu is my primary system.

---

### Post by ArminasAnarchy on 2013-04-22
One of the things that I found confusing about this when I was new to Linux and the command line was how to "change" the option without a cursor to move around. It's tab key, btw. :D

If you want to save yourself the effort of having to install the restricted-extras package each time you get a clean install, you might want to have a look at Mint. It comes with Flash and Java installed by default, as well as the codecs. It's compatible with Ubuntu so you can still use any software you've come to love.

Also, if you change you desktop environment, you might want to know the package is just the same still :P I'm not a Unity user (I thought it looked awful from day 1, and then the whole thing with them sending your searches off to Amazon just cemented that opinion), I'm using XFCE (Xubuntu) at the moment. The package is therefore just 

```
xubuntu-restricted-extras
``` or ```
kubuntu-restricted-extras
``` etc

---

### Post by d4m1r on 2013-04-22
You do not need to do "sudo bash".....Only "sudo apt-get remove libavcodec53 libavutil51".

---

### Post by GUZZLR on 2013-04-22
ok...It worked. thank you

---

