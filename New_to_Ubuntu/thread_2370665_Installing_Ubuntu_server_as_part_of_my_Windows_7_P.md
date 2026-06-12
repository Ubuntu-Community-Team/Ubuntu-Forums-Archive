---
title: "Installing Ubuntu server as part of my Windows 7 PC"
date: 2017-09-06
forum: New to Ubuntu
---

### Post by basicboy on 2017-09-06
I am starting Ubuntu from scratch and need to convert part of my C drive to an Ubuntu server with serving MySQL with Apache and PHP.
I presently develop database applications with VB6 and Access.

1. I think I will have to partition my disk to run the Ubuntu server as an operating system on the server - is that right - and if so, can I partition it even if I am running Windows 7 on the rest of the disk as my main operating system?
2. Is Ubuntu server the right Linux operating system to use?
3. Will the next step be to install MySQL, Apache, PHP and phpadmin on that partitioned part of the disk with Ubuntu server?

Thanks so much
PK

---

### Post by Bucky Ball on 2017-09-06
1. Yes. Use Windows tools like Disk Management (NOT Linux ones) to shrink a partition so you have free, unallocated space to create a Linux partition and install Ubuntu Server to.
2. For what you want to do? Probably yes.
3. Don't know as not a server guru.

Question 1 is not server specific (you need free, unallocated space to install Ubuntu regardless of the flavour or spin). Question 2 and 3 and all other server related questions probably belong in a new thread in the Server sub-forum.

Good luck. ;)

---

### Post by HermanAB on 2017-09-06
Err... a dual boot system is usually rather unsatisfactory, especially if the one is a server that is expected to be always running.

I suggest that you look into virtualizers such as Virtualbox and KVM.  With those, you can run both systems at the same time.  You could either run Linux on Windows, or Windows on Linux.  Since Linux has a better scheduler, Windows on Linux tends to work a little better than vice versa.

---

### Post by basicboy on 2017-09-06
Thanks to you both,
I only wanted to shrink partition of the C: drive, make a new G:\ drive and install MySQL server on the G:\ drive and test my Windows VB6 programs with a database on the Ubuntu G:partition.
However, I have installed Ubuntu on the new partition and selected to keep the Windows or the Windows partition.
Now I am unable to boot into Windows.
As far as I can see Ubuntu has taken over BIOS and I cannot set the Windows partition (still drive c:) as boot device.
PK

---

### Post by mastablasta on 2017-09-06
ubuntu doens' ttake over BIOS. what oyu might see at the start is GRUB boot menu.

to test you windoews VB6 programs you could have just installed it all in virtualbox. or better yet for what you need there are images such as for exampel bitnami stack which don't even need any installing. just set up a virtual PC extract the image and you are good to go.

also for dual boot ubuntu needs unformatted free disk space. and with dualboto only one OS at a time can run. wzhile with virtualbox you cna have many running concurrently (depending on how much ram and how many cores you have).

server works fine with 512 MB, so i have no problem running it for tests on my old single core pc with 4 Gb ram.

another benefit of virtual images is that you can take a snapshot, mess it all up and then just restore the snapshot and thus getting a previous non messedup state within seconds.

---

### Post by basicboy on 2017-09-06
Thanks mastsblasta, I unfortunately saw HermanAB's comment only after I installed Ubuntu.
I see you both have this virtual box comment which I will try,  but how do I get into my old Bios, because F2 takes me to this new fake Bios or grub unknown to.me.

---

### Post by basicboy on 2017-09-06
In fact, I cannot even get to that Bios with F2 anymore, apart from the fact that it was apparently modified by Ubuntu to see only the Ubuntu drive partition.
The Gnu window does not want me to select anything else than loading the Ubuntu operating system.

---

### Post by oldfred on 2017-09-06
Did you leave Windows hibernated?
Grub only boots working Windows. Or Windows that is not hibernated, nor needs chkdsk. 
The NTFS driver does not let you mount NTFS read/write if hibernated or needs chkdsk to prevent damage.

With dual boot, you cannot run two systems at once. Or from Windows you cannot access a data base on Linux as Linux is not running. You need two systems, not sure how that may work with virtual systems.

Is Windows 7 installed in the old BIOS boot mode, or newer UEFI boot mode? Most Windows 7 systems are BIOS.

If BIOS, you have to restore Windows boot loader to directly boot Windows if it needs repairs.
       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by mastablasta on 2017-09-07
once you fix it, virtualbox install instructions with pics: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by basicboy on 2017-09-07
Thank you both very much. I will try.

---

