---
title: "Canon ip1800 PPA repository doesn't work"
date: 2013-03-24
forum: New to Ubuntu
---

### Post by SeoulGamer on 2013-03-24
My Canon iP1800 printer doesn't work with Ubuntu. Ubuntu can detect the printer, but nothing happens when I select "Print".

I googled how to do it and found these instructions:[INDENT] [FONT=arial]sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-ip1800series[/FONT]


The problem is that when I type these commands into Terminal, I get errors telling me the repository does not exist:

E: Unable to locate package cnijfilter-ip1800series

Could someone please point me to an up to date repository for the Canon iP1800 printer? This one seems to have been taken down at some point.

Very much obliged to anyone who can help.

[/INDENT]

---

### Post by pdc on 2013-03-24
Canon supplied drivers for your printer in an rpm format: rpm seemed to be predominant package in Japan; 

one can convert rpm to deb with alien

[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)

one gets alien first of all by 

> [COLOR="#FF0000"]sudo apt-get install alien[/COLOR]

so by going here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0900718405.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0900718405.html)

you get the COMMON PACKAGE as [COLOR="#008000"]**cnijfilter-common-2.70-1.i386.rpm**[/COLOR]

it comes down to your Downloads directory so 

> [COLOR="#FF0000"]cd Downloads[/COLOR]

and then convert and install 

> [COLOR="#FF0000"]sudo alien -i cnijfilter-common-2.70-1.i386.rpm[/COLOR]

and then get the ip1800 package [COLOR="#008000"]**cnijfilter-ip1800series-2.70-1.i386.rpm**[/COLOR] from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0900718601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0900718601.html)

and install as before

---

### Post by SeoulGamer on 2013-03-27
Thanks, that does point me in the right direction. However, I'm using a 64-Bit version of Ubuntu. Do you know if there's a version of the ip1800 driver for 64-bit architectures? I believe the i386 is 32-Bit. I should have specified what version of the OS I use in my opening post-my apologies.

Attempting to use the 32-Bit driver on my system generated the following error message in terminal: "cnijfilter-common-2.70-1.i386.rpm is for architecture i386 ; the package cannot be built on this system".

---

### Post by pdc on 2013-03-28
......................matching an old printer..............to the latest OS.....................ie 64bit...................................may produce clashes..........................matching an old printer..................with an older-type system..............ie 32bit ..........................may produce a working system,.....................

you will need to google all this yourself.....................

> cnijfilter-common-2.70-1.i386.rpm is for architecture i386 ; the package cannot be built on this system

you need to detail what you did.................that produced this message.................................

---

### Post by davetube24 on 2013-06-21
I know how! Go to software sources in Update Manager(software updator) go on "Other Software" edit ppa:michael-guru/canon from precise to oneiric[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]

---

### Post by gordintoronto on 2013-06-21
Here's a completely different approach. Depending on what version of Ubuntu you are using, run Printers or Printing. Click on "Add" or "+". Your printer should appear after a few seconds; select it, then "yes" "OK" or "continue" until it is installed and working.

Doesn't work for every printer, but it has worked for my networked Brother laser for about three years, in many different versions or distros.

---

### Post by shelbydz on 2013-11-02
These instructions worked for me:
[http://linuxg.net/how-to-install-printer-driver-canon-pixma-ip-series-on-ubuntu/]("http://linuxg.net/how-to-install-printer-driver-canon-pixma-ip-series-on-ubuntu/")
I realize they take you through adding the ppa and installing it that way (as described by the op), but my 1800 didn't work using the canon sanctioned drivers. 

It's my guess that the op didn't add the repository correctly. should be ppa:michael-gruz/canon-trunk . Looked like he may have forgotten /canon-trunk

---

### Post by segui_santiago on 2013-12-23
Thanks shelbydz,

Instructions in [http://linuxg.net/how-to-install-pri...ies-on-ubuntu/]("http://linuxg.net/how-to-install-printer-driver-canon-pixma-ip-series-on-ubuntu/") worked for me too, but first I had to uninstall all previous stuff I have tried from the web. This is exactly what I did:

- old drivers: go to synaptic, and uninstall anything that appears when looking for "canon"
- old repositories: go to synaptic, settings, repositories, and delete any repository from michael-gruz
- unplug canon printer in case it is connected to PC
- reboot system
- in a terminal type:

sudo add-apt-repository ppa:michael-gruz/canon-trunk
sudo apt-get update
sudo apt-get install cnijfilter-ip1800series

-reboot, connect and turn on printer and...voilà!

For other printers the options are listed at [http://linuxg.net/how-to-install-pri...ies-on-ubuntu/]("http://linuxg.net/how-to-install-printer-driver-canon-pixma-ip-series-on-ubuntu/")

Cheers

Santi

---

### Post by empitt on 2014-04-23
Script install drivers Canon iP1800 for Ubuntu 14.04 LTS & old version:
```
cd /tmp && wget http://www.bagbit.pl/download/canon_ip1800_deb.tar.gz && tar xzf canon_ip1800_deb.tar.gz && sudo canon_ip1800_deb/install.sh
```

---

### Post by GreenRaccoon on 2014-06-18
> **empitt said:**
> Script install drivers Canon iP1800 for Ubuntu 14.04 LTS & old version:
```
cd /tmp && wget http://www.bagbit.pl/download/canon_ip1800_deb.tar.gz && tar xzf canon_ip1800_deb.tar.gz && sudo canon_ip1800_deb/install.sh
```

You, sir, are a lifesaver. Works for me, even with 64 bit.

The ppa:michael-gruz/canon-trunk repository hasn't been updated for 14.04, so you need to use empitt's method.

---

