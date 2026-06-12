---
title: "Installed 12.10 from LiveCD.   Won't boot from HD"
date: 2013-02-20
forum: New to Ubuntu
---

### Post by thomas2013 on 2013-02-20
Hello Community,
From a 12.10 LiveCD I am attempting to completely replace Windows 8 with 12.10.  Here is some background info:

**My System:**  Toshiba Satellite L875D;  CPU Type:  AMD A6-4400M APU with Raydeon HD Graphics.

After running the install from the LiveCD a partial listing of **my partition** is as follows:

/dev/sda1   ext4              590.71 GiB       boot
/dev/sda2   extended    5.46 GiB 
/dev/sda5   linux-swap  5.46 GiB

After the install I removed the LiveCD and attempted to boot into Ubuntu from the Grub 2.00 window.  I choose **Ubuntu** and get the following message: > [7.xxxxxxx] kvm: disabled by bios.   Then the screen slowly fades from black with white text to all white (very curious).  Note that during the above procedure I have the System **Boot Mode** set to [CSM Boot].

If, on the other hand, I set the **Boot Mode** to [UEFI]  I get a message saying 'No Bootable Device' and I'm stuck there.

Note also that during the install my System had the **Boot Mode** set to [CSM Boot] and the **Secure Boot**Disabled].

That's my status -- I no longer have Windows 8 and can currently only use my computer from the Ubuntu 12.10 LiveCD.  

Thanks very much in advance for help and suggestions.
--TM

---

### Post by DuckHook on 2013-02-20
Welcome to the forums!

For a quick and dirty solution, read [this]("https://help.ubuntu.com/community/UEFI") guide. If you can hang on until later tonight, I can provide some instructions that may be very useful to you. Need 2 hours.

---

### Post by thomas2013 on 2013-02-20
Thanks DuckHook,

I already have some history with that document.  I'm guessing the solution may come from the Boot Repair.    Anyway, my first install attempt was using the SecureRemix (because the help doc recommended it because it includes Boot Repair) .  I abandoned SecureRemix because there was no executable after I burnt the iso?!   Then I tried the straight 12.10.  I initially had no luck with 12.10 with the Boot Mode set to UEFI.  Finally, by setting the Boot Mode to CSM I at least got the LiveCD working (thanks to other threads on the forum).  And that's where I stand as previously posted.

Before I go poking around any more I would be smart to take you up on your offer for further instructions.  If I don't see it tonight then I'll check tomorrow -- in either case many thanks for your time.

TM

---

### Post by DuckHook on 2013-02-20
> **thomas2013 said:**
> ...I no longer have Windows 8 and can currently only use my computer from the Ubuntu 12.10 LiveCD.

Wow. You went "all in".

Again, welcome to the forums. Gotta lend a hand to someone so courageous as to do a triple backward summersault blindfolded and with no safety net.:)

Since it is a brand new install that doesn't work, there is obviously no important data, so no backup needed. And since you've already installed over W8 once, you are in the enviable and exhilarating position of having absolutely nothing to lose. So, there is no need to tread carefully. In a situation like yours, I highly recommend that you install into UEFI mode and do all of your future installations in this mode from now on. The primary advantage of UEFI is future-proofing your system. Additionally, if you prepare your system properly for it, then you can dual boot, triple boot, and install side by side a lot more OSes than you ever thought possible.

Here's what I recommend:

Preparation:

1. Make sure you have the 64-bit version of Ubuntu. 32-bit cannot use UEFI. The 64-bit install image is called ...amd64. The 32-bit is ...i386. Don't be mislead by the "amd". It will work on both AMD and Intel processors.
2. Hash the install disk/usb to ensure that it was a good burn.
3. Boot into your bios and make sure that your system, including HDD, is set to boot UEFI. This can be no more than general instuctions because there are as many different UEFI bioses as there are MOBOs.

Partitioning:

1. We are going to partition your drive properly. Open gparted in your Live CD.
2. Choose every partition and delete them. All of them. Apply.
3. Device>Create Partition Table: Choose GPT, not MBR. Apply
4. Create a tiny 200MB (make sure it is megabytes, not gigabytes) partition at start of HDD. This will act as your future UEFI partition. Format as FAT32. Do not apply yet.
5. Next, create 50 GB (this one must be gigabytes) smack up against your first partition. This will act as your future / (root) partition. Format as ext4. Do not apply yet.
6. The next partition involves a choice. You can create a smaller partition, say, 100GB (make sure it is gigabytes) for your future /home directory, or take up most of the remainder of the disk. A smaller /home partition can always be expanded later. A large one can be shrunk (if you need to make space for alternate OS) but the shrinking process is more time consuming and risky than expanding. It's your choice. In the latter case, you must leave enough room for a swap partition at the very end (see next point). Do not apply yet.
7. Create a partition at the very end of your disk for swap. The size is another choice. If you don't care to hibernate, then 2 GB will do. If you want hibernation, then you must create one equal to all of your system RAM + 1GB. Make sure this partition is at the very end of your disk geometry. If choosing the small /home partition in step 6, then this will leave a large unpartitioned space in the middle of the disk. This is perfectly okay because the point was to leave you with future flexibility. Under file type, choose "swap"
8. Double check that your disk geometry reflects all of the above. If satisfied, Apply. This might take a few minutes.

You now have a properly partitioned disk with the new GPT partition table, ready to install Ubuntu. The next steps will install Ubuntu to your disk.

Installing Ubuntu:

1. Boot using LiveCD, but ***very important*** choose UEFI as your boot mode, whether using DVD or USB. See the earlier link provided.
2. Choose to install Ubuntu.
3. When you get to "Allocate Drive Space" dialogue, again, ***very important***, choose "something else". Do NOT choose  "alongside" or "Erase Disk and install". This is where you get the chance to map each of the important Ubuntu directories to the partitions that you created earlier.
4. If you partitioned according to above scheme, the dialogue box should now show:
sda1 200MB
sda2 50GB
sda3 100GB
sda4 xxGB (xx being whatever gigabytes you defined earlier for swap)
5. assign sda2 (check to make sure it is your 50GB partition) to /
6. Assign sda3 (check that it is 100GB) to /home
7. The system will automatically detect your earlier swap partition.
8. Apply
9. When the install process gets to the "Install GRUB" dialoque box, it will ask you where you want to install GRUB. Choose the whole of sda. ***Important*** do NOT choose the specific sda1 partition; just sda. For some reason, Ubuntu won't install the bootloader if you specify a partition. Only a disk. The install process will then find the small 200MB partition and install the bootloader and /boot.
10. Finish your installation and reboot, remembering to remove your DVD/USB when it tells you to.

It should now boot into Ubuntu.

Fair warning. Am doing this from memory, so some steps may be incomplete or inaccurate. If you want to double-check my procedure, check against previous link. The good thing about Ubuntu is that it can be reinstalled in 20 minutes.

---

### Post by DuckHook on 2013-02-20
Didn't see your follow-up post before posting my long instructions.

> **thomas2013 said:**
> I initially had no luck with 12.10 with the Boot Mode set to UEFI.

I'm not sure what you mean by this... did LiveDVD not boot at all? Or do you mean that it booted into LiveCD desktop but you were unable to install to HDD?

If former then, you probably downloaded 32-bit Ubuntu, which can't boot into UEFI,

If latter, you not only have to choose UEFI boot for the DVD/USB but set your HDD for UEFI as well.

You mention that you already disabled secure boot. Good. You also need to disable fast boot.

Please double-check all of these prerequisites.

---

### Post by thomas2013 on 2013-02-20
By  *** I initially had no luck with 12.10 with the boot mode set to UEFI *** I meant that the LiveDVD did not boot at all.  But I'm pretty sure that I have the 64 bit version (* ubuntu-12.10-desktop-amd64.iso *).  

I did try the Boot-Repair a little while ago.   That didn't fix the problem.  The URL that Boot-Repair gave me is:  ** [http://paste.ubuntu.com/1696296/](http://paste.ubuntu.com/1696296/) **.

I have seen it noted in these forums and the UEFI help doc that if Windows had boot mode set  to UEFI then Ubuntu must also have boot mode set to UEFI.  However, we also have this from the UEFI help doc:  >  Here is a 2nd example of BIOS, simpler, where the "Boot Mode" parameter  allows one to choose the boot mode ("UEFI" or "Legacy") for all media  (hard disk, CD, USB...) at the same time. .  

Since my computer does allow this, that gave me the idea that it would be ok to set to Legacy Mode and then install.

And also, now that I don't have windows anymore  I'm not sure if it really matters if I have UEFI enabled or not.

I will be off line all day tomorrow but will resume the day after with your instructions as you posted unless you give me an update.  Thanks again,

TM

---

### Post by DuckHook on 2013-02-21
It is perfectly fine to install and boot into legacy BIOS mode. If so, then you must make sure all BIOS settings for HDD are set to legacy (or your mobo's equivalent), and the LiveDVD is not booted in UEFI but legacy as well. You won't need to install the small 200MB EFI partition either. Excise my instructions on UEFI and the rest should still be valid.

If you install future OSes, you must make sure to install them as legacy also.

Good Luck, and let us know how it goes.

---

### Post by thomas2013 on 2013-02-22
I think we can declare installation success with the following postgame comments:

1.  At no time was my computer ever able to run the LiveCD with the Boot Mode set to UEFI.  No matter, I used legacy, but it still bugs me since all forum/help docs imply that the UEFI mode should work.

2.  I followed your prep/partition/install instructions faithfully.  The install went ok but at no time was I ever presented with an "Install GRUB"  dialogue box.

3.  After the install, and re-boot:  At the menu simply choosing Ubuntu resulted in a non-boot frozen screen situation.  After a hard re-boot I chose Advanced Options > Recovery Mode > Resume Boot.  Finally, this allowed me to boot into Ubuntu from the HDD.   Hooray Hooray.  Sometimes ignorance works just fine.

4.  After installing software packages etc.  I seem to be ok booting up as long as I make sure to log out of a session and then restart manually.   Choosing Restart without logging out results in the frozen screen situation as described above.  Minor annoyance.

So I think we can declare success and mark this one solved.  I'd buy you a beer, but a simple thanks will have suffice.

TM

---

### Post by DuckHook on 2013-02-22
> **thomas2013 said:**
> At no time was my computer ever able to run the LiveCD with the Boot Mode set to UEFI. No matter, I used legacy, but it still bugs me since all forum/help docs imply that the UEFI mode should work.

UEFI is a relatively new technology and some vendors haven't worked all of the bugs out of their implementation yet. If you bought your box at about the time their BIOSes were initially changing over, I would not be surprised if it had some bugs. Sometimes a bios update will clear things up. It is also worth checking to see if fastboot was enabled. If so, then on some systems this will bypass UEFI checking, but I don't see why this would affect a LiveCD. Anyways, my rule of thumb is usually to leave well enough alone.

> After installing software packages etc. I seem to be ok booting up as long as I make sure to log out of a session and then restart manually. Choosing Restart without logging out results in the frozen screen situation as described above. Minor annoyance.If your shutdown freezes, it is a good idea to track down the cause and squish it. You are right. It's a minor annoyance, but it offends my sense of propriety. You have no pressure anymore, so take your time and do this at your leisure. This forum is very helpful on such matters. You can see what is happening behind the frozen screen by pressing the <Esc> key during the shutdown process. This will often give you a clue about what specific part of the shutdown process is hanging.

> I'd buy you a beer, but a simple thanks will have suffice.It's a pleasure to help. Only you can mark the thread "solved" by choosing this option at top of thread in "thread tools". Virtual beers are much appreciated. Less filling and low-cal.

---

### Post by oldfred on 2013-02-22
Some systems work with UEFI and some have issues. A few just do not work.

       Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)
    
       Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries
Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

---

### Post by GrouchyGaijin on 2013-02-22
> **thomas2013 said:**
> I think we can declare installation success with the following postgame comments:


4.  After installing software packages etc.  I seem to be ok booting up as long as I make sure to log out of a session and then restart manually.   Choosing Restart without logging out results in the frozen screen situation as described above.  Minor annoyance.

TM

I wonder if the shutdown problem is related to this:
[http://ubuntuforums.org/showthread.php?t=1968376]("http://ubuntuforums.org/showthread.php?t=1968376")

---

