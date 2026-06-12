---
title: "Another: error: no such partition grub rescue&gt;"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by Mr Smiler on 2012-06-25
Hi, total noob here.

I have this error
error: no such partition grub rescue>

I have run Boot-Repair & have a diagnostic url:
[http://paste.ubuntu.com/1058941](http://paste.ubuntu.com/1058941)


I tired a repair:
[http://paste.ubuntu.com/1058971](http://paste.ubuntu.com/1058971)


I also know that I have an issue with the NVIDIA GPU.


Any help would be appreciated.
Thanks in advance

---

### Post by Cheesemill on 2012-06-25
Do you know why FlexNet is on your system?
It could be this causing the problem.

[http://en.wikipedia.org/wiki/FlexNet_Publisher#Issues_with_Bootloaders](http://en.wikipedia.org/wiki/FlexNet_Publisher#Issues_with_Bootloaders)

---

### Post by NikTh on 2012-06-25
> **Cheesemill said:**
> Do you know why FlexNet is on your system?
It could be this causing the problem.

[http://en.wikipedia.org/wiki/FlexNet_Publisher#Issues_with_Bootloaders](http://en.wikipedia.org/wiki/FlexNet_Publisher#Issues_with_Bootloaders)

Sorry but were how did you configure that he has FlexNet software installed ? 
I cannot locate it from boot info script..
Thanks .

---

### Post by Cheesemill on 2012-06-25
It mentions it at the bottom of the OP's second link.
```
grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
grub-setup /dev/sda: exit code of grub-setup /dev/sda:0
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store
```

It is only a warning, not an error so it might not be the problem, just something worth considering.

---

### Post by NikTh on 2012-06-25
> **Cheesemill said:**
> It mentions it at the bottom of the OP's second link.
It is only a warning, not an error so it might not be the problem, just something worth considering.


Apologize for my blindness. I didn't saw it. 
Yes it is possible this software cause problems.. as i read in  your quoted wiki page. 
Thanks for info.

---

### Post by Mr Smiler on 2012-06-25
I have no idea how or why FlexNet is on there.

I installed onto a HDD that already had Windows XP on it.

Now nothing works.

How do I remove FlexNet?

Will this solve the problem?

---

### Post by drs305 on 2012-06-25
Flexnet writes to the same area of the disk as do older versions of Grub. Grub 1.99 works around this issue.

Boot Repair can fix this. Install BR from a LiveCD or running Ubuntu, selected "Advanced" and "Reset extra space".

There is a link for Boot Repair in my signature line.

---

### Post by Mr Smiler on 2012-06-25
> **drs305 said:**
> Flexnet writes to the same area of the disk as do older versions of Grub. Grub 1.99 works around this issue.

Boot Repair can fix this. Install BR from a LiveCD or running Ubuntu, selected "Advanced" and "Reset extra space".

There is a link for Boot Repair in my signature line.

I already ran BR from a CD & tried a repair, no change.

When I run the install CD, I need to hit F6 & select "nomodeset" to overcome the GPU issue.

Can I run BR from the install CD?

---

### Post by drs305 on 2012-06-25
> **Mr Smiler said:**
> I already ran BR from a CD & tried a repair, no change.

When I run the install CD, I need to hit F6 & select "nomodeset" to overcome the GPU issue.

Can I run BR from the install CD?

Yes you can. When you ran BR did you specifically try the "Flexnet" fix option. I don't know if BR will run that automatically with the recommended repair option.

*If you get Grub working*, since you had to use 'nomodeset' with the CD you may need to use it on a normal boot as well until you can install the video drivers. If you are able to fix Grub, to temporarily add the nomodeset option to the Grub menuentry:
Press 'e' to edit the menu.
Cursor to the end of the 'linux' line.
Remove 'quiet splash vt.handoff....' and add *nomodeset*
F10 or ctrl-x to boot.
Once booted, add your video driver via Additional Drivers.

---

### Post by YannBuntu on 2012-06-26
Hi
The "Recommended repair" does not use the "FlexNet" option by default. So you need to tick it in the "Advanced options" of Boot-Repair.

---

### Post by Mr Smiler on 2012-06-26
Thanks for your help chaps, but I think I'm seriously out of my depth with this.

I performed a fresh install, removing the original HDD contents & installing 12.04 LTS to a single partition.

I managed to install an NVIDIA driver so the system boots with a legible screen.

Now all I need to do is get the WiFi working (hopefully).

This is very different to the PC install I tried about 18 months ago, that worked perfectly first time.

I guess the hardware on the Dell Inspiron laptop is a bit more tricky.

Again, thanks for taking the time to help me on this & please look at my other thread on the WiFi if you can help.

:)

---

