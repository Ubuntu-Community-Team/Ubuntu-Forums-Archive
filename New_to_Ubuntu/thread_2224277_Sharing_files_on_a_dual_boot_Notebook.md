---
title: "Sharing files on a dual boot Notebook"
date: 2014-05-15
forum: New to Ubuntu
---

### Post by gordon99 on 2014-05-15
I am still trying to learn of problems I might face when I install Ubuntu 12.04 alongside (dual boot)my present OS, Windows 7, on a HP Compaq notebook. 
I would like very much to learn if I will be able to open and edit all files in both Windows and Ubuntu. I may have read that this requires all the files to be in the "C" drive  NTFS partition. Is this correct? If it is, what do I have to do when installing Ubuntu to ensure files raised in Ubuntu go into the shared partition?
If a shared partition is not necessary or maybe even not best, are there good alternatives that are easy to set up and work with? 
Apologies again for what I guess are pretty basic questions.

---

### Post by LastDino on 2014-05-15
Why not 14.04?

Not in the ''C'' drive particularly, anywhere as long as it is NTFS partition its fine. Umm just leave one partition as logical and format it as NTFS (Mind you,storing on C: works too but it is usually better to not access main drive of other OS installation with different OS). You need to pick ''something else'' when installation asks for it and make those partitions; both required by Ubuntu and this extra storage NTFS one. 
Linux requires following partitions:
/ = root, size should be around 20 GB. Format it to ext4.

/home = if space on  HD you're willing to assign under ubuntu is bigger than 40GB, feel free to make this one and it is usually bigger than ''/''. Otherwise you can simply not make it and installation will automatically make your home directory in your ''/''. This should be in ext4 as well.

SWAP = This should be generally equal to your RAM. If RAM is more than 8GB and you've no plans to hibernate, you can forget about making this too. If you do need (usually you do) to make it, simply assign it as ''swap area'' and it will be taken care of automatically.

And one extra partition formatted to NTFS. This will be your storage drive. 

Tool used for formatting during installation is G-parted, it is advised that you look up how to use it (even though you can easily use it with basic knowledge of partitions). Also, make sure not to select ''replace'' option while installing, that will erase everything on your HD. Please, take backup before you start doing this whole thing. 

Good luck!

---

### Post by newbie2244 on 2014-05-17
When you say all files, do you mean documents? If so, then Ubuntu.Linux will allow you to see to all docs, even those created under Windows7. But Windows7 will not be able to see docs created in Linux.

---

### Post by gordon99 on 2014-05-18
Thank you LastDino and newbie for your responses to my enquiry. I intend to consider 14.04, which I have only recently become aware of, as I understand it will have long term support.

On the subject of creating partitions,  I will have to delete either the 'Recovery' partition or the 'HP_Tools' partition as all four partitions are occupied on my Compaq Notebook. I do have DVDs for recovery which I made when the Notebook was new three years ago but one reads conflicting advice as to which partition to make available for Linux. My inclination now is to delete the 'Recovery' partition but I am not not at all certain that this is the best option. I will also have to shrink the 'C' drive to make more space. I understand that although I should use G-parted to create logical partitions for Ubuntu I must use Windows Disk Management to deleted any existing partition and shrink 'C' drive.

Perhaps you can tell me if I have to combine the freed up disk spaces formed when I shrink 'C' and delete Recovery or Tools partitions before I commence the installation of Ubuntu. If I do what does this involve?

What files go unto /home and what go into storage drive? What is a 'data' partition or is this just another name for storage? I suppose I am confused because everything in Windows just seems to go into 'C' drive without having to bother about / (root) , '/home', 'swap' or 'storage' etc.

I gather it is not advisable to work on documents in one OS (say 'C' drive) using another OS. However, am I correct in my understanding that any document produced in Linux and placed in a NTFS formatted logical partition would not be readable in Windows OS but any such document produced in Windows would be readable (and editable) in Linux?  I assume this document however, if edited in Linux, would not be readable any more in WindowsOS.

I would be grateful if you would be able to answer the above additional questions and correct me if I am in error in anything I have written.

---

### Post by pfeiffep on 2014-05-18
@gordon99,>  [COLOR=#000000]I gather it is not advisable to work on documents in one OS (say 'C' drive) using another OS. However, am I correct in my understanding that any document produced in Linux and placed in a NTFS formatted logical partition would not be readable in Windows OS but any such document produced in Windows would be readable (and editable) in Linux? I assume this document however, if edited in Linux, would not be readable any more in WindowsOS.[/COLOR]
My experience is somewhat different from other posters. I have a separate drive used for "shared OS storage" I'm able to use Libre Office on both Windows 7 and Ubuntu 14.04 to read and write documents on my separate drive which is formatted NTFS.

---

### Post by Mark Phelps on 2014-05-18
Shrinking the "C" drive involves using ONLY the Windows Disk Management tool, as using other tools risks corrupting the Windows filesystem and rendering it unbootable as a result.

If you remove the Recovery partition, you will have no way of ever restoring your PC to its original condition.  You would do better installing Macrium Reflect (the free version) in Windows, use that to make a image backup of your Windows install, before removing the Recovery partition.  That will allow you to restore Windows later from the backup.

If you have an HP Tools partition, then read through the material below before you go charging into doing the dual-boot setup:

Simply removing HP_TOOLS is not the solution -- as it is too small to be of any use.

So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by LastDino on 2014-05-18
What is data partition is quite subjective, but generally it is same as storage, in your case it is going to be this NTFS partition.

/ = root is basically your C: on windows and if you don't bother to make /home, Linux will store everything in it as Windows does with its C:. Linux however, gives you power to use separate ''/'' and ''/home'' to store your OS with whatever software you install on it and other stuff mentioned bellow respectively.

/ home is basically where stuff you download, your music and other documents etc go. 

SWAP is more or less what you know as pagefile area on windows, it just works better than that :p

I couldn't dare to answer your other questions considering how well they've been dealt with by Mark, so please follow his post to T. However, if you face any issues, do post here, we are happy to help.

---

### Post by Impavidus on 2014-05-18
> **gordon99 said:**
> I gather it is not advisable to work on documents in one OS (say 'C' drive) using another OS. However, am I correct in my understanding that any document produced in Linux and placed in a NTFS formatted logical partition would not be readable in Windows OS but any such document produced in Windows would be readable (and editable) in Linux?  I assume this document however, if edited in Linux, would not be readable any more in WindowsOS.Every file on the NTFS partition can be created, written, read, modified, whatever in both Linux and Windows – provided of course that you have a program to handle the file format on both systems. It's just not a good idea to let Ubuntu write to the C partition, as it may damage Windows. Executing programs/scripts stored on an NTFS partition in Linux is also a bit problematic, but there should be no need for it.

---

### Post by gordon99 on 2014-05-18
Thanks everyone for your replies. Mark, I do have  Recovery DVDs which I made, as advised by HP, when the Notebook was new. I also have a Win.7 repair CD. Presumably I can therefore go straight to removal of the Recovery partition and shrinking "C" partition, after doing a full backup that is. If I do not need the HP Tools partition for Linux should I just leave it alone? I shall download MR as you suggest to create and burn the Linux Boot CD.

 I understand it is advisable to defrag. the HDD a couple of times after shrinking "C" drive so I shall do that.

Is the setting up of the new partitions during installation a reasonably straightforward process? I note I must avoid selecting 'replace' when setting up partitions. I am still in the dark as to how/when the freed up Recovery partition and the disk space made available by shrinking "C"
come together on the HDD to form an extended partition  for the new logical partitions. Maybe this happens automatically during installation of the new OS. I would very much like to know.

---

### Post by gordon99 on 2014-05-18
Sorry, I should have said I defrag BEFORE shrinking "C" partition and reboot a couple of times after altering partitions.

---

### Post by LastDino on 2014-05-18
**If **everything has been done properly, the freed-up space should show up in g-parted when you click ''something else'' during installation process.

---

