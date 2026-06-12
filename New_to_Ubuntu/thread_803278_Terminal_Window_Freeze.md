---
title: "Terminal Window Freeze"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by wariskampar on 2008-05-22
Hello, I want to enter something in Terminal but when I open it, the Terminal Window seem to freeze(Window appear but no Menubar and seem like processing something). At first I thought this is exclusive to Terminal but when I try TOTEM, and few other program, same problem happen. I can not even xkill the windows and have to resort to Restart my system. This problem happened to me just now but after restarting, everything goes back to normal. What is the problem? 

I will try not sound too skeptic but since this problem i was curious about the stability and integrity of Ubuntu since. I really worry that this problem is just a tip of the iceberg.

---

### Post by Joeb454 on 2008-05-22
Do you have compiz fusion running?

If so can you hit Alt+F2 and type ```
metacity --replace
``` and see if the issue still exists when you open a terminal?

---

### Post by HotShotDJ on 2008-05-22
> **wariskampar said:**
> At first I thought this is exclusive to Terminal but when I try TOTEM, and few other program, same problem happen. I can not even xkill the windows and have to resort to Restart my system.I've been using Linux exclusively for about 6 years, and Ubuntu for the last two years, and I can assure you that it has been more stable than Windows for me.  I say this not to trivialize your current difficulty, but just to assure you that it is not a problem endemic to Ubuntu or Linux.  I think if we are able to get this issue sorted for you, you'll find Ubuntu to be a highly stable desktop operating system.

I'd like you to please give me a little bit of information about your computer... CPU, RAM, Hard Drives, Video Card.  Also, what version of Ubuntu have you installed?  (8.04 Hardy Heron? 32 bit? 64 bit?).  I'm suspecting one of three things -- a Video Card issue, a RAM/Swap issue, or a full root partition (in that order).

Also, if you could please run the following two commands in a terminal and post the output:```
lspci | grep VGA
sudo fdisk -l
```that very last letter is a lower case "L"

---

### Post by wariskampar on 2008-05-22
@Joeb454: yes, i'm using compiz but only enable 3d tube feature (that is all as far as i know). may i know what the code you're giving suppose to do. sorry because i'm bit paranoid a far as a 'remove' word is concern:)

@HotShotDJ: this the list and i'm using HP Pavilion dv4000 laptop, Pentium M 1.83Ghz, 1GB Ram.


aznan@aznan-laptop:~$ lspci | grep VGA 
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
aznan@aznan-laptop:~$ sudo fdisk -l 

[sudo] password for aznan: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94e494e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1883    15125166    7  HPFS/NTFS
/dev/sda2            1884        9729    63022995    f  W95 Ext'd (LBA)
/dev/sda5            1884        3165    10297633+  83  Linux
/dev/sda6            3166        7774    37021761   83  Linux
/dev/sda7            7775        9561    14354046   83  Linux
/dev/sda8            9562        9729     1349428+  82  Linux swap / Solaris
aznan@aznan-laptop:~$ 

Frankly, my wife is quite irritated when I swith to Ubuntu. So far my experience with the OS is great and one of the best is great support from community.

---

### Post by Joeb454 on 2008-05-22
The code disables compiz and uses the default window manager again. To re-enable compiz afterwards, you hit ALT+F2 again, and type ```
compiz --replace
``` post back if you still encounter the problem after running the command I posted first :)

---

### Post by HotShotDJ on 2008-05-22
> **wariskampar said:**
> @HotShotDJ: this the list and i'm using HP Pavilion dv4000 laptop, Pentium M 1.83Ghz, 1GB Ram.Ok, I don't see any obvious issues there.  I'm thinking along the same lines as Joeb now.  Run the command he suggested.  Also, make sure that with the cube, you do NOT have transparency enabled... the integrated intel video cards do NOT like that particular feature (personal experience!)

(Actually, you'll be disabling compiz for a little while, so the cube/transparency thing won't matter until you re-enable compiz.)

---

### Post by wariskampar on 2008-05-22
OK guys! i will do that and post any problem later. Thanks for your great help:)

---

