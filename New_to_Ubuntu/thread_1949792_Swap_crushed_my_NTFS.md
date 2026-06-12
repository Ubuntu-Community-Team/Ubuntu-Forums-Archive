---
title: "Swap crushed my NTFS"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by CADILLAC1960 on 2012-03-30
Hi All;
 
OK, I am late to the party here (should have been on Linux years ago), and my first experience is giving me some grief. Hopefully someone here can help me recover.
 
Downloaded the XBMSubuntu distro, and created a flash drive to install. Took that drive to the target computer (Dell Studio 1737 laptop) and booted to it. All went well. Came time to install and I chose a partiion on the 2nd drive in the system (10 GB partition). It then asked me for a "Swap" partition, and I figured it would be OK to use the main partition on that second drive, even though it was NTFS formatted and I wanted to keep that data. Figured SWAP would just use space that was free and would not need to format.
 
All installed great, and I had some fun playing with the XBMS, but when I then rebooted to go to my Win 7 install, I could no longer see the 2nd drive.
 
I have downloaded Boot-Repair-Disk and tried to fix using this tool, but I am now seeing that the format of my large partition is now Swap v1.
 
Is there any way for me to recover what was on my NTFS partition prior to this stupid move on my part?
 
Any help appreciated.
 
Thanks
W

---

### Post by oldfred on 2012-03-31
How much memory do you have? If you do not have much memory or loaded a lot of programs and used swap then it overwrote your NTFS partition.

You can try testdisk, if you did not use swap then it may work. If testdisk does not work, then you may be able to recover some files with photorec but it is a huge, huge task. I have used photorec and got files back but it was days of work for just a few files.

Always when reconfiguring systems have good backups.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
As described, it has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS. 
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by CADILLAC1960 on 2012-03-31
Thanks for the reply oldfred.  I really appreciate you taking the time to try and help me out.
 
As for memory, 4 GB.  Did not really do much when I loaded the ubuntu, just poked around really.  Set up NO libraries or anything and loaded absolutely no additional programs.  Hoping I can recover.  98% of that drive is backed up in two other locations, so I am only after the 2% that was added over the past two weeks or so, and I know it is less than a dozen files I care about.
 
I will look through the threads you have kindly provided and do what I can with the recommended tools and guides.
 
Thanks again for the assist and if you or anyone else has additional suggestions, I am open to other ideas/solutions.
 
Cheers~
W

---

### Post by CADILLAC1960 on 2012-03-31
OK, here is where I am at.
 
Downloaded TestDisk and ran with admin priveleges. Followed the closest instructions I could find for my scenario, which involved trying to change the partition type, but could not get it to work. It is listed as a Swap Linux partition type and I could not get it to change to a NTFS partition type (I did choose "Create" log file when I started the prog, but I am not sure where it is stored - if I need to find it, I will and pass on). 
 
I then ran the cfdisk from a terminal window in ubuntu, and did some commands to try and change the partition type there (it was listed as Bootable and Swap Linux, had a * next to it as well). It would not take my changes (and yes I did select "Write" when done making the mod). I also restarted after these changes per soft request of cfdisk and still no NTFS.
 
I also tried using some command line prompts to modify and mount this drive partition (sdb3), no luck. 
 
I then read about someone who removed drive, put in external enclosure and was able to fix with Partition Table Doctor. I did just this and Partition table doctor said it could not modify a "Dynamic Drive" which is what win 7 was seeing it as in the usb external enclosure.
 
Don't know if this helps, but here is a breakdown of this drive:
 
320 GB laptop drive
sdb1 Partition 100MB FAT16 or FAT32 - can't quite remember, win 7 recovery partition
sdb2 Partition 10GB Partition that I installed Ubuntu to (can't remember if Ext3 or 4)
sdb3 Partition 278GB Partition - Was my win 7 system partition and storage partition, now marked as Swap (but still with a * and Bootable)
 
So, still not seeing what I need to see, and if anyone has suggestions, I sure would appreciate.
 
Cheers~
W

---

### Post by oldfred on 2012-03-31
I think you can go deeper into testdisk. 

You also be able to change to type 07 (NTFS) with Disk Utility. Edit partition, change type. I do not think that formats it but just changes partition table.

Testdisk normally finds all the old partitions and multiple versions of the partition layout with different formats.

Testdisk also has a function to recovery the backup NTFS boot sector, but you have to have changed it to NTFS first. Testdisk can also create a new NTFS boot sector, but I think it makes the old XP version and you have to then use a Windows 7 repairCD/USB to run the fixBoot.

You can also change type to 07 with sfdisk. Since you are not changing partition sizes it is a bit easier.

First backup partiton table
sudo sfdisk -d /dev/sda > parts_sda.txt

Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)
Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)

---

### Post by CADILLAC1960 on 2012-04-01
Hey oldfred;

Thanks again for all you help on this.  I do not have it yet and am hoping you can guide me to my next step.  I have attached a print screen of the drive in question.  I had done a "Deep Scan" and this is what came up.

When I try and look at the "List of files", I do  not see my files listed.  Yesterday, first time I did the deep scan, it did show the old users, but that is gone now (perhaps it was my attempts to Recover Boot sector or something).

Anyway, I can not make heads or tails of where I should go next with these results, and it does take about 1.5 hours to generate this deep scan report, so hopefully I will only need to do it once more after I have some instruction on what to do with it from here.

BTW, I have worked through the links you have given me and appreciate them.  The solutions there have not yet produced the results I am looking for when I have tried to implement them.

Your help is greatly appreciated.

Thanks
W

---

### Post by oldfred on 2012-04-01
You are now showing all partitions as D - deleted?

I would change your NTFS that you have highlighted as it shows the same start & ends as swap. But you show a 100MB Windows boot partition, the 204800 sectors and that is normally a Windows 7 boot/repair partition that should have boot flag. Did you have a separate Windows 7 boot partition? It would usually be hidden in Windows so you do not normally see it. Should not everything but the old swap be undeleted, except where you have overlaps and that is from changes some where. If one overlaps I never know which then is correct. 

It does say it sees the backup boot sector which at least sounds good, but that deep search now does not find anything is not so good. You maybe should have copied files at that point. 

If you think deep search takes a while wait until you try photorec (hopefully you do not). On my 160GB drive it was 6 or 8 hours, but it found just about every file including the ones I had saved many times. That made for a huge sorting task.

---

### Post by CADILLAC1960 on 2012-04-01
Hey oldfred;

Thanks again for taking the time to get me back on track here.

OK, the drive originally had the 100 MB hidden win 7 partition, a 10GB partition and the ~280GB partition, which contained Win 7 and storage.

I tried to install XBMCbuntu to the 10GB partition, and mistakenly chose the 280GB partition as my "Swap" partition (I now know better).

If XBMCbuntu gets completely wiped, I don't care.  Nothing there.  If I don't get back the win 7 boot, I don't care.

Just focusing on getting the data back off of the 280GB partition.

So do I need to change any of this stuff before I run photorec or can I just start that process?  Do I need to do the "Un Delete" on the partitions as you suggested before I go to photorec (deep scan window still open so I can make changes without the long deep scan wait time)?  Also, how do I know which of the large partitions to recover (3 listed, two are ntfs, one of those says "Can't open filesystem.  Filesystem seems damaged, the other of the NTFS lists Bootsect.bak and Users, Users does NOT have the users that were there previously)?

BTW, I would have copied, but all it showed was the "Users" folders, and I store no data in Windows usual file structure (i.e. my pictures are NOT stored in My Pictures of a specific user), so all I could have recovered from what was listed at that point would have been cached files, browser history, application data and stuff like that.

Thanks thanks thanks for the help.

Cheers~
W

---

### Post by CADILLAC1960 on 2012-04-01
Hey oldfred;

OK, a little research indicated to me that I do NOT need to restore these partitions before I use photorec.  I have started that process and it is chugging along recovering files.

Will post once it has completed (currently looks like about 6 hours for it to do it's thing).

Thanks again for all the help.

Cheers~
W

---

### Post by oldfred on 2012-04-01
Photorec recovers anything that looks like a file on the hard drive. It only recovers the extension or file type based on its analysis of what it found. I had it recover deleted files and sometimes fragments that happened to be next to each other.

Some files have internal data that you can use to rename like music & photos. After my experience I put a file name in every text, script or .py file I create.

Some tools to help:
Use scripts to help sort files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by CADILLAC1960 on 2012-04-02
Kudos to yudos oldfred.  You already anticipated my next, and hopefully final, question on this topic.  I have some file bulk rename utilities I use in windows, so I think I am going to bounce over there and work with these recovered items rather than go through another learning curve (have been on a fairly steep one since Friday or so).

Anyway, about 200,000 files recovered.  I am sure whatever I need is there.

Good tip on the "use text in every file name".  I will try and tag my files best I can.

Thanks again for all the help and time you have given me on this topic.  Hopefully I will be able to contribute to the forum in the years to come.

Cheers~
W

---

### Post by CADILLAC1960 on 2012-04-02
Well 223,798 files recovered, 735 of them mp3, but NONE of them the ONE I was looking for.  Must have been because it was such a recent addition to the drive that the location on the disk was vulnerable.  Oh well.  Learned alot (including how to not make such a stupid decision again) and recovered some other files.
 
Thanks again oldfred ;~))
 
Cheers~
W

---

### Post by Bucky Ball on 2012-04-02
Perhaps you can get things more in order by resizing some partitions (NOT Windows with Ubuntu's Gparted).

To do so you need to boot from a LiveCD, Try Ubuntu, open Gparted. That way all partitions will be unmounted. You can delete /swap or make it smaller and create another partition also.

If you have four primary partitions a problem. You need to create an extended partition as the fourth and put logical partitions in that.

---

### Post by CADILLAC1960 on 2012-04-02
Well as a last ditch effort, thought I would give it a go (photorec) from within Windows 7 and got what I needed. Turns out that photorec found over 10,000 mp3's before I stopped the process (it had found what I wanted), and had found only 735 when I ran it from command line in ubuntu. I am sure that in other cases the scenario may be reversed. Whatever the case is, I would recommend to users of photorec (and searchers of lost records), try and run this program in it's different versions on different OS's. RESULTS WILL VARY (at least they did in my experience). Other than that, I think this program does a really good job at what it does.
 
If I had recovered the partitions first, would photorec have recovered the items with their original names and folder structure or would it still have been the fxxxxxxx.xxx naming convention? Or is there a photorec setting to try and recover file structure and file name information?
 
Thanks again oldfred and all others who help out here.
 
Cheers~
W

---

