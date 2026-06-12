---
title: "Ubuntu Installation Won't Load Past Location Page"
date: 2016-03-09
forum: New to Ubuntu
---

### Post by Headless_Horseman on 2016-03-09
UPDATE: It turns out there is something wrong with the location page  specifically. My computer ended up shutting off out of no where so I  went back through the install process and it's doing the same thing but  specifically on the location page everytime.

So I was in the middle of installing Ubuntu and everything was going fine until I hit the location page.
I clicked my location and hit continue and now for the past 40 minutes it's been sitting with my cursor loading but nothing happening. 
I looked it up and most people said just click back and then continue, but I can't because the back button was grayed out.
Suddenly though, after about 30 minutes, it magically wasn't grayed out anymore, but now everytime I click it, nothing happens. It shows that it's being clicked but I just sit on the same page.
I'm a little scared to force my computer to shutdown because with my luck, that'll probably end up corrupting my bootable USB somehow. Anyone have any other ideas on how to fix this?

EDIT: I thought it might be useful to include that I'm installing 15.10

---

### Post by Headless_Horseman on 2016-03-09
Anyone there? I'm still looking for an answer. My computer has just been sitting on the location page.

---

### Post by Headless_Horseman on 2016-03-09
UPDATE: It turns out there is something wrong with the location page specifically. My computer ended up shutting off out of no where so I went back through the install process and it's doing the same thing but specifically on the location page everytime.

---

### Post by yancek on 2016-03-09
It might be a bad download of the Ubuntu iso file.  Did you do an md5 checksum on the iso after download?  See the link below for info on how to check it.

 -

---

### Post by sammiev on 2016-03-09
Here's a link for [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM").

---

### Post by Headless_Horseman on 2016-03-09
Hmmmm... that doesn't seem to be it. The MD5 checksums match. I'm still gonna redownload and report back if there are any problems.

---

### Post by Headless_Horseman on 2016-03-10
I'm back. Still not working. It got stuck on the location screen again and I did verify that the new ISO had the correct MD5 checksum.

---

### Post by yancek on 2016-03-10
Sorry about the 'missing link' above.  Since that matches, what software did you use to put Ubuntu on the flash drive?  Can you post some information on your hardware?  Is this an older computer or an especially new computer?

---

### Post by grahammechanical on 2016-03-10
To reduce installation time the install process continues while we are providing the needed information. My guess is that the installation is stopping where it is not because of a problem with setting the location but because of a failure to provide correct information earlier on in the process and the installer has only just caught up with it.

Regards.

---

### Post by Headless_Horseman on 2016-03-11
> **yancek said:**
> Sorry about the 'missing link' above.  Since that matches, what software did you use to put Ubuntu on the flash drive?  Can you post some information on your hardware?  Is this an older computer or an especially new computer?

I used Universal-USB and Rufus to put it onto the flash drive. I tried to different kinds to see if one would work. As for hardware, the computer is pretty new. Only bought 3 months ago.

---

### Post by mastablasta on 2016-03-11
2 install options 

boot - install
boot - live OS - then install

which one are you using?

alternative install option - use mini ISO - install in text mode, then use apt-get install command to install ubuntu-desktop package

---

### Post by Headless_Horseman on 2016-03-11
> **mastablasta said:**
> 2 install options 

boot - install
boot - live OS - then install

which one are you using?

alternative install option - use mini ISO - install in text mode, then use apt-get install command to install ubuntu-desktop package

I've tried both boot - install and boot - live OS - install.
Same thing happens. Just stops on the location screen. Is there a way I can set the location on the Live OS before installing?

---

### Post by fantab on 2016-03-11
Is Ubuntu the only OS on the computer or is there more? 
Have you checked the BIOS/UEFI for any location specific settings?
Have you tried DVD as install medium? 

Can you LiveBoot Ubuntu? I mean can you "try Ubuntu" from LiveUSB?
I have experienced that *buntu installs go smoother if you install from LiveDesktop with internet access... perhaps if you setup your location in Livedesktop.

---

### Post by Headless_Horseman on 2016-03-11
> **fantab said:**
> Is Ubuntu the only OS on the computer or is there more? 
Have you checked the BIOS/UEFI for any location specific settings?
Have you tried DVD as install medium? 

Can you LiveBoot Ubuntu? I mean can you "try Ubuntu" from LiveUSB?
I have experienced that *buntu installs go smoother if you install from LiveDesktop with internet access... perhaps if you setup your location in Livedesktop.

Ubuntu isn't the only OS. I also have Windows.
I haven't, because I don't know how to.
I don't have DVDs with enough space, nor can I buy them at the moment.
I tried livebooting and the same thing happened.

---

### Post by yancek on 2016-03-11
> Ubuntu isn't the only OS. I also have Windows.

Any particular reason why you didn't mention that earlier?  It makes a major difference if you are installing to an empty drive or not. 

First off, which version of windows are you using?
Was it pre-installed on the machine or did you install it?
You enter the BIOS by re-booting and watching the screen on boot.  You should see a message, usually at the very bottom of the screen on the first screen you see telling which key to hit "to enter setup".  Take a look around.  You should have various settings including UEFI if you have it.  If you have windows 8 or newer you undoubtedly have a UEFI install.  You'll have to check if that's available in your BIOS.

Windows installs will generally take up the entire disk.  Do you have any unallocated space available outside your windows partitions?  If you select the Try Ubuntu option and boot to the Desktop, click on the Ubuntu logo in the extreme upper left of the Desktop.  There is a search box.  Type in the work terminal and you should see an icon labelled terminal, click on it and enter this command and post the output here:

```
sudo fdisk -l
```

That's a Lower Case Letter L in the command.  This will give info on drives/partitions.

---

### Post by fantab on 2016-03-11
Along with *sudo fdisk -l* also post the output of:
```
sudo parted -l
```

Also try burning the ubuntu.iso to another USB drive, just to rule out a faulty USB device.

---

