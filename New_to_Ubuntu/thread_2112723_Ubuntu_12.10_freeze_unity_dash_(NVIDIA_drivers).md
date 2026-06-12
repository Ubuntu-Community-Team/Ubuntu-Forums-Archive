---
title: "Ubuntu 12.10 freeze unity dash (NVIDIA drivers)"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by Adonai Araya on 2013-02-05
First... my english is not good, sorry about all grammar mistakes ;)

Hello, I'm new in this forum and (sadly) in Linux. I installed Ubuntu 12.10 and all is perfect except for one little big problem, when I enter in the unity dash usually the system freeze and I can't do nothing but restart Ubuntu.

I read some post about it and I found (or I think I found) that the problem is my graphic card and the drivers.

I have a NVIDIA GeForce 6150SE nForce 430

I try the privative drivers of my graphic card but the was even worse because I barely can move the mouse at all.

Thanks for all ^^

---

### Post by omeomi on 2013-02-05
How did you install the Nvidia drivers and which ones did you install?

---

### Post by quailstorm on 2013-02-05
Startup Ubuntu and log in. So you've got kernel 3.7 if I'm right, and you've enabled the private repositories too. Also you've installed nvidia-current, and made a huge mistake.
For kernel 3.7, the only available driver is version 313, and it's in beta stage. It works well, I use it.

So after you logged in, and still unable to anything else than moving the cursor, press ctrl+alt+F2
login with your username and password
and type this:

```
sudo apt-get install nvidia-settings-313 nvidia-313 nvidia-313-dev
```

Computer will ask to reboot, and everything will be working.
You can remove old kernels to save space: [http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/]("http://www.liberiangeek.net/2011/11/remove-old-kernels-in-ubuntu-11-10-oneiric-ocelot/")

---

### Post by Adonai Araya on 2013-02-05
> **omeomi said:**
> How did you install the Nvidia drivers and which ones did you install?

I install the Nvidia drivers with the software source? (I don't know how is the english name for that, but by graphical mode).

Later I unintall all the private drivers that I installed before (by comand line) and come back to the open source driver that works fine except for the unity dash crash and that I can't play games (not a big problem for me anyway)

the driver -->  X.Org X server

[QUOTE=quailstorm]Startup Ubuntu and log in. So you've got kernel 3.7 if I'm right, and you've enabled the private repositories too. Also you've installed nvidia-current, and made a huge mistake.
For kernel 3.7, the only available driver is version 313, and it's in beta stage. It works well, I use it.

So after you logged in, and still unable to anything else than moving the cursor, press ctrl+alt+F2
login with your username and password
and type this:

```
sudo apt-get install nvidia-settings-313 nvidia-313 nvidia-313-dev
```

Computer will ask to reboot, and everything will be working.
You can remove old kernels to save space: [http://www.liberiangeek.net/2011/11/...neiric-ocelot/](http://www.liberiangeek.net/2011/11/...neiric-ocelot/)[/QUOTE]

I tried but the system said that it can't locate the packages nvidia-settings-313 nvidia-313 nvidia-313-dev

Maybe I did something wrong because I'm new on this and I have little experience with Ubuntu.


Thanks and sorry the troubles.

---

### Post by quailstorm on 2013-02-06
Currently, you haven't got any nVidia repositories added to your package manager.
```
uname -a
```
If this tells you: ```
3.7.0-7-generic
```
You can install nvidia-313 packages, if not, DO NOT INSTALL FOR YOUR OWN SAFETY. Kernel 3.7 is currently in a stable release state with Ubuntu 12.10.

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update 
```

Then you will be able to install them.

---

### Post by quailstorm on 2013-02-06
You can also add the nVidia private repository by creating a file named: ```
ubuntu-x-swat-x-updates-precise.list
```
in: ```
/etc/apt/sources.list.d/

```
Containing these two lines:
```
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu quantal main
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu quantal main
```

alt+F2 gksudo gedit

Then paste, and save the file.

---

### Post by Adonai Araya on 2013-02-10
> **quailstorm said:**
> You can also add the nVidia private repository by creating a file named: ```
ubuntu-x-swat-x-updates-precise.list
```
in: ```
/etc/apt/sources.list.d/

```
Containing these two lines:
```
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu quantal main
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu quantal main
```

alt+F2 gksudo gedit

Then paste, and save the file.

Thanks for the help quailstorm, but sadly it didn't work. Maybe I did something wrong (I'm a totally Linux noob)

First I use the ```
uname -a
```

it returned this 3.5.0-23-generic, so I have a previus version of the kernel I guess ?

So there is a solution for my problem ?

did you know if this problem will be resolve with the ubuntu 13.04 release ?

Thank you so much for the answers !

---

### Post by quailstorm on 2013-02-10
Yes it seems that you are using an older kernel. Also I don't know why did my computer autoupdated to 3.7, but I don't mind as long as it's working properly.

But nevermind, your VGA card will never get those updates.

The last driver that will work on your computer is:[http://www.geforce.com/drivers/results/51453]("http://www.geforce.com/drivers/results/51453")

You will have to install it via terminal with NO X11 running.

[First disable nouveau]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") (maybe you'll have to reboot, and will see an ugly software rendered shell in low resolution)
then press ctrl+alt+F2, login and type:
```
sudo stop lightdm
```
cd ~/Download/nvidia package  (just an example)
sudo ./nvidia package

The installer will guide you through the process, and after reboot, hopefully it will work. But I think, it doesn't support kernel 3.7.

---

### Post by Adonai Araya on 2013-02-11
Well... sadly It didn't work... but thank you all for the help ;)

In Ubuntu 13.04 I hope that somehow the problem will fix itself!

---

### Post by quailstorm on 2013-02-11
I don't think so. I'm using Ubuntu since 10.10 and there were always problems with nVidia drivers. But I was able to solve it, and my cousin too. So it wasn't really difficult, and worth the time, because the performance got better and better with every update.
I remember that on 11.04, every kernel update broke the whole x-server, and all I got after reboot, was an only text terminal...

Also I don't have more advices for you, if you can't give further information on how did you fail with the install process. Also don't expect me to be a linux pro, I'm just a home user, but nobody responded to your thread, and I had similar issues in the past, but I have a currently actively supported card, a GTS450.

Off topic:
This is the first time I'm seeing the forum on windows XP. The fonts look really strange and furry. On ubuntu, some websites like [mobilarena.hu]("http://mobilarena.hu/") has similar font problems... What's this font/OS war?

Maybe you'll have to go back to Windows 7 that "died on you PC". I still can't work without at least XP and win7, but linux is also necessary for me. What about a dual boot, and you can fix the driver issues whenever you want, and you still have a working stable and reliable operating system. For me, linux isn't it... After apt-get died with no reason, I can't understand why my friend changed to ubuntu from windows because it's more stable. Although, I'm a professional windows user, and currently my XP and win7 are 2,5 years old...

---

### Post by andrasszoke on 2013-05-04
Hi!

I have the same problem under 13.04, I have nvidia c73 (geforce7100/nforce 630i) and it freezes randomly when I use unity icons, the system is pretty slow anyway. I use the opensource x-org driver, with the closed one it's much slower. The kernel is 3.8.0-19. Do you have any idea?
thanks for your attention,

Andras.

---

### Post by quailstorm on 2013-05-04
> **andrasszoke said:**
> The kernel is 3.8.0-19. Do you have any idea?
thanks for your attention,

Andras.

Sorry but no support for that new kernel with the closed source drivers. The last is maybe 3.5 or 3.2. I think You'll have to downgrade Ubuntu to an older version...

nVidia nem fogja frissíteni a drivert, nem tudsz mit tenni mint visszamenni egy korábbi ubuntura, vagy elt&#369;rni. Esetleg új videókártya...
A videódrivert újra kell fordítani minden kernel alverzióhoz, és ilyen régi eszközhöz már legacy support sem jár. A nyílt driver meg szar volt mindig is... Nekem GTS450-em van, arra remek fejlesztések vannak, a váltáson kívül nem tudok mást javasolni, sajnálom.

---

### Post by quailstorm on 2013-05-04
You could also take a look at here: [http://ubuntuforums.org/showthread.php?t=2106616](http://ubuntuforums.org/showthread.php?t=2106616)
[http://ubuntuforums.org/showthread.php?t=2097058&page=4&p=12417951#post12417951](http://ubuntuforums.org/showthread.php?t=2097058&page=4&p=12417951#post12417951)

Maybe you can find a solution.

---

