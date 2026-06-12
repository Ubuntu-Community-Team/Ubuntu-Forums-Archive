---
title: "how do I get a 2ed hard drive to start up when starting the computer."
date: 2014-02-22
forum: New to Ubuntu
---

### Post by EZZ9 on 2014-02-22
I have two hard drives first one has Ubuntu on it the 2ed has my mp3 files. evertime I turn off the computer, then back on the 2ed hard drive is not running, I can see this because evertime I turn on rhythmbox there is no music on it and I have to go to the 2ed hard drive and turn it on, then wait for all the mp3 files to load every time. Can anyone help with this thank you.

---

### Post by IvoGuerreiro on 2014-02-22
Good night
You check your 2ed hard drive shunt?

---

### Post by whitesmith on 2014-02-22
> **EZZ9 said:**
> I have two hard drives first one has Ubuntu on it the 2ed has my mp3 files. evertime I turn off the computer, then back on the 2ed hard drive is not running, I can see this because evertime I turn on rhythmbox there is no music on it and I have to go to the 2ed hard drive and turn it on, then wait for all the mp3 files to load every time. Can anyone help with this thank you.

This question could have been posted with greater clarity. Do you mean your 2nd drive is an external thingie that lives in a switched box? If, more likely, "not running" means "not recognized," then you've got to add it to /etc/fstab, preferably by UUID. Do you know how to do this? If not, we'll help with the details. Apparently you have the mount point issue solved because the drive operates manually. Cheers.

---

### Post by whitesmith on 2014-02-22
> **IvoGuerreiro said:**
> Good night
You check your 2ed hard drive shunt?
Most modern SATA drives don't require shunting. Drive order is handled in software. Of course, the OP may have an older IDE drive that requires it.

---

### Post by IvoGuerreiro on 2014-02-22
Thank for the notice, i just keep learning on this forum. It's not a joke, i really mean it.O:)

---

### Post by ncooke98 on 2014-02-22
Having had a similiar problem, I read through this posting list.

When I run: sudo blkid

/dev/sdb1: LABEL="DISK2_VOL1" UUID="AAB0974FB097213D" TYPE="ntfs" 
/dev/sda1: UUID="bef7b1e3-7c63-417a-910e-ee74ab6f72db" TYPE="ext4" 
/dev/sda5: UUID="9cdff70f-3ccd-4cbe-82ab-b40a45628547" TYPE="swap"


The drive I'm trying to have automatically mounted at boot-up is DISK2_VOL1.  

Reading through the Fstab File Configuration Help, I understand that I need:

1.) The Device  
2.) Mount Point  sudo mkdir /media/importedmusic
3.)File System Type:  Auto
4.)Options:  Defaults
5.) Dump: 0
6.)Pass: 2

Am I going in the right direction?  I guess I'm just unsure of the final syntax I'll need for the command line entry.  Or am I over-thinking/complicating this?

Thanks in advance.  Ubuntu newb here...Lol.

Spawned998

---

### Post by EZZ9 on 2014-02-22
Sorry new to all this computer talk and I don't know the lingo, the hard drive is inside the computer and is a SATA, I can see it on the dock and click on it to start, then move files to and from it and only after I click it the rhythmbox see the files. But on a restart the 2ed hard drive is not mounted and there are no files in the rhythmbox.

---

### Post by EZZ9 on 2014-02-22
will this help sdb1 is the one not mounting 
/dev/sda1: UUID="a0833ad3-f9a6-4f3a-accb-909f0b814b3b" TYPE="ext4" 
/dev/sda5: UUID="b4b952e2-ec75-4c88-b51f-7f67c794a2cd" TYPE="swap" 
/dev/sdb1: LABEL="my_data" UUID="4818bcbe-5b1f-47c0-942b-9530e0f00648" TYPE="ext2"

---

### Post by Vladlenin5000 on 2014-02-22
Dear, we already know that, you're just repeating your original post.

The thing is, unlike your old Windows OS, Ubuntu by default **doesn't** mount additional drives at the startup. You need to tell it to do it and what drives to mount: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
If there's something you don't understand please post back and someone will try to explain it. However, I would recommend you to read carefully, understand the concepts - additional Google searches if you must - and then try to apply the procedure to your specific configuration.

PS - It would have been much better to have a separated /home partition and just copy/move the files to the respective folder (ex: Music) instead of having them in a 'foreign' partition/drive.

---

### Post by EZZ9 on 2014-02-22
That's the tone of the problems I keep getting people saying do it this way, do it that way. When you don't know how to do any of this. One gets stuck doing it the wrong way or half way on one and half the other and reading 1000's of pages of info that just don't help with what one wants, and now I'm stuck with this wall.

You said "it would have been much better to have a separated /home partition and  just copy/move the files to the respective folder (ex: Music) instead of  having them in a 'foreign' partition/drive" I have no clue what that is? But sound like what I wanted.
 I just wanted more space two hard drives more space, I thought. Just plug it in and it's good, I thought, But got stuck doing a partition not know what that was. Had to take info from a page off the net to do it. Did not get it right, I see now. I am willing to start over, whipping the 2ed hard drive blank if it would make things easier to set up. Going on a week of this and still not there, is just getting to me. If I was 10 years old I would have gotten it in 10 mins being over 50 and only owned a computer for only 7 years puts me in the driver's seat of a bowing 707, when I only know how to drive a car. Lol

---

### Post by Vladlenin5000 on 2014-02-23
First of all, you're over-blowing my post-scriptum, intended *only* as a side remark. You can do the way you want and that's fine but I felt I should tell how I would do it.

My last post goal was twofold: First and foremost make you _understand_ why it h[SIZE=1]appens the way[/SIZE] it happens and the underlining philosophy. Bottom line: Your issue is a non-issue, it's actually like that by design. Secondly _explain_ what you should do in order to achieve the desired results That's the wiki link, of course. Bottom line: The link gives you the knowledge required to comprehensibly and definitively answer [SIZE=1]your question because "how do I get a 2nd hard drive to start up when starting the computer" actually translates to **"how do I configure it to have a partition automatically mounted?"**. You don't need to read further down, just up to Gnome Mount so hardly 1000 pages... C'mon
Again, if there's something you don't understand there JUST ASK but don't expect to be spoon-fed. Actually, if your hungry - and you are - NEVER ask me for a fish, ask me to teach you how to fish and I gladly do it.
[/SIZE]

---

### Post by squakie on 2014-02-23
Is this the same drive you have another post for?  If so, these threads should be combined.

Vladlenin5000 is correct in saying you really do need to understand the concepts involved.

The are a few unknowns for us right now, the biggest being what is the format of the drive you are trying to access?

Your "system" disk will automatically mount at boot time.  If you don't know what mount is, you should read up on it.  Basically you are telling the system to take a file system and make it available via some place in a folder tree.  You have to mount a file system before you can access it.

The file fstab in /etc is the file system table used at boot (or when a file system comes online).  It says to mount this file system to this place in a folder tree, the file system is of type "x" (i.e., ext4, ntfs, etc.), and some additional options.  With an entry in this file for your 2nd disk it would automatically mount.

However, that is way over simplifying things.  You really do need to understand the concepts of a file system, the mount command, the entries in fstab, the type of file system - as it makes a difference on how the file system is mounted and how permissions are assigned to it, and you need to understand permissions.

Most people want a simple "do-this" answer, and this really just isn't one of those cases.  With enough information from you we could tell you how to do it, but is is important you understand the concepts involved.

---

### Post by fdrake on 2014-02-23
for info read [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

how about we start with this.  Mount the drive by clicking on the icon and then open the terminal run this command and post its output:
```
mount -l
```
then we will edit your fstab.

---

### Post by whitesmith on 2014-02-23
> **ncooke98 said:**
> 
Reading through the Fstab File Configuration Help, I understand that I need:

1.) The Device  
2.) Mount Point  sudo mkdir /media/importedmusic
3.)File System Type:  Auto
4.)Options:  Defaults
5.) Dump: 0
6.)Pass: 2

Am I going in the right direction?  I guess I'm just unsure of the final syntax I'll need for the command line entry.  Or am I over-thinking/complicating this?

Thanks in advance.  Ubuntu newb here...Lol.

Spawned998

Hi,Spawned998! My /etc/fstab is pretty large, so I limited myself to 3 drives
```

UUID=ac36ebf9-714b-4701-895a-cf805e47db03   /media/HomeExt       ext4      discard,noatime,nodiratime                                                  0       2    # internal Linux drive
UUID=49865350-1257-4fbe-ac9a-ac6a571b341b   /media/FreeAgent     ext4      auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=FreeAgent   0       0    # external Linux drive
UUID=01CC034F5DECC700                               /media/Data-SLA360  ntfs      defaults                                                                             0       0    # an internal Windows drive

```
Linux doesn't differentiate between internal an external drives. The stuff beginning with # is just an explanatory comment that doesn't belong in fstab. Hope this helps you.

---

### Post by monkeybrain20122 on 2014-02-23
> **EZZ9 said:**
> I have two hard drives first one has Ubuntu on it the 2ed has my mp3 files. evertime I turn off the computer, then back on the 2ed hard drive is not running, I can see this because evertime I turn on rhythmbox there is no music on it and I have to go to the 2ed hard drive and turn it on, then wait for all the mp3 files to load every time. Can anyone help with this thank you.

So basically you need the partition in your second drive that has the music to be mounted automatically so say, if you open your music player it will find the music automatically, is that it?

The easy way: see point #1 and screenshot
[http://ubuntuforums.org/showthread.php?t=2206951&p=12935744#post12935744](http://ubuntuforums.org/showthread.php?t=2206951&p=12935744#post12935744)

---

### Post by EZZ9 on 2014-02-24
?

---

### Post by whitesmith on 2014-02-24
> **monkeybrain20122 said:**
> So basically you need the partition in your second drive that has the music to be mounted automatically so say, if you open your music player it will find the music automatically, is that it? Yup. Change fstab and reboot the system or refresh the mount subsystem, your choice. Cheers!

---

### Post by EZZ9 on 2014-03-05
looks like I got it just took me some time to getting around to have the time to try it

---

