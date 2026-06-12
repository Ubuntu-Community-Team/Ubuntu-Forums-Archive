---
title: "Epson DX4400 cartridge change"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by sunnycreatives on 2013-05-18
I had windows xp and Ubuntu running alongside each other but mostly used Ubunto.

My printer works fine with Ubunto until a cartridge needs replacing. When this happens I go to the ink/toner option and get a message saying that I can't check the ink levels with Ubuntu.

Up until my windows completely collapsed (I can't start up windows at all now) I would switch OSs and check the cartridges with windows and print from there.

So...basically, how do I get the ink levels to show up with Ubunto as I am unable to print off any invoices...neccessary for my business.

Someone suggested I just check the cartridges manually...which I can't do as the carrier doesn't sit anywhere where I can get to it. Also...checking manually doesn't tell me which cartridge needs changing...so I would have to change all cartridges when only one needs replacing.

Also...why would I want to do this manually when I should be able to check levels with any operating system I use.

---

### Post by MoebusNet on 2013-05-18
Perhaps this will help:

[http://ubuntuforums.org/showthread.php?t=1885112](http://ubuntuforums.org/showthread.php?t=1885112)

Application named 'Stylus-Toolbox' from Sourceforge. I haven't had to use this, but it might be worth a try.

---

### Post by Mark Phelps on 2013-05-18
I've used several Epson printers, and in every case, there's a button combination you can  press on the printer that will move the cartridge holder so you can see which cartridge needs replacing.  I would be surprised if the DX4400 did not have this feature.

As to checking ink levels, it's not an OS function; instead, it's a driver function.  Epson distributes their ink monitoring utility with their Windows installations, but does not (AFAIK) make such a utility for Linux.

What I've used in the past (and still use) is mtink.  You should Google for this, download and install it, and go through the steps to have it find your printer.

---

### Post by pdc on 2013-05-18
there has been a thread running where a correspondent was installing [COLOR="#0000FF"]**[SIZE=3]inq[/SIZE]**[/COLOR] 

[http://www.fioreltech.net/project/start](http://www.fioreltech.net/project/start)

and asked for some help

[http://ubuntuforums.org/showthread.php?t=2145083&highlight=epson](http://ubuntuforums.org/showthread.php?t=2145083&highlight=epson)

install page here [http://www.fioreltech.net/project/inq/version-1.0.0/doc/en/doc-installation](http://www.fioreltech.net/project/inq/version-1.0.0/doc/en/doc-installation)

inq requires a few extra packages; with the command

> [COLOR="#FF0000"]sudo apt-get install libxtst-dev build-essential libqt4-dev qt4-qmake libinklevel-dev[/COLOR]

that should all that seemed needed................*before* !! one begins the download and install of inq itself !!

my interest was piqued and I have installed it and it is good; if one makes onself a user of the lp group, it runs more easily

> [COLOR="#FF0000"]sudo gpasswd -a <your user> lp[/COLOR]

so for me as pdc the command was gpasswd -a pdc lp and for simplicity a restart before starting inq for the first time

---

