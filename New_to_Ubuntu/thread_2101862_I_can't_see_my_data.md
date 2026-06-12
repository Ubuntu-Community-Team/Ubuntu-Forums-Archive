---
title: "I can't see my data"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by kmelkon on 2013-01-05
Hi there,
So i wanted to try out Ubuntu 12.10 on my laptop and i already had windows 7 installed and windows 8 (which i installed after W7) so i made a live usb of ubuntu and i installed it over the partition where W7 was at. Everything went fine and it booted properly but whe i restarted there no windows 8 in the GRUB and i could only boot to Ubuntu, i tried using W8 CD to repair it but i didnt work and i could'nt even install it again over any partition. At this point somehow my Ubuntu could not boot again so i installed it one more time and now all my paritions are one partition and it is in ext4 format and it says it's full but i can't see anything of the data on it and in order to install W8 again i have to format everything (which i don't wanna do unless it's the only solution) .. 

*i just want my data back (if that's possible) and install W8 alongside Ubuntu 12.10

Thanks all.

---

### Post by ugm6hr on 2013-01-05
I would suggest prioritising recovery of your data, if its important.
Hence, you should stop trying to change or modify any partitions until you have done this.
I would suggest booting from the Ubuntu LiveCD/USB, and then looking at the partitions / files present from there.
If you locate your personal files, copy them on to an external HD.
Once the data is secure, come back and ask how to set up a W8/Ubuntu dual boot.

---

### Post by kmelkon on 2013-01-05
> **ugm6hr said:**
> I would suggest prioritising recovery of your data, if its important.
Hence, you should stop trying to change or modify any partitions until you have done this.
I would suggest booting from the Ubuntu LiveCD/USB, and then looking at the partitions / files present from there.
If you locate your personal files, copy them on to an external HD.
Once the data is secure, come back and ask how to set up a W8/Ubuntu dual boot.

Thanks, I will do that and see what will happen and then come back :D

---

### Post by oldfred on 2013-01-05
Is Windows 8 in a primary partition?

Windows only boots from or repairs an install in a primary partition with the boot flag formatted NTFS.

Since your Windows 7 was installed first, it was the active partition (boot flag) and all the Windows 8 boot files were installed to the Windows 7 partition. If Windows 8 is primary, move boot flag to that partition & rerun repairs. It will probably also install its boot loader to the MBR, so you will have to reinstall grub2's boot loader to the MBR after you get Windows working.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by tlhIngan on 2013-01-05
> **kmelkon said:**
> Hi there,
So i wanted to try out Ubuntu 12.10 on my laptop and i already had windows 7 installed and windows 8 (which i installed after W7) so i made a live usb of ubuntu and i installed it over the partition where W7 was at.


Give us a little bit more details in terms of partitions please, in chronological order.
Where was the Win7 installed?
Then, where did you install Win8 and did you change any partitions?
Finally, where did you install Ubuntu what changes did you make to partions?

---

### Post by kmelkon on 2013-01-06
> **tlhIngan said:**
> Give us a little bit more details in terms of partitions please, in chronological order.
Where was the Win7 installed?
Then, where did you install Win8 and did you change any partitions?
Finally, where did you install Ubuntu what changes did you make to partions?

well i had the windows 7 first and other 3 logical partitions .. then i installed W8 which i think as @oldfred said that it was using shared boot files from windows 7 .. 
I made a new clean partition for W8 and installed it there..
i tried to install Ubuntu over W7 partition after formatting it ..

Now i've used a utility called testdisk which recovered most of my data (400GB) some of it is broken but most of it is working, and it recovered the data in 4000+ folders (not sorted) so i have to check every folder for the data i need cuz theres a lot of .dll's and .cab's which are not usable .

---

### Post by kmelkon on 2013-01-06
Now I will put all my recovered data on an external hard disk, then install Windows 8 and Ubuntu 12.10 ..

Can you please give me some basic instructions on how to do it w/o breaking everything again ?

Thanks all for your help.

---

### Post by TheFu on 2013-01-06
> **kmelkon said:**
> Now I will put all my recovered data on an external hard disk, then install Windows 8 and Ubuntu 12.10 ..

Can you please give me some basic instructions on how to do it w/o breaking everything again ?

Thanks all for your help.

I am not convinced that you've actually lost any data.  Partitions and booting has become extremely complicated with multiple partitioning schemes (MBR/GPT), different physical disk organizations (512b vs 4K) and the addition of UEFI vs BIOS.  It is complex.

There is a script called **bootinfoscript** [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) that will check out your HDDs and all partitions and will dump information about them.  If you could run that and post it, we'd have all the necessary data to understand your situation. Run it from a LiveCD or off a flash drive boot.

There is also a great tool for fixing the most common boot issues between Windows and Linux - **boot-repair**.  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) It is just a Linux program, so you can install it from a LiveCD, then run it.  It will find Windows OS partitions AND Linux partitions, then add them to a boot menu. It is pretty amazing. 

Of course, nothing can replace a good backup method. Before doing anything like loading a NEW OS, having a complete, 100% working, tested backup **FIRST** cannot be understated.  Backups save our bacon all the time.

And in case this isn't clear, Linux can read and write to unencrypted NTFS partitions, but to get Windows to read from any Linux file system requires an $80 driver that may or may not actually work, depending on the file system(s) involved.  In all my years running Linux systems, I do not know anyone - not a single person - who has used a windows driver to directly access UNIX or Linux file systems.  We use network sharing ALL-THE-TIME, but that doesn't work in a dual or multi-boot situation.

Backups, backups, backups.

---

### Post by oldfred on 2013-01-06
+1 on all of TheFu comments.

Assumes BIOS/MBR - lot different with UEFI/gpt.
Windows default install is a small 100MB boot/repair partition and the main install. The boot partition has to be primary NTFS with the boot flag. If installing to an empty drive Windows will automatically create the two files. If you have partitions created in advance you can install to one partition, but should then have a repair flash drive in case you need to repair Windows.

Window 8 also is always hibernated. Either full or partial for fast boot. When dual booting the can lead to issues. See below.  Best to set Ubuntu to only have read-only rights into Windows. Create another shared NTFS data partition for any data you may want to share.

Then use rest of drive as extended partition and create logical partitions for Ubuntu. If most of you data is in  a shared data partition you may not need a separate /home, just a slightly larger / (root).  

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by kmelkon on 2013-01-07
thanks theFu for your comments .. they're all useful .. i will look into it a bit more before dual booting .. and ill come here asking you for help if anything comes up.

---

