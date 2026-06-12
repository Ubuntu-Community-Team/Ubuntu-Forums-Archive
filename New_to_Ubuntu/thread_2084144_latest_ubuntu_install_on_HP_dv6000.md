---
title: "latest ubuntu install on HP dv6000"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by mackconsult on 2012-11-14
Burned the iso to a disk and let it do a side by side install on my XP Professional HP DV6000.

The install went fine, and first boot was all good.  Then I started getting errors, so I allowed all the updates to occurr.

Now when I boot into ubuntu, the graphics are all messed up.

Not sure what to do besides doing an uninstall of ubuntu ... which I don't even now how to do.

help ..... I am a very technical savvy guy and used/programmed on linux in the past so if any one wants to give some help greatly appreciated.

HP DV 6000
128 GB SSD
AMD Durion 64 x2 Mobile
Technology TL-60
2.00 GHz 1.93 GB of RAM

---

### Post by Gone fishing on 2012-11-14
To uninstall simply delete the Linux ext4 partion which you could do from Windows or Partition editor on the live cd. Then simply reinstall using this space. To completly remove you would also use fixmbr from a Windows cd.

However the messed up graphics can probably be fixed but moe detail is needed.

---

### Post by mackconsult on 2012-11-14
Well I am interested in keeping ubuntu to play around with.  Want to build some simple ubuntu pc's for my kids.

Where should I begin .... should I boot into command line of something.

---

### Post by Bucky Ball on 2012-11-14
When you boot, do you get a list of kernels/OSs to boot? If not, hit shift after the BIOS screen and that should get you there.

Select the kernel you want to boot and hit 'e' to edit it;
Look for the line that ends in 'quiet splash' or just quiet or just splash;
Type a space and add 'nomodset';
Follow the instructions at the bottom of the screen to save changes and continue with boot.

Did that sort out the graphics issue? You will now be using the open-source default graphics driver probably, or even low-res. Go to 'Additional Drivers'. Is there anything there for graphics?

I ran Ubuntu faultlessly on my DV6000 until it died an unfortunate death (the DV6000, not Ubuntu) so there is hope ... ;)

---

