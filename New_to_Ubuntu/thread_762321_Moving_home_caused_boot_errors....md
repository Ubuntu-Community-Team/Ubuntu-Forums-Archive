---
title: "Moving /home caused boot errors..."
date: 2008-04-22
forum: New to Ubuntu
---

### Post by stevek123 on 2008-04-22
Total noob in ubuntu (7.10). i386-1000Mhz w/ 3x128MB ram, 13G HD, OLD hardware...A programmer friend, well versed in terminal (but not in gnome/gui), came over and helped me install some hardware including an additional 60G HD. We (he) moved my home folder onto the new drive - messed up a number of things as a result. Upon boot-up the system does not recog gnome and doesnt open the f7 gui. It will run in f1/terminal just fine (does me NO good - I'm clueless). I figured out that if I run gksudo nautilus in failsafe terminal and click on the new HD - it THEN sees it as the /home folder. Then i need to Ctrl-Alt-Bkspc and relog into Gnome to get it to open - sometimes need to log in twice... but it works. It looks like a number of gui/gnome files are in the /Home folder and I suspect that if I move them back to the OS HD it will run normally (=problems recognizing the new slave HD on boot-up). Then all I really need to do is move the sub-folders I want to use/fill/network back onto the slave HD and I will be fine. Problem is I have no clue how to do this without causing more problems. Seems like it should be an easy fix...help?

---

### Post by sdennie on 2008-04-22
It sounds like your new /home directory isn't being mounted at boot time.  If you could post the contents of /etc/fstab, it should be possible to make your /home disk automatically show up when you boot your computer.

---

### Post by stevek123 on 2008-04-22
> **vor said:**
> It sounds like your new /home directory isn't being mounted at boot time.  If you could post the contents of /etc/fstab, it should be possible to make your /home disk automatically show up when you boot your computer.

Can you tell from my orig post I still think in windows terms???:(
 I think this is the log you asked to see... I've no clue what it says....(Thanks for kwik reply)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=28f5669f-a96e-4f3d-a619-5efabcf43b61 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=5e41d5d3-b315-4403-887c-ff6750f376f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1        /home/steve  auto    rw,user,noauto,exec 0       0

---

### Post by sdennie on 2008-04-22
> **stevek123 said:**
> 
/dev/sdb1        /home/steve  auto    rw,user,noauto,exec 0       0

I think if you change "noauto" to "auto" on that line it will mount /home/steve when you boot.  However, I'm not sure that will do exactly what you want.  Can you post the output /proc/mounts once you have /home working?  That should help narrow down the correct options.

---

### Post by stevek123 on 2008-04-22
Hey-Thanks. I changed the /etc/fstab sdb1 line to read 'auto' and restarted the computer. It booted right up. I figured this was a simple fix :)

---

### Post by Oldsoldier2003 on 2008-04-22
> **stevek123 said:**
> Hey-Thanks. I changed the /etc/fstab sdb1 line to read 'auto' and restarted the computer. It booted right up. I figured this was a simple fix :)

another issue is you are mounting it as /home/steve which may or may not cause additional problems in the future. you should be mounting it as /home in the fstab

---

### Post by stevek123 on 2008-04-22
> **Oldsoldier2003 said:**
> another issue is you are mounting it as /home/steve which may or may not cause additional problems in the future. you should be mounting it as /home in the fstab

When I first did this I created a backup folder /home/old_home_steve  that I kept on the orig HD to make sure i didnt lose it. I then used /home/steve to specify that path and make sure new stuff went to where there was more space and stay out of the basic OS. If this can cause future issues, I am unaware of it = total noob at this. Issues how??? (Plz be gentle-I get lost in ubuntu language easily...yet ;) ). Easily fixed? rm the old... folder and rename the path to /home?

---

