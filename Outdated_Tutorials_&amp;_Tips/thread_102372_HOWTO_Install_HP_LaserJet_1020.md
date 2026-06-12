---
title: "HOWTO: Install HP LaserJet 1020"
date: 2005-12-11
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-12-11
Written originally by **[Johnp_g]("http://ubuntuforums.org/member.php?u=51975")**

Edited and re-written by **Arnieboy**

The HP LaserJet 1020 driver is not included with Ubuntu Breezy by default. This is how to install it:
Open up terminal and do:
```
sudo apt-get install cupsys-bsd foo2zjs make build-essential
wget http://support.ideainformatica.com/hplj1020/foo2zjs-patched.tar.gz
tar zxvf foo2zjs-patched.tar.gz
cd foo2zjs
make
sudo make install
sudo make install-udev
sudo udevstart
```
Now when u power up the HP 1020 printer you should hear it whirring as it powers, then whirring again as the new firmware is uploaded. now do:
```
sudo /etc/init.d/cupsys restart
```
Do the following to make plain (lpr) text print nicely:
```
sudo lpoptions -o cpi-12 -o lpi=7 -o page-left=36 -o page-right=36 -o page-top=36 -o page-bottom=36
```
Hope this helps.

EDIT: For users having problems printing A4 size sheets, Jenda seems to have a solution:
```
sudo gedit /etc/cups/ppd/LaserJet-1020.ppd
```
and change the default page size to A4

---

### Post by Jenda on 2005-12-15
Thanks to both of you - but my printer is still fuzzy... changing paper size doesn't help.

---

### Post by cyaconi on 2005-12-15
Thank you!... I'm trying to print over a windows network. I've a notebook and the printer is attached to a windows XP machine.
Do I need to connect the printer to the notebook first??... I mean, to upload the firmware...
Thanks again!

---

### Post by arnieboy on 2005-12-16
[QUOTE=cyaconi]Thank you!... I'm trying to print over a windows network. I've a notebook and the printer is attached to a windows XP machine.
Do I need to connect the printer to the notebook first??... I mean, to upload the firmware...
Thanks again![/QUOTE]
I dont think that wud be necessary...

---

### Post by lizardking on 2005-12-16
I have it and it works. Some thing for the economy mode?

---

### Post by Jenda on 2005-12-16
OK, what I had to do to fix that was "sudo gedit /etc/cups/ppd/LaserJet-1020.ppd" and change the Default page size to A4. Maybe you should add that for users of A4.

---

### Post by arnieboy on 2005-12-16
[QUOTE=Jenda]OK, what I had to do to fix that was "sudo gedit /etc/cups/ppd/LaserJet-1020.ppd" and change the Default page size to A4. Maybe you should add that for users of A4.[/QUOTE]
Thanks! added.

---

### Post by Jenda on 2005-12-18
OK, Arnieboy: it anly fixed the test page. Printing from OO.org is still fuzzy.

---

### Post by arnieboy on 2005-12-18
not fuzzy on my printer.

---

### Post by Jenda on 2005-12-18
OK, I got it now. The thing was that OOo refused to set the paper size to A4, but after a few reinstalls, it gave in... :)).
Thanx

---

### Post by acorrigan on 2006-03-26
will changing the firmware in anyway affect the printer in windows?

my wife won't be happy if I get it working in linux at the expense of changing its ability to print in windows.

---

### Post by arnieboy on 2006-03-26
[QUOTE=acorrigan]will changing the firmware in anyway affect the printer in windows?

my wife won't be happy if I get it working in linux at the expense of changing its ability to print in windows.[/QUOTE]
No.

---

### Post by acorrigan on 2006-03-26
thanks!

---

### Post by acorrigan on 2006-03-26
Thank you Arnieboy for this helpful howto.

I just went through it step-by-step and did everything with one exception:
changing
SYSFS{idProduct}=="2B17"
to
SYSFS{idProduct}=="2b17"

the reason was that my 58-foo2zjs.rules file came with a 'b' there, not a 'B'  I heard the printer whirring when you said it should.  Now that I finished the howto nothing seems to have changed, when I go to print there is no printer there.

---

### Post by arnieboy on 2006-03-26
thats because you did not add any printer. This is just the driver installation howto. now that your system has the requisite drivers, you need to go to system --> administration --> printing and add your printer from there.

---

### Post by acorrigan on 2006-03-26
thank you arnieboy, that was not obvious to me, a perpetual n00b

now everything i print is fuzzy: test page, pdf file from document viewer, web pages from firefox, a text file from gedit  ](*,) 
i checked what size a4 paper is and it's not what i have 
the documents appear to be blurred horizontally, not vertically

if anyone has any suggestions I'd really appreciate it.  :D

---

### Post by arnieboy on 2006-03-26
[QUOTE=acorrigan]thank you arnieboy, that was not obvious to me, a perpetual n00b

now everything i print is fuzzy: test page, pdf file from document viewer, web pages from firefox, a text file from gedit  ](*,) 
i checked what size a4 paper is and it's not what i have 
the documents appear to be blurred horizontally, not vertically

if anyone has any suggestions I'd really appreciate it.  :D[/QUOTE]
go to system --> adminsitration --> printing and right click ther printer and hit properties.
now go to the "paper" tab
and select "A4"
hit close and try reprinting again.

---

### Post by acorrigan on 2006-03-26
it's still horizontally blurred.

---

### Post by arnieboy on 2006-03-26
try this:
```
sudo gedit /etc/cups/ppd/LaserJet-1020.ppd
```
and change the Default page size to A4 from "Letter"

---

### Post by acorrigan on 2006-03-28
thank you for all of your help arnieboy.  there is no more blurring!

Unfortunately the bottom of pages are cut off.  Do you know if this letter blurring problem might be fixed in a future driver release?

---

### Post by jarlz0r on 2006-04-25
[QUOTE=acorrigan]thank you for all of your help arnieboy.  there is no more blurring!

Unfortunately the bottom of pages are cut off.  Do you know if this letter blurring problem might be fixed in a future driver release?[/QUOTE]

Try this command again, looks like it should set the correct margins.
```
sudo lpoptions -o cpi-12 -o lpi=7 -o page-left=36 -o page-right=36 -o page-top=36 -o page-bottom=36
```

***arnieboy***: Thank you so much for this guide, will be trying it in a month or so when I buy this printer!

---

### Post by bungrudi on 2006-05-01
So... has anyone found any fix or workarround to this blurry-if-not-set-to-A4 problem? This is really annoying. We have 9 unit of HPLJ 1020, and recently forced to buy 3 XP Home licences just to get them print on letter and envelope size.

---

### Post by beeldings on 2006-05-01
I tried to set up the 1020 using this guide as well as [this]("http://foo2zjs.rkkda.com/") foo2zjs guide, and I am unable print anything. I first attempted using arnieboy's guide on a Dapper install, but that did not work. I re-installed Breezy and followed the foo2zjs guide and I am still unable to print. After following the foo2zjs guide, the gnome-cups-manager utility was able to detect the printer and posted the foo2zjs driver in the driver drop-down menu, but even if I chose that driver, I am unable to print a test page or upload the firmware. I restarted hotplug and cups and nothing happens, even if I switch the printer on and off. It powers on, but that's about it.

UPDATE: I plugged the cable into a different USB port and I was able to print a very blurry test page. I am going to go over both guides again and see if I can correct the blurriness.

UPDATE #2: To fix the problem with blurry print-outs, I re-installed Breezy and followed arnieboy's guide. Instead of "sudo make install-udev" I ran "sudo make install-hotplug" and then restarted cups and udev. I used the gnome-cups-manager and installed the 1020 using the foo2zjs driver. I clicked properties and chose 1200x600 DPI and printed a test page. It appears that everything is in order. That took long enough.

---

### Post by k.mankiller on 2006-05-11
I followed arnieboy's and beeldings' directions.  I have blurry printouts on Breezy with the foo2zjs driver and  letter sized paper, and (unlike beeldings) my Resolution dropdown in properties is greyed out.  What am I doing wrong?  

UPDATE:  Editing the wrapper file as described here seems to have solved the blurry printouts on letter sized paper for me:  [http://forums.gentoo.org/viewtopic-t-378173.html](http://forums.gentoo.org/viewtopic-t-378173.html).

---

### Post by EasyUwe on 2006-05-12
Hi together! your suggestions about the installation, helped me a lot so far! but i still have some priblems with the printer installation!

The  HP1020 is not connectet to the comp while i do the first steps of installation. i downloaded the patched packet and unziped it and tried to "make" the file afterwords. the problems and errors which are shown in the attached txt file.

can anybody help me?

THX Uwe

---

### Post by stucki7 on 2006-05-12
hi uwe,

maybe your system needs libc6-dev ;-)
br

[QUOTE=EasyUwe]Hi together! your suggestions about the installation, helped me a lot so far! but i still have some priblems with the printer installation!

The  HP1020 is not connectet to the comp while i do the first steps of installation. i downloaded the patched packet and unziped it and tried to "make" the file afterwords. the problems and errors which are shown in the attached txt file.

can anybody help me?

THX Uwe[/QUOTE]

---

### Post by EasyUwe on 2006-05-16
[QUOTE=stucki7]hi uwe,
maybe your system needs libc6-dev ;-)
br[/QUOTE]

That was the Problem THX!

But now i've got anotherone! I've installed the driver so far and everything was fine! i pluged on the printer but it doesent make the wiring like described. i thing the problem now is the firmware i found following on ```
http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020:

 The firmware of the printer must be uploaded after turning it on. You can use a hotplug/udev script which comes with foo2zjs, or do it manually: "cat /usr/share/foo2zjs/firmware/sihp1020.dl >  /dev/usb/lp0".
```

but the problem is i dont have this folder (firmware) in foo2zjs! I think i need to update the firmware of the printer! but does this work? can somebody help me?

THX UWE

---

### Post by bazi on 2006-09-15
> **beeldings said:**
> I tried to set up the 1020 using this guide as well as [this]("http://foo2zjs.rkkda.com/") foo2zjs guide, and I am unable print anything. I first attempted using arnieboy's guide on a Dapper install, but that did not work. I re-installed Breezy and followed the foo2zjs guide and I am still unable to print. After following the foo2zjs guide, the gnome-cups-manager utility was able to detect the printer and posted the foo2zjs driver in the driver drop-down menu, but even if I chose that driver, I am unable to print a test page or upload the firmware. I restarted hotplug and cups and nothing happens, even if I switch the printer on and off. It powers on, but that's about it.

UPDATE: I plugged the cable into a different USB port and I was able to print a very blurry test page. I am going to go over both guides again and see if I can correct the blurriness.

UPDATE #2: To fix the problem with blurry print-outs, I re-installed Breezy and followed arnieboy's guide. Instead of "sudo make install-udev" I ran "sudo make install-hotplug" and then restarted cups and udev. I used the gnome-cups-manager and installed the 1020 using the foo2zjs driver. I clicked properties and chose 1200x600 DPI and printed a test page. It appears that everything is in order. That took long enough.

my 1 month long exepriment with ubuntu ends here. hey i mean printing ... that REALLY SHOULD work outta box. sorry guys.

---

### Post by Alex.Gorban on 2006-09-18
I've hp1022 (it is seems to very similar to th hp1020).

If I choose hpijs driver for my printer, printing process is too slow due to delay between pages printing (that is very unusual for that printer)

If I choose foo2zjs driver, printing speed is normal, BUT content of printed pages tightened (compressed) in vertical direction so that it occupy only top half of the page.

---

### Post by Alex.Gorban on 2006-09-19
> **Alex.Gorban said:**
> I've hp1022 (it is seems to very similar to th hp1020).

If I choose hpijs driver for my printer, printing process is too slow due to delay between pages printing (that is very unusual for that printer)

If I choose foo2zjs driver, printing speed is normal, BUT content of printed pages tightened (compressed) in vertical direction so that it occupy only top half of the page.

Today I've found the way to solve my problem (with help of this forum)
Here is the [remedy]("http://foo2zjs.rkkda.com/")

The important note:
> DON'T USE the foo2zjs package from Ubuntu ...

I've installed driver for HP1020 and now everything is ok!:cool:

---

### Post by coalastonmatt on 2006-11-25
If anyone is still trying to get this to work... I couldn't get the above to compile on up-to-date Dapper. Had to upgrade to Edgy and a lot of other stuff but now works:

[http://ubuntuforums.org/showthread.php?t=190782&highlight=HP1020](http://ubuntuforums.org/showthread.php?t=190782&highlight=HP1020)

---

### Post by cdobica on 2007-09-05
I dont know what am i doing wrong but i cant install my printer. If tou can help me i will apreciate it

---

### Post by Openrulers on 2010-05-05
Thank you very much for these post.
I installed HP laser jet 1020 on Ubuntu 10.04 with commands but 
sudo /etc/init.d/cupsys restart
not worked. 
Had some top margin problem, which I think I can sort later..

---

