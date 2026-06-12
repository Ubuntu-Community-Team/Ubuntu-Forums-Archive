---
title: "Canon Pixma MG2140 Printer Installation Problems"
date: 2012-08-24
forum: New to Ubuntu
---

### Post by Gonda on 2012-08-24
Hi, 

I just purchased the above printer and installed it using cnijfilter-mg2100series-3.60-1-deb. It printed a test page in black and white successfully, but it won't print in colour. 

I did not install via the cd's that came with the printer as the instructions only include windows and mac.  I am not sure if it is a printer issue or a driver issue. 

1. What should I do?
2. Can I switch over to XP and instal with the cd's as well as have the same printer installed on Ubuntu? I don't want to mess it up, but I thought that if I do that I can see if it functions correctly on XP then i will know for certain it is a problem on Ubuntu.
3. I have searched the Canon site for drivers but this make is not included in the drop down options list. 
4. Do you know where with Ubuntu i can find colour drivers and how do I install them etc?


My pc is partitioned with XP and Ubuntu. PC: Inte (R) Core (TM) 2 CPU, 32 bit res, Nvidia GeForce 7300GT.

---

### Post by Gonda on 2012-08-24
Ok, well printer works perfectly in windows - problem is that I was hoping to move away from windows entirely.

Can anyone suggest a way to get the colour working in ubuntu?

---

### Post by rooikoos on 2012-09-03
I have the same problem with my MG2140..worked fine in Windows. I might have to ditch Linux if I can't get it working.

---

### Post by pdc on 2012-09-06
the driver from post #1 should be fine: 

as you can see, canon release a 2100 series printer driver; so whether it is 2140 or 2160 or 2170 is fine............

one can get them from Canon europe or canon asia...

*and curiously canon usa doesn't list a linux driver*...

anyway, here is the canon asia driver for anyone else...

[http://support-sg.canon-asia.com/P/search?model=PIXMA+MG2170&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-sg.canon-asia.com/P/search?model=PIXMA+MG2170&menu=download&filter=0&tagname=g_os&g_os=Linux)

are you both running 32bit ubuntu?........64bit?

I installed a 2100 series printer recently; I downloaded the scangearmp and printer drivers; ....installed from a terminal and both the scanner and printer are fine; .......colour on tap............

which programmes will not give you colour?

I have looked in settings to try to puzzle this out... beats me......

......mine just worked .........out of the box........

> installed it using cnijfilter-mg2100series-3.60-1-deb. ............using terminal.......archive manager......is the printer showing in the printer configuration menu?

---

### Post by rooikoos on 2012-09-15
Thanks, pdc. Got mine working. Downloaded the drivers and installed them. Had to delete the printer and then added it again. Now the colour is good. Yes, I am running 32 bit. Now for the scanner. After installing the printer and running the scanner drivers, simple scan says there are no scanners detected. How do I set up this scanner? I'm new to linux, in every sense, so I would appreciate clear guidelines if you don't mind. Thank you.

---

### Post by pdc on 2012-09-15
well done to get the drivers installed for the printer; enjoy!

for the scanner, Canon makes a programme called ScanGear and they make a debian package 

..so go here.....

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100392902.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100392902.html)

and download the MG2100 series ScanGear MP Ver. 1.80 for Linux (debian Packagearchive)

Gdebi installer is likely to jump in when you click to download it: 

it will offer 

a) open with archive manager or

b) save

.........either is good.......whichever you do.........

If you open the debian package of scangear; by clicking on it;

there is an install.sh script............

......if you double click on that, it should run...........

(I installed mine from the terminal ..so I didn't actually do the above but when I look at the GUI setup, it should........all work)

once you have scangear installed, the first way to test it is

copy and paste into a terminal

> scangearmp

......that should open the Canon scanning programme (scangear)..

.....to make this easier for repeated uses, one creates a launcher

[http://www.geekyboy.com/archives/384](http://www.geekyboy.com/archives/384)

use Method 2 from the above post

......the essence of it is the two commands below.........

> sudo apt-get install --no-install-recommends gnome-panel

and that installs gnome-panel ..and then 

> gnome-desktop-item-edit ~/Desktop/ --create-new

and that should give you a dialogue box

..in that........

Type: Application
Name: ScanGear (or whatever you wish........)
Command:scangearmp

.........then you should get an icon on your desktop to launch scangear; you should be able to change the icon as you wish........

let us know how it goes..

.if you subscribe to a thread (thread tools at top right) you can get an email to tell you a reply awaits you ........

---

### Post by codingman on 2012-09-15
I happen to have the mg5320 of the pixma series, and I found a bunch of drivers on the canon ireland site. Apart from that the drivers above should work fine.

---

### Post by pdc on 2012-09-15
indeed; to be sure; isn't it after being the same driver as I mentioned above?

---

### Post by codingman on 2012-09-15
Pretty much, yup!

---

### Post by rooikoos on 2012-09-21
Thanks a lot! Got everything working now:) well, as far as the printer goes!

---

### Post by pdc on 2012-09-22
...........so scangear is working well for you.....that's great; enjoy;

there is always something new to learn in linux for everyone!

---

