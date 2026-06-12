---
title: "Ruined Windows loader while installing Ubuntu 14.04"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by Catenaccio on 2014-04-25
I involuntarily screwed it up when trying to install Ubuntu, I need some help to recover now my Win7 loader. Short story:

Using a USB "live cd", after testing it a little bit in my notebook, I decided to install Ubuntu. My notebook has 2 HD, one had Win 7, the other one was storage. Ubuntu offered to install Ubuntu in the second one, but I wanted to have the to OS in one HD, and leave the second one just for storage. 

I had installed Ubuntu 12.04 back then in another older laptop that I had (just one HD) and I've done it with no problems at all, using the same USB-liveCD method. I had been able to re-size the HD, make 2 new partitions (one for Ubuntu, the other one for the swap file) and everything had worked wonderfully, so I thought it would be even easier this time. Wrong.

I realize now that my mistake was to think that I was re-sizing the first HD but apparently I didn't; I just created a half-size partition ext4 and left the other one empty. Important clarification: I NEVER COMPLETED THE PROCESS, I DID NOT FORMAT THE HD, I just pick the option that was given to create a new partition or something like this and, in the next screen, when I realized that the W7 loader had disappeared, I tried to revert and, when unsuccessful, I just cancelled the whole process, so I think I only wrote something in the first HD's index or something like that but I don't think I've deleted anything regarding the information.

I have thought as Plan B to install Ubuntu now on the second drive (as offered initially) and then try to recover the other HD. My question is:

Is there a way to restore the first HD to its original state or, at least, to recover access to its original content? I had backed up most of the relevant information but still I'd like to recover the HD as it was instead of starting from scratch.

Thanks in advance!

---

### Post by WoodenWalker on 2014-04-25
Do you have a Windows 7 install disk? And how recently did you upgrade the system to Windows 7? Can you post an image of your screen during boot time? Thanks in advance.

---

### Post by Catenaccio on 2014-04-25
Hi!
I think I have some Win7 disk, not sure if it's the original installation disk or a "recovery disk". My notebook is home and I am at work now, that's why I cannot confirm. The win7 I had was the one that came installed with the computer, I never change it. The system upgrades were set to automatic, last time was yesterday night (some basic update).

I can try to upload later a boot screenshot, but I can tell you right now what it says: after the first screen (the one showing an Asus logo, my notebook's brand) it goes directly to a black screen and one sentence "Missing OS". If I restart and press "ESC", I can have access to the boot menu and make the notebook to boot on the USB-Ubuntu.

---

### Post by WoodenWalker on 2014-04-25
When you access the boot menu I'm assuming it still has a listing for your hdd, correct? If so, you will most likely need to use your recovery cd that came with the computer to fix your MBR prior continuing the Ubuntu install. (Assuming you wish to have a dual-boot setup) Did the manufacturer send you a recovery disk, or just store it on the system?

---

### Post by oldfred on 2014-04-25
If you overwrote the partition table, you probably have to use testdisk to find old partition table and restore it.
Windows is very particular, so whether it will work or not remains to be seen. If not other data was written it may be ok.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

      
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

I do prefer to have Windows on one drive with its boot loader. And Ubuntu on another drive with its boot loader.
Then when (not if) one drive fails you can still from BIOS boot the other drive.
And you then can copy some data from Ubuntu drive to Windows drive as backup and vice-versa. Full backups still required.

---

### Post by debsid on 2014-04-25
What happens when you boot on the first hard drive? Do you see any error message?

You need to make sure the system partition is still intact before recovering the loader. Try booting on the Windows disc, select "repair my computer" and see if it can detect your Windows partition.
Then, proceed to the command line and type:
bootrec / ScanOS
Can it see your Windows partition? If yes,
bootrec /fixboot
bootrec /fixmbr
should fix the loader. You can also try bootrec /rebuildbcd

If it can't see anything, try using diskpart, then list disk, list partition and list volume. If it can find your Windows partition, you can mount the volume and use bootrec to fix the loader from there.

As suggested, it would be wise to install winload on one disk and Grub on the other, so your setup is more dependable.

---

### Post by Catenaccio on 2014-04-26
Thank you all. 

Apparently, when I screwed it up, even without doing much, I screwed it up badly. 

First of all, on the Windows side, no, unfortunately, I don't have a recovery or install disk. It came already installed, and that's it. I had an old recovery disk for my old laptop (Windows Vista), but it only gave me the option of installing windows right away, no repair or something similar. 

Then, I tried testdisk. It was complicated because I didn't have anywhere from to run it (my Ubuntu 14.04 live cd didn't allow me to install it), but I eventually created a Unbuntu Mix Rescue CD that I found in a link in the TestDisk webpage and, booting from there, I managed to run the utility.

But, unfortunately, to no avail. It did not found out the Windows partition, it found a FAT32 boot info and backup, but it claimed both were "bad", so, again, I was not able to recover anything. There were a couple of deleted partitions, but they were all Linux ext4, no news from my old windows partition, gone with the missing Malaysia airplane. 

I am running TestDisk a second time, just to see if I may rescue something. 

Thank you all of you for your help, it gave me a chance, but it seems I'm beyond salvation. I'll keep you posted on the final outcome.

---

### Post by oldfred on 2014-04-26
If you have some files that you did not backup and they are essential, testdisk also includes photorec. It can recovery many types of files as long as they were not overwritten.

But it is a very long process as it just scans drive for anything that looks like a file. And it does not recover file names, just extensions, so you have to review many files to find the ones you want. For me it also found some text files I had saved many times and found all the old deleted ones. So I had to sort thru them, compare to last backup and try to add or delete the changes I made in the recovered files. Long process.

       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)

---

### Post by Mark Phelps on 2014-04-26
My own advice is to use Windows data recovery apps to restore Windows partitions  and/or files.  

To try to restore the partitions, download and burn a CD of the Minitool Partition Wizard Boot CD.  Boot using that and see if it offers you the option of recovering the partitions.  If it does, try that and see what happens.

If that does not work and you still need your files back, and you're willing to spend some money to do that, let us know and I can direct you to a site to purchase a Widows data recovery app.

---

### Post by Catenaccio on 2014-04-27
Thanks Mark,
Unfortunately, by the time I read your post, I had already decided to start from scratch. A friend of mine gave me his copy of Win7 (he updated to Win8 so he was not using it anymore) and I installed from scratch. I tried before the recovery utilities that that disk had, but they were similar to the one I used, again to no avail.

Thank you all in any case. I had saved my files, I just wanted to save myself the tedious process I am right now: re-installing all W7 updates and then the soft I had (MS office and so). The good news is I&#314;l have a very slick version of W7 and just with the software I intend to use in W, which is little.

No, question for everybody:

What really pissed me off is that when I installed Ubuntu 12.04, as I said, in one notebook with just 1 HDD, it was all great, I coudl re-size and create a new partition (actually, 2, one for Linus and one swap file) without affecting windows. 

I thought U14.04 would be the same. Wrong. The set up menu is not intuitive at all. I just wanted to re-size the windows partition in the first drive, install linux there, and use the second HDD as data for both OSs.

Now, everybody recommends me to install U14.04 in the second drive, but after my experience with this I am puzzled: I am afraid that I might screw up similar to what happen with the other HDD (at the end of the day, to install U14.04 in the second drive I'll have to re-size the current partition and create 2 new for Linux and the swap.

So, is anyone familiar with the new installing system of U14.04 and, thus, why in the damn world I can just resize and create partitions as easily as with the previous version?

---

### Post by oldfred on 2014-04-27
Both Mark & I consistently suggest using the Windows own partition tools to shrink the Windows NTFS partition and reboot Windows so it can run chkdsk and fix up what ever it needs before using gparted to create new partitions or just using installer to create partitions.

And I typically link to one of Mark's posts on using Macrium Reflect to fully backup Windows. 

And you should always have a current version repair CD/DVD/flash drive for every system you have installed. You can easily make a Windows repair tool from Windows when it is working, but it costs a lot to download one after Windows breaks and you do not have one.

Some report that the installer works and it just about worked all the time with older XP installs. But since Windows 7 we get a lot of posts about Windows issues after install.
Windows NTFS partitions do have partition start and size info in the NTFS PBR or partition boot sector that must match partition table or it will not work. Chkdsk normally fixes that.
But if chkdsk flag is set or hibernation file flag is set the Linux NTFS driver will not mount and may not correctly see the NTFS partition. And there are other reasons for issues like where Windows incorrectly converts a gpt drive to MBR(msdos) and others.

There does seem to an issue on re-installs on systems with Window 8. It may offer to over install Ubuntu and not mention Windows and then erases entire drive. 

I have always had concerns about any auto process. So I normally partition in advance with gparted and then use Something Else and manually install to those partitions. But I am not using Windows anymore.

Often best to use Windows tools for Windows and Linux tools for Linux.

---

### Post by Catenaccio on 2014-04-28
OK, for everybody's knowledge, the end of the story:

After I re-install W7, I decided to again try to do what I intended first. I know that everybody recommended to put one OS on each drive, I got it, I just wanted to figure out what the h... I did wrong the first time (with absolutely nothing to lose now).

So, I think I know now: when you pick the "Something else" option at the beginning, when Ubuntu is showing the installation options, you're shown the list of drives and its inner partitions. So, I intuitively picked the already created Windows partition (that was OK) and click on change (that was OK too). The next thing was the mistake: I thought (wrongly) that I could use that option to create the new Linux partition along the old one, because it gives you all the options in blank (so, I thought it was asking me for something new). So, what I did was to tell the installer that I wanted a 250 GB partition for Linux in ext4 format... which the installer created, leaving another 250GB blank (it's a 500 GB blank) and completely replacing the original 500GB NTSF partition. That killed everything.

This time, realizing what I did, I click in the 500GB NTSF W7 partitiion, change, and when all the blank options came up, I just picked 250 GB, NTSF, leave the rest blank, good to go: the old partition was reduced to 250 GB, windows still there, and I was able to usu the 250 unallocated GB to create a 240 GB Linux partition plus a 10GB swap file. And that was all, it all went OK, I'm right now double booting with both OS in one HD and all the data in the other one (which I don't if it's the best set up, it's just what I intended to do first).

End of story, I think what made impossible to recover the original partition was that I (involuntarily) replaced it by the new ext4 before reducing the size of the original one.

I know that this happened to me because I was not expert enough to use the "something else"  menu, but all of you, guys in Canonical: if one picks the "install next windows" (or something like that) option, it takes you to a BEAUTIFUL graphical screen when you see the HD and color bars showing you how it's going to be parted and you can edit every bar and get for each drive the size you want, and it's so graphical that you know what's going on... Why don't you just to the same for all the drives in the "Something else" option?????

Thank you all who tried to help me here!!!!

---

