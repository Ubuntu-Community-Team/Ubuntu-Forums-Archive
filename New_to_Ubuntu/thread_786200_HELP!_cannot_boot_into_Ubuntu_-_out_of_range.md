---
title: "HELP! cannot boot into Ubuntu - out of range"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Vegadark on 2008-05-07
Ok, so in trying to get the video card working at full resolution, I installed a driver using a utility from synaptic. Now when I boot the PC, I get "1280x1024 60Hz Out of Range" warning from my screen. How do I fix this. I have gotten to the recovery thing at startup, but I cannot get into Ubuntu.

---

### Post by dtrot55 on 2008-05-07
does your monitor or vcard not support that resolution...if your monitor doenst do you have one around that does...and vice versa with your vcard...if not...guess re-install and start over

---

### Post by Vegadark on 2008-05-07
Really, thats the only option? No way to change anything back to the default?

---

### Post by ablinkin on 2008-05-07
can you access the command line?

---

### Post by Vegadark on 2008-05-07
yes, i can, but don't know what to do once there.

---

### Post by ablinkin on 2008-05-07
try this from the command line: (if your running gnome)

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

---

### Post by ubuntu-freak on 2008-05-07
> **Vegadark said:**
> Really, thats the only option? No way to change anything back to the default?

 
What packages did you install? Envy related? If so, execute this command in recovery mode:
 
**envyng --uninstall-all** 
 
Then reboot. 
 
How did you try and set your resolution? You can try Envy again, but set your resolution with:
 
**gksudo displayconfig-gtk** 
 
Hope that helps,
 
Nathan

---

### Post by Vegadark on 2008-05-07
ok, so I did that, was it supposed to return something? it just gave me another command prompt. Should I reboot and see what happens?

---

### Post by ablinkin on 2008-05-07
yeh, reboot ....it will not return anything to the console

---

### Post by Vegadark on 2008-05-07
> **reassuringlyoffensive said:**
> What packages did you install? Envy related? If so, execute this command in recovery mode:
 
**envyng --uninstall-all** 
 
Then reboot. 
 
How did you try and set your resolution? You can try Envy again, but set your resolution with:
 
**gksudo displayconfig-gtk** 
 
Hope that helps,
 
Nathan

yes it was envy. i already did what the previous poster listed, but did not do anything beyond that so far.

---

### Post by Vegadark on 2008-05-07
doing the envy uninstall now. we'll see how that goes. If I get back to where I was before installing it, i'll start a new thread about the screen resolution.

---

### Post by ubuntu-freak on 2008-05-07
> **Vegadark said:**
> yes it was envy. i already did what the previous poster listed, but did not do anything beyond that so far.

 
No comment.

---

### Post by Vegadark on 2008-05-08
ok, so i uninstalled envyng, now the screen goes off saying no signal instead of out of range. If I have to reinstall the complete thing again, can I do it with out partitiioning the drive again?

---

### Post by Sef on 2008-05-08
> ok, so i uninstalled envyng, now the screen goes off saying no signal instead of out of range. If I have to reinstall the complete thing again, can I do it with out partitiioning the drive again?

Yes, you can.  What you would have to do for the reinstall is the following:

1) **Back up** all your data.

2) At the partitioner, go into Manual Partition

3) Delete the the root partition and set it up again.

4) It will reformat your root partition and your swap. 

5) If you are not sure how to do that, leave a message here, and I will go into more detail.

---

### Post by ubuntu-freak on 2008-05-08
> **Vegadark said:**
> ok, so i uninstalled envyng, now the screen goes off saying no signal instead of out of range. If I have to reinstall the complete thing again, can I do it with out partitiioning the drive again?

 
Yeah, can't improve on what Sef said.
 
Completely power-down everything and try to boot again though, just seems strange that it's not booting into safe graphics mode.
 
Nathan

---

### Post by Vegadark on 2008-05-08
ok, so i am reinstalling everything fresh again. 3rd time since my first time sunday (yay!)

at least i expected a steep learning curve going into this.

---

### Post by CanadianLinux on 2008-05-08
I think its just the resolution as said from the start, Ive had this problem myself when I first installed Linux. Just do
 
sudo vim /etc/X11/xorg.conf 

Then go to the monitor section and delete all the high resolutions and keep the low basic ones down to 1024X768 save by pressing 

:exit 

Then go back to alt-ctrl-F7 and restart X by presssing alt-ctrl-bksp.

This works for me

---

### Post by ubuntu-freak on 2008-05-08
> **CanadianLinux said:**
> I think its just the resolution as said from the start, Ive had this problem myself when I first installed Linux. Just do
 
sudo vim /etc/X11/xorg.conf 

Then go to the monitor section and delete all the high resolutions and keep the low basic ones down to 1024X768 save by pressing 

:exit 

Then go back to alt-ctrl-F7 and restart X by presssing alt-ctrl-bksp.

This works for me

 
A fresh install of Hardy won't show graphics driver info or resolutions in /etc/X11/xorg.conf, as far as I know. Also, dpkg-reconfigure etc doesn't reconfigure the graphics driver/resolution anymore, but in desktop mode you can use "gksudo displayconfig-gtk" (without "-gtk" in Kubuntu). 
 
Nathan

---

### Post by CanadianLinux on 2008-05-08
> **reassuringlyoffensive said:**
> A fresh install of Hardy won't show graphics driver info or resolutions in /etc/X11/xorg.conf, as far as I know. Also, dpkg-reconfigure etc doesn't reconfigure the graphics driver/resolution anymore, but in desktop mode you can use "gksudo displayconfig-gtk" (without "-gtk" in Kubuntu). 
 
Nathan

Yes you are right, when you do the dpkg-reconfigure command you do not get video options. But there is still an xorg.conf file that you can edit manually. And sometimes certain resoltuions dont work out of the box.

---

### Post by ubuntu-freak on 2008-05-08
> **CanadianLinux said:**
> Yes you are right, when you do the dpkg-reconfigure command you do not get video options. But there is still an xorg.conf file that you can edit manually. And sometimes certain resoltuions dont work out of the box.

 
Yeah, I know of some experienced (and anti-auto config) users who practically write there own xorg.conf file. 
 
Nathan

---

