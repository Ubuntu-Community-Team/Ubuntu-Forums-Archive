---
title: "How do I fix NTLDR without reinstalling Ubuntu"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by arashiko28 on 2008-11-15
So, a very aggressive virus invaded my computer (windows, obviously), it has evaded all antivirus and scans and then presented itself as an antivirus. In short, this thing deleted my NTLDR files and now, windows do not start (obviously). Now, How do I recover these files without modifiying the MBR, because I know if this happens, I will lose the linux GRUB and won't be able to boot on ubuntu without a reinstallation which I'll be profoundly grateful in avoiding. (Need to work now!!!) As far is my only hope, so pleeeaaaseee, help me to do this without loosing ubuntu.8-[

---

### Post by shifty_powers on 2008-11-15
do you have the original windows cd?

if so then

[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

will help

---

### Post by PocketDog on 2008-11-15
Also, don't worry about replacing the MBR if you have to. At worst you'll have to re-install Grub using an Ubuntu or Grub CD, you won't have to re-install Ubuntu

---

### Post by Duck2006 on 2008-11-15
If worst comes to worst and you have to reinstall windoze and then reinstall grub. Some info on grub,

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by arashiko28 on 2008-11-16
Geez, that GRUB recovering guide gave a headache... I'm a bit afraid to try this, seems pretty difficult to re-install GRUB... I see for a GRUB for dummies before I jump that cliff...:confused:

Can't anyone tell me to do this in slow and calmed english? I'm not an IT, so I get lost pretty easily...

I have the USB ready, my backup system is Ubuntu 8.04. I'm trying to understand, but it's a bit too complicated for me... please, help!!!

---

### Post by The Cog on 2008-11-16
Reinstalling GRUB after reinstalling windows is easy. Use the Ubuntu installer CD and take the option to rescue your Ubuntu installation. When it gives you a command prompt, use the command:
**grub-install /dev/sda**

---

### Post by unutbu on 2008-11-16
You can get the NTLDR files, and instructions on how to reinstall them here:
[http://ubuntuforums.org/showthread.php?p=5082723#post5082723](http://ubuntuforums.org/showthread.php?p=5082723#post5082723)

---

### Post by markharding557 on 2008-11-16
to get rid of your virus you can install clamav and a front end gui like clamtk and then scan the windows drive from ubuntu.
if you can't boot it can be done with a live cd

---

### Post by markharding557 on 2008-11-16
sorry duplicate post internet playing silly buggers

---

