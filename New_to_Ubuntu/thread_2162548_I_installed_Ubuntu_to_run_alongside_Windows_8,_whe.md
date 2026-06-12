---
title: "I installed Ubuntu to run alongside Windows 8, when I meant to partition it.."
date: 2013-07-15
forum: New to Ubuntu
---

### Post by koertigs on 2013-07-15
Is it to late for me to partition ubuntu? It's currently running off of my flash drive, and I want to be able to boot into ubuntu without going through the boot loader or using my flash drive. I searched for a few hours and everything I found was related to (at least seemingly) initial installation.
What are my options? Can I run ubuntu off of a partition even though I already intalled it to run along side windows 8?

---

### Post by Gone fishing on 2013-07-15
> Can I run ubuntu off of a partition even though I already intalled it to run along side windows 8? 

Yes.

No reason to use a flash drive. If you boot on a live cd you can use the partion editor and resize the existing windows partition to make space for Ubuntu. I would have 3 partions for Ubuntu / , /home and swap. It is a good idea to backup your data before partitioning in case you delete a partition with your files on it.

---

### Post by Mark Phelps on 2013-07-15
> If you boot on a live cd you can use the partion editor and resize the existing windows partition to make space for Ubuntu. 

BAD idea ... Resizing Windows OS partitions with Linux utilities can lead to Windows filesystem corruption, rendering Windows unbootable.

Better to use the Win8 Disk Management tool to shrink the Windows OS partition.

---

### Post by oldfred on 2013-07-15
I do not understand. You say you installed along side. That would be into a new partition. One of the other choies is just to overwrite the entire drive (totally erase Windows).

May be best to see details. You can install this into your flash drive installer or download a liveCD/Flash version with it installed.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Paqman on 2013-07-15
> **Mark Phelps said:**
> BAD idea ... Resizing Windows OS partitions with Linux utilities can lead to Windows filesystem corruption, rendering Windows unbootable.

Better to use the Win8 Disk Management tool to shrink the Windows OS partition.

I don't know about this. I've used Linux tools to alter Windows partitions many times, without issue. Do you know of any actual cases where it's caused a problem?

---

### Post by oldfred on 2013-07-15
We have seen multiple cases in forum.
I also suggest using Windows tools for Windows and Linux tools for Linux. But never create partitions in Windows as it may convert to dynamic which does not work with Linux.

We also have seen a lot of users post that they have resized with gparted or installer and it has worked. 

Not sure what circumstances cause it, but by resizing with Windows and rebooting then Windows can run its chkdsk. Sometimes it just cannot run chkdsk or os-prober does not mount Windows as chkdsk flag is (or should be) set.
Then user blames gparted or Ubuntu for Windows not working when it may be just a Windows issue or an issue they even had before. Helps reduce the conflict issues.

---

### Post by Gone fishing on 2013-07-16
Oldfred is right - I should have suggested resizing using the Windows utlities. 

I think it is less likely to cause a problem with recent releases of gparted but if you use the Windows utilitie to resize NTFS then you have very little risk of there being a problem.

Sorry I've been doing a lot of XP machines recently.

---

