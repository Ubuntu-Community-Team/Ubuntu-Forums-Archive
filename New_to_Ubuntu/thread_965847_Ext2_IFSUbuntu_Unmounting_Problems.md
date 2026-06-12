---
title: "Ext2 IFS/Ubuntu Unmounting Problems"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by cheesypoof on 2008-10-31
First of all I have Windows Vista installed as well as 8.10(dual boot). All updated completely. I like to be able to view my ubuntu files in Vista. This led me to install Ex2 IFS. I made sure not to give Windows write abilities by the way. Unfortunately, when I click on the Ubuntu drive in Vista, it says "You need to format the disk in drive E: before you can use it." "Do you want to format it?". This leads me to believe that Ubuntu is not unmounting properly on shutdown. Additionally, here is the diagnosis from a program on the Ex2 IFS website.

> C:\Users\-\Desktop>mountdiag E:
The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.11 software did not
mount it because the file system has an inode size unequal to 128 bytes (inode
size: 256 bytes).
The only way to solve it is to back up the volume's files and format the file
system: give the mkfs.ext3 utility the -I 128 switch. Finally, restore all
backed-up files.
After that, the Ext2 IFS software should be able to access the volume.

Any clues on how I can get this working properly?

---

### Post by talsemgeest on 2008-11-01
I always got that problem when Ubuntu had not been shut down properly. First thing you should do is boot up Ubuntu, then shutdown again once you get to the desktop. Boot back into windows and see if it works now.

---

### Post by Yashiro on 2008-11-01
> The current version of Ext2 IFS only mounts volumes with an inode size of 128 like old Linux kernels have.

Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes. Ext2 IFS 1.11 is not able to access them. 

Run [COLOR="Green"]sudo tune2fs -l /dev/sda1 | grep Inode[/COLOR]
If it returns inode > 128 then you are stuffed until the Windows driver is updated.

---

### Post by snuffy on 2008-12-23
Anyone know of a solution yet... this is likely to be a make or break reason to leave linux... yet again. :-(

---

### Post by talsemgeest on 2008-12-23
> **snuffy said:**
> Anyone know of a solution yet... this is likely to be a make or break reason to leave linux... yet again. :-(
The only solution if you still want to use ext2ifs is to format and install ubuntu hardy heron, then upgrade to ibex using the update manager. NOTE: I do not recommend doing this. There is always some risk when upgrading ubuntu, please back up all precious data first.

However, since ubuntu has such good NTFS support, simply keep all the files that you want to access on your windows partition. It is by far the simplest way to do it and I can't see it being a make or break reason to leave Linux.

---

### Post by snuffy on 2008-12-26
Thanks, but i found a program called Ext2Fsd that works... for now anyway.

cheers. 
tim.

---

### Post by talsemgeest on 2008-12-26
Awesome, I will have to give that a try.

---

### Post by Ocean Machine on 2009-04-20
Have there been any solutions to this problem? I'm receiving the same mountdiag return as the original poster.

Does Ext2Fsd work on Vista? The website makes it seem as if it doesn't.

---

### Post by RealG187 on 2009-07-27
I have the inode 256 bytes thing and cannot use EXT2IFS and EXT2FSD always makes my system BSOD.

I need a way to access my EXT3 partition in Vista...

---

### Post by talsemgeest on 2009-07-28
> **RealG187 said:**
> I have the inode 256 bytes thing and cannot use EXT2IFS and EXT2FSD always makes my system BSOD.

I need a way to access my EXT3 partition in Vista...
Well, I still havent found a way, probably just best to copy your files from a live cd to the ntfs partition.

---

### Post by RealG187 on 2009-07-28
I need direct access while in Windwows, I am trying to back up the partiiton. My Ubuntu install is fired because it [says there no free space even though there is]("http://ubuntuforums.org/showthread.php?t=1221107")

---

### Post by talsemgeest on 2009-07-28
> **RealG187 said:**
> I need direct access while in Windwows, I am trying to back up the partiiton. My Ubuntu install is fired because it [says there no free space even though there is]("http://ubuntuforums.org/showthread.php?t=1221107")
Well, if you are trying to back it up you should be able to use the Ubuntu Live cd. Because, like I said, it doesnt look like any ext2ifs drivers work.

---

### Post by RealG187 on 2009-07-28
I need to be able to still fully use my computer while backing up and I want to use [Beyond Compare]("http://bestwikiever.wikidot.com/Beyond_Compare") to back it up.

---

### Post by talsemgeest on 2009-07-29
> **RealG187 said:**
> I need to be able to still fully use my computer while backing up and I want to use [Beyond Compare]("http://bestwikiever.wikidot.com/Beyond_Compare") to back it up.
Well, feel free to create your own driver then ;)

---

### Post by RealG187 on 2009-07-29
I don't know how to make programs or drivers

---

### Post by talsemgeest on 2009-07-30
> **RealG187 said:**
> I don't know how to make programs or drivers
Well, there are many tutorials on the internet for creating drivers if you really must have access from windows. However, what I am trying to say is that if there are no drivers that work with ext3, then you must look for an alternative solution, such as using a live cd to shrink the ext3 partition, create an ntfs partition and copy all the files onto that. From there they can be accessed from windows and backed up however you want.

Such is the ethic of Linux: if a solution doesnt exist, create one yourself :)

---

### Post by RealG187 on 2009-07-30
It order for me to create a new partition I have to remove that one, and in order to do that I have to remove that one, so I need to back them up.

---

### Post by EvilTchnlgy on 2009-08-11
EXT2IFS works fine in vista, it also work s in windows 7 if compatibility mode on the exe is set to vista. I was just looking up this error as i was able to access my ext3 partition before, but not now, and now realize my last ubuntu boot crashed. if you cant boot into ubuntu just use the live cd and cleanly mount and unmount your ext3 partition and it should resolve your issue

---

### Post by RealG187 on 2009-08-12
I think the reason why it's not working isn't because I am running Vista, but rather because the inode size of my partition is bigger. I think mine is 256 but EXT2IFS only supports 128...

---

### Post by Mike090830 on 2009-08-30
> **RealG187 said:**
> I think the reason why it's not working isn't because I am running Vista, but rather because the inode size of my partition is bigger. I think mine is 256 but EXT2IFS only supports 128...

That's right. Currently the only solution is to backup your files (recommended anyway :mrgreen:), reformat the partition with an inode size of 128 bytes and copy your files back.

See here: [http://ubuntuforums.org/showthread.php?p=7870122#post7870122](http://ubuntuforums.org/showthread.php?p=7870122#post7870122)

---

### Post by RealG187 on 2009-08-31
My files were backed up, what took a while was verifying the backed up files were recent and verified good and backing any files that were new, outdated, etc...

I don't know how to change the inode size, I just used what the installer gave.

I formatted my new partition as NTFS. Ubuntu reads NTFS better than Windows reads EXT...

---

### Post by Earl_Maroon on 2009-10-23
I was having difficulty with this, but things seem to be working now.

I started Ubuntu and logged in as root. I then unmounted my home partition. I'm not sure if that did anything though.

I then restarted Windows (7) and installed **Ext3fsd**. I restarted, opened the settings manager. It allowed me to choose a drive letter for my home partition. I then had to restart to use the partition. The first time I tried browsing my ext3 home partition Windows BSoD'd. However, I could see my files for a split second before it did. I restarted and everything seems to be working.

Fingers crossed.


*Edit*
I got another BSoD opening a folder properties dialogue box. After yet another restart the folder dialogue box opened fine.

---

