---
title: "Epson printer wf 2630"
date: 2016-03-31
forum: New to Ubuntu
---

### Post by allister_guy2003h on 2016-03-31
Hi
 I am new to Linux but have been using computers for many years, my first was the Sinclair Zx with a massive 16k memory!
I have had spectrum, bbc, Atari, another one ,good for video work but can't remember the name and finally pcs. windows came on floppy discs then.
The problem.
I have just installed Ubuntu 15.04 on my Windows 7. I think without any problems until I tried to add my Epson printer.
the system seems to look for drivers but just freezes not sure what to do. Internet connection,emails seems to work fine.
Any  suggestions greatly appreciated
Allister C Guy

---

### Post by $yl9pAR%t on 2016-03-31
First of all, Ubuntu 15.04 is out of date. Install Ubuntu 14.04.1 if possible.

Drivers for your printer you will find here:
[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

---

### Post by Geoffrey_Arndt on 2016-03-31
As the next LTS (Long Term Support) version of Ubuntu comes out in about 3 weeks, maybe it's best to stay on your current version, and then download the new iso (16.04) after April 21.

About your Epson Workforce Printer 2630 - - it's well supported in Ubuntu.    But since 15.04 may not have the drivers downloaded, here's what can be done"

1).   Goto the Ubuntu Software Center and search for the program "gdebi" and install it (just click the install button),
2).   Get the driver package, in the format of a "deb" file, 64 bit version or 32 bit version depending on your PC specs, and download it.   It can be found at OpenPrinting.org (search for Epson WF 2630 or just WF 2630.
3).   Navigate to the downloads folder in your home directory (that's where saved files usually go) - - then right click the deb file and you should see an option to open it using "gdebi"  (gdebi is a "stand-alone" installer for installing individual deb files that you've downloaded from an internet site.).   This is similar to Windows installs, and not usually the way to install programs in Linux/Ubuntu, but for rare instances like this, it works well.

Lastly - - go to System Settings>Printers and follow the wizard or guided screens to finish the install.   Good Luck!   (ps, there are other ways to do this install, this is just one, but it should work).

---

### Post by allister_guy2003h on 2016-04-01
Hi
thanks for the advice.
 I have tried to instal 14,04 but it will not accept my password just says wrong password. I have reinstalled 14.04 three times and have been very careful when setting up the password but it just says wrong password. Weird!
Allister

---

### Post by $yl9pAR%t on 2016-04-01
1. So after installation you were not able to login even once?

2. Do you have Nvidia GPU?

---

### Post by Geoffrey_Arndt on 2016-04-01
As info, Linux passwords are case sensitive, unlike Windows.    So, be sure to be aware of cases, space, etc.   Your password is assigned on one of the last installer screens.    That same password is the admin (or sudo) password from thereon.

---

