---
title: "Use live cd to fix Hardy screen Resolution"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by lance bermudez on 2008-05-06
I have an old dell computer with built in video card that used the i810 driver. After i had set my resolution then restarted my computer i would have no screen that i could use to see and the computer would freeze so i could not use the cltr+alt+f1 to get the terminal. the xfix command from the repair thing at start would not reset my video for me and the commmand xserver-xorg no longer works  with hardy. I use the live cd for dapper drake and mounted my root drive and copyed the xorg.conf file from /etc/X11 from the live cd to the root of my harddrive in the /etc/X11 to replace the root harddirve xorg.conf file their restarted my computer and things seem to work fine. I also found out that my xorg.conf has more in it now then it frist did becuse i thing that hardy was unable or not willing to detect my video and monitor.

---

### Post by amohanty on 2008-05-06
Hardy uses the latest Xorg which does not particularly need xorg.conf (I am oversimplifying). However you can always use a custom one and override the default settings.

To reset your xorg to the orignal version, from the grub menu boot into the recovery console and type:
dpkg-reconfigure xserver-xorg
and click through.

hth
am

---

### Post by lance bermudez on 2008-05-07
The commmand did not work for me. I have tried that before that is why i copyied the xorg.config file from the live cd. thank you for your help.

---

### Post by bodhi.zazen on 2008-05-07
yea, xorg.conf bombs out with the i810 which is a surpize.

You can get a working gui by either booting to recovery mode and using xfix or

sudo dpkg-reconfigure xserver-xorg

Now that will look ugly :(

I hand wrote a xorg.conf for this card and can post it later tonight (@ work now).

It helps but does not fix the problem. No I have not been able to copy-paste previous sections from previous versions of xorg.

For what it is worth, I think it is a problem with xorg 7.3 as I have the same problem with Fedora 9 Preview.

---

