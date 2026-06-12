---
title: "I see the printer on workgroup and need to install?"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-19
After installing Hardy, the USB 8187 Adapter and the LAN Workgroup became functional.

I can see the following folder but I do not know how to install the Brother MFC-440cn printer:

smb://jandesktop/print$/w32x86/brothermfc_440cn3120/bril06a.dll
smb://jandesktop/print$/w32x86/brothermfc_440cn3120/brio06a.dat
smb://jandesktop/print$/w32x86/brothermfc_440cn3120/brio06a.dll
smb://jandesktop/print$/w32x86/brothermfc_440cn3120/brio06a.hlp
smb://jandesktop/print$/w32x86/brothermfc_440cn3120/brio06aa.bcm
smb://jandesktop/print$/w32x86/brothermfc_440cn3120/brio06ab.bcm
smb://jandesktop/print$/w32x86/brothermfc_440cn3120/brio06ac.bcm
smb://jandesktop/print$/w32x86/brothermfc_440cn3120/brio06af.bcm
smb://jandesktop/print$/w32x86/brothermfc_440cn3120/brio06ag.bcm
smb://jandesktop/print$/w32x86/brothermfc_440cn3120/briu06a.dll
smb://jandesktop/print$/w32x86/brothermfc_440cn3120/briwm06a.ini
smb://jandesktop/print$/w32x86/brothermfc_440cn3120/brmf440c.ini
smb://jandesktop/print$/w32x86/brothermfc_440cn3120/brmf440c.pdd
smb://jandesktop/print$/w32x86/brothermfc_440cn3120/brqikmon.exe
smb://jandesktop/print$/w32x86/brothermfc_440cn3120/brqikmon.hlp

Suggestions of how to install please.

---

### Post by mastablasta on 2012-04-19
not a good way to go since hardy (desktop) is not supported. continue your efforts on later Ubutnu edition. 
 
in hardy you would also need to install printer.
 
if you see it in hardy you should also see it in a later Ubuntu version. if you are using USB to ocnnect you need to trouble shoot that one or samba.

---

### Post by Boyntonstu on 2012-04-19
> **mastablasta said:**
> not a good way to go since hardy (desktop) is not supported. continue your efforts on later Ubutnu edition. 
 
in hardy you would also need to install printer.
 
if you see it in hardy you should also see it in a later Ubuntu version. if you are using USB to ocnnect you need to trouble shoot that one or samba.

My desktop is Ubuntu 11.10.

I used Hardy to install the USB wifi adapter and to get the LAN running.

I do not see Hardy or know that it exists beyond that.

---

### Post by mastablasta on 2012-04-19
well then it's the same procedure as usual.
install printer driver. 
then
add printer 
type in the printer place (or browse to it) smb://jandesktop/print$/yourprintername
or it could be smb://mshome/jandesktop/print$/yourprintermane
i ofund out that smbtree show it best.
 
then continue, select your printer form the list and it should work.

---

### Post by roger_1960 on 2012-04-19
Hi

I would start by studying these pages.  You need the LP and CUPS drivers.  There are pre install things to do and "general settings" for scanner driver to follow.  If you follow it all it will probably work.  I am on my 2nd Brother printer/scanner and it all works (but not the same model as you)

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

(The files you list in your first post are windows driver files and wont work with ubuntu)

Good luck

---

### Post by Boyntonstu on 2012-04-19
> **roger_1960 said:**
> Hi

I would start by studying these pages.  You need the LP and CUPS drivers.  There are pre install things to do and "general settings" for scanner driver to follow.  If you follow it all it will probably work.  I am on my 2nd Brother printer/scanner and it all works (but not the same model as you)

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

(The files you list in your first post are windows driver files and wont work with ubuntu)

Good luck

Thanks,

I used CUPS and installed the printer.

This is where we are:

Printer added.

Almost there:

[img]http://i348.photobucket.com/albums/q339/BoyntonStu/Screenshotat2012-04-19123013.png[/img]

---

