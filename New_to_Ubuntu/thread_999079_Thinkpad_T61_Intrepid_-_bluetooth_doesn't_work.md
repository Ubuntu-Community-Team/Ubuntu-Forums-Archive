---
title: "Thinkpad T61 Intrepid - bluetooth doesn't work"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by ben.king on 2008-12-01
Hi,
I'm new in using kubuntu. So excuse me, if I don't know the right expressions.
I have the problem that my OS  didn't recognize the intern Bluetooth. I'm using a Thinkad T61, Linux version 2.6.27-9-generic. I don't know which informations you need so please tell me which commands I have to type in so you can help me. I searched around a littlebit and tried some commands:

:~$ /proc/acpi/ibm/bluetooth
bash: /proc/acpi/ibm/bluetooth: No such file or directory

:~$ hcitool scan
Device is not available: No such device

It is no problem to activate and deactivate WLAN by pressing FN+F5, but this has no effect upon Bluetooth.
If there is a thread which solved my problem please tell me, i searched for an answer but didn't find one.

---

### Post by PegMonster on 2008-12-02
This is from the [[COLOR="Red"]*release notes*[/COLOR]]("http://www.ubuntu.com/getubuntu/releasenotes/810") page-


> Bluetooth is not supported in Kubuntu 8.10 because KDE does not yet support the bluez 4.x stack required for compatibility with the kernel used in 8.10. A fix for this is being evaluated as a post-release update. [*[COLOR="#ff0000"](Bug 280997)[/COLOR]*]("https://launchpad.net/bugs/280997")

I don't know when the fix is to be released.

Not good news for now, but at least you know its not you at fault.

It seems some are installing bluez-gnome, which is an option, but it comes with a whole load of other gnome stuff.

I'd prefer to wait for the fix.

J

---

### Post by Ben Webber on 2008-12-02
If Bluetooth is really important, non-KDE Ubuntu supports it out of the box on my T61p. If it's not then wait for that update.

---

### Post by ben.king on 2008-12-02
Thank you for the answer. I think I have to read the Release-notes more carefully ;-)
Hope the update cames right in time

---

### Post by katana2k on 2008-12-05
the problem isnt just KDE, they havent really addressed your problem. I'm running ubuntu 8.10 and have the same issue on gnome. Fn+F5 doesnt seem to enable or disable the internal bluetooth like its supposed to. $/proc/acpi/ibm/bluetooth produces the same result for me as well (not found)

---

### Post by ben.king on 2009-01-23
Hello katana2k,

I have recently "changed" my kubuntu into an ubuntu. I had some little problems with KDE and compiz so I changed to gnome. And yes katana your right. Same Problem here, no bluetooth at all. 
Slowly but steady I believe I don't even have bluetooth. Is there a possibility to be sure I have  bluetooth inside my Thinkpad T61? I thought I paid for it (it was mentioned in the sale descreption)

TIA

---

### Post by katana2k on 2009-03-06
yeah, im fairly certain my laptop has bluetooth built in too but im not seeing any indication of it at all. I even have a bluetooth dongle that works in any other computer but refuses to allow me to pair anything to my t61p under intrepid.

---

