---
title: "Flash Player"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2011-11-25
After updating Flash Player yesterday (may have been day before), it keeps crashing. 

Is anyone else having problems ? Its the first time i have had problems with it since i installed Flash Aid.

Can someone tell me what the best approach to sorting it out is please :D:D

---

### Post by sandyd on 2011-11-25
> **MadMonkey1966 said:**
> After updating Flash Player yesterday (may have been day before), it keeps crashing. 

Is anyone else having problems ? Its the first time i have had problems with it since i installed Flash Aid.

Can someone tell me what the best approach to sorting it out is please :D:D
hmm...
Seems to be a widespread issue with the lastest update...
Theirs been some other threads around as well.

---

### Post by MadMonkey1966 on 2011-11-25
> **sandyd said:**
> hmm...
Seems to be a widespread issue with the lastest update...
Theirs been some other threads around as well.

Oh, at least its not just me.....now need someone to tell me how to roll back to the last one hat worked fine lol ;)

---

### Post by sammiev on 2011-11-25
If 64 bit this should help. Works great for me. :)

Adobe Flash now provides *OFFICIAL* flash with no funky scripting required.

Simply uninstall flash that you installed from sevenmachines, type
Code:

"sudo rm /usr/lib/mozilla/plugins/libflashplayer.so"

and then

Code:

"sudo apt-get update && sudo apt-get install adobe-flashplugin"

Leave out the ""

---

### Post by anewguy on 2011-11-25
Even with flashaid, I have given up on most flash videos.  They either start to play and crash, or they sit there for ever and then I get a message saying the video is no longer available - and half the time the video at least starts to play behind that message.

I've tried a LOT of things - the simplest being removing flash and trying to load an older version - but to no avail.

I have no idea what is causing this - in all releases prior to 11.04 I had no problems.  Starting in 11.04 and continuing into 11.10 I've had nothing but problems.  Is Linux to blame?  Doubtful, but who knows if some simple little change broke this for a lot of us.  Is it video driver dependent?  Doubtful, but I don't think any type of poll has been taken on that.  Is it just flash?  This one I have to say no to.  I really think it is something external to flash -> that's why it works for some but not for others.  Somewhere in the updates to the kernel - perhaps some driver support - or in another package (doubtful on desktop managers, as I've seen this complaint from more than just Unity or Gnome) - I have no idea.  But something simple somewhere broke things for a lot of us.  I don't normally call wolf on Linux, and I don't mean to at this time either.  I think it's an unforeseen combination of things that is making this fail.  I don't think anyone is to blame per se - I just hope someone can find a solution.

My 2 cents worth again, and only my opinion.

Dave ;)

---

### Post by MadMonkey1966 on 2011-11-25
> **sammiev said:**
> If 64 bit this should help. Works great for me. :)

Adobe Flash now provides *OFFICIAL* flash with no funky scripting required.

Simply uninstall flash that you installed from sevenmachines, type
Code:

"sudo rm /usr/lib/mozilla/plugins/libflashplayer.so"

and then

Code:

"sudo apt-get update && sudo apt-get install adobe-flashplugin"

Leave out the ""

I wish, only 32 bit :(

---

### Post by MadMonkey1966 on 2011-11-25
> **anewguy said:**
> Even with flashaid, I have given up on most flash videos.  They either start to play and crash, or they sit there for ever and then I get a message saying the video is no longer available - and half the time the video at least starts to play behind that message.

I've tried a LOT of things - the simplest being removing flash and trying to load an older version - but to no avail.

I have no idea what is causing this - in all releases prior to 11.04 I had no problems.  Starting in 11.04 and continuing into 11.10 I've had nothing but problems.  Is Linux to blame?  Doubtful, but who knows if some simple little change broke this for a lot of us.  Is it video driver dependent?  Doubtful, but I don't think any type of poll has been taken on that.  Is it just flash?  This one I have to say no to.  I really think it is something external to flash -> that's why it works for some but not for others.  Somewhere in the updates to the kernel - perhaps some driver support - or in another package (doubtful on desktop managers, as I've seen this complaint from more than just Unity or Gnome) - I have no idea.  But something simple somewhere broke things for a lot of us.  I don't normally call wolf on Linux, and I don't mean to at this time either.  I think it's an unforeseen combination of things that is making this fail.  I don't think anyone is to blame per se - I just hope someone can find a solution.

My 2 cents worth again, and only my opinion.

Dave ;)

I had no problems as such until this week. Maybe had the odd moment, and that was in 11.04. Wish i had not bothered when FlashAid suggested it, but normally it OK for me

---

### Post by whatthefunk on 2011-11-25
Flash aid has a bug...it tries to install a flash program that is no longer in the repositories.  All it does is delete all your other flash stuff.  The program in its current form is worthless.  Unistall it and install a flash plugn manually.

---

### Post by MadMonkey1966 on 2011-11-25
> **whatthefunk said:**
> Flash aid has a bug...it tries to install a flash program that is no longer in the repositories.  All it does is delete all your other flash stuff.  The program in its current form is worthless.  Unistall it and install a flash plugn manually.

OH hasit ? Its been fine up till this week, unless i just been lucky lol....i will have a go, not too clever at these manual things :-\"

---

### Post by ajgreeny on 2011-11-25
I am not sure about this bug in flash-aid, but the new beta version of flash that the flash-aid add-on installs as default will not work at all on my old desktop machine;  it just gives me empty white flash windows.

I found that telling flash-aid to install the stable version of flash from the ubuntu repos works very well at the moment.  This is on the first page of flash-aid if you choose the "Wizard mode" from the Flash-aid icon.

It's a great pity that this seems to haver happened, as flash-aid has, up till now, been a real boon which I have recommended to a lot of ubuntu users.  This is the first time it has been a problem for me.

---

### Post by MadMonkey1966 on 2011-11-25
> **ajgreeny said:**
> I am not sure about this bug in flash-aid, but the new beta version of flash that the flash-aid add-on installs as default will not work at all on my old desktop machine;  it just gives me empty white flash windows.

I found that telling flash-aid to install the stable version of flash from the ubuntu repos works very well at the moment.  This is on the first page of flash-aid if you choose the "Wizard mode" from the Flash-aid icon.

It's a great pity that this seems to haver happened, as flash-aid has, up till now, been a real boon which I have recommended to a lot of ubuntu users.  This is the first time it has been a problem for me.

Yes, that was the one i was using. I have disabled FlashAid for now until i read up on it. I installed Flash from the Software Center and that seems fine so far. I will close the thread, until something else happens lol

Thanks everyone

---

### Post by anewguy on 2011-11-26
I removed flash-aid for the "umteenth time", removed the .so for the "umteenth time" and installed flash as suggested for the "umteenth time" with the same results for the "umpteenth time".

For me, flash movies have become impossible to watch.

---

### Post by beew on 2011-11-26
It is not fair to blame flash-aid for most likely Adobe's problem. Flash-aid doesn't create flash, it just downloads what is available, cleans up your system by removing conflicting versions and automates some optimizing tweaks. If your web browser melts down because of flash that is most likely Adobe's fault.

---

### Post by anewguy on 2011-11-26
I don't know if others are, but I'm not blaming flash-aid.  My earlier posts explain where I stand - and I don't think it's flash's fault either.

Dave ;)

---

### Post by sandyd on 2011-11-26
I used to develop the now-defunct adobe-flash-tools project, until the release of flash-aid, because flash-aid was easier to use.

However, it was admitted that flash-aid did not fix some of the problems since its impossible to get root access.....

32bit
```

sudo apt-get -y remove nspluginwrapper
sudo rm /var/lib/dpkg/info/flashplugin*
sudo rm /var/lib/dpkg/info/adobe-flashplugin*
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
sudo apt-get -y  purge flashplugin-installer gnash mozilla-swfdec
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so 
sudo rm ~/.mozilla/plugins/libflash*
sudo rm /usr/lib/firefox-4*/plugins/libflash*
sudo apt-get -y remove --purge flashplugin-installer
sudo apt-get -y remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash
sudo apt-get -y remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin
sudo apt-get -y remove --purge swfdec-mozilla libflashsupport iceape-flashplugin
sudo apt-get -y remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin
rm -f ~/.mozilla/plugins/libflash*
rm -f ~/.mozilla/plugins/ns*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/libflash*
sudo rm -f /usr/lib/firefox/plugins/libflash*
sudo rm -f /usr/lib/iceape/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/iceweasel/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/midbrowser/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/mozilla/plugins/libflash*
sudo rm -f /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/xulrunner/plugins/flashplugin-alternative.so
sudo rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
wget http://fpdownload.macromedia.com/get/flashplayer/pdc/11.1.102.55/install_flash_player_11_linux.i386.tar.gz
mkdir flash
tar xvfz install_flash_player_11_linux.i386.tar.gz -C ./flash
mkdir ~/.mozilla/
mv flash/*so ~/.mozilla/plugins

```64bit
```

sudo apt-get -y remove nspluginwrapper
sudo rm /var/lib/dpkg/info/flashplugin*
sudo rm /var/lib/dpkg/info/adobe-flashplugin*
sudo dpkg --remove --force-remove-reinstreq adobe-flashplugin
sudo apt-get -y  purge flashplugin-installer gnash mozilla-swfdec
sudo rm /usr/lib/mozilla/plugins/libflashplayer.so 
sudo rm ~/.mozilla/plugins/libflash*
sudo rm /usr/lib/firefox-4*/plugins/libflash*
sudo apt-get -y remove --purge flashplugin-installer
sudo apt-get -y remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash
sudo apt-get -y remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin
sudo apt-get -y remove --purge swfdec-mozilla libflashsupport iceape-flashplugin
sudo apt-get -y remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin
rm -f ~/.mozilla/plugins/libflash*
rm -f ~/.mozilla/plugins/ns*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/libflash*
sudo rm -f /usr/lib/firefox/plugins/libflash*
sudo rm -f /usr/lib/iceape/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/iceweasel/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
sudo rm -f /usr/lib/midbrowser/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/mozilla/plugins/libflash*
sudo rm -f /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
sudo rm -f /usr/lib/xulrunner/plugins/flashplugin-alternative.so
sudo rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
rm -rf $HOME/.wine/dosdevices/c:/windows/system32/Macromed/Flash
wget http://fpdownload.macromedia.com/get/flashplayer/pdc/11.1.102.55/install_flash_player_11_linux.x86_64.tar.gz
mkdir flash
tar xvfz install_flash_player_11_linux.x86_64.tar.gz -C ./flash
mv flash/*so ~/.mozilla/plugins

```
However, I eventually stopped development due to lack of interest.

Run the above script.

---

### Post by raven on 2011-11-27
Sandyd, your script worked for me

but FYI and I find it strange on my FF 3.6.24 with Ubuntu 10.10_64
I have multiple FF profiles and all of them were working except the main one (white box on flash movies) even with Epiphany which I believe use the same flash plugin was working fine on youtube....

nevertheless thanks, you saved me hours of frustrations...

---

### Post by anewguy on 2011-11-27
Sandyd, thanks for the script.  It runs fine for me, but alas my flash is still all messed up.  Being on a DSL connection I suspect that these problems may be being compounded by time outs in flash when connecting/buffering the video.

Dave ;)

---

