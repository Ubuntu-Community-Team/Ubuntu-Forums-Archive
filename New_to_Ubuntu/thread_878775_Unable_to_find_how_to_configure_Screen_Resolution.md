---
title: "Unable to find how to configure Screen Resolution"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by SusiBiker on 2008-08-03
Hi. TOTAL newbie.

All searches I have done have left me with a lot of ideas, but no knowledge on how to make them work...

Installed 8.04.1 a couple of days ago, but cannot work out how to install the driver for my nVidia graphics card as I am currently limited to 800x600.
I have the driver, NVIDIA-Linux-x86-173.14.12-pkg1.run, but cannot workout how to install it as all the methods of accessing X that I have tried have come to a dead end. I have a viewsonic VX912 capable of 1280x1024@60Hz,and an nVidia GeForce 7050 integrated graphics processor.

Baby steps please.

I'm sorry to come begging for help, but I am totally out of my depth here.
Not a computer newb, but years of being a MicroSoftie...

Sorry too, if I've posted in the wrong place.
Regards,
Susan

---

### Post by stoneybroke on 2008-08-03
Hi Susan Have you tried System>Administration>Hardware Drivers? if not go there and click the box where it says Enable and it should download the latest Nvidia drivers

We Hope,

---

### Post by wolfen69 on 2008-08-03
welcome to ubuntu. you do not have to apologise for asking a question.this is what the forums are for. feel free to ask a million questions. people will be more than happy to help. after you install the nvidia driver as mentioned by stoneybroke, if you still dont have the resolution you desire, go to applications>accessories>terminal and type(copy and paste) in:```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then hit enter. enter password.then  reboot.

---

### Post by SusiBiker on 2008-08-03
Thanks for the reply guys. Much appreciated.

I had already tried stoneybroke's (thanks for trying!) method and rebooting, but that removes the 800x600 & 640x480 modes and replaces and replaces it with the options 640x480 & 320x240.

wolfen69's method, then returns the screen back to 800x600 & 640x480 only. Nothing higher.

The system gave a warning about the nVidia drivers. I'll try again and post the warning if it comes up again.

My noodle is melting.

---

### Post by bobnutfield on 2008-08-03
If you have an nVidia graphics card, many find it easier to install EnvyNG to automatically detect and install the correct video drivers.  You can find it in Synaptics package manager.  The resolution issues I have always had were solved by doing this because EnvyNG also sets up you Xorg.conf file automatially.

---

### Post by ellgor on 2008-08-03
Hi,

Check to see if you have a package called nvidia-settings (synaptic) install if not, then, open a terminal and type in:

gksudo nvidia-settings

a new window will open with the nvidia settings for you to look/adjust (if I recall right its the second option down, Xorg or something) scroll down the page to get at the changeable settings and adjust to taste, hope this helps.

Regards, Ellgor.

---

### Post by SusiBiker on 2008-08-03
Dear bobnutfield, it worked!

If anyone else is interested-
I installed EnvyNG as suggested. Ran it. Let it do it's thing. Restarted. Got the reduced resolution 640x480 screen again. Went to Hardware Drivers, installed nVidia driver.
Restarted.
On restart, got a warning that the screen resolution was in "Reduced Mode", and opted to configure my monitor manually as it was not in the list. Let ubuntu boot up.
Still had only 800x600 max option available.
Restarted again, to try and set resolution again. This time got no warning regarding resolution and as ubuntu booted I had 1280x1024!!

Damn, you guys are good!

Lots of love and thanks,
Susi.

PS. Thanks to Ellgor too.

---

### Post by bobnutfield on 2008-08-03
Congratulations!  Nice when it works.

---

