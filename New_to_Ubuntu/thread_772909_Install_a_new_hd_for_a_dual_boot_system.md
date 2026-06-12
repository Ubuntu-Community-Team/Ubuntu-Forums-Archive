---
title: "Install a new hd for a dual boot system"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by mshu on 2008-04-28
Hello all,

I have winxp (500G) as primary & Ubuntu (250G) as slave on my ASUS P5GD2 Deluxe P4 machine.

I would like to install a new hard drive for storing all my VMs & ISOs, I asked my friend to partition the new hd for me with NTFS (since Ubuntu can see NTFS, if I format it using ex3 then winxp cannot see it)

When I plug that new hard drive (NTFS) in I receive a GRUB error 17
What is the best way to achieve it and what tool(s) do I need ?

Thanks in advance

---

### Post by LaRoza on 2008-04-28
> **mshu said:**
> Hello all,

I have winxp (500G) as primary & Ubuntu (250G) as slave on my ASUS P5GD2 Deluxe P4 machine.

I would like to install a new hard drive for storing all my VMs & ISOs, I asked my friend to partition the new hd for me with NTFS (since Ubuntu can see NTFS, if I format it using ex3 then winxp cannot see it)

When I plug that new hard drive (NTFS) in I receive a GRUB error 17
What is the best way to achieve it and what tool(s) do I need ?

Thanks in advance

Are you using Sata drives?

Do you have enough ports for this?

From what you describe, Windows XP on the master and Ubuntu on the slave, it seems that grub was installed on the primary hard disk (if it weren't, Windows XP would boot only, unless you have the slave to boot first). If you moved the Ubuntu hard drive, you will get grub errors.

Grub is installed to the MBR, but that part of Grub just points to the real grub which is in /boot. So the system boots, the MBR tries to find grub and fails. 

If you are not moving the Windows or Ubuntu hard disks, please describe your setup in greater detail.

---

### Post by mshu on 2008-04-28
Thanks for the quick reply =D

Yes I am using SATA drives my mother board ASUS P5GD2 Deluxe allow a max. 4 hd (w/ RAID)
This is how I set it up at the very beginning:

1) Only XP was installed in a 500G hd (Primary Master) -> under BIOs it's indicated as third master
2) Then I installed a new 250G hd (Slave) for Ubuntu -> under BIOs it's indicated as third slave

Everything is running happily and I am able to dual boot =D

3) Now I would like to add in a third hd to store my VMs & ISOs. I have it currently formatted as NTFS.
BIOs indicated as fourth Master. Once i pop the hd in, I cannot pass through GRUB and was given an error 17. 

I have double check the boot order My XP hd still the 1st hd to boot (although I have CD ROM & floppy as primary & secondary boot sequence). 

Once I have removed the new hd my computer boot hapily and GRUB allow me to choose which OS I want to be in.

Thanks in advance =D

---

### Post by LaRoza on 2008-04-28
> **mshu said:**
> Thanks for the quick reply =D

Yes I am using SATA drives my mother board ASUS P5GD2 Deluxe allow a max. 4 hd (w/ RAID)
This is how I set it up at the very beginning:

1) Only XP was installed in a 500G hd (Primary Master) -> under BIOs it's indicated as third master
2) Then I installed a new 250G hd (Slave) for Ubuntu -> under BIOs it's indicated as third slave

Everything is running happily and I am able to dual boot =D

3) Now I would like to add in a third hd to store my VMs & ISOs. I have it currently formatted as NTFS.
BIOs indicated as fourth Master. Once i pop the hd in, I cannot pass through GRUB and was given an error 17. 


Just to let you know, with Sata, there is no such thing as "master" and "slave". 

The easiest, if longer, way of fixing this is to put to reinstall grub after everything is plugged in.

I put my OS's on the same disk, and use my other hard disk for storing data to prevent such confusion.

---

### Post by mshu on 2008-04-28
Sounds like a plan. Do you happen to have a link regarding how to re-install GRUB ?

Also just wondering in your case to have OS in one hd and storage in another hd, do you use NTFS on your storage hd ?

Cheers and thanks very much for your time =]

---

### Post by LaRoza on 2008-04-28
> **mshu said:**
> Sounds like a plan. Do you happen to have a link regarding how to re-install GRUB ?

Also just wondering in your case to have OS in one hd and storage in another hd, do you use NTFS on your storage hd ?

Cheers and thanks very much for your time =]

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Yes, I use NTFS.

I have two hard disks, but 250 GB. I have a 35 GB Windows Vista partition and a 35 Ubuntu partition. The rest of that drive used to be for storage also, but at the moment, it is unformatted (don't ask). The other disk is all one big NTFS partition, and I have swap on the other disk as well.

---

### Post by mshu on 2008-04-28
Million Thanks, 

I am not too familiar with the partition part with Linux, if you can explain a bit to me that would be great =] Still trying to learn how things work =]

I know there are 3 - 4 partition all together in Ubuntu. (swap, home and others)

What's the benefit to put the swap and home in different drives? I saw some posts said if you have your home partition on another drive, it's good for data recovery ?

If you can provide me additional information regarding on partition and what are they meant for that would be great. Again thank you very much for your time =]

---

### Post by mshu on 2008-04-28
Just did some testing and follow the link to re-install GRUB.
The search part returns hd(1,0) and I continue the setup, after that reboot, still GRUB error 17

So I decide, may be I should try to delete the new hd (NTFS partition, thus treat it as a new hd install). So I insert the windows setup disc and delete such partition. Now the new hd has nothing and not partition yet.

When I rebooted and ran GRUB again, it return error 22. Once i removed the un partition hd, things work fine and I can boot into both Ubuntu & Win Xp 

Any idea ? Thanks

---

### Post by LaRoza on 2008-04-28
> **mshu said:**
> Million Thanks, 

I am not too familiar with the partition part with Linux, if you can explain a bit to me that would be great =] Still trying to learn how things work =]

I know there are 3 - 4 partition all together in Ubuntu. (swap, home and others)

What's the benefit to put the swap and home in different drives? I saw some posts said if you have your home partition on another drive, it's good for data recovery ?

If you can provide me additional information regarding on partition and what are they meant for that would be great. Again thank you very much for your time =]

A drive has to be formated to be used. A partition is needed to hold the file system. The simplist scheme is one big partition on the drive. 

The benefit of having swap on another drive is that it is faster. Although I haven't been in a situation where swap is actually used because I have a lot of RAM. 

I really don't want to give you too much information on partitioning, as I am not there. Doing something wrong makes for headaches.

If you go into Windows, and you go to Computer Management and go to Disk Management (in Vista, just open the start menu and type "Computer" and click on Computer Management.) does the Windows (C:) drive have a lot of free space? If it does, you could install Ubuntu next to Windows and use the other drives for storage.

I am sorry for not being specific, but I don't want to give you enough information to break something without giving you enough to be able to avoid problems or fix them.

---

### Post by mshu on 2008-04-29
Sounds fun. So I guess I will try to re-formatted my new hd using my windows set up disc and then reinstall GRUB and see does that work, if not then booooo. Thanks very much for your and and your help.

---

### Post by mshu on 2008-04-29
Just wondering, do you think I need to update the menu.lst from GRUB ? Coz I am thinking may be we missa step and need to update the menu.lst from GRUB so it will actually list on the Bootloader ?
Please advise =]

---

### Post by mshu on 2008-05-02
Alright finally got things figure out.
The reason why I keep getting GRUB Error 17 is because the GRUB has a different disk listing then my BIOS

Grub listing my ubuntu hd is on hd1 but BIOs settings hd1 is my storage NTFS disk, thus GRUB cannot find it it needs and BOOOM

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945) has a very nice way to solve the problem. However you can also edit your BIOs hd listing to match your GRUB hd listing.

Once that's done problem solve and I'm a happy man agian !

---

