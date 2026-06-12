---
title: "Get HP Laserjet 1320 working perfectly!"
date: 2006-08-12
forum: Outdated Tutorials &amp; Tips
---

### Post by denisesballs on 2006-08-12
After over a year working with Ubuntu and the Laserjet 1320, I've come to realize that both the Postscript driver and the HPLIP driver have problems. The postscript driver doesn't print more than 600x600dpi and the HPLIP driver causes the power buttun to blink and make you press it to get things printing. I've noticed a lot of people complaining about these issues. However a recent trip to [http://linuxprinting.org/](http://linuxprinting.org/) showed me someone has resolved these issues themselves with a script that will "download/extract the ppd for this printer from HP and then patch it to fix problems mentioned above as well as problems reported by cupstestppd". This is from [http://linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1320](http://linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1320) .

To install this you grab the script:

```
wget http://users.adelphia.net/~david.everly/ppd/hplj1320.sh
```

then make it executable:

```
chmod +x hplj1320.sh
```

make sure you have mscompress:

```
sudo apt-get install mscompress
```

just run it, and it will do the rest for you:

```
sudo ./hplj1320.sh
```

Boom! That will install a patched driver for the HP Laserjet 1320 that  allows 1200x1200dpi printing, duplex, and no more pusing the power button. It even has some extra configurations too!

DISCLAIMER:

The creator of this script says:

> With the ppd produced with this utility the printer works and you can configure every available option, but sometimes it doesn't print very 'difficult' jobs (e.g. 4 pages condensed in one, in duplex mode, even when the file size is small and everything should fit in RAM). If I use the hpijs ppd this problem goes away but so do lots of options. In particular, I can't seemingly print in draft mode at 600x600 dpi (the page appears a lot blacker than it did with the ps ppd).

However, I haven't hasd any issues yet.

---

### Post by inetguy on 2006-08-16
I am running into the following error with the script:

```

./hplj1320.sh: line 19: msexpand: command not found

```

I guess I'm missing something on my system?  I am running Dapper 6.06

I'm also having trouble with Networking the thing--it prints in Ubuntu, but not over the network from Windows or Mac OSX

Thanks for any help.

---

### Post by denisesballs on 2006-08-16
> **inetguy said:**
> I am running into the following error with the script:

```

./hplj1320.sh: line 19: msexpand: command not found

```

I guess I'm missing something on my system?  I am running Dapper 6.06

I'm also having trouble with Networking the thing--it prints in Ubuntu, but not over the network from Windows or Mac OSX

Thanks for any help.

Oh yeah, I had that too and I forgot to add it. You need mscompress:

```
sudo apt-get install mscompress
```

should take care of it. I'll add it to the original post.

---

### Post by inetguy on 2006-08-17
Thanks for the tip, I was looking for msexpand for which there is no package :(

FWIW, some folks may also need dos2unix, which is part of sysutils.  Just do a:

```

apt-get install sysutils

```

That should finish it off.

Thanks for the help on this, Jesse!

~Dennis

---

### Post by TheLimey on 2006-11-12
Is there an alternative download location as [http://users.adelphia.net/~david.everly/ppd/hplj1320.sh](http://users.adelphia.net/~david.everly/ppd/hplj1320.sh) is no longer working?

---

### Post by therbert on 2006-11-24
I have the 1320 on a Mac OS X system.  I can print from any of the three Mac OS X machines on my home network and from my Ubuntu Linux PC.  However, when the Ubuntu machine prints, the yellow light on the printer blinks and I need to press the green printer button to start printing.

Do I apply the fix mentioned above to the Linux machine?  I guess I don't understand enough about CUPS and ppd files to understand if the printing uses the Linux ppd file or one on the Mac.

Thanks in advance... Tom

---

### Post by daller on 2006-12-14
I've installed the new driver, but do I have to setup the printer again, to use this driver instead?

---

### Post by octokiddie on 2007-01-09
works great! thx a lot for this script
had to install cabextract though

```
sudo apt-get install cabextract
```
took care of it

---

### Post by bingotailspin on 2011-01-15
Can get the script to download but I found this great thread that fixed my printer:  [http://ubuntuforums.org/showthread.php?t=1101273](http://ubuntuforums.org/showthread.php?t=1101273)  You just use the generic driver already installed.

---

