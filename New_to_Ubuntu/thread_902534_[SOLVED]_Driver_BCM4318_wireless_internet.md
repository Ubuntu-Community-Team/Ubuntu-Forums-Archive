---
title: "[SOLVED] Driver BCM4318 wireless internet"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by Bonbonbloc on 2008-08-27
Hello,

I am completely new to the linux system. I installed ubuntu a couple days ago on my computer and I thought with some internettutorials I should be able to find my way somehow. But there started my first problem and al the other problems so far are caused by this first problem.

My computer had (when it driverd on windows xp) a wireless connection with my router. I am not able to go wired due some problems (called parrents). So I do need the wireless thing. But ubuntu can't connect to my router somehow. I tryed to type the details in myself to connect to it but it just doesn't work. It ask's me everytime again for the wepkey. Then I type it in again and it searches and then it askes again for the key.

So I thought maybe the thing needs a driver. So I searched for drivers and how stupid it may be I found a driver and with some help of a friend I actually installed it and then I found out it was for my lan card and not for my wlan card. So I searched again.

And there starts the big problem. I found out that my wlan card is a BCM4318 and I found out that there are only windows drivers. Or I just can't find the linux version but I read on some fora that there aren't linux drivers. Now I searched further and I found out there is this program for linux called ndiswrapper. With this program installed I should be able to install a windows driver on my linux system and then hopefully my wireless internet works.

But I don't have a clue how to install it. I did found a version on the internet of ndiswrapper but I got some errors like can't leave the directory after the installation and then the complete installation quits and nothing is installed (I did this installation by the readme file).

Can someone please help me with a good how to install the ndiswrapper and then install my driver? And maybe if someone knows where to find the good install of the ndiswrapper and the driver (maybe the files are corrupt I don't know).

I don't know what command's to use I am completely new to the linux system, I just found some commands and with a good explanation I should be able to find my way. But I am really stuck here. Cause I can't even listen music cause I need a codec plugin but without the internet I can't download it. And wired internet is really not a option so please don't start about wired.

Can someone please help me?

---

### Post by Het Irv on 2008-08-27
[http://ubuntuforums.org/showthread.php?t=262201](http://ubuntuforums.org/showthread.php?t=262201)

See if this thread and the one it links to helps you any.

---

### Post by RequinB4 on 2008-08-27
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

A dead horse could do it with this link :guitar:

---

### Post by Bonbonbloc on 2008-08-27
Thanks, it's a clear explanation but I got stuck there to. I got [http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482) the stable version there. I unzipped it on my laptop with windows and then got it in to my ubuntu system. But the command in that tutorial doesn't work and the readme file with the files don't work either. It says to go in to the diretory. I got in. Then type make install when I do this I get:

make -C driver install
make[1]: Entering directory `/home/chocolaatje/Bureaublad/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.24-19-generic M=/home/chocolaatje/Bureaublad/ndiswrapper-1.53/driver
make[2]:Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
     Building modules, stage 2.
     MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
echo /lib/modules/2.6.24-19-generic/misc
/lib/modules/2.6.24-19-generic/misc
mkdir -p /lib/modules/2.6.24-19-generic/misc
install -m 6044 ndiswrapper.ko /lib/modules/2.6.24-19-generic/misc
install: cannot remove `/lib/modules/2.6.24-19-generic/misc/ndiswrapper.ko': Permission denied
make[1] *** [install] Error 1
make[1] Leaving directory `/home/chocolaatje/Bureaublad/ndiswrapper-1.53/driver'
make: *** [install] Error 2

oh and Bureaublad is destkop :D I have the dutch version here :).

But what does it mean's or what am i doing wrong?

---

### Post by Het Irv on 2008-08-27
Did you use "sudo" with any of those commands
that looks like your problem

---

### Post by Bonbonbloc on 2008-08-27
Yes I do use sudo, what do I have to use then?

Oh wait not with these commands I did use it with other commands.

Here it says:

make uninstall
  make

Login as root and run
  make install

Login as root I use sudo bash... maybe I need something else? With that make uninstall I get:

cannot remove `/lib/modules/2.6.24-19-generic/misc/ndiswrapper.ko': permission denied....

---

### Post by Het Irv on 2008-08-27
Technically in Ubuntu you do not login as root, you use sudo before each command to elevate your current user to root status.  

And just in case you ask, yes you can do some things to enable logging into root, but that is not recomended, and is not supported by these forums.

---

### Post by Bonbonbloc on 2008-08-27
But now I have this in the info:

make uninstall
make

Login as root and run
make install

so I used sudo make uninstall and that one worked. But the make I get a error, even if I use sudo make.

Both I get an error like:

make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/chocolaatje/Bureaublad/ndiswrapper-1.53/utils'
make: *** [all] Error 2

Same error apears when I use:

make install or sudo make install

So what to use then? Or what's wrong?

---

### Post by Het Irv on 2008-08-27
I am not sure what to make of that... let me ask around.

---

### Post by Bonbonbloc on 2008-08-27
Shure :) I'll be waiting here haha.

---

### Post by Het Irv on 2008-08-27
Alright try this...
```
sudo apt-get update && sudo apt-get upgrade
```

after that finishes

```
sudo apt-get install build-essential
```


The first part will look for updates and install them, the second will install some things you might be missing that are needed to successfully run make.

---

### Post by Bonbonbloc on 2008-08-28
Euhm there is a problem there... I don't have internet on the ubuntu pc... so the first command doesn't work.

So the second one also doesn't work...

---

### Post by Het Irv on 2008-08-28
Doh! My bad, I typed that while at work, to many support calls, not enough brain cells.  Luckly, there is another way.  

The build-essential package is on the Ubuntu Live CD.  I don't have one in right now, but I know it is in there somewhere.  I think it in the Packages folder under the subfolder "B".  Install it from there and try again.

---

### Post by RequinB4 on 2008-08-28
> **Het Irv said:**
> Doh! My bad, I typed that while at work, to many support calls, not enough brain cells.  Luckly, there is another way.  

The build-essential package is on the Ubuntu Live CD.  I don't have one in right now, but I know it is in there somewhere.  I think it in the Packages folder under the subfolder "B".  Install it from there and try again.

Or you can simply add the livecd as a repository in system - admin - software sources.

Or go to another computer and go to packages.ubuntu.com, download the deb from there, transfer it to the other computer, and install.

---

### Post by Bonbonbloc on 2008-08-28
Well so far I got a bit closer :D thanks for the help so far.

I got to that site and got the ndiswrapper-common.deb and the ndiswrapper-utils-1.9.deb

I typed:

sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

This didn't worked so I thought lets try them seporately.

sudo apt-get install ndiswrapper-common

I get: Couldn't find ndiswrapper-common
When I typed:

sudo apt-get install ndiswrapper-utils-1.9

It actually installed :P yaay. So I am halfway now cause the ndiswrap-command still doesn't work so I need to get the common file installed to. Still working on that one now. If you see me doing anything wrong here please tell haha.

---

### Post by RequinB4 on 2008-08-29
You can just double click the deb you got from packages.ubuntu.com

---

### Post by Bonbonbloc on 2008-08-29
Thanks for that tip :D I got it installed now finally.

But ghehe it still doesn't connect to my router. Isn't there any scan or something? So he will search for all the available wireless connections in the nabourhood?

---

### Post by RequinB4 on 2008-08-30
You have to follow all of the instructions in that link I posted, then restart.  If you don't, ubuntu will accidently load the bad drivers instead of the ones you want.

here is it again: [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by Bonbonbloc on 2008-08-30
I have internet!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Yay :D thank you very much all of you :D finnaly ghehe. Thank you Thank you :D

---

### Post by RequinB4 on 2008-08-30
> **Bonbonbloc said:**
> I have internet!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Yay :D thank you very much all of you :D finnaly ghehe. Thank you Thank you :D


:guitar:

Glad you made it!

Please mark this thread as solved ([http://ubuntuforums.org/showpost.php?p=4527051&postcount=6](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6))

---

