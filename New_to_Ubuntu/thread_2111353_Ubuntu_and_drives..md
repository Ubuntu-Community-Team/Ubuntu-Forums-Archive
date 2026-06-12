---
title: "Ubuntu and drives."
date: 2013-02-01
forum: New to Ubuntu
---

### Post by Onigami on 2013-02-01
I need help with Ubuntu wanting to install on my spare HD I use for storage, why is it doing this? I try to select another drive but it refuses to show any others. However when I choose the "New Partition" option it shows all the drives, but when I try to make a new partition on it, it claims that all other partitions will be no longer accessible or something to the degree of possible deletion.

I have a 465 GB HD (500 GB it claims but Disk Manager says 465) and a 290 GB secondary I use for storage, I want to split the 500GB into 150/60 for Windows 7 and Ubuntu, how can I do this without messing anything up and allowing Ubuntu to install on the same drive? Is this possible? I'm installing 12.10, not 12.04.

I installed Ubuntu on my secondary drive before and noticed it wouldn't give me the option to choose which OS I wanted to boot into, simply booted into Windows. Could it installing itself on my secondary drive be the reason for this? How I recovered the data was through Disk Manager, I simply deleted the partition and re-extended the drive back into it. Is there a simpler method to doing this? I made a USB stick to boot from using a USB creator tool mentioned by the Ubuntu site.

I'd appreciate any help. Thanks.

If there's any info needed, let me know.

---

### Post by drunkenbrawler on 2013-02-02
> I need help with Ubuntu wanting to install on my spare HD I use for  storage, why is it doing this? I try to select another drive but it  refuses to show any others. However when I choose the "New Partition"  option it shows all the drives, but when I try to make a new partition  on it, it claims that all other partitions will be no longer accessible  or something to the degree of possible deletion.

Can you post exact error message or a screen shot of Gparted (if you are using that)?

> 
I installed Ubuntu on my secondary drive before and noticed it wouldn't  give me the option to choose which OS I wanted to boot into, simply  booted into Windows.


This maybe because grub was installed on second disk and you have boot configuration that says boot from first disk. This can be fixed easily, but you will have to search a little.

 > I want to split the 500GB into 150/60 for Windows 7 and Ubuntu, how can  I do this without messing anything up and allowing Ubuntu to install on  the same drive?


yes, this can be done without messing things up. Do you have windows installed already? or are you going to install it too?

If you have installed windows and need to make a partition, use Gparted to easily shrink windows partition and create new partition for ubuntu.
If you have installed windows and already have a partition for ubuntu, process is straightforward.
If you are going to install windows and need to create partitions and all, then I suggest first create partitions from live CD, then install windows, and then install ubuntu, so you don't have to change grub entries.

---

### Post by Onigami on 2013-02-02
Thanks, I finally got it to install on the separate partition and configured the grub to boot from the Windows 7 loader on the C: drive, only now I'm facing grub> when I try to boot up Ubuntu. I tried using a program called EasyBCD to configure it, and it doesn't help, it allowed me to fix the boot loader so I can select Ubuntu, but then immedietly takes me to the command line grub> and gives me the option to hit TAB for commands I don't know how to use.

I installed 12.10 64 bit because I have 8GB of RAM, could the 64 bit be causing more problems than if I simply used a 32 bit installation?

Thanks for the help.

---

### Post by grahammechanical on 2013-02-02
There could be reasons for the seemingly strange behaviour of the installer.

1) The hard drive with Windows 7 on it is already partitioned into 4 primary partitions. There cannot be more than 4 primary partitions on a disk.

Ubuntu will install into a Logical partition but one of the 4 primary partitions must be an Extended partition so that the Ubuntu installer will create 2 logical partitions (one for Ubuntu, one for swap) in the primary/extended partition. The installer is wanting to install Ubuntu on the only hard drive present with less than 4 primary partitions.

2) The partitioner can only create a new partition by deleting one of the existing 4 primary partitions. This is why it is warning you about destroying the contents on those partitions.

3) Ubuntu will install a boot loader (Grub) into the Master Boot Record (MBR) of the drive it is being installed on - unless we direct it to install the boot loader somewhere else. If Ubuntu is on the secondary drive with Grub installed into the MBR of the secondary drive but the BIOS is set to boot from the primary drive then you will never get to see a boot menu. The BIOS will look for an OS on the primary drive. It will see Windows 7 and boot it.

I suggest that you think very carefully about what you are doing. You could lose not only data but also Windows. You need to review some of the posts on this forum about dual booting Ubuntu and Windows.

From what I have seen from some of these posts you must use Windows tools to change the sizes of those Windows partitions. There is a procedure to follow if you do not want to make mistakes.

If I am right about the disk already having 4 primary partitions, then one of them will have to be emptied, converted into an Extended partition and then re-sized to create enough space for Ubuntu. You would have to do this even if you allowed the Ubuntu installer to Install alongside setting its own partition sizes.

Regards.

---

### Post by Onigami on 2013-02-02
I used the 'shrink' option to create a second 60GB partition on my main HD, which uses Windows 7. Disregarding my secondary drive, C: is cut into 4 sections it shows on Disk Management, it is cut into 100MB System Reserved, 407.07GB Windows 7, 50.61GB for Ubuntu and 7.98 Swap for Ubuntu.

The main drive, C: began with only 2 partitions, the 465GB partition which was used for Windows 7 and a small 100GB partition for System Reserve.

Once again, thanks for the help.

---

