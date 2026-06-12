---
title: "native driver support"
date: 2013-03-17
forum: New to Ubuntu
---

### Post by noobman29 on 2013-03-17
ill just start out by saying im a complete noob and i havve used windows or dos my whole life but wih 8 and the office anuual fee now being inacted i want to try somthing difrent im curently working on a harware compadibility list trying to determine what dll's need downloading aand install and how to do it i gurss what i need is a list of native dll's provided with linux install if theres any way someone could point me in the direction of a list i would be very gratfull

---

### Post by noobman29 on 2013-03-17
heres the semi comploete list
pc= acpi 32bit
hdd= 2 sata one wd usb
video =nvidia quadro nvs290
standard floppy
wirless=belkin fsd8053
or
netgear wna1100n150
cpu= intell duo cpu e6550@2.33
audio= sundblaster hd x-fi usb and atsc ub445-u internal
make = dell precision3400
thanks again

---

### Post by noobman29 on 2013-03-17
cd/dvd  ts-8493b

---

### Post by Mark Phelps on 2013-03-17
You're question about downloading DLLs indicates that you are unfamiliar with the Linux architecture.  Windows uses DLLs, Linux does not.

The only place that DLLs come into play is with Wine -- but those are custom versions that CodeWeavers rewrote to use Linux system calls instead of Windows system calls.

If your intent in coming to Linux is to use Windows apps (like Office), then you're setting yourself up for major disappointments and a LOT of work.

IF you go to the WineHQ website, and look up the Windows apps you want to use (in their application compatibility page), you will see their ratings in using Wine.  Anything you need to use daily, that either is not listed, or is rated lower than GOLD, is going to be a waste of your time.

---

### Post by noobman29 on 2013-03-17
sorry mistype i realize that there nodlls and the architecture is difrent and that i wont be able to use windows software i actuly planned on looking for a way to safley surf and do things like stream audio video on the web now that vista update has stoped working and no one knows why or how to fix it and use vista for audio and video activitys now because of the fact that my x-fi hd  is unsopported as well as my tv dongle so i have downloaded the deb package for my wna1100 wireless adaptor and set up a separate usb soundcard that i own tat is compatable and just installed wudi 12.1 and if everything is cool plan is to migrate it toa free drive so sorry for not using the wright terminology after all im a noob oh ya i realize flash isnt supported but i can use minitube for you tube and a shoutcast client for audio

---

