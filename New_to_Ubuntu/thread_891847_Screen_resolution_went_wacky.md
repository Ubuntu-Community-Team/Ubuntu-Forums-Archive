---
title: "Screen resolution went wacky"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by lavadisco on 2008-08-16
I had everything seemingly working perfectly in Ubuntu, then I went and followed these instructions for getting wineasio to work:

[http://ferama.netsons.org/wp/index.php/2007/11/14/guitar-rig-on-ubuntu-gutsy-howto/](http://ferama.netsons.org/wp/index.php/2007/11/14/guitar-rig-on-ubuntu-gutsy-howto/)

I restarted after the last step, and suddenly Ubuntu tells me it can't detect my display and defaults to a screen resolution of 800 x 600. I even went into the manual configuration and changed it to my previous resolution (1920 x 1200), but it didn't work. My card is an NVIDIA GeForce Go 7900 GS. 

Any idea what I can do to fix this?

Thanks!

---

### Post by Sycron on 2008-08-16
It seems that you've screwed up the **/etc/X11/xorg.con**f file... but i'm not sure

---

### Post by overdrank on 2008-08-16
> **lavadisco said:**
> I had everything seemingly working perfectly in Ubuntu, then I went and followed these instructions for getting wineasio to work:

[http://ferama.netsons.org/wp/index.php/2007/11/14/guitar-rig-on-ubuntu-gutsy-howto/](http://ferama.netsons.org/wp/index.php/2007/11/14/guitar-rig-on-ubuntu-gutsy-howto/)

I restarted after the last step, and suddenly Ubuntu tells me it can't detect my display and defaults to a screen resolution of 800 x 600. I even went into the manual configuration and changed it to my previous resolution (1920 x 1200), but it didn't work. My card is an NVIDIA GeForce Go 7900 GS. 

Any idea what I can do to fix this?

Thanks!

Hi and I did not read all of the "how to" but I did catch the real time kernel and that is probably the issue with the nvidia driver as you had it setup with a different one.How did you install the nvidia driver as you may need to reinstall.

---

### Post by WinterMadness on 2008-08-16
> **Sycron said:**
> It seems that you've screwed up the **/etc/X11/xorg.con**f file... but i'm not sure

i just had this problem and thats exactly what did it.

within the SAME folder xorg.conf is, there will be a backup file named xorg.conf.(random numbers)

you want to copy the contents in the backup and put it in the normal xorg.conf and save it, and restart. it immediately fixed the problem for me

---

### Post by lavadisco on 2008-08-16
> **WinterMadness said:**
> i just had this problem and thats exactly what did it.

within the SAME folder xorg.conf is, there will be a backup file named xorg.conf.(random numbers)

you want to copy the contents in the backup and put it in the normal xorg.conf and save it, and restart. it immediately fixed the problem for me

Gave this a try, but it says I don't have permission to save the file. Do I need to log in as root or something? And if so, how do I do that?

EDIT: Nevermind, I figured it out! Restarting now...

---

### Post by lavadisco on 2008-08-16
Well, no luck. Anything else I might try?

Just downloaded the NVIDIA Linux x86 drivers from here:

[http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html)

And have followed the instructions all the way up to using the utility to change the x-server config file. When I go to Administration --> NVIDIA X Server Settings it tells me:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

---

### Post by WinterMadness on 2008-08-16
> **lavadisco said:**
> Gave this a try, but it says I don't have permission to save the file. Do I need to log in as root or something? And if so, how do I do that?

EDIT: Nevermind, I figured it out! Restarting now...

let me know if it worked for you. I almost did a reinstall thinking i messed up big time haha. luckily the terminal program let me know of the backup file when i was throwing commands at it.

Good luck dude.

---

