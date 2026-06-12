---
title: "how do you install the flash 10 plugin"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by hazman on 2008-08-25
how do you install the flash 10 plugin? i'm a bit new to this got the package and extracted files now what

---

### Post by tuxulin on 2008-08-25
[http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/)


hope it helps
Tuxulin

---

### Post by aysiu on 2008-08-25
Download [this file](http://mirror.optus.net/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2_i386.deb) and double-click it.

---

### Post by hazman on 2008-08-26
still unable to get flash 10 plugin to work

---

### Post by tuxulin on 2008-08-26
can post the steps on how you are trying to install please

Tuxulin

---

### Post by billgoldberg on 2008-08-26
The link Tuxulin posted should do the trick.

What error do you get when doing them?

---

### Post by tuxulin on 2008-08-26
yea i just ran through the steps on the
supplied link within a virtual setup and it does work 100%


Tuxulin

---

### Post by Bucky Ball on 2008-08-26
```
cd /tmp
wget [http://download.macromedia.com/pub/l..._070208.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz")
tar -zxvf flashplayer10_install_linux_070208.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer
```

Like that, type in terminal one line at a time (not all at once!) :)

---

### Post by aysiu on 2008-08-26
> **Bucky Ball said:**
> ```
cd /tmp
wget [http://download.macromedia.com/pub/l..._070208.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz")
tar -zxvf flashplayer10_install_linux_070208.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer
```

Like that, type in terminal one line at a time (not all at once!) :)
Two things:

1. There's a more recent version of Flash 10 available. So the second command should be: ```
wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz
``` and the third command should be ```
tar -xvzf flashplayer10_install_linux_081108.tar.gz
```

2. Please do yourself a favor and do not retype the commands. Copy and paste them instead.

---

### Post by hazman on 2008-08-26
i think what i did was copy all the text and copied straight to terminal so did it line by line and still no joy. Do i have to uninstall flash 9 first if so how? dont use terminal that much cos when i go to youtube to see if it worked its says i'm use flash 9

---

### Post by aysiu on 2008-08-26
> **hazman said:**
> i think what i did was copy all the text and copied straight to terminal so did it line by line and still no joy. Do i have to uninstall flash 9 first if so how? dont use terminal that much cos when i go to youtube to see if it worked its says i'm use flash 9
How did you install Flash 9 in the first place?

---

### Post by hazman on 2008-08-26
thru synaptic i think . thats where i unistalled it

---

### Post by hazman on 2008-08-26
tried installing as root but asks for a valid installation path and flumaxed me big style

---

### Post by tuxulin on 2008-08-26
ok since you are not good with the terminal try this

gksudo nautilus

navigate to /usr/share/mozilla/

once your there can you see a folder called plugins
if so go into it.

can you see these two files flashplayer.xpt and libflashplayer.
if so then delete them

next goto your home directory
click on "View >> Show hidden files"

now scroll down till you see **.**mozzilla   ( please note the . )

now go in to .mozilla >> Plugins and delete the files

close nautilius

now follow the link that was provided earlier in this thread to install

Tuxulin
flash 10

---

### Post by tuxulin on 2008-08-26
i think you can enter something like
/usr/lib/mozilla-firefox 

or

/usr/lib/mozilla

---

### Post by hazman on 2008-08-26
both said invalid directory

---

### Post by tuxulin on 2008-08-26
ok can you go there (/usr/lib/) then create this directory 
within nautilus " mozilla-firefox " then rerun the flash installer again.

Tuxulin

---

### Post by tuxulin on 2008-08-26
if all else fail then try this
/home/your_user_name/.mozilla

Tuxulin

---

### Post by cardinals_fan on 2008-08-26
Download  [this file]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz") to your desktop.  Type the following:```

cd /home/yourusername/Desktop/
tar xvzf flashplayer10_install_linux_081108.tar.gz
cd install_flash_player_10_linux/
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
```

---

### Post by hazman on 2008-08-29
tried all these but still no joy.it now asks for administrator to delete xpti.dat file

---

### Post by Bucky Ball on 2008-08-30
> **aysiu said:**
> Two things:

1. There's a more recent version of Flash 10 available. So the second command should be: ```
wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz
``` and the third command should be ```
tar -xvzf flashplayer10_install_linux_081108.tar.gz
```2. Please do yourself a favor and do not retype the commands. Copy and paste them instead.

Hey, aysiu, thanks for that tip. One problem. Throwing this error message, which didn't happen before ...

```
ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.
```Any suggestions? For some bizarre reason my flash has stopped working, although I haven't touched anything, so am trying to reinstall! (youtube was working last night and not today ... weird).

---

### Post by Dr Noam on 2008-08-30
Hi, also question about flash. I was advised to do:
> sudo aptitude install flashplugin-nonfree
which I did, and it seemed to install. But no joy with youtube or videos on news sites or flash-based games. I then tried applications-> add/remove -> flashblock which seemed to work, and was acknowledged when I started up Firefox but still no joy. Can someone explain what's going on to a newb and what the possible solutions are?

Thank you.

---

### Post by aysiu on 2008-08-30
64-bit is actually not natively supported by Adobe Flash player, as far as I know.

I think there are complicated workarounds, but I don't know of any guides for installing Flash 10 beta for 64-bit Ubuntu.

---

### Post by Bucky Ball on 2008-08-30
All cool aysiu. I fiddled around with software sources and rebooted and things returned to normal. All running as was. Not sure exactly how I fixed it but there you go. My original install of Flash 10 with my original instructions (minus the new ones) seems to be working and I haven't actually re-installed or uninstalled anything. :)

---

### Post by t0p on 2008-08-30
If you follow [this guide]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472"), it's actually a pulseaudio fix but also installs flash 10.

---

### Post by hazman on 2008-09-04
still cannot get the plugin [flash 10] to work in xubuntu

---

### Post by diogenes1 on 2009-08-09
> **hazman said:**
> still cannot get the plugin [flash 10] to work in xubuntu
i had the same problem as you with xubuntu. I ended up downloading the debian version from the adobe website and it worked. Just download it and it will install itself and restart firefox

---

### Post by Bucky Ball on 2009-08-11
Tried Synaptic Package Manager and a search for:

ubuntu-restricted-extras

Not sure which version that would load and guess that would depend on which version of Ubuntu your running, not sure.

---

