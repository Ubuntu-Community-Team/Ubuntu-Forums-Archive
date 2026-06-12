---
title: "Boot Repair Disk question"
date: 2015-03-03
forum: New to Ubuntu
---

### Post by penny3 on 2015-03-03
At the risk of sounding incredibly stupid, I need to ask this question. I ran a bootinfo summary (at this link if you need or want to see the whole long string -    [http://paste.ubuntu.com/10497935/](http://paste.ubuntu.com/10497935/) )  but what I was looking at was the very bottom where is has the repair suggestions. Now I know that sometimes things are suggested but they don't really need to be done or, if they are, might result in other problems which is why I need to ask ... if Boot Repair Disk suggests a repair, should you always do it? And is it telling me that this is something I need to do or will Boot Repair automatically do it? Thank you!

Here is what it suggests:


=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda3 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot


=================== Final advice in case of suggested repair


The boot files of [The OS now in use - Ubuntu 14.04.2 LTS] are far from the start of the disk. Your BIOS may not detect them. 
You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools 
such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. 
([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))


=================== User settings
The settings chosen by the user will not act on the boot.

---

### Post by Bucky Ball on 2015-03-03
Is the machine booting and running okay? If so, I'd leave it. If it ain't broke, don't fix it! If you are having an issue, which is the reason you ran boot repair and not just out of curiousity, please elaborate on what that issue is and we'll see what we can do.

---

### Post by grahammechanical on 2015-03-03
The author of Boot Repair is advising us. It is our responsibility to make the decision. I think Boot Repair is an excellent utility but like all things it does not work miracles. And it does not claim to do that. For example, it cannot fix OS loading problems. It concentrates on getting the boot loader doing its stuff. And the simplest and perhaps most effective way to do that is the reinstall the Linux boot loader.

I think that the author of boot repair is trying to give comprehensive advice and avoiding trying to do too much which might cause a greater mess. It does not create or resize partitions. It seems to me that the author of Boot Repair is well aware that those most in need of this utility are those who are least knowledgeable about Linux. The author, as I can see things, tries to avoid baffling us with science whilst at the same time providing full relevant information about the system for anyone who understands the information. I do not include myself in that group.

Regards.

---

### Post by oldfred on 2015-03-03
The first suggestion is the reinstall of grub which is the most common boot problem.

Some older BIOS and many external USB drive installs seem to have issues with boot files beyond a certain point on a drive. Very old BIOS have a known issue of no boot file beyond 137GB on drive, so a large / or /boot or a / partition after a larger Windows partition has caused boot issues. Usually the partition cannot be found (but that is not the only reason for that issue.)

But all new systems with UEFI and most newer systems do not need boot drives near beginning of drive. 
And if an external drive best to have a smaller / of 25GB at beginning of drive anyway.

As posted above if it works, you do not need to do anything. But still useful to run Boot-Repair just to have summary report to document install.

---

### Post by penny3 on 2015-03-03
Thank you! The 'if it ain't broke, don't fix it' is exactly what I was hoping to hear. :)  I am having no issues booting into the system (duel boot with Win 8,1 - which I am planning on completely removing as soon as I am totally comfortable with Ubuntu). 

Bucky - I ran the Bootinfo summary because of the Wine and the couple of apps I uploaded from Winetricks issues as discussed in a previous thread. Thought that maybe bootinfo would indicate something in there to point to the problem. Partition disks seem a pretty unlikely culprit even to a computer idiot like me. Will leave well enough alone and continue on with 'the Ubuntu journey'.

---

