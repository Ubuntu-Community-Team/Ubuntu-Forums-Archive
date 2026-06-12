---
title: "Ubuntu on Windows"
date: 2020-05-06
forum: New to Ubuntu
---

### Post by ivatt1815 on 2020-05-06
I have a need to copy down files from my Ubuntu to W10 as I am setting up new hardware.

I have looked at various suggestions using Terminal commands all of which seem a bit too complicated for me with my limited Ubuntu knowledge. There were a lot of articles talking about Samba which got me lost.

Then I came across and article talking about The Windows Subsystem For Linux and I found Ubuntu in Microsoft store. I installed this (using my user name and password from Ubuntu) and have it as a tile and when I click I go into a Terminal window.

The same  site has an interesting article which seemed to be in my language, if you get what I mean, [https://www.tenforums.com/tutorials/127857-access-wsl-linux-files-windows-10-a.html](https://www.tenforums.com/tutorials/127857-access-wsl-linux-files-windows-10-a.html)
which I have tried to follow.

If I type explorer in the Ubuntu terminal window it brings up my Windows Explorer, so that seems to work but I can't get into my Ubuntu account. When I look at File Explorer I don't have any entry for Distros as the link states.

Have I misread what I can do or am I doing something hopelessly wrong or missed something.

Thanks

PS Should have said I dual boot with W10 and as yet I haven't reinstalled Ubuntu. I have some settings and files in Ubuntu I want to retain and I don't know if I reinstall with the same id and password if they will be retained so I would like to copy some files off Ubuntu and keep them on Windows until I reinstall Ubuntu, just in case.

---

### Post by CatKiller on 2020-05-06
If you're dual-booting, anything that you do within Windows (including installing a second copy of Ubuntu within WSL) is completely independent of your Ubuntu install.

It's actually relatively straightforward to mount your Windows partitions from within Ubuntu to copy files to them, since being able to read Windows filesystems is useful enough that people have reverse-engineered the way to do that. Going the other way is much harder, since Microsoft like to pretend that non-Windows filesystems don't exist, although I understand that it is still possible.

Much easier would be simply copying the files that you want to keep (optionally putting them in a tar) onto a USB thumb drive or similar.

---

### Post by ivatt1815 on 2020-05-06
Thanks WSL?? I can see my Windows folders in Ubuntu but if I try to copy all I get is the drive is read only. One I need is my x-plane installation but that is too big to go onto a USB thumb drive as it's nearly 80GB and my biggest is 64GB. I will take another look and see if I can break the folders down so I copy a few at a time. Also whether a tar file would be small enough, what about a zip file as an alternative?

If I am reading you correctly if I do a fresh install of Ubuntu then even if I use the same id and password nothing is brought across so I would lose the changes, mainly in rules, which would be a real pity as it took some time to get them right.

As I said I am a novice with Ubuntu so really don't know what I can or cannot do, or how to do it for that matter.

---

### Post by crip720 on 2020-05-06
Windows has a 'FastBoot' option turned by default.  This puts windows in hibernation instead of a complete shutdown.  Reading/writing to windows from Ubuntu in this state is not good.  Can turn off fast boot in windows and then can copy.  You say set up new hardware, can you explain better so we have better understanding, you might just need a cable or external drive enclosure and copy everything over after.

---

### Post by CatKiller on 2020-05-06
As crip720 says, you've not given us much information about your setup, or what you're trying to achieve.

> **ivatt1815 said:**
> Thanks WSL?? 

Windows Subsystem for Linux. You brought it up. It's a VM-like part of Windows so that you can do Linuxy things. Installing Ubuntu in that would be completely unrelated to your (presumed) Ubuntu install that you're trying to back up files from.

> I can see my Windows folders in Ubuntu but if I try to copy all I get is the drive is read only. 

When trying to access files on a partition, you need some route to access them; a mount point under Linux or a drive letter under Windows. There are plenty of reasons why a Windows partition might be mounted read-only, ranging from the dirty shutdown of Windows that crip720 mentioned, to simply having the incorrect options selected. If you gave details of the specifics of how you were trying to mount your Windows partition, someone might be able to help you.

> One I need is my x-plane installation but that is too big to go onto a USB thumb drive as it's nearly 80GB and my biggest is 64GB. I will take another look and see if I can break the folders down so I copy a few at a time. Also whether a tar file would be small enough, what about a zip file as an alternative?

The advantage of tar is that it will maintain permissions for you even when the underlying filesystem (such as FAT) has no understanding of them, and frees you from having to worry about things like file size, or which characters (and how many) are used in file names. Compression is optional, and not the main advantage. For a bunch of files from one user's Home folder, created by a cross-platform game, these things are probably not an issue; file transfer from other places can cause Windows filesystems' limitations to be really painful. .zip files may well have these same advantages - I have no idea.

> If I am reading you correctly if I do a fresh install of Ubuntu then even if I use the same id and password nothing is brought across so I would lose the changes, mainly in rules, which would be a real pity as it took some time to get them right.

From the information that you've given, you (presumably) have some Ubuntu installation that you are trying to preserve files from for some future (not really specified) endeavour. You have (maybe) installed a different version of Ubuntu within Windows' VM solution which, yes, is completely unrelated even if you used the same username and password. At some point you are planning to install a new version of Ubuntu - somewhere - which will also be completely unrelated to your existing Ubuntu install.

The scenario that's similar to where you appear to be coming from is that *if your /home partition is separate from your / partition* doing a fresh install of Ubuntu *without formatting your /home partition, and with mounting your /home partition at the new /home* then creating the same users with the same names in the same order will automagically give all the users their settings and files when they log in. You've not given any indication that that's the situation you're in.

That also wouldn't preserve any changes that you'd made to the hardware detection rules. Since you're interested in the files from a flight-sim and you're talking about rules, I'm guessing that you've created some custom files for your input hardware; you likely created them in /etc/udev/rules.d, and they're just text files. You can copy them somewhere and then copy them to the same place in your new installation.

Having backups of your important files that you can restore is an important capability even when you aren't planning hardware upgrades. Neither hard drives nor SSDs will last forever, even in the absence of fire, flood, lightning, or children putting Summer Fruits squash in your computer.

---

### Post by TheFu on 2020-05-06
Zip doesn't retain file metadata that tar does. That metadata includes the owner,group,permissions,ACLs, and xattrs.  You don't know that you need them until it is too late and you don't have them.  if you just need the data and are positive the other metadata isn't needed, just copy the files off using any method you like - samba, sftp, usb flash storage, NTFS USB HDD, ext4 HDD, whatever.  There are 50 others too.

But 1GB really is too large for tar or zip, even if people use it that way.  They were designed when 500 MB was considered HUGE. 

Really, a backup solution and storage are needed.  $40 gets a 2TB USB3 external disk, so there really isn't much excuse NOT to have proper backups today. There must be 50 backup tools for end-users on Linux.  Back-in-Time is easy, but the target storage must be native Linux, not Windows exFAT, FAT32, NTFS.  This requirement is to maintain the metadata about the files.

Lots of good advice above.

Cannot help with WSL.  Never seen it. Sorry.

---

### Post by ivatt1815 on 2020-05-07
Thanks for the replies. By way of clarification my situation is that on my old PC I had dual booting between W10 and Ubuntu 18.04 with Ubuntu as first boot choice. At some stage whilst trying to change boot option so that W10 would be first choice I managed to corrupt/delete the grub mbr but after some messing about I got W10 mbr back. The only way then I could access my Ubuntu was through super grub.

The changes in Ubuntu referred to were to make my Saitek panels for x-plane work correctly. This was done with the help of members of x-plane.org and took sometime as I had to follow verbatim the instructions given to me and to my best knowledge this meant writing rules for the Saitek products. I have a separate x-plane install in Ubuntu as I was told this would work better with my system at that time.

I now have a new PC which I am setting up and I have a 200GB SSD on which I have W10 installed and a partition ready for Ubuntu but **I have not as yet installed Ubuntu**.I was told  that if I did a fresh Ubuntu install and used the same id and password this would transfer over the rules I had set up in the original install but this seems not to be the case.

I have x-plane running in it's own partition on a 2TB SATA drive and am planning to install x-plane through Ubuntu (when installed) in a separate partition so I end up with 2 x-plane installs, one Windows and one Ubuntu.

The original Ubuntu install is bigger than the SSD partition available because I think it includes x-plane which is 140GB so I was hoping to transfer the Ubuntu x-plane across to spare space on the SATA drive so I would have it in tact. I should mention that whilst setting up the new PC one of my SATA drives failed and this was my working W10 drive and had all my latest x-plane setup on it. I have a Macrium image but this is not current having been done before all the latest changes to x-plane.

If I can transfer x-plane out of Ubuntu then that would solve one problem but there still remains the changes I made in Ubuntu which as I say were I think in rules that I need to copy over to a new Ubuntu install. I do have all the exchanges on x-plane where i followed the instructions but this would take time to make sure I only made such changes as necessary as there were one or two abortive attempts in the process.

I hope this clarifies my situation.

I should also mention that as I have said I would prefer to have W10 as the first boot option preferably with the W10 mbr but if not grub.

Once everything is back and working correctly the first order of th day is a Macrium image, I have learned in the past how useful they are.

---

### Post by CatKiller on 2020-05-07
A couple of things that should make your life a bit easier:

UEFI/GPT for both Windows 10 and Ubuntu is much easier than BIOS/MBR. It lifts the four partition limit and means that you don't have to chain bootloaders: as many as you want can just live in the EFI System Partition (ESP).

The Live Ubuntu installer is a fully functional Linux environment; if you have trouble booting into your existing Ubuntu install, you can do anything you need from the installer instead. 

From your description, the rules you created should be at the path I mentioned, so you should be able to examine them and copy them wherever you like for safekeeping. And ultimately put them in the right place in your new install. 

As I understand your description, you're having Windows 10 and Ubuntu on an SSD, leaving your old HDD spare. In which case, you wouldn't need to fit two copies of your large data on your small SSD: you could continue to use the HDD as well. Either having a /home partition on a HDD or having a flat data partition (or several!) on a HDD are relatively common configurations. You'd have to decide for yourself which would best fit your needs, and you'd still need to do *some* data shuffling (but only on the one drive rather than squeezing it all into the small one) to get things tidy, and you'd need to familiarise yourself with mount points and mount options - but that's useful knowledge to have in any case. There is the possibility that you'll accidentally delete everything, but as long as you're paying attention to what you're doing you should be OK.

You can mount a partition wherever you like within the Linux filesystem tree - you have a lot of flexibility for how you approach things there. You can also add or resize partitions however they would best suit you - with the caveat that you can't fiddle with a mounted partition, meaning that's the kind of operation that's often best done from within the live installer. When you're, for example, putting entries in your /etc/fstab it's best to use UUIDs rather than device paths, since those paths can change but the UUIDs won't. There's lots of information available about how to find UUIDs, and mounting partitions, and so on.

I'm pretty sure that Grub's OS menu order is fairly straightforward to configure - especially if you're using UEFI - but it's not something I've personally done. I haven't used Windows in a very long time.

---

### Post by ivatt1815 on 2020-05-07
Thanks fast boot already disabled.

---

### Post by ActionParsnip on 2020-05-07
Make sure the NTFS is consistent by running a Windows chkdsk in Windows. The NTFS access you are enjoying is a best effort attempt as only Microsoft truely knows how NTFS works. It is a proprietary file system

---

