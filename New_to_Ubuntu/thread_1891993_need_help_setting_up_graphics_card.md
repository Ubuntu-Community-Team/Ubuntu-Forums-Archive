---
title: "need help setting up graphics card"
date: 2011-12-07
forum: New to Ubuntu
---

### Post by 450rOOST on 2011-12-07
ok, when I had 11.04, I was unable to get my graphics card working correctly.  I believe I am having the same problem.  

This is the message I am getting, but I don't know what to do and last time I tried to fix this myself, I had to reinstall ubuntu cause it would no longer boot.

[IMG]http://i678.photobucket.com/albums/vv143/RideRed/Screenshotat2011-12-06221554.png[/IMG]

I tried installing tuxsuperkart to no avail, no other games that I installed work either.  The icon on my launcher is orange, it will pulse between transparent and orange about 5 times then nothing happens.  any ideas?

Thanks

dell xps15 (L502x)
intel core i7-2630QM CPU @ 2.00 GHz
8gb RAM
64-bit
nvidia GeForce GT 525M

---

### Post by mastablasta on 2011-12-07
did you install the driver?

---

### Post by 450rOOST on 2011-12-07
I activated the post-release accelerated graphics card.  I tried that, and the recommended driver.  I've tried both that you see in this screenshot.

[IMG]http://i678.photobucket.com/albums/vv143/RideRed/Screenshotat2011-12-06210422.png[/IMG]

---

### Post by zero2xiii on 2011-12-07
This is simmilar to the "These drivers are installed but not in use" issue people are having.

Try in a terminal:
**sudo nvidia-xconfig**
Then reboot and see if it helps. Nvidia's drivers might not be activated.

Cherz

EDIT: Please scale down the images, or capture a window specific shot. It is unecesary to upload FULL res pics.

---

### Post by 450rOOST on 2011-12-07
yes, that sounds like the problem I am having.  I will reboot, but incase I cannot reboot like last time I did this, here what I got:

> smoker@smoker:~$ sudo nvidia-xconfig
[sudo] password for smoker: 

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

smoker@smoker:~$ 


I will scale down the screenshots, I just wanted whoever to be able to see what was written, I do not know how to take window specific screenshots yet...

---

### Post by 450rOOST on 2011-12-07
yup, sure enough, can't boot into ubuntu now, only into windows.  

time to reinstall again...:(

---

### Post by mastablasta on 2011-12-07
use a live CD and check what was written in new xorg.conf file. you could also post the file here in code tags. maybe someone get's an idea.

---

### Post by 450rOOST on 2011-12-08
> **mastablasta said:**
> use a live CD and check what was written in new xorg.conf file. you could also post the file here in code tags. maybe someone get's an idea.

time for some honesty, I don't know what your talking about, ha!

I already reinstalled.  Back up and running, I just saw that there is a dell ubuntu support sub-forum, I'm gonna take my noobness over there and see if I can get some help.

Thanks folks!

---

### Post by mastablasta on 2011-12-08
i was refering to what you posted:
> Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: **Data incomplete in file /etc/X11/xorg.conf**.
Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

 
 
something could be missing in the xorg.conf file. it's the file that provides configuraiton settings for graphics.

---

### Post by beew on 2011-12-08
> **mastablasta said:**
> i was refering to what you posted:

 
 
something could be missing in the xorg.conf file. it's the file that provides configuraiton settings for graphics.
 
No, that part is fine. It is the standard output whenever I activate a Nvidia driver the first time by running "sudo nvidia-xonfig". it just says that it has to create an updated xorg.conf to replace the old one. 

If OP cannot reboot as a result may be the driver is too old or too new  for the kernel so they don't bind,--something like that. It happened to me before. But I have to try hard to remember what happened, it is 3 am. :)

---

