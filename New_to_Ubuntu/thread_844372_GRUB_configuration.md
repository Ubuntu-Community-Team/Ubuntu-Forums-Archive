---
title: "GRUB configuration"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by marlin9800 on 2008-06-29
Good afternoon all,

I have (3) hdds in my box; (1) Vista, (1) Ubuntu, and I have just added a 3rd hdd and installed Slack. After some research I decided to keep the GRUB instead of using slack's lilo. Shouldn't be a big deal, but I am running into a small problem. When I edit the menu.lst file to add the slack install to it, I can't figure out what the (hdx,x) should be. I know that my M$ is (0,0) and my Ubuntu is (1,0) so I assumed that the slack would be (2,0), but when I try to edit with the instructions found here; [http://ubuntuforums.org/showthread.php?t=393379](http://ubuntuforums.org/showthread.php?t=393379) (post #4) I get an error message about not being able to load partition (or something to that effect). What do those numbers mean? I thought maybe the first number represented the hdd and the second was for multiple partitions, am I wrong?

Also I have tried (3,0), (4,0), (2,1)...

Thank You

---

### Post by The Cog on 2008-06-29
The first number is the disk number - 0 would be hda etc. The second number is the partition number, starting at 0 so that hda1 would be 0,0 and hdc5 would be 2,4.

---

### Post by phidia on 2008-06-29
Open a terminal in ubuntu and type fdisk -l *you might have to preface with sudo. That should provide you with your disks and partitions.
BTW there is a grub package for slackware if you want to use it.
I always liked installing each respective distros bootloader(grub) to the root "/" partition when I multibooted and then just chainloaded each distro from the grub installed to the mbr.

---

### Post by kansasnoob on 2008-06-29
Check out this guide on GRUB's numbering:

[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

Actually the whole guide might be helpful:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by marlin9800 on 2008-06-29
> **phidia said:**
> Open a terminal in ubuntu and type fdisk -l *you might have to preface with sudo. That should provide you with your disks and partitions.
BTW there is a grub package for slackware if you want to use it.
I always liked installing each respective distros bootloader(grub) to the root "/" partition when I multibooted and then just chainloaded each distro from the grub installed to the mbr.

Thank you phidia, so when I do that here is what I get;

```
Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc1c5c1c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         395     3172806   82  Linux swap / Solaris
/dev/sdc2   *         396        9964    76862992+  83  Linux


```

and according to The Cog, that should read as (hd2,1) correct? Because that is not working for me.

---

### Post by phoenix_abhi on 2008-06-29
U have Vista in a HD, using Easy BCD is good solution.

---

### Post by caljohnsmith on 2008-06-29
> **marlin9800 said:**
> Good afternoon all,

I have (3) hdds in my box; (1) Vista, (1) Ubuntu, and I have just added a 3rd hdd and installed Slack. After some research I decided to keep the GRUB instead of using slack's lilo. Shouldn't be a big deal, but I am running into a small problem. When I edit the menu.lst file to add the slack install to it, I can't figure out what the (hdx,x) should be. I know that my M$ is (0,0) and my Ubuntu is (1,0) so I assumed that the slack would be (2,0), but when I try to edit with the instructions found here; [http://ubuntuforums.org/showthread.php?t=393379](http://ubuntuforums.org/showthread.php?t=393379) (post #4) I get an error message about not being able to load partition (or something to that effect). What do those numbers mean? I thought maybe the first number represented the hdd and the second was for multiple partitions, am I wrong?

Also I have tried (3,0), (4,0), (2,1)...

Thank You
In Grub's world, although it can be confusing, unfortunately all numbering starts with 0:
```
(hd0,0) = 1st HD, 1st partition
(hd0,1) = 1st HD, 2nd partition
(hd1,0) = 2nd HD, 1st partition
...
```
So your 3rd HD should be (hd2,0) as you surmised. To check which drives grub sees, probably the easiest way is to go to the Grub CLI (either at startup or by doing "sudo grub" in a terminal), and then type:
```
grub> null (hd
```
and then hit TAB. "null" could actually be any bogus or real command, but the point is to take advantage of the TAB-completion feature in Grub, so you should get a list of your drives by doing the above.

If you do get (hd2,0) as a valid drive, then the syntax you are using in your menu.lst to load Slackware is most likely incorrect. If you can, one of the easiest ways to add additional distros to your menu.lst is to install each distro with its own Grub/Lilo into the boot record of the partition of the distro in question. Thus when you install Slackware to your third HD, if there are no other partitions on that drive, have Slackware install Lilo into the MBR of the drive or (hd2), and not (hd2,x) which is the syntax for installing the bootloader into a specific partition on the 3rd HD. That way you can simply use the "chainloader" syntax in your Ubuntu's menu.lst to then boot your 3rd HD:
```
title		Slackware
root		(hd2,0)
makeactive
chainloader	+1
```
That's all it should take to load Slackware.

---

### Post by marlin9800 on 2008-06-29
> **caljohnsmith said:**
> In Grub's world, although it can be confusing, unfortunately all numbering starts with 0:
```
(hd0,0) = 1st HD, 1st partition
(hd(0,1) = 1st HD, 2nd partition
(hd(1,0) = 2nd HD, 1st partition
...
```
So your 3rd HD should be (hd2,0) as you surmised. To check which drives grub sees, probably the easiest way is to go to the Grub CLI (either at startup or by doing "sudo grub" in a terminal), and then type:
```
grub> null (hd
```
and then hit TAB. "null" could actually be any bogus or real command, but the point is to take advantage of the TAB-completion feature in Grub, so you should get a list of your drives by doing the above.

If you do get (hd2,0) as a valid drive, then the syntax you are using in your menu.lst to load Slackware is most likely incorrect. If you can, one of the easiest ways to add additional distros to your menu.lst is to install each distro with its own Grub/Lilo into the boot record of the partition of the distro in question. Thus when you install Slackware to your third HD, if there are no other partitions on that drive, have Slackware install Lilo into the MBR of the drive or (hd2), and not (hd2,x) which is the syntax for installing the bootloader into a specific partition on the 3rd HD. That way you can simply use the "chainloader" syntax in your Ubuntu's menu.lst to then boot your 3rd HD:
```
title		Slackware
root		(hd2,0)
makeactive
chainloader	+1
```
That's all it should take to load Slackware.

Ok, Thank you caljohnsmith, all of that helped a great deal. I was able to figure out that I should be using (hd2,1), [0 is the swap partition] but this did not fix the issuse. While following the instructions here ([http://ubuntuforums.org/showthread.php?t=393379](http://ubuntuforums.org/showthread.php?t=393379)) I did so blindly because I have learned that if I try to change or deviate form the steps in anyway, it doesn't work. Had I paid attention this time though I would have noticed that all that tab work was just filling in text for me, not some special step (just like my cisco ios!) and the problem is it just wouldn't read the directory or files, even though I can mount the hdd in ubuntu and view them directly. 

My whole reason for doing this is because I wanted to make the switch from ubuntu to slack, but heard it was a pain to install and I wanted to test drive the install before formating my ubuntu (which I love). Ubuntu got me into linux and is a great distro, but my goal was to learn linux, not ubuntu. So I think now I am going to remove 3rd hdd and just go for the gold and format the ubuntu drive. Thanks again

---

