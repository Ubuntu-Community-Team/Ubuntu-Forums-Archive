---
title: "Busting My butt to get wifi working"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by xroox on 2008-10-29
I've installed OS on my new acer aspire one... a few problems 'out of the box' ie usb flash drive working (got that going) and most notably, wifi.

Reading the AspireOne article at ubunutu.com ([https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")) they explain two ways of fixing this, but i'm having some fundamental difficulties installing these fixes.

My main problem is (i'm new), where to I install/unpack these things? I can enter the terminal instructions... but it's very unclear as to where they are to be unpacked or installed to.

Here are the instructions verbatim:

[SIZE="1"]ndiswrapper

Download drivers for your wireless card from: [http://download2.dvd-driver.cz/atheros/drivers/ar5008/xp32-6.0.3.85.zip](http://download2.dvd-driver.cz/atheros/drivers/ar5008/xp32-6.0.3.85.zip)[/SIZE]

*[COLOR="RoyalBlue"](done)[/COLOR]*

[SIZE="1"]Unzip those drivers.[/SIZE]
[I]
[COLOR="RoyalBlue"](where to?)[/COLOR][/I]
[SIZE="1"]
Install ndiswrapper, and launch the installer:

sudo aptitude install ndisgtk
sudo ndisgtk

Find the net5416.inf file, and install it.[/SIZE] *[COLOR="RoyalBlue"](how?)[/COLOR]*

[SIZE="1"]If you have tried madwifi, unload it with:

madwifi-unload

Restart your AA1, and everything should work.[/SIZE]

Help? Thanks! simple answer I'm sure, hard question to ask. Ha!

---

### Post by Titan8990 on 2008-10-29
Alright, first off, you unzip them to wherever you prefer to put them.

Typically, this will be your home folder.

> Find the net5416.inf file, and install it. (how?)


You just unzipped it (if you did step 2).

Hope that helps.

Also, you may need to do this after those steps in order for it to work:


sudo modprobe ndiswrapper

---

### Post by Mazza558 on 2008-10-29
Where it says install it, do

> sudo ndiswrapper -i net5416.inf

---

### Post by teaker1s on 2008-10-29
if you upgrade to intrepid then atheros drivers are included in restricted drivers. Plus there is an active aspireone intrepid thread if your interested.

---

### Post by porchrat on 2008-10-29
> **teaker1s said:**
> if you upgrade to intrepid then atheros drivers are included in restricted drivers. Plus there is an active aspireone intrepid thread if your interested.

Don't joke!

Are you serious?  You mean I could drop my horrid madwifi system and stop the need for a make install after every header upgrade?!?

YES!!!!!!

---

### Post by teaker1s on 2008-10-29
currently running intrepid kernel, now I've no issue with wifi- I would suggest that you read all of thread prior to upgrade here
[http://ubuntuforums.org/showthread.php?t=894852]("http://ubuntuforums.org/showthread.php?t=894852") as there is talk of intrepid back ports package for latest kernel

---

