---
title: "[SOLVED] Dual boot question."
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Axis on 2008-10-08
There are tons of tutorials on moving from windows to dual boot with ubuntu.

However I have ubuntu and need to dual boot with windows and cannot seem to find a tutorial for it. How can I reduce the size of my ubuntu partition and then install the windows in the new free space? How do I make the GRUB recognize the new windows partition after install?

Thanks,
Axis

P.S. The applications will not run in wine no matter what I do (they just aren't compatible) and virtualbox isn't working it for me either. Trust me moving back to a little windows was my last resort :(

---

### Post by kk0sse54 on 2008-10-08
To shrink your Ubuntu Partition pop in a Ubuntu liveCD and open up the Partition Editor or Gparted and then just resize and format the new partition. Then after installing Windows on the correct partition you will have to reinstall GRUB in order to be able to boot into Ubuntu. Here's a tutorial for installing grub off a liveCD [http://ubuntuforums.org/showthread.php?t=224351&highlight=installing+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=installing+grub) .Usually after you've finished reinstallting grub it will automatically detect Windows otherwise just type in the terminal ```
sudo gedit /boot/grub/menu.lst
``` and edit your grub to point to the correct place on the hard drive where Windows is located for example (hd0,0) or (hd0,1) depending on your hard drive name and the partition placement. A typical windows entry in grub would be:

title		Windows
root		(hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by Axis on 2008-10-09
I installed windows, and the GRUB. However I cannot see my windows partition when I boot.

It should ask me if I want to boot to ubuntu or windows correct?
Because I'm not seeing that at all, it just boots straight into ubuntu.

I did what you told me, however it didn't make a difference. Its worth nothing that, that file was empty when I got there. Is that a problem?
I just added the lines you told me, to the file and then saved it.

---

### Post by handydan918 on 2008-10-09
> **Axis said:**
> I installed windows, and the GRUB. However I cannot see my windows partition when I boot.

It should ask me if I want to boot to ubuntu or windows correct?
Because I'm not seeing that at all, it just boots straight into ubuntu.

I did what you told me, however it didn't make a difference. Its worth nothing that, that file was empty when I got there. Is that a problem?
I just added the lines you told me, to the file and then saved it.
Unlikely. That file is required for GRUB to work at all. Any chance you mistook the filename?
Say, for example, the last three characters are lowercase LST, not 1ST.

---

### Post by Big_Kahunaca on 2008-10-09
> **Axis said:**
> I... that file was empty when I got there. Is that a problem?
I just added the lines you told me, to the file and then saved it.

Yeah, that would be a problem.  Are you sure you typed the path correctly?

If that file was empty, you wouldn't even be able to boot into Linux, which would lead me to believe you created a NEW file that won't be reference by anything.

Also, if you're not getting a menu when you boot, it could be the timeout for GRUB is set too low.

make sure you type "sudo gedit /boot/grub/menu.lst" (without the quotes of course..)

Or, could you "cd" into /boot/grub/ then type "ls" and post the results?

---

### Post by Axis on 2008-10-09
First things first.

I restarted and now the file is opening fine.

However two new problems have arised.

1. The windows part only shows up if I press escape and then look at it. Even though I kinda like it that way is it the only way I can view it or can I make it ask and choose every time?

2. When I select windows I get an error saying its incorrect. If you can't tell what the error is by looking at my file I will check again and see what it is.

Please answer the questions seperatley as I may want to keep the file the way it is.

I have copied my .lts file to a .txt so that you can examine it and possible see where I made my error.

Thank everyone so much for helping me thus far!

---

### Post by Big_Kahunaca on 2008-10-09
If you put a # in front of the line "hiddenmenu" that should solve that problem.

---

### Post by Big_Kahunaca on 2008-10-09
Windows cannot be on (hd0,0) because that's the Linux partition.

Could you "sudo fdisk -lu" and post the results?

---

### Post by Axis on 2008-10-09
The error I was receiving was:
Error 13: Invalid or unsupported executable format.

Results from the command you asked for are...

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   238999004   119499471   83  Linux
/dev/sda2       238999005   300431564    30716280    7  HPFS/NTFS
/dev/sda3       300431565   312576704     6072570    5  Extended
/dev/sda5       300431628   312576704     6072538+  82  Linux swap / Solaris

```

---

### Post by Big_Kahunaca on 2008-10-09
Thank you!

In the windows section of your .lst file, change where it says "root (hd0,0)" to say "root (hd0,1)"

---

### Post by Axis on 2008-10-09
Thank you so very much!
I can boot to windows now just fine.

---

### Post by Big_Kahunaca on 2008-10-09
> **Axis said:**
> Thank you so very much!
I can boot to windows now just fine.

Excellent!

Now stop booting into windows. :)





No. Seriously.

---

### Post by Axis on 2008-10-09
I can't develop the game with the engine I need in linux or virtual box, and the same applies to a few games I play.

If only I could completley avoid it :(

---

### Post by Big_Kahunaca on 2008-10-09
Cool, you're a game developer?



Can I have a job?

---

