---
title: "New laptop setup suggestion"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by mrgoodfox on 2013-02-16
(thanks to the help I got from this forum) I put Ubuntu on my laptop as dual boot along with a Windows 7. My laptop is pretty old and falling apart so its time to buy a new one. 

Once i get the new laptop I'd like to learn the ins and outs of Ubuntu better and start using it as my main operating system (instead of the Windows 7 that i use now). I do however need Win7. 

The solution that I have in mind is an Ubuntu base computer and running a number of images inside of it for the other operating systems (ie WIN7) that I need. I'm putting 16GB of RAM and i7 processor in the new laptop so running Ubuntu along with one or two images in it shouldn't be a problem.

What are your thoughts?

---

### Post by arpanaut on 2013-02-16
If you are getting a NEW laptop it will probably have the new uefi bios so you will need to be aware of this:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
which will allow dual/multiple boot set up

Another option is to use virtualisation from within Windows
or you can run windows from within Ubuntu
[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by PIE09gbLmgG6 on 2013-02-16
Someone pointed me at system76.com....

Going to do the same thing...hate having to have windows for work...makes byod not such a good thing...

ego-

---

### Post by DuckHook on 2013-02-16
+1 @arpanaut

Another option is WINE which requires a little more tinkering to get right, but which has the potential to be the slickest solution. WINE success is highly dependent on app compatibility. If you are using only a small set of standard Windows productivity apps, then good chance of success. If you must use AutoCAD, Quickbooks, etc. then it won't work.

---

### Post by DuckHook on 2013-02-16
> **egosophist said:**
> I remember something called lindows years ago...it was here then gone...figured microsquish squished'em...

or they just died from lack of demand. As I recall, they charged money, which is difficult for users to justify when a hundred distros are available for free.

> Tried wine when i downloaded 12.04 last year...gave up...might be different this time around...It is finicky. It must be tweaked and fine-tuned. And the WINE terminology is a whole 'nuther "undiscovered country". I.e. what is a prefix? I know now, but it took a long time to puzzle it out. The WINE [subforum]("http://ubuntuforums.org/forumdisplay.php?f=313") is very helpful.

---

### Post by Mark Phelps on 2013-02-16
The two most-used Windows products (MS Office 2010 and IE 9.x) don't work well in Wine, so relying on that to use them is an exercise in frustration.

Since you're going to install Windows in a VM anyway, don't even bother with Wine.

---

### Post by mrgoodfox on 2013-02-16
Im gonna go head and use Ubuntu as base and Windows in an image inside of it for work and other needs.  That way I'll learn Ubuntu better too

---

### Post by JayKay3OOO on 2013-02-16
I have to run Windows 7 in VirtualBox. As long as your computer has enough RAM and a bit of horsepower or batterypower then the things you 'need' or think you need Windows for work fine although aero is disabled.

I thought I needed Windows for a long time and now I literally have to scratch my head for anything I need it for. Oh I know. So that when clients phone me that their Windows machine broke I can go fix it. :D

---

### Post by marks_linux on 2013-02-16
On that note (sorry to hijack). Is there a way to virtualise a current win7 install so I can then run as a virtual machine under Ubuntu. I can then remove my pesky dual boot. Laptop came preinstalled with win7 but without media.

---

### Post by DuckHook on 2013-02-16
> **marks_linux said:**
> Is there a way to virtualise a current win7 install...

  	 	 	 	 	It is possible, but very tricky, very risky.

[https://www.virtualbox.org/wiki/Migrate_Windows](https://www.virtualbox.org/wiki/Migrate_Windows)

Many who have tried this have not only failed but have left their W7 installation no longer bootable as dual boot. If you are dual booting without problems (aside from the inconvenience), I would leave it alone and just consider myself blessed.

---

