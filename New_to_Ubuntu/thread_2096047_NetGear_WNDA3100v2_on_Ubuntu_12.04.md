---
title: "NetGear WNDA3100v2 on Ubuntu 12.04"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by avengedalice on 2012-12-18
Ok, I am having a hard time trying to install the drivers needed to use my device, and I need some help. Im posting to the Absolute Beginners because i honestly dont know most of the things YouTube videos are telling me to do. I have a Dell Vostro standalone desktop, and im trying to install all the needed programs through a  flashdrive. Im asking whether anyone else has acomplished this task ,or knows the required steps to achieve my goal. Forgive me if I have posted this in the wrong section, but im desparate and in need of major help. thanks! 

P.S Im a major Linux noob...

---

### Post by Ms. Daisy on 2012-12-18
Welcome to the forums.

Just so I'm clear, your goal is to install Ubuntu 12.04 on the flash drive? 

If so, please see this:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by avengedalice on 2012-12-18
no, my computer already has 12.04. my question is how do i get the drivers nessesary to use my NetGear USB adapter without internet already on my computer.

---

### Post by Ms. Daisy on 2012-12-19
If there's absolutely no way you can plug in an ethernet cable somewhere, then you'll have to download the driver to a cd or flash drive and transfer it to the Ubuntu computer.

---

### Post by squakie on 2012-12-19
With the adapter plugged in, do lsusb and post back the results.  If we can get the correct chipset (I'm not familiar with your adapter), perhaps we can give you instructions for doing so.

---

### Post by kurt18947 on 2012-12-19
That adapter seems somewhat notorious.  Here is an 11 page thread:

[http://ubuntuforums.org/showthread.php?t=1964173&highlight=NetGear+WNDA3100v2&page=11](http://ubuntuforums.org/showthread.php?t=1964173&highlight=NetGear+WNDA3100v2&page=11)

It seems to require NDIS wrapper.  Bear this in mind  with NDISwrapper.  It is intended to work properly only with Windows XP drivers.  It seems some people have had success with windows drivers for Vista or Win 7 but I certainly wouldn't count on it.  Also if you have a 64 bit O.S., you must use the 64 bit Windows XP driver.  

For myself, I prefer devices whose chipset manufacturers provide linux support.   I've had very good luck with Realtek devices.  Dlink DWA-131 and TrendNet TEW-649UB (both Realtek RTL-8192SU devices) are  plug 'n' play for me.  They're both N150 though, not N300.

Here's the nitty-gritty on the WNDA3100v2:
[http://www.wikidevi.com/wiki/Netgear_WNDA3100v2](http://www.wikidevi.com/wiki/Netgear_WNDA3100v2)

---

### Post by squakie on 2012-12-19
If you need ndiswrapper as kurt18947 has suggested, please do not follow old posts on the net or the forum for that - there are tons of them.  Instead, post back and we can give you step by step instructions.

The first steps, of course, are to install ndiswrapper and it's gui'd interface ndisgtk.  If you have a wired connection you should be able to do that via the package manager.  If not, the packages are located on the install media in the /pool/main/n folder - a folder for ndiswrapper and a folder for ndisgtk.  Click each of the files in those 2 folders to begin its install.

---

