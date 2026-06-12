---
title: "adobe flash player 10 installation"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by Matt26 on 2008-07-21
has anyone been able to successfully install Adobe Flash Player 10 beta 2 yet?  i downloaded it from the adobe labs site and started to install it, but when i get to the portion of the install where it asks for the installation directory of Firefox i am stuck- i tried /home/username/.mozilla but i get an error message saying the directory is invalid/incorrect.

so where is FireFox installed?

thanks.

---

### Post by silkstone on 2008-07-21
Look at this tutorial...

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

... and scroll down to the section headed 'Troubleshooting - Adobe Flash Player'.

That gives instructions for installing Flash 10 beta, and it works fine for me. However, you may get better results with beta 1 than beta 2 - you can always copy the alternative .so file over if you like.

---

### Post by WRDN on 2008-07-21
Firefox is installed in /usr/lib/firefox-3.0
The flash plugin however, is installed in /usr/lib/flashplugin-nonfree

---

### Post by bumanie on 2008-07-21
I think adobe has a final release of flash 10 for linux. I installed it two days ago to my ubuntu box via a .tar.gz download - I'm at work and  can't double check the version on my box. It is the only thing that got you tube working - falsh 10 beta did not work for me.

---

### Post by gandaran on 2008-07-21
> **WRDN said:**
> Firefox is installed in /usr/lib/firefox-3.0
The flash plugin however, is installed in /usr/lib/flashplugin-nonfree

it's installed there when you install the flashplugin-nonfree from the repos 

the adobe tarball, you either choose to install to the hidden home .mozilla/plugins folder or /usr/lib/mozilla/plugins folder.
you can run the installer or just unpack/extract the tar.gz package and drag the libflasplayer.so file to any of the mentioned plugins folders.

---

### Post by gandaran on 2008-07-21
> **bumanie said:**
> I think adobe has a final release of flash 10 for linux. I installed it two days ago to my ubuntu box via a .tar.gz download - I'm at work and  can't double check the version on my box. It is the only thing that got you tube working - falsh 10 beta did not work for me.

where did you get it? I only could find the 10 beta 2!

---

### Post by Matt26 on 2008-07-21
> **gandaran said:**
> where did you get it? I only could find the 10 beta 2!

same here- i have looked around different sites and haven't found mention yet of any official linux version of flash player 10..

---

### Post by bumanie on 2008-07-21
As said, I'm at work and can't check the exact version I have on my ubuntu box. Have a look here [http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)
I may be mistaken with the version I got - but I know that it fixed you tube video when nothing else would. Possibly it is the beta 2 version - sorry, my memory is not too lucid at present as I only had two hours sleep today due to working and study.

---

### Post by silkstone on 2008-07-21
I think you'll find that the latest version is beta 2, released on 02 July.

---

### Post by Matt26 on 2008-07-21
> **bumanie said:**
> As said, I'm at work and can't check the exact version I have on my ubuntu box. Have a look here [http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)
I may be mistaken with the version I got - but I know that it fixed you tube video when nothing else would. Possibly it is the beta 2 version - sorry, my memory is too lucid at present as I only had two hours sleep today due to working and study.

i believe the link you provided is for version 10 beta 2 (the URL in the instructions points to adobe's lab site).. i tried looking at this site last night as well.

---

### Post by billgoldberg on 2008-07-21
> **Matt26 said:**
> has anyone been able to successfully install Adobe Flash Player 10 beta 2 yet?  i downloaded it from the adobe labs site and started to install it, but when i get to the portion of the install where it asks for the installation directory of Firefox i am stuck- i tried /home/username/.mozilla but i get an error message saying the directory is invalid/incorrect.

so where is FireFox installed?

thanks.

```
cd /tmp
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz
tar -zxvf flashplayer10_install_linux_070208.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer
```

Will do download it and start the install script. Just answer yes or no as you see fit.

**You'll need to remove flash plugin from /home/user/.mozilla before doing it though.**

---

### Post by bumanie on 2008-07-21
Oh well, that was probably what I downloaded - didn't notice the beta 2 to be honest, may be I was not observant, but I was happy that you tube finally worked. :)

---

### Post by lswb on 2008-07-21
If you enable the hardy backports repositories you can install it with apt-get or synaptic. Be forwarned that there is a bug in the version 10 player that crashes firefox on many web sites.

---

### Post by silkstone on 2008-07-21
> **lswb said:**
> If you enable the hardy backports repositories you can install it with apt-get or synaptic. Be forwarned that there is a bug in the version 10 player that crashes firefox on many web sites.

That's with beta 2. If you can find beta 1 somewhere (I've seen a link to it in another thread here), that should work fine.

---

### Post by Bucky Ball on 2008-07-21
During installation using Billgoldburg&#347; method, I get this;

> Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla    

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): 

... although /usr/lib/mozilla does exist, therefore a valid path I guess. Everything seems to be on the right track, though.  Installed Flash on my laptop ok (don´t remember how though!) but having trouble with the desktop (both booting Hardy 8.04). Any suggestions anyone?

---

### Post by Matt26 on 2008-07-21
> **Bucky Ball said:**
> During installation using Billgoldburg&#347; method, I get this;



... although /usr/lib/mozilla does exist, therefore a valid path I guess. Everything seems to be on the right track, though.  Installed Flash on my laptop ok (don´t remember how though!) but having trouble with the desktop (both booting Hardy 8.04). Any suggestions anyone?

that was the same message i got trying to install version 10 beta 2 using the URL provided in this thread- however i was using /home/name/.mozilla as the install directory which i thought might have been incorrect... please post back if you succeed with your install.

---

### Post by Bucky Ball on 2008-07-21
Scratch all that. Tried exactly the same thing by running the installer. Didnt bother with asking me for a path this time, the installer just picked one. I clicked yes, all installed fine and I was told to remove xpti.dat from mozilla components, log out and restart session.

Following this, when I logged in again, youtube worked fine and goes to full screen too (something my laptop doesnt do, for some reason).

So thanks, billgoldberg, for the quick fix. :)

And Matt26, that is right. the path the installer chose, was as you mention, /home/name/.mozilla

---

### Post by Ptero-4 on 2008-07-21
The install dir IIRC is ~/.mozilla/firefox or /usr/lib/firefox. The script actually considers valid any dir that contains a "components" and a "plugins" directory within it (that's the directory structure firefox uses to store it's plugins).

---

### Post by Matt26 on 2008-07-21
> **Bucky Ball said:**
> Scratch all that. Tried exactly the same thing by running the installer. Didnt bother with asking me for a path this time, the installer just picked one. I clicked yes, all installed fine and I was told to remove xpti.dat from mozilla components, log out and restart session.

Following this, when I logged in again, youtube worked fine and goes to full screen too (something my laptop doesnt do, for some reason).

So thanks, billgoldberg, for the quick fix. :)

And Matt26, that is right. the path the installer chose, was as you mention, /home/name/.mozilla

that's interesting- i have attempted the install a number of times and it has always asked me where the install directory is for Firefox... i wonder if i'm using a different installer than the one provided in the steps listed..

---

### Post by Matt26 on 2008-07-21
i got the latest flash player installed- unfortunately Firefox has started crashing again every few minutes so i need to uninstall it- i tried removing the files for the flash player:

cd ~/.mozilla
$ rm flashplayer.xpt libflashplayer.so

but i get an error message saying that there is no such file or directory- how can i uninstall the flash player now?

thanks.

---

### Post by Matt26 on 2008-07-21
> **Matt26 said:**
> i got the latest flash player installed- unfortunately Firefox has started crashing again every few minutes so i need to uninstall it- i tried removing the files for the flash player:

cd ~/.mozilla
$ rm flashplayer.xpt libflashplayer.so

but i get an error message saying that there is no such file or directory- how can i uninstall the flash player now?

thanks.

i got flash player uninstalled, now i need to find version 10 beta 1 to see if it will work for me..

does anyone have a link?

---

### Post by Bucky Ball on 2008-07-22
> cd /tmp
wget [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz)
tar -zxvf flashplayer10_install_linux_070208.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer

These instructions from billgoldberg on the last page did you no good? Worked no prob for me ...

---

### Post by bumanie on 2008-07-22
Just checked the .tar.gz I downloaded. It says flash player 10 without any other parameters added to the name. It however have numbers that make it look as though it was released early July, therefore, I assume it is flash player 10 beta 2 - although it makes no mention of beta 2 on the package. Guess that's why I thought it was flash 10 final, as there is no mention of it being a beta version. Any way, as stated, it was the first thing to get you tube playing again.

---

### Post by Matt26 on 2008-07-22
> **Matt26 said:**
> i got flash player uninstalled, now i need to find version 10 beta 1 to see if it will work for me..

does anyone have a link?

for anyone who is looking for this version of the flash player:

[http://ubuntuforums.org/showthread.php?t=795253](http://ubuntuforums.org/showthread.php?t=795253)

although i can't get the .deb package to install- says it is missing depencies (libflashsupport and libasound2-plugins) and i get the same random crashing of Firefox happening when i used the tar.gz package..

---

