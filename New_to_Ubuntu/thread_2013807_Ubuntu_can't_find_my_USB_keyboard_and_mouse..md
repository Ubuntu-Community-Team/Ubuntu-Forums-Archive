---
title: "Ubuntu can't find my USB keyboard and mouse."
date: 2012-07-01
forum: New to Ubuntu
---

### Post by Metalslave on 2012-07-01
I'm fairly green when it comes to Ubuntu. I've run it on two other machines without any real issues. This is a new machine, though. I'm running Windows 7 as my main OS, but wanted to keep Ubuntu on the side. Installation (Wubi) went fine, but when I try to run Ubuntu, I only get as far as the login screen.

For some reason, Ubuntu can't find my USB keyboard (Razer Black Widow) and mouse (Razer Death Adder) and I'm not getting anywhere. I have tried plugging them in every USB connector I have, without any success. There's nothing actually wrong with the USB connectors, either. They work fine in W7.

Any ideas?

---

### Post by angry_johnnie on 2012-07-01
the only time i had something like that happen to me, it was because "legacy usb" wasn't enabled in the bios.  you may want to check into that.

---

### Post by Metalslave on 2012-07-26
I looked in the BIOS settings, but I can't find anything that mentions Legacy USB in there.

---

### Post by Ubun2to on 2012-07-26
Try a live CD. If it works there, it is a problem with the installation.
If you plan on using this as a long term install, don't use Wubi.

---

### Post by Metalslave on 2012-07-26
So, I attempted to reinstall Ubuntu. This time, Ubuntu did manage to find my mouse after 4-5 minutes. It didn't do much good, though. I was unable to click on any menus, etc. I could click all I wanted, but nothing happened. With the exception of the mouse cursor, Ubuntu appears to be completely frozen. Same mouse and keyboard as before, btw.

I let it sit for maybe 20 minutes, just to see if it would eventually find my keyboard too, but no. I had to do a hard reboot to get out of it.

Also, why shouldn't I use Wubi for a long term install? Is there anything wrong with it? How long is a "long term" install, anyway?

---

### Post by Ubun2to on 2012-07-26
> **Metalslave said:**
> So, I attempted to reinstall Ubuntu. This time, Ubuntu did manage to find my mouse after 4-5 minutes. It didn't do much good, though. I was unable to click on any menus, etc. I could click all I wanted, but nothing happened. With the exception of the mouse cursor, Ubuntu appears to be completely frozen. Same mouse and keyboard as before, btw.

I let it sit for maybe 20 minutes, just to see if it would eventually find my keyboard too, but no. I had to do a hard reboot to get out of it.

Also, why shouldn't I use Wubi for a long term install? Is there anything wrong with it? How long is a "long term" install, anyway?

Well, you should try using a PS/2 (not to be confused with the PlayStation 2) mouse and keyboard. If you don't know what those are, those are the ones with the connectors that are shaped like circles and have the pins inside them. If you don't have PS/2 ports, you are basically out of luck, unless it is a defective keyboard.
Wubi is not good for long term installs simply because you can only use up to 32 GB of space with it-it creates a virtual drive inside the Windows partition, so you can't expand it. To move your Wubi virtual drive to a new partition is a lot of work. I did it, and I wasn't too happy about how long it took.
A long term install is if you plan on keeping Ubuntu on your machine-Wubi is very useful if you just want to test it out on a computer for the first time (although the same concept can be accomplished via a live CD, this may be more convenient if you can't boot from a CD or USB, don't have a CD or USB drive, or can't create ISO images because you don't have Windows 7 and don't feel like installing any software). If you keep it on your machine for awhile, and you use it besides just to see what the OS is like, that space fills up extremely quick.

---

### Post by Juseeas on 2012-07-27
Just arrived. You are givving me a lot of hope. Thx!

---

### Post by Metalslave on 2012-08-21
I haven't owned a non-USB mouse and keyboard in years now. The mouse and keyboard I have work fine in W7, so there's nothing wrong with them. The problem remains that Ubuntu refuses to recognize any of my USB ports properly.

Does anyone have any idea?

---

### Post by Ubun2to on 2012-08-21
> **Metalslave said:**
> I haven't owned a non-USB mouse and keyboard in years now. The mouse and keyboard I have work fine in W7, so there's nothing wrong with them. The problem remains that Ubuntu refuses to recognize any of my USB ports properly.

Does anyone have any idea?

Well, does your computer have PS/2 ports? They are the purple and green circle shaped ones, if that helps. If so, see if any of your friends will let you borrow one. If that does not work, I'm not sure what is wrong with it.
Can you boot from a live CD and use your keyboard and mouse on it?

---

