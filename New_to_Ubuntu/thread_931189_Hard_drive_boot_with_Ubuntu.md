---
title: "Hard drive boot with Ubuntu"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Philthebeat on 2008-09-27
Hi, 
I am really new to Ubuntu and wouldlike to get to know how to use it. I still need to have Windows as there is a lot of work I do with Windows. Is there a way to use a external hard drive where I could install Ubuntu and boot my laptop from the external drive?
If anyone could help and point me in the write direction then it would be helpful. 

Also would I need to partition the hard disk with the Ubuntu part and the data storage part? 

Thanks

---

### Post by didiercool on 2008-09-27
Ya, I did this with my ipod for a while!  Plug in your external hard drive and use the live CD.  When it gets to the partitioning part, there should be a 'partition' that is your external drive.  Choose that one.  If you still want to use it as data storage apart from ubuntu you could go ahead and use the partitioner on the live CD.  Then just install it normally from then on.  To boot from that, you'll have to change your BIOS options to include USB boot (older BIOS's don't have that option and you'll have to upgrade the software).  That should work for you!  It worked quite nicely on my Ipod!  Good luck!

~peace

ps. Another thing you might consider is dual boot.  That's how I started using Ubuntu.  To do that, don't change anything in windows (make sure its installed and all :)) and don't try to partition anything with windows.  Back everything up (just to be safe) and install using the live cd.  The partitioner on that is really easy to use and self explanatory.  Then you'll be asked upon each boot which operating system you want to use.  Your external drive could then remain primarily as a backup drive.

---

### Post by Philthebeat on 2008-10-03
Thanks a lot. 
I will give this a go and see how it goes. 
:D

---

### Post by scotty2 on 2008-10-03
I have done this successfully with a reasonably new laptop.  The only difficulty I encountered related to where GRUB was stored.  As I did not want to make any alterations to the laptop I wanted GRUB on the external drive.  With the USB disk at the top of the list of boot devices, you see the GRUB menu if the external drive is connected.  If it is not connected the laptop boots as normal with no GRUB menu.  I recall having to set this up under the "Advanced" tab on the final screen of the install process.

---

