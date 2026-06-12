---
title: "Hardware issues. Computer freezing up &quot;I/O Error&quot;"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by usernamoftheubuforums on 2012-05-11
Maybe this is the wrong forum, but I thought i'd try anyway.

I was getting the BSOD on windows a lot, so I thought i'd try clearing everything and loading Ubuntu to see if it was a software or hardware issue.

I'm now getting errors at the same frequency as the BSODs. Only now, on linux, my programs close/freeze up and I can't open any programs up, but I'm free to use the terminal. except the terminal gives me "I/O Error" when I try to do things.
It usually doesn't freeze up till about 1-3 hours of use.

I try to reset the system with ctrl+alt+delete but nothing happens.
alt + sysRq thingis change the screen but won't reboot it.

So if anyone has an idea as to what's wrong with my computer, please help. maybe the RAM has problems?

---

### Post by critin on 2012-05-11
Since the error is the same for both systems, I'd suspect a hardware problem.  The HDD?
You can go into disk utility in ubuntu and click Smart Data.  It can give insight into the state of the HDD.

---

### Post by usernamoftheubuforums on 2012-05-11
I have an SSD. I looked in the Disk Utility thingy and checked the SMART data status. Everything in there was good.

---

### Post by usernamoftheubuforums on 2012-05-11
Okay, so I have a lead on what might be the problem. I'm reading the crucial forums to figure out how to update my firmware on ubuntu.


(firmware bug causes SSD to have problems after X hours of time)
[http://www.theverge.com/2012/1/17/2713178/crucial-m4-ssd-firmware-update-fixes-recurring-bsod](http://www.theverge.com/2012/1/17/2713178/crucial-m4-ssd-firmware-update-fixes-recurring-bsod)

---

### Post by usernamoftheubuforums on 2012-05-11
okay, so I'm trying to update my firmware but can't figure out how.

I tried using WINE on the executable, but nothing happens.


Any ideas? The website has the updater in only these formats:
Windows® 7 Updater Application
Manual Boot File for Windows and Mac

---

### Post by usernamoftheubuforums on 2012-05-11
Okay, turns out the boot loader worked. I had to run it twice since the first time it gave me an error.
but my firmware is upgraded, and now hopefully that was the problem.

---

