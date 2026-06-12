---
title: "Installing new wireless firmware?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by bilekbp on 2008-04-27
Greetings!

I am a brand new Ubuntu user attempting to install Ubuntu 8.04 on an HP Pavilion ze2000 notebook.  I haven't used a Unix-based operating system for 10 years, since then I have been DOS/Windows only.  So all this is a little confusing for me ;)  All I remember from my Unix terminal days is ls, case sensitivity, and never to type rm * -r :)

Currently I am having issues with connecting to wireless networks.  Going to the Hardware Drivers section I see that my Broadcom Wireless adapter has a supported driver but that firmware is required which cannot be sent with the O/S (why is that?).  So I've found some instructions on how to correct this, at the link below:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

My adapter is the (supported) bcm4318.  Following these instructions, I had problems:

If you are using the b43 driver from linux-2.6.24, follow these instructions.

Use version 011 of b43-fwcutter.
Download, extract the b43-fwcutter tarball and build it:

wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..

Use version 4.80.53.0 of Broadcom's proprietary driver.
Download and extract the firmware from this driver tarball:

export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
tar xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o

Note that you must adjust the FIRMWARE_INSTALL_DIR path to your distribution. The standard place where firmware is installed to is /lib/firmware. However some distributions put firmware in a different place.

I am able to follow the instructions just fine, I think.  However, when I type "make" in the b43-fwcutter-011 directory, I get a whole bunch of error messages.

excess elements in struct initializer, unknown field 'offset' specified in initializer, unknown field 'flags' specified in initializer, and much more.  It finally ends with "make: *** [fwcutter.o] Error 1.

Of course, the steps that follow cannot be completed without this being successfully "made."  Can anyone explain to this newbie what he is doing wrong, and what these error messages mean?


Finally, can anyone please let me know what to do to restart the system after it has gone to sleep?  With power settings I have the laptop going to sleep after a certain amount of time, but once it says PM: Entering Memory Sleep or somesuch and locks the console, the only thing I seem to be able to do is power cycle the laptop to get it back running.

Thanks very much for any help!

-Brian

---

### Post by bilekbp on 2008-04-27
I'm new to this forum, so I don't know the etiquette here, but it seems like posts get lost rather quickly, so I am bumping this in the hope that someone can answer my questions, or at least point me to something I can read that can help me with this.

Thanks!

---

### Post by bilekbp on 2008-04-28
Hi guys, is there a better forum in which to ask this question, or someplace I can go to look it up myself?

Thanks!

---

### Post by marufaberlin on 2008-04-28
As far as I know, the bcm43xx drivers never work well. Try using ndiswrapper and a windoze driver, there are a number of tutorials on the internet.

---

### Post by Cypher on 2008-04-28
I downloaded that application and managed to build the application. The attached DEB file will install the application in your /usr/local/bin directory.

Install it with
```

sudo dpkg -i b43-fwcutter_011-1_i386.deb

```

---

### Post by TerpInHotLanta on 2008-04-28
Use synaptic to get b43-cutter. This will ensure it installs correctly.

---

### Post by TerpInHotLanta on 2008-04-28
Sorry-- I meant to say if the b43-cutter prog will work, but I'll defer the remaining answers to the others, who clearly have more broadcom experience than I do.

'Luck!
Charlie

---

### Post by bilekbp on 2008-04-28
Thank you for your assistance!

I installed the .deb package, but couldn't get further.  I tried following the steps to install the firmware, but I get the following error message:  sudo: ../../b43-fwcutter-011/b43-fwcutter:  command not found

What else should I do to be able to install the firmware?

Thank you again!

---

### Post by bilekbp on 2008-04-28
Also, when clicking on the .deb file, I was told that a newer version was available via the "software channel" or somesuch.  What in the world does that mean?

---

### Post by Tom--d on 2008-04-28
> **bilekbp said:**
> Also, when clicking on the .deb file, I was told that a newer version was available via the "software channel" or somesuch.  What in the world does that mean?

That means that there is a newer version of the file in the repos. 

System > Admin > Synpatic package manager > search the .deb file. 

It should there, and click the white box and install.

---

### Post by bilekbp on 2008-04-28
Unfortunately I have no internet connection with the computer that I am trying to get working with wireless, so I can't upgrade that package.

But now that someone provided me with the .deb, and I installed it, where do I find it to use it?

Thanks!

---

### Post by bilekbp on 2008-04-29
Update:  Thanks to Cypher and others, I was able to successfully extract the firmware, install it, and get wireless networking working yesterday!  I connected the day of the install to a public network just fine.

However, today I attempted to connect to the same network, and have been unable to do so.  The driver still shows as active, I made no configuration changes to the computer, but yet it fails to connect whenever I try.

Any ideas?  :(

Thanks,

-Brian

---

