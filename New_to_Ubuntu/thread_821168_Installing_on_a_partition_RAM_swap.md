---
title: "Installing on a partition RAM swap"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by qwaszx86 on 2008-06-06
Back when I installed vista on my new computer, I created a 15 gigabyte partition to one day install linux on. Unfortunately I was not thinking and I made c: the small partition and the rest of the drive (bout 450 gigs) was left for Vista.

I checked out my drives and according to vista, the c drive (small one) is listed as a primary drive, although E is the boot drive. I noticed that 3.2 gigs of C are in use, but there are no files on C. I have 4 gigs of RAM and vista recognizes 3.2 of them...coincidence? or is that where the RAM swap is? 

If I resize the partition through ubuntu and install it on the c drive, will I screw my vista installation? Is there a way to move the ram swap onto the proper drive?

Thanks for the help, really looking forward to getting Ubuntu up and running.

-Qwaszx

---

### Post by Najand on 2008-06-06
I think that 3.2 GB of file in your C: drive belongs to the paging files windows make as virtual memory. See if it works for you.

1. Click start in your Windows Vista and type: [FONT="Courier New"]diskmgmt.msc[/FONT] and then press <Enter> to open the Disk Management utility (click Continue in the User Account Control, if necessary) The bottom pane shows each disk on your system and the drive letter that corresponds with each partition. See the capacity of your harddisks and see how much of it have been used.

2. Disable Windows to make virtual memory on your C: drive.
In Vista, start the System Properties dialog box directly by clicking Start, typing [FONT="Courier New"]systempropertiesadvanced[/FONT], and pressing <Enter>. As with the preceding method, you may have to click Continue in the User Account Control dialog box.
In the Performance section, click Settings and then the Advanced tab. Under Virtual Memory, click Change. Uncheck Automatically manage paging file size for all drives, if neccessory. You'll see a paging file size already listed on your Windows drive; leave it alone fot now. 
See the size of that paging data for your drive C. 

3. If so, don't rush. You would need to make some space for Virtual memory on other drives. Select No paging files for drive C and before clicking OK change System Managed Size for your Windows Partition. Select Custom size only if you want to set the size yourself and type in the initial and maximum size (Microsoft says making them the same amount is most efficient); Microsoft's rule of thumb is to make the file 1.5 times the amount of RAM in your system. Or select System managed size to let Windows determine the size (XP and Vista only). Click Set, then OK.

4. You'll see a reminder that the changes will take effect the next time you restart your system. Windows will most often use the paging file on the least-busy drive, which means your new paging file will do most of the work.

I hope it will work for you. If it was not like that, send me more information and I will help you more on that.

---

### Post by qwaszx86 on 2008-06-07
Ok that worked great, thanks for the help. Now I'm unsure of exactly how to install on that partition however. The automatic thing wants to change its size, which I don't want to do, but I'm confused about how to use manual.

Manual, as I understand it, needs you to set a partition for the installation (would that be set to NTFS?) but you also need to set a swap file...does that go in a different partition? And there is something about mounting location that has two options /dos and /windows. I don't get it. Thanks for the help.

-Qwaszx

---

