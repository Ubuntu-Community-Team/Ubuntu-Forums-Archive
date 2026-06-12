---
title: "Cannot get to GRUB"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2012-03-18
I'm in LiveCD mode, now as the BIOS is running, but the GRUB isn't. 

This box has both Oneiric 11.04 and Windows 7. Originally the Windows 7 was installed and then Ubuntu.

On an ordinary boot, I use XFCE, but as I'm not getting further than the BIOS showing the USB devices, which is the last thing it does before handing off to the hard drive's MBR and bootloader.

The monitor screen shows a flashing rectangular block, about one inch lower than where it would appear, just before the handoff from BIOS to GRUB.

HEHHHHHHHHHeeeeeeeeeellllllllllpppppppppp!

---

### Post by NikTh on 2012-03-18
Hi , 
i think the easiest way to restore grub is to do it with boot-repair. 
From liveCD do the following . 
```
sudo add-apt-repository ppa:yannubuntu/boot-repair 
sudo apt-get update
sudo apt-get install -y boot-repair
```and run the recommended way .

---

### Post by Mark_in_Hollywood on 2012-03-18
I have "solved" this problem by removing what is called a jump drive, flash drive, USB memory stick or thumb drive from the USB port.

I doubt this is a "solution", but as I've have Oneiric and Win7 back, I don't want to mess with what is working. "If it ain't broke, don't fix it", must be the applied rule here.

Last thought: I have 4 usb thumb drives, 256 meg, 1 gig and 8 gig. The offending drive was 4 gig. Nothing had any truecrypt or other OTF security on it. Go figure.

I'm sorry if you came here looking for a solution.

---

### Post by Mark_in_Hollywood on 2012-03-18
> **NikTh said:**
> Hi , 
i think the easiest way to restore grub is to do it with boot-repair. 
From liveC do the following . 
```
sudo add-apt-repository ppa:yannubuntu/boot-repair 
sudo apt-get update
sudo apt-get install -y boot-repair
``` 
and run the recommended way .

YES, but I CAN NOT get to a command prompt, as there is no handoff from the BIOS to GRUB.

---

