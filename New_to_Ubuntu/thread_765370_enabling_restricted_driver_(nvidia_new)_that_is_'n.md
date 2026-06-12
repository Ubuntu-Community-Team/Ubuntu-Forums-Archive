---
title: "enabling restricted driver (nvidia_new) that is 'not in use' on Hardy 8.04"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by alwiap on 2008-04-24
Hi,

I just upgraded to Hardy 8.04 a few minutes ago, and I have this problem enabling my nVidia driver (I have a 7800gt), and I need it to be 'in use' so I can adjust my resolution to 1400x900 as it is at 1280x1024 right now and I can't do anything.  See my screenshot for info, does anyone know how I could enable anything?  I can't make it 'in use'.

Thanks so much!

---

### Post by macogw on 2008-04-24
After enabling it, try restarting X with ctrl+alt+backspace

---

### Post by Perfect Storm on 2008-04-24
Try restart X and see if allows it to use that module.

---

### Post by bitzbox on 2008-04-24
I've just had exactly the same problem and I solved it by installing the ***nvidia-glx-new*** package from the repos.

Regards .....

---

### Post by alwiap on 2008-04-24
> **bitzbox said:**
> I've just had exactly the same problem and I solved it by installing the ***nvidia-glx-new*** package from the repos.

Regards .....

Hi,

I didn't have to do that, but I restarted the X server (should have thought of that anyway) like my friends above suggested, and then I was able to install the 'NVIDIA accelerated graphics driver (latest cards), and after a restart it defaulted to my normal 1440x900 which I was looking for.

Thanks for your help, and hope this helps others who have the same problem :)

---

