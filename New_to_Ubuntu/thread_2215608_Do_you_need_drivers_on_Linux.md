---
title: "Do you need drivers on Linux?"
date: 2014-04-07
forum: New to Ubuntu
---

### Post by Tar_Ni on 2014-04-07
Hi,

After a fresh install of Ubuntu, everything already work ''out-of-the box''. I mean one does have sound, audio, wireless ect Do you really need to add proprietary drivers on Ubuntu? I see that I have an Nvidia graphic driver available but is it really worth it to bother with drivers on Linux?

I am not a gamer, I only play some flash games on facebook on a laptop..

I should want to hear your opinions.

---

### Post by carl4926 on 2014-04-07
Most drivers, as you have found just work. They are part of the kernel.

Proprietary nvidia driver will improve overall performance in most cases.

---

### Post by meistersreign on 2014-04-07
As carl4926 mentioned, in most circumstances everything will work fine without proprietary software. As you have said you don't really do a lot of gaming, so even the Nvidia proprietary drivers aren't needed. As they say, if it's not broke don't fix it. :)

---

### Post by 23dornot23d on 2014-04-07
They are not really needed - unless you have specific applications that will not run without them.

They can speed things up frame rates for things like doing 3d and games ......

Flash works ok as long as the flashplugin-installer is loaded usually ........

in a terminal these commands will ensure it is installed ..... 

[B]sudo apt-get update
sudo apt-get install flashplugin-installer[/B]

Then try out whatever it is you use .......

---

### Post by whitesmith on 2014-04-07
Drivers -- in Linux they are generally called modules -- are built into the Linux kernel. This can sometimes be a mixed blessing. For example, if you want to add new hardware to your Linux system for which the necessary module isn't in the kernel, you may have to temporarily forgo installing that equipment or obtain the required module, incorporate it into the kernel code yourfself and recompile -- something beyond the abilities of most users. On the other hand, support for most popular hardware is already part of Linux so installation of hardware is generally easier. As regards Nvidia I would go with their proprietary driver for the reason noted by **carl4926**. Regards.

---

### Post by SeijiSensei on 2014-04-07
Support for audio over HDMI is usually better with proprietary drivers, too.

---

### Post by Tar_Ni on 2014-04-07
Thanks guys. Very helpful.


Then I will stay with the drivers that are part of the kernel, since all already works well for me. The flash player plug-in shall do for watching streamings online.


Have a nice day!

---

### Post by m-dw on 2014-04-07
> **meistersreign said:**
> As carl4926 mentioned, in most circumstances everything will work fine without proprietary software. As you have said you don't really do a lot of gaming, so even the Nvidia proprietary drivers aren't needed. As they say, if it's not broke don't fix it. :)

In general though, if you have an NVidia card it WILL work better (faster) in both 2D and 3D with the proprietary driver installed, and you will also probably get better resolutions.  Unity will look prettier your experience will generally be better BUT....

It will also mess up the nice Ubuntu splash screen you get while the system is booting and the console text (outside the GUI) will be big and ugly.  This can be fixed if it causes you distress however.  I found the answer in the General Help forum.

---

### Post by mastablasta on 2014-04-07
sometimes proprietary drivers are needed for better power saving features and such. especially on laptops this can be important.

---

