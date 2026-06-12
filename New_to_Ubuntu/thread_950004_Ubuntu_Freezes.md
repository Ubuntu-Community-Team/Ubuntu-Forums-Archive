---
title: "Ubuntu Freezes"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by crzytoxicant on 2008-10-16
Here's the deal, I just recently installed Ubuntu 8.04 on my Dell Inspiron 8600, and everything went smoothly. The computer runs great, and I only have one problem, everytime i log out and try to log back in, Ubuntu freezes, showing only my cursor and the background of my desktop. Anyone have a clue what is wrong?

---

### Post by randy78 on 2008-10-16
When you get to your login screen, select session>Failsafe Terminal and login

Then do:
sudo dpkg-reconfigure xserver-xorg

Let it finish and then type:
sudo reboot 

Let us know if that helps

Also, what kind of graphics card and processor does this have?
How much memory?
If the system has a 64 bit processor, are you sure that you're using the 64 bit version of Ubuntu?

Take Care

---

### Post by crzytoxicant on 2008-10-16
alright, well my graphics card is an ATI Radeon 9600, and I'm currently running on 512 MB of DDR ram. I believe it's pc 2100, but I'm not entirely sure. I'm almost 100% sure it's a graphics card driver issue, as I tried to log out, and this time, it told me it couldn't recognize my card, and the resolution was extremely low. i tired using the commands in failsafe terminal, but had no idea what I was doing, so i just left it as is.

---

### Post by Zzl1xndd on 2008-10-16
Are you using the Open source or Proprietary driver?

---

### Post by randy78 on 2008-10-17
Ok

Write down the commands and enter them exactly as I typed them out

Try this and we'll go from there
:D

---

### Post by crzytoxicant on 2008-10-17
No, what I meant by I had no idea what i was doing, I mean that I had already punched in the first command into the terminal, and got all the way up to the part when it started asking for keyboard detection. After that, I had no idea what the thing was asking me to name or enter a value.

---

