---
title: "Existing installation, move drive to new machine?"
date: 2019-09-17
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2019-09-17
Can I move an ssd with Ubuntu already installed and fully configured to a new machine with any trouble? Or will it require a full fresh installation? I know Windows chokes when this is done, never questioned about Linux though. If this can be done it solves a great deal of problems for me with minimal downtime.

---

### Post by Autodave on 2019-09-17
The only thing that I would be concerned with is drivers for wifi, video, and sound cards.  You may want to remove them first.

I have an HD that has been in probably 20+ machines with no issues whatsoever.  I plop it in and it has always worked.  The first boot on it normally takes 10-20 seconds longer than subsequent boots (as it sees new hardware and configures it), but after that I have had no issues at all.

---

### Post by SeijiSensei on 2019-09-17
I've moved drives a number of times as well with no issues.  Linux is remarkably robust in this way, but then it isn't keeping track of licenses like Microsoft does.  When you first start Windows, it creates a license key based on features of the hardware and stores that on MS's servers.  When you move the drive, the key doesn't match.

---

### Post by Tadaen_Sylvermane on 2019-09-17
As far as drivers I have nothing special. No custom graphics drivers, no wifi, no special sound. It's just whatever comes with Ubuntu. The current machine is an AMD based system, it would change to Intel. I'm guessing it would just load the proper stuff on as needed?

Current machine is an AMD Kabini APU. I don't know if the install blacklisted or whatever on video drivers. Not even sure how to check that.

---

### Post by SeijiSensei on 2019-09-17
Just pop it in and see if it works. Empiricism is the best approach for a lot of computer issues.  You can't damage anything.

---

### Post by Autodave on 2019-09-17
I have never had it *not* work.  AMD to Intel and back to AMD.  Whatever.  Like I stated before, it is a drive that I have had for years.  I kept it just for checking machines out.  Actually, come to think of it, I have 2 of them: one IDE and one SATA.

---

### Post by rbmorse on 2019-09-17
Unlike Windows, Linux keeps drivers for most devices in the kernel itself, and does device detection at every startup, so moving the system drive from box to box is largely business as usual at the next startup. 

 The only exceptions are drivers for devices with a proprietary license (some video, some ethernet, some wi-fi, some bluetooth and printers, scanners and other I/O devices) because they cannot be included in the kernel for legal reasons.

---

### Post by oldfred on 2019-09-17
If UEFI system, new system will not have the UEFI boot entry. 
You should be able to boot a fallback or hard drive boot entry then use efibootmgr to create new UEFI boot entry for Ubuntu. 
Or you can use Boot-Repair from an Ubuntu live installer and totally reinstall grub which uses efibootmgr to create the "ubuntu" entry in your new systems UEFI  one time boot menu, often f10 or f12.

---

### Post by Tadaen_Sylvermane on 2019-09-17
Thank you all for answers. I will report back when the chip shows up to get the other machine running. I'll drop it in and report what happens, either way. Everything you have all said tells me I should have zero problems. But I will post back when I find out for sure. New i5 chip will be here on Saturday roughly, although I likely won't get to messing with it till Monday or so.

---

### Post by Tadaen_Sylvermane on 2019-09-20
We have success so far. It booted with no difficulty. I had to chase down how to fix hdmi sound but once done it works great. Forced the issue with a custom default.pa in /home/"$ONLYUSER"/.config/pulse/default.pa. Runs like a top. The Ripjaw ram sticks I had in the old machine didn't fit, heat spreader too tall. Changed them to my desktop and taking the regular sticks from there into the server / htpc. Very pleased thus far. I do appreciate the replies. It went perfect.

---

### Post by #&amp;thj^% on 2019-09-20
That was kind of you to add your solution. :)
Goes to show, effort pays dividends. :K:

---

### Post by Tadaen_Sylvermane on 2019-09-20
Figured I should share what I had to do to get the Intel HDMI sound working. Took quite a bit of googling for me to find this. Created a patch file. This is Ubuntu 16.04. Assuming it would work on future releases as well.

[https://unix.stackexchange.com/questions/293399/how-to-set-hdmi-sound-output-as-default-on-ubuntu-16-04](https://unix.stackexchange.com/questions/293399/how-to-set-hdmi-sound-output-as-default-on-ubuntu-16-04)

```
--- /etc/pulse/default.pa    2018-05-02 02:40:35.000000000 -0700
+++ /home/kodimain/.config/pulse/default.pa    2019-09-20 13:06:10.429004455 -0700
@@ -30,7 +30,7 @@
 
 ### Automatically restore the volume of streams and devices
 load-module module-device-restore
-load-module module-stream-restore
+load-module module-stream-restore restore_device=false
 load-module module-card-restore
 
 ### Automatically augment property information from .desktop files
@@ -38,7 +38,7 @@
 load-module module-augment-properties
 
 ### Should be after module-*-restore but before module-*-detect
-load-module module-switch-on-port-available
+#load-module module-switch-on-port-available
 
 ### Load audio drivers statically
 ### (it's probably better to not load these drivers manually, but instead
@@ -162,3 +162,5 @@
 ### Make some devices default
 #set-default-sink output
 #set-default-source input
+
+set-card-profile 0 output:hdmi-stereo
```

---

