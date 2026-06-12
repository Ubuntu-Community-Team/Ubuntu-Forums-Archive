---
title: "HOWTO: Get an HP Laserjet 1000 to print"
date: 2006-01-04
forum: Outdated Tutorials &amp; Tips
---

### Post by dragonfyre13 on 2006-01-04
I searched for nearly 4 hours for this info, so I thought I would throw it in a howto for those of you that also needed it.

Basically, the problem with the Laserjet 1000, is that the firmware is really crappy. It requires a firmware flash constantly, and being a $200 laser printer, what do you expect? In windows, it has a circumvention for this specific printer, but in linux, we have to set it up manually. Don't worry, it's pretty simple.

For this How-To, you'll need the following nonstandard packages:

LPR | LPRNG

(Either one works, to my knowledge. I personally used LPR, but the commands are the same)

NOTE: This is only for a printer hooked directly to the computer, not over a network. (Only For Local printing)

1. Get the working firmware from the nice people who made your print driver in the first place. Then extract your firmware, /foo2zjs/sihp1000.img from it to somewhere you can remember. This file will be loaded upon logging in to your profile.

[http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)

2. Make sure that the printer is setup normally, (You can see it in the 'System -> Administration -> Printing' menu. Also, make sure that there are no jobs waiting to be printed. Unplug the printer, wait for a moment, and plug it back in.

3. 'System -> Preferences -> Sessions' -- 'Startup Programs' tab. Click the Add button, and type this in the box: 
```

lpr /directory/you/extracted/to/sihp1000.img
```

4. Log out, and then back in. Try printing a test page. If it does not work, unplug the printer, shut down the computer, then plug the printer in, and start the computer back up. This fully wipes the queue, and reflashes the firmware upon logging in.

---

### Post by gilrim on 2006-03-24
Could you please clarify a few things?

specifically, you referr to system->preferences->whatnot. where is this "system"? I've looked at the k-menu, in the system settings and such. 

What print manager do you use? Cups, generic or? Also, I tried running lpr sihp1000.img, but that gives me "lpr: lp: unknown printer".

If I try adding the printer, using cups, I can find it in the list of printers. But proceding with any of the availible drivers claims to work - but doesn't print. 

Where is this session->startup program?

---

### Post by maulattu on 2006-03-25
an easiest way:
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000)

point out these tasks:
```

1. wget http://foo2zjs.rkkda.com/foo2zjs.tar.gz
2. tar xzvf foo2zjs.tar.gz
3. cd foo2zjs
4. make
5. ./getweb 1000
6. sudo make install
7. sudo make install-hotplug

--------------
Note for Debian users: As 'make-install-hotplug' had some error
  '/etc/hotplug/usb.usermap: No such file or directory', I tried the
  following hack:
  'ln -s /usr/share/doc/hotplug/examples/usb.usermap /etc/hotplug/usb.usermap'
  and the firmware download with hotplug and the printing worked.
--------------

Switch off-and-on the printer, you should see something like this
in your /var/log/messages:

kernel: usb 3-2: new full speed USB device using address 8
kernel: drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 8 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0517
/etc/hotplug/usb/hplj1000: loading HP LaserJet 1000 firmware /usr/share/foo2zjs/firmware/sihp1000.dl to /dev/usb/lp0 ...
/etc/hotplug/usb/hplj1000: ... download successful.

Then set up your printer queue by running system-config-printer-gui:
1. click New, and Forward.
2. Enter a name and description.
3. Queue-type: Locally Connected, /dev/usb/lp0
4. Choose HP LaserJet 1000
5. Finish, and print a test page!

```

it worked very good for me;)

---

### Post by minisori on 2006-03-31
[QUOTE=maulattu]an easiest way:
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000)

point out these tasks:
```

1. wget http://foo2zjs.rkkda.com/foo2zjs.tar.gz
2. tar xzvf foo2zjs.tar.gz
3. cd foo2zjs
4. make
5. ./getweb 1000
6. sudo make install
7. sudo make install-hotplug

--------------
Note for Debian users: As 'make-install-hotplug' had some error
  '/etc/hotplug/usb.usermap: No such file or directory', I tried the
  following hack:
  'ln -s /usr/share/doc/hotplug/examples/usb.usermap /etc/hotplug/usb.usermap'
  and the firmware download with hotplug and the printing worked.
--------------

Switch off-and-on the printer, you should see something like this
in your /var/log/messages:

kernel: usb 3-2: new full speed USB device using address 8
kernel: drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 8 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0517
/etc/hotplug/usb/hplj1000: loading HP LaserJet 1000 firmware /usr/share/foo2zjs/firmware/sihp1000.dl to /dev/usb/lp0 ...
/etc/hotplug/usb/hplj1000: ... download successful.

Then set up your printer queue by running system-config-printer-gui:
1. click New, and Forward.
2. Enter a name and description.
3. Queue-type: Locally Connected, /dev/usb/lp0
4. Choose HP LaserJet 1000
5. Finish, and print a test page!

```

it worked very good for me;)[/QUOTE]

This is the way i got mine working but i have to update manually the firmware for some reason make install-hotplug fails in my dapper.

---

### Post by dragonfyre13 on 2006-04-06
[QUOTE=gilrim]Could you please clarify a few things?

specifically, you referr to system->preferences->whatnot. where is this "system"? I've looked at the k-menu, in the system settings and such. 

What print manager do you use? Cups, generic or? Also, I tried running lpr sihp1000.img, but that gives me "lpr: lp: unknown printer".

If I try adding the printer, using cups, I can find it in the list of printers. But proceding with any of the availible drivers claims to work - but doesn't print. 

Where is this session->startup program?[/QUOTE]

Make sure to install lpr from the repositories.

I am running gnome. This is for Ubuntu, not Kubuntu. I assume that it will also work in Kubuntu, however, by just adding the line that I specified to a startup script.

If there is no Laserjet 1000 printer in your drivers, choose an hp printer with the foo2zjs driver, and follow the rest of the Howto.

---

### Post by scorp001 on 2006-06-02
Thanks Dragon but it just does not seem to work - done the exercise 5 times.

ref your tagline - It is reasons like these where one has to compile programs that Linux is not going anywhere. It will remain popular with afew unless a concept of making binaries becomes a standard.

I will have to toss ubuntu out soon as it has very poor printing support and our Ubuntu team does not seem to be bothered about it. Understand Dapper too has the issues with this printer, I am using breezy.

The fact that a compiler is not included is message enuf from the ubuntu team that it shud not be required - in which case they need to have some one also looking into these forums and sort issues.

I sound very upset - I am - There is no way i am going to struggle with compilers etc.

---

### Post by dragonfyre13 on 2006-06-02
Try this,

Get a printer that doesn't require you to flash the firmware on the printer itself every time you print.

It's as simple as that. I have since thrown this printer away, simply becuase I wanted one that I didn't have to go through this much trouble with every time I run into a problem, or every time I want to print from somewhere else.

Even if you do throw Ubuntu out, which I don't reccomend, I would suggest pitching the printer. Even in windows it gives you a slow, buggy print at best. The thing is, the windows drivers are made to flash the firmware to the printer constantly. They were made by HP and Microsoft to fix the problem with the printer, so that HP didn't have to do a recall.

P.S. Do you realize that out of the box, Ubuntu has support for over 4 times that number of printers Windows does out of the box? It also has better drivers, more secure software, and a more stable base. With Ubuntu, I rarely compile anything, unless someone screwed up somewhere along the line. (IE, HP when they made this printer. There's a reason the 1010 came out about a month later with a price tag that was the same.)

---

### Post by maulattu on 2006-06-04
[QUOTE=minisori]This is the way i got mine working but i have to update manually the firmware for some reason make install-hotplug fails in my dapper.[/QUOTE]

[QUOTE=neoflight]thanks a lot... i think its working ok with dapper....[/QUOTE]

me too. it seems that in dapper there's not hotplug, so it uses udev. look at this:
```
nano /etc/udev/rules.d/11-hplj10xx.rules
```
it has as default action ```
RUN+="/etc/hotplug/usb/hplj1000"
``` but it doesn't download anything.. why???:-k :-k :-k 
anyway,,,, let's use the shell:
```
sudo /etc/hotplug/usb/hplj1000
```
but it doesn't work. it downloads the firmware, but when i add my printer (i use kubuntu) it doesn't recognize the driver (a bug??? a malformed xml???) so i downloaded it from [www.linuxprinting.org](www.linuxprinting.org) but it does not work...

any tips? :)

---

### Post by maulattu on 2006-06-04
i've reinstalled the new version of the foo2zjs drivers, but it doesn't work, damn...
this is my syslog:
```
Jun  4 10:53:34 localhost kernel: drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 14 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0517
Jun  4 10:53:35 localhost /etc/hotplug/usb/hplj1000: loading HP LaserJet 1000 firmware /usr/share/foo2zjs/firmware/sihp1000.dl to /dev/usb/lp0 ...
Jun  4 10:53:35 localhost /etc/hotplug/usb/hplj1000: ... download successful.
```
i configure the printer under kcontrol, but the driver provided doesn't work. i've downloaded a new ppd file from linuxprinting.org but it doesn't work...
if i turn off the printer, then when i turn it on :
```
Jun  4 11:01:37 localhost kernel: drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 16 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0517
Jun  4 11:01:38 localhost /etc/hotplug/usb/hplj1000: loading HP LaserJet 1000 firmware /usr/share/foo2zjs/firmware/sihp1000.dl to /dev/usb/lp0 ...
Jun  4 11:01:38 localhost /etc/hotplug/usb/hplj1000: ... download failed.
```
the firmware must be uploaded manually to the printer...
anyway it prints anything... under kcontrol i can see the job status as 'processing...' and the ipp report says:
```
printer-state-message --> Printer fault!
```

hp = :-x :-x :-x :-x :-& :-& :-&
hp = f**k

---

### Post by scorp001 on 2006-06-04
Thanks again Dragon  :D

Ok I have sorted my voes and my printer works - yes i did install make and g++ and all the compilers it kept asking me for. I followed the procedures listed on this page : [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000)

The importants steps are:
1. wget [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
2. tar xzvf foo2zjs.tar.gz
3. cd foo2zjs
4. make
5. ./getweb 1000
6. make install
7. make install-hotplug

Also u may need this line as well:
ln -s /usr/share/doc/hotplug/examples/usb.usermap /etc/hotplug/usb.usermap

The step 5 is important as the firmware is downloaded for hotplug in this step which updates the firmware each time u restart system or the printer.

Also if u want to use over the network printing within ubuntu network - have a read here - it works :) : [http://occy.net/printing](http://occy.net/printing)
I am using Firestarter and have set the incoming connections for the print server - in my case 192.168.1.3

Thanks again - cheers

---

### Post by dragonfyre13 on 2006-06-09
Neat, thanks for the link on network printing.

As for the other link, I've seen it before, and I don't remember why, but it never worked for me.

---

### Post by maulattu on 2006-06-25
if your hp laserjet 1000 does not work, look at this page:
[http://www.ubuntuforums.org/showthread.php?t=200179](http://www.ubuntuforums.org/showthread.php?t=200179)
pay attention to change the "DeviceURI" section after the printer was configured in kde/gnome. restart cups and voilà: your hp spites pages and pages (it works ;) )

---

### Post by rsidle on 2009-07-09
Thanks a million, this finally did it! Why is it that even in Ubuntu 9.04 this issue still exists? :(

---

