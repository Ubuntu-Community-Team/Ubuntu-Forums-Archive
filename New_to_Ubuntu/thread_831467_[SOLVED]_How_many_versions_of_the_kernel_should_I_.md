---
title: "[SOLVED] How many versions of the kernel should I keep?"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by dimitri57 on 2008-06-16
I installed Hardy about a month ago (AMD64) and I love it.  I'm fewer reasons each day for booting into Vista.

Since then there have been three updates to the linux kernel, so I now have four versions installed. (2.6.24-16, 17, 18 and 19).  It seems like I can remove old versions easily with the Synaptic Package Manager, but I'm wondering how many versions to keep.  Intuitively is seems that two would be for sure and MAYBE a third just in case.

What is a reasonable practice for this?  Disk space is not a problem.

Thanks.

---

### Post by dasunst3r on 2008-06-16
If the latest one works for you, then you should keep just one kernel.  Each of the kernel installations take up almost 200 MB for me, so freeing up that bit of space would be nice.

---

### Post by shad0w_walker on 2008-06-16
To be honest, I just leave them all installed. If disk space isn't an issue then it can't hurt to keep the around, however I assume you want to get rid of them to tidy up the grub menu?

If so, you can edit the grub settigs to show only X number of the latest kernels, so for example it will show the current updated kernel and the previous one. 

To do this follow these instructions, just be careful what you are editing or take a backup before hand.

1. Press Alt+F2 to open run dialog
2. Run this command:  
```
gksu gedit /boot/grub/menu.lst
```
You should be prompted for your password as this is an admin task, just enter your normal users password.
3. Find the following line

```
# howmany=
```
4. Replace the current number on that line with the number of kernel versions you want to display.

5. Optional extra tweaks.
```

# memtest86=   Used to add/remove the memtest option in the grub menu
# alternative=  Used to display the alternate (Recovery) boot option
default 0  Used to select the default boot option in grub, simply enter  the position of the entry in the list. Note: Starts counting from 0
timeout 10   Time before the default choice is activated

```

---

### Post by drs305 on 2008-06-16
Here's guidance on how to change grub displays and other options.

I believe you should keep the current and one backup kernel, and definitely keep the recovery option of the current kernel displayed.

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by Dougie187 on 2008-06-16
I typically leave them all, but in the past i have heard a good rule of thumb is to keep the current one with the previous one, if they both work good. if not, keep the current one and the last one that worked good. You can clean up grub really easy too if they bother you. The only way I would only keep the current one, would be if it works great for you, and you are really worried about the disk space, since they don't take up a whole lot of space for most modern hard drives.

---

### Post by dimitri57 on 2008-06-16
I had seen a previous post about editing the boot menu so I've already used StartUp-Manager to limit the number of versions displayed at boot time to two.

---

### Post by hariprs on 2008-06-16
I always keep atleast two kernels, the current and the previous one. But after upgrading to a new kernel don't delete the oldest kernel until you feel the new kernel is stable and everything works for you. And always read the release notes of a the new kernel before upgrading.

---

### Post by dimitri57 on 2008-06-16
Seems like I should keep two.

Followup question:  Synaptic gives options to uninstall, and to uninstall and completely remove.  I assume that I should completely remove the old versions.  Is this correct?

---

### Post by drs305 on 2008-06-17
> **dimitri57 said:**
> Seems like I should keep two.

Followup question:  Synaptic gives options to uninstall, and to uninstall and completely remove.  I assume that I should completely remove the old versions.  Is this correct?

Yes, that is correct. Should you ever need it, you can always restore a piece of software as long as it's in the repositories. Synaptic is designed so as  not to remove items necessary for other programs to operate.

---

### Post by hariprs on 2008-06-17
> **dimitri57 said:**
> Seems like I should keep two.

Followup question:  Synaptic gives options to uninstall, and to uninstall and completely remove.  I assume that I should completely remove the old versions.  Is this correct?

Yes, you can remove it completely. It is also one way of keeping the machine clean. But it is not applicable for all softwares. Especially for the software that has some configuration file that can be used in future.

---

