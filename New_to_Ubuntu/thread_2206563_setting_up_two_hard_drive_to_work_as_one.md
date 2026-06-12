---
title: "setting up two hard drive to work as one"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by EZZ9 on 2014-02-19
I am new to all this, so if I don't have the right nomenclature on things you know why.
I love my music and have gotten to the point of using 90% of my hard drive making the computer slow down. I was told to get another hard drive and put the music files on it. Was told it's called master & slave. This took me a bit of time, but I got it. I moved the music file to the other hard drive. But I see it acted alone, like a backup USB? Copying the files rather than moving them. I found out if I hold down Shift while dragging the file, the mouse cursor has a &#8598; and moves the files not copying them. I did this. Then I turned on the rhythm box and it does not find the music files. So I know I don't have it quite right.
  What I want is having all my music, photo & document files on the new hard drive and the operating systems on the other and have them working together. I know this should be an easy thing to do. But after reading so much about it, I'm lost. Can anyone help.
I do know how to use the terminal and commands, just so you know.
Thank You.

---

### Post by ian-weisser on 2014-02-19
Please post the contents of your /etc/fstab file.
Please post the results of the command **sudo blkid**

---

### Post by EZZ9 on 2014-02-19
"Contents of your /etc/fstab file" what and where is this one found?

From  the command **sudo blkid**
/dev/sda1: UUID="9da554d4-13a5-4c3e-a555-a29d1a8b951b" TYPE="ext4" 
/dev/sda5: UUID="b4b952e2-ec75-4c88-b51f-7f67c794a2cd" TYPE="swap" 
/dev/sdb1: LABEL="my_data" UUID="4818bcbe-5b1f-47c0-942b-9530e0f00648" TYPE="ext2"

---

### Post by EZZ9 on 2014-02-19
"Contents of your /etc/fstab file" what and where is this one found?

From  the command **sudo blkid**
/dev/sda1: UUID="9da554d4-13a5-4c3e-a555-a29d1a8b951b" TYPE="ext4" 
/dev/sda5: UUID="b4b952e2-ec75-4c88-b51f-7f67c794a2cd" TYPE="swap" 
/dev/sdb1: LABEL="my_data" UUID="4818bcbe-5b1f-47c0-942b-9530e0f00648" TYPE="ext2" 

found it 

 GNU nano 2.2.6              File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=9da554d4-13a5-4c3e-a555-a29d1a8b951b /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=b4b952e2-ec75-4c88-b51f-7f67c794a2cd none            swap    sw           $








^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by whitesmith on 2014-02-19
There are several approaches to this problem. The one I adopted was to use LVM (logical volume management) SW to let me string together SATA 3 SSDs of dissimilar capacity that Ubuntu sees as a single drive. Advantage: There's no need to play with gparted to resize partitions, ever. I had a library of FLACs that was closing in on the size (64 GB) of the SSD where it was stored. By hooking up all the SSDs into a single logical volume, additions exceeding the 64 GB boundary automatically moved to another SSD. Awesome! Disadvantage: When LVM gets borked (bad drive or whatever) it is **really** borked, but that, in my experience, rarely happens. Look into it!

---

### Post by EZZ9 on 2014-02-19
I have never used windows I have always used Linux. I have only had a computer for less than 7 years. For me to take the time to read a book about the difference of the two, is useless to me and will take time, I just don't have.  I just want to get this to work. Is there not a program I can use to get it right or command lines to change it. Or step by step instructions to follow?

---

### Post by Topsiho on 2014-02-20
> **EZZ9 said:**
> I have never used windows I have always used Linux.

Great! First time that I see this kind of information. For me this is a special day ...

I never used LVM but I think that is the first suggestion that comes to mind here. With LVM you can add and remove disks as you want, the LVM system will adjust it self to the new situations, and always act as if there is only one drive, even if there are a lot of them.

But I fear you have to install everything anew again.

I found this information:

[http://www.howtogeek.com/howto/36568/what-is-logical-volume-management-and-how-do-you-enable-it-in-ubuntu/](http://www.howtogeek.com/howto/36568/what-is-logical-volume-management-and-how-do-you-enable-it-in-ubuntu/)

and hope this will help you.

Topsiho

---

### Post by oldfred on 2014-02-20
I am not a fan of LVM, because of the disadvantages. Hard drives do fail and if any drive fails you do lose all data in the LVM. Backup then are vital.
 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

You need to mount your data partition. And using ext2 is not recommended anymore. That does not have a journal and a power failure or abnormal shutdown may cause data damage that then cannot be fixed with a fsck.


 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Modify fstab to add your data partition.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

If you can already copy data, then it sounds like you have already see ownership & permissions to use data partition.

---

### Post by buzzingrobot on 2014-02-20
> **EZZ9 said:**
> ...I turned on the rhythm box and it does not find the music files. So I know I don't have it quite right.
  

Is that the real problem you are trying to solve? Getting Rhythmbox to find the files you have moved to the new disk? That should be considerbly less complicated than "setting up two hard drives to work as one".

Rhythmbox is probably looking for files in the original location and they aren't there.   By default, it expects files in the "Music" folder located inside your "Home" folder.  But, it can be pointed at another folder.

Launch Rhythmbox and go to "Preferences" in the menu.  Click on the "Music" tab. You will see a "Library Location" label and beneath that will will be a field tagged "Music files are placed in:".  Click the "Browse" button on the right and navigate to the folder with your music files on the new disk.  (You should see a list of folders, etc., in the left panel. You will probably need to navigate via the "Computer" link.)

---

### Post by whitesmith on 2014-02-20
> **oldfred said:**
> I am not a fan of LVM, because of the disadvantages. Hard drives do fail and if any drive fails you do lose all data in the LVM. Backup then are vital.As usual you're 100% on the backup issue. LVM without good, solid and **tested** backups is like doing a hire-wire act without a net. Just say no!

---

### Post by EZZ9 on 2014-02-20
YES!!! Loading music now, sweet! This works for me. I can keep my mp3 files there on the 2ed hard drive and have it back up my photo & document. This will back up, the important things and give space for the operating system to run faster. You guys rock. Thank You.

---

