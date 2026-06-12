---
title: "HOWTO: Xerox Phaser 3122 - printing with Dapper 6.06"
date: 2006-08-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Copter on 2006-08-25
**[COLOR="Red"]UPDATE 3[/COLOR]**

This printer works just fine in Edgy Eft 6.10 with default CUPS installed. Just provide my edited .ppd file when adding new printer.

**[COLOR="Red"]UPDATE 2[/COLOR]**

The best way to use Xerox Phaser 3122 on Dapper with Cups 1.2 is to hack / edit orginal Phaser-3122 and Samsung-Ml-6040 ppd and Foomatic files. Modyfied files are in the attachments.

/usr/share/foomatic/db/source/printer/Xerox-Phaser-3122-Copter.xml - we need to copy this manualy. Next add printer using KDE's gui printer setup and as the driver choose suplied Phaser-3122-Copter.ppd file. This method uses default (not manualy modyfied) cupsd.conf file. _Maybe_ adding cupsys to shadow group is needed (see below). Try it when you have problems with passwords.

Method showed below is brute force method, does not support undo and can  break cups. I recomend not using it or do it at own risk.

[CENTER]---------------------------------------------------------[/CENTER]

Hi!

It took me more than 5 hours to configure this USB laser printer on Kubuntu 6.06. This howto can also be useful for Samsung printer users because some Xerox models are the same as Samsung printers.

What does this howto solves? If you see error messages like those below than there is high possibility that I can help you
```


cupsdAuthorize: Local authentication certificate not found!
Could not find a suitable printer!
/usr/lib/cups/filter/ppmtospl2 failed

```

The problem is with **cupsys version 1.2**. No matter what will you try to do with it I assure you that you will fail with printer detected but unable to print anything.

Soultion is quite simple : **downgrade cups**
```


sudo apt-get remove cupsys

```
I did it using Adept though. Some other packages were removed during this process (like hplip, bluez-cups, printconf ...). I really wanted this printer working so I didnt care about that. Everything seems to be working OK now. No error messages.

After removing old cupsys remove also /etc/cups directory (or rename it to something else for safety)
```


sudo mv /etc/cups/ /etc/cups_old

```

Now download old version of cups from [http://www.cups.org/software.php]("http://www.cups.org/software.php"). I used version 1.1.23 ([http://www.cups.org/software.php?VERSION=1.3svn-r5850&FILE=cups/1.1.23/cups-1.1.23-source.tar.bz2]("http://www.cups.org/software.php?VERSION=1.3svn-r5850&FILE=cups/1.1.23/cups-1.1.23-source.tar.bz2")). Then unpack it
```


tar -xjvf cups-1.1.23-source.tar.bz2 /tmp

```

Compile and istall it
```


cd /tmp/cups-1.1.23
./configure
make
sudo make install

```

There is possibility that previous version of cups did not unload properly from memmory so the best solution here is to reboot. I know, it should be possible without restart of the system just restarting cups deamon but IMO it is safer to reboot.

After reboot run setup.sh from your Xerox Driver CD.
```


cd /cdrom
sudo setup.sh

```

If it fails than copy whole CD (~80mb) to another directory and then run it
```


cp -R /cdrom/ /tmp/
cd /tmp/cdrom
mv ppd/c/ ppd/C/
sudo setup.sh

```

There select Recommended and when it finish choose Start. It should be quite easy from there.

When everything is running OK delete all leftovers
```


rm -fR /tmp/cdrom
rm -fR /tmp/cups-1.1.23

```

If you have some problems with authentication then try adding cupsys and cupsd to shadow group - find shadow:x: and add cupsys,cupsd there (my shadow line looks like this **shadow:x:42:cupsys,cupsd**). Dont touch nor change other setting there. It can mess whole system quite well.
```


sudo kedit /etc/group

```

Hope it helps,
Copter :]

---

### Post by canopic on 2006-09-04
Hi Copter

Don't know if you saw my posting for help with installing Xerox Phaser printer [canopic: Phaser 3115.PPD]; 2 days ago, but reading your thread it seems I need to do something similar!

Can you expand?  I think you are warning against down grading cups and removing cupssys.  Instead you recommend that I should modify my Phaser3115.ppd ?  Is that right?

What sort of changes did you have to make to your PPD file to get it to work?
Was it just file names or paths, or other stuff?  How did you figure out what to change or was it obvious?

I see you have kubuntu and KDE, but I only have ubuntu and Gnome. You used KDE's gui printer setup, but I need to use what Gnome provides. Do you think this would make any difference?  My guess is it shouldn't matter?

Appreciate your comments. thanx

---

### Post by Copter on 2006-09-04
Hi Canopic,

Here is exacly what I did. First Ive found that Xerox and Samsung printers are quite simmilar. In some thread Ive seen that Phaser 3122 and Samsung ML-6040 are the same printers. Ive installed Phaser 3122 using built-in Ubuntu ML-6040 ppd driver. It worked but it has got different options than my printer (for example no 1200x600 dpi support). I tried most of supported Samsung's drivers and it worked only with this one. There is also one thing that I cant handle - margins. Test pages are being printed like 'moved' to the upper-left corner about 2-3 milimeters. It is not that much so I dont care. When printing with user set margins - all 1 cm - than it doesnt matters.

What to change in ppd file - I will attach default and modyfied files for you. It was only 3 or 4 lines to edit, add or comment. To be hones I just copied from Samsung ppd file line with foomatic gdi option / script and everything else I left untouched. I also took Samsung xml and simply edit it. Try it. There is not much to tweak there except for vendor name and resolution.

Why not to downgrade cupsys? Ive did it but it didnt let me to replace all packages. When I tried to install older libs it said that KDE depend on newer ones and I have to remove 100+ KDE essential packages. Ive force apt to install some of cupsys old packages. **But not all**. This way it wasnt 100% compatible. When I tried to install back Dapper's default cupsys then it poped some weird error messages like 'chiled process killed'. Even when having all cups' packages of the same version cups did not wanted to start. I have to remove cups' directories manually, remove with purge option with apt, than install them back. Ofcourse, as I wrote before, not all packages could be purged. It took me about 2 days to handle that. It is not worth trying. It is better to edit those files manualy.

I hope it help. Believe me, it is possible to run Xerox printer on Dapper :). Btw. installing cupsys 1.3 from cvs also didnt helped on old drivers.

About Gnome - I have no idea how priter manager works there but I think that you can do the same by entering [http://localhost:631](http://localhost:631) and add printer there. If you have problems with passwords there then check /etc/cups/cups.conf file for authetycation. To reboot cups type
```


sudo /etc/init.d/cupsys restart

```
It is needed to process modyfied .conf file.

oh, I have to say that in general I have no idea what most options in ppd files are meaining. I just comment, edit, add some lines, add new printer, test print and so on...

Good luck,
Copter :]

---

### Post by birgi on 2006-11-27
Copter,

Worked great for me, thanks a lot for this howto...

Birgi

---

### Post by Copter on 2006-11-27
Im glad I could help :)

---

