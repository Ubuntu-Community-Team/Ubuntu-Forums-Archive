---
title: "Howto: Set up HP laserjet 1000 printer on Dapper"
date: 2006-06-19
forum: Outdated Tutorials &amp; Tips
---

### Post by paulmilliken on 2006-06-19
The HP laserjet 1000 printer does not work "out of the box" with Dapper Drake at the time of writing.  Furthermore, the instructions on [http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/"), which work under Hoary and Warty, do not work without some modification.  This Howto describes the required modifications.

1.  Follow the instructions on [http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/") to download the firmware and drivers for your printer and to install the drivers.
2.  As root, edit the file /etc/cups/printers.conf and find the line starting with "DeviceURI".  Now edit this line such that it reads:
"DeviceURI file:///dev/usb/lp0"
3.  Now restart cups by typing: "sudo /etc/init.d/cupsys restart" at the command line.  (Thanks to the posters at [https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/43824]("https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/43824")  for steps 2 and 3).
4.  Now try printing a page :)

There is a link on [http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/") where you can donate money to the author of the driver.  If you are able, I'm sure he/she will appreciate it.

---

### Post by jostein on 2006-06-24
I installed kubuntu dapper yesterday, and had my hp laserjet 1000 printer up and running quickly, by just following the add printer wizard in the kde control centre. In the wizard, the printer had two entries: one where it was connected to "hp:/blablabla" and one connected to "usb:/blabla". Choosing the former connection and the recommended driver, the printer was up and running immediately. But maybe this is more diffucult in GNOME?

---

### Post by maulattu on 2006-06-25
[QUOTE=paulmilliken]The HP laserjet 1000 printer does not work "out of the box" with Dapper Drake at the time of writing.  Furthermore, the instructions on [http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/"), which work under Hoary and Warty, do not work without some modification.  This Howto describes the required modifications.

1.  Follow the instructions on [http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/") to download the firmware and drivers for your printer and to install the drivers.
[B]2.  As root, edit the file /etc/cups/printers.conf and find the line starting with "DeviceURI".  Now edit this line such that it reads:
"DeviceURI file:///dev/usb/lp0"[/B]
3.  Now restart cups by typing: "sudo /etc/init.d/cupsys restart" at the command line.  (Thanks to the posters at [https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/43824]("https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/43824")  for steps 2 and 3).
4.  Now try printing a page :)

There is a link on [http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/") where you can donate money to the author of the driver.  If you are able, I'm sure he/she will appreciate it.[/QUOTE]

you ARE the man!:mrgreen: :mrgreen: :mrgreen: 
thank you mate8)

---

### Post by davidgypsy on 2006-07-03
Strange thing... when I try to run the command "make", it tells me that command is not found. How do I get it to do this command?

So sorry, newbie question... :)

---

### Post by maulattu on 2006-07-06
[QUOTE=davidgypsy]Strange thing... when I try to run the command "make", it tells me that command is not found. How do I get it to do this command?

So sorry, newbie question... :)[/QUOTE]

```
sudo apt-get install build-essential
sudo apt-get install make
```

then you are able to compile ;)

---

### Post by davidgypsy on 2006-07-09
Thanks! Doing it now... 
Nice dog.

---

### Post by CPSC Sam on 2006-07-16
It didn't work, it just said "Printer fault!"

Edit: IT WORKED!

1) First install the drivers from the site.
2) Then ADD THE PRINTER TO CUPS
3) Change the line to "DeviceURI file:///dev/usb/lp0"
4) Restart cups

I was doing it in the wrong order.. I added the line then added the printer.

---

### Post by davidgypsy on 2006-07-25
After all this it says "The CUPS server could not be contacted"

What now?

---

### Post by alvonsius on 2006-07-25
Damn ... i just realize that HP1000 was suported in Dapper. And it works even from Windows shared networks ... cool dude ... way to go developers!!! Love you all !!! :D

---

### Post by davidgypsy on 2006-07-26
> **alvonsius said:**
> Damn ... i just realize that HP1000 was suported in Dapper. And it works even from Windows shared networks ... cool dude ... way to go developers!!! Love you all !!! :D

It didn't work for me, and now my CUPS doesn't seem to work either. ](*,)

---

### Post by paulmilliken on 2006-07-27
Davidgypsy,

Please post some more information - Plug your printer in and turn it on.  Now check to see if dev /dev/usb exists?  How about /dev/usb/lp0?  Also, please check if /dev/usblp0 exists (yes, there is no "/" between usb and lp0).

You can do this with the "ls /dev/u*" command or by browsing in the gui.

Paul

---

### Post by daller on 2006-11-14
Does this also apply to Edgy?

---

### Post by Sianis on 2006-12-13
Yes, it does.

But, after install, you must restart the system.

---

### Post by sinaen on 2007-05-08
hmm.. tried everywhere to find the correct uri for my printer. i have a hp laserjet 5l that is to run hpjs protocol. via cups.
but i dont know what uri to write. as i only have a default kernel. and it doesnt find any devices on lp it doesnt create /dev/lp*
its very annoying...

---

### Post by sinaen on 2007-05-08
The bastards motherboards ports where disabled

---

### Post by Strog on 2008-11-24
Little outdated theme but id helped me to make my HP LJ1000w work ;).

---

### Post by Lars Emil Gutt on 2009-03-23
Im pretty new on ubuntu, and i don't know how to edit printers.conf:( Could someone tell me how to do that?

---

### Post by Lars Emil Gutt on 2009-03-23
Got it fixed now :p

---

### Post by heroidi on 2009-05-26
not yet working for me :S:(:(

---

