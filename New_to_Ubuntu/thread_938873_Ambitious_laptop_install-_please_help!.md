---
title: "Ambitious laptop install- please help!"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by ionizd on 2008-10-05
Hello all,
  I own an old toshiba 660CDT that I'd love to run on Xubuntu or maybe DSL, and I don't know quite how to proceed.
  The problem is that the only way to boot this laptop is by a 1.44Mb floppy or the hard drive.  The CDROM isn't bootable, and it can only be added to the (non-hot swappable) drive bay after a shutdown and replacement of the floppy drive.  I guess what that means is that either I need to be able to put a bootloader on the hard drive that will recognize the CDROM and make it so I can use an install disc, or I need to install the entire OS from floppy. This machine runs Windows 98 now, but it's much too slow and unstable as it can possibly be.
  Any ideas on how to do this?

---

### Post by iponeverything on 2008-10-05
The easiest way to do it would be to just put the hd from that laptop into one that has a cdrom and install it.  After the install finishes and it ask you reboot, shut it down take the drive out and put it back into the other laptop.

---

### Post by bobnutfield on 2008-10-05
It is indeed possible to install with a bootable floppy.  Once the floppy is booted, you can then mount your cdrom.  This is an article which will interest you:

[http://blogs.howtogeek.com/jatecblog/posts/make-a-floppy-boot-disk-for-ubuntu-from-linux/]("http://blogs.howtogeek.com/jatecblog/posts/make-a-floppy-boot-disk-for-ubuntu-from-linux/")

---

### Post by olddoser on 2008-10-05
Go to [http://www.mwpms.uklinux.net/msdosw9x.htm](http://www.mwpms.uklinux.net/msdosw9x.htm) and follow the 
directions.  Instead of inserting the Win9x cd use linux. I've used this several time with no problem.

---

### Post by halitech on 2008-10-05
I've got the tecra 550cdt and I did a floppy install of debian using the steps here

Install:
[http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)

fine tuning:
[http://forums.debian.net/viewtopic.php?t=7314](http://forums.debian.net/viewtopic.php?t=7314)

speeding up:
[http://forums.debian.net/viewtopic.php?t=14129](http://forums.debian.net/viewtopic.php?t=14129)

multimedia:
[http://www.debiantutorials.org/content/view/161/1/](http://www.debiantutorials.org/content/view/161/1/)

worked fine for me and the person using it likes it better then DSL as he now has GAIM installed so he can use msn

---

### Post by melojo on 2008-10-05
[http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_dtlView.jsp?soid=403623&moid=1073769771](http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_dtlView.jsp?soid=403623&moid=1073769771)

[http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_modItemList.jsp?moid=1073769643&rpn=PA1126U&ct=DL&BV_SessionID=@@@@1544451604.1223225089@@@@&BV_EngineID=cccjadefgelifdmcgfkceghdgngdgmn.0](http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_modItemList.jsp?moid=1073769643&rpn=PA1126U&ct=DL&BV_SessionID=@@@@1544451604.1223225089@@@@&BV_EngineID=cccjadefgelifdmcgfkceghdgngdgmn.0)

Links to toshiba protege 660cdt.

The specs show its capable of booting from cd rom but it can't read cd-r or cd-rw it does not support the format.

---

### Post by snowpine on 2008-10-05
Can you tell us more about your system specs? I googled your model number and saw that the 660cdt came with 16mb of ram, upgradeable to a maximum of 80mb. I would not recommend Xubuntu on anything less than 256mb of ram. DSL may be your best bet, and I've read it can be installed using a floppy:

[http://www.damnsmalllinux.org/wiki/index.php/Boot_Floppies](http://www.damnsmalllinux.org/wiki/index.php/Boot_Floppies)

Good luck, sounds like a fun project!

---

### Post by ionizd on 2008-10-05
> **snowpine said:**
> Can you tell us more about your system specs? I googled your model number and saw that the 660cdt came with 16mb of ram, upgradeable to a maximum of 80mb. I would not recommend Xubuntu on anything less than 256mb of ram. DSL may be your best bet, and I've read it can be installed using a floppy:

[http://www.damnsmalllinux.org/wiki/index.php/Boot_Floppies](http://www.damnsmalllinux.org/wiki/index.php/Boot_Floppies)

Good luck, sounds like a fun project!  This laptop has the maximum amount of RAM,  and sadly, the floppy drive and the CDROM cannot co-exist.  The floppy and the CDROM can't even be swapped without powering down the laptop.
  Does anyone know if you can copy the necessary linux files from a floppy to a clean, formatted hard drive so that I can then shutdown, swap the drives, then boot up and use the CDROM to load the OS?
  My only other option is to find a way to copy the OS to a hard drive
on another computer and swap it to the laptop.
  Or maybe this project isn't worth the trouble!

---

### Post by drowner on 2008-10-06
> **ionizd said:**
> 
  My only other option is to find a way to copy the OS to a hard drive
on another computer and swap it to the laptop.
  Or maybe this project isn't worth the trouble!

Sounds like fun, to be honest!

Do you have access to another computer?

Why don't you put the old HD into a new computer, and install via CD (as suggested above)?

---

### Post by Bibek on 2008-10-06
> **ionizd said:**
> Or maybe this project isn't worth the trouble!

Give it a try once and then forget it :)

You could try some old linux distros like the onces that were available in the late 90s if you can get them. i will do a search in the internet lets see if i can find some antique distros.

---

### Post by halitech on 2008-10-06
if you have 80meg of ram and can boot from the floppy and you have an ethernet port, you can still install debian. It will be a little slower then my tecra 550cdt but it can be done using the first link I posted.

system specs: [http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=223&product=1650&part=1290#spectop](http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=223&product=1650&part=1290#spectop)

---

### Post by stalkingwolf on 2008-10-06
a net install might also be an answer.  try Unetbootin.
as I recall both Puppy and DSL have floppy boot options.

---

