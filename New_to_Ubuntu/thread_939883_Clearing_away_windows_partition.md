---
title: "Clearing away windows partition"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by le singe on 2008-10-06
Hello.

I'd like to erase my windows partition in order to have more hard drive space in Ubuntu.  After installing Ubuntu, I've found that I never boot windows anymore, and after booting into windows last night just to check it out, it gave me an error and wouldn't even run anyhow.  

So Ubuntu was installed after windows.  I first formatted my computer, installed windows clean, then installed Ubuntu afterwards on, I guess, a separate partition.  Since I haven't missed windows at all :)

I have the Hardy Heron live CD, and so I can boot from that and just use GParted to clear/format my windows partition and free up the space it holds, but I have a few questions:

First, how smooth does this typically run?  I mean, I don't have a means to back up my files right now... should this be a worry?  

Second, is the process straightforward and will I have to know anything in particular about partitions or have to assign the freed space a letter name or something?

Lastly, I read a post where someone said that you can actually run GParted from within Ubuntu, without a live CD, and that the result is an extra empty drive where windows used to be as opposed to simply expanding the space on the Ubuntu partition.  I didn't think this was possible... if it is, is it recommended?

Alright.... my thanks to any replies, I just want to get some feedback before I do this.

---

### Post by Idefix82 on 2008-10-06
You need to decide what you want to do with the freed space. If you don't want to change the size of any existing Ubuntu partitions then you can certainly run GParted from within Ubuntu. In fact, in that case that's what I would recommend, since you then can't break your Ubuntu installation because GParted won't let you make any changes on the mounted partitions.

If on the other hand you want to increase one of the Ubuntu partitions then you need to boot from the LiveCD. In this case, backing up data would be rather desirable, since you never know what can go wrong.

The safest and easiest way is probably to delete Windows from within Ubuntu using GParted and format the partition as Ext3. After that you can use it in any way you like, eg. just like an extension of your Home folder. For example you could put your music there and under ~/Music create a link to this new partition.

---

### Post by Sephoroth on 2008-10-06
Backing up important files can't hurt if something goes wrong though in my experiences everything has gone smoothly (just make sure your LiveCD is in good condition, i.e. no scratches, etc).  You should only have to unformat your NTFS partition and then extend your ext3 (or whatever appropriate file systems you currently use).

When running GParted within Ubuntu, I dout it will let you extend your current partition while booted from it.  If you have a working LiveCD available, I'm not sure if there is too much benefit from it (though there might be a speed benefit if you merely modify another partition).

---

### Post by le singe on 2008-10-06
> **Idefix82 said:**
> You need to decide what you want to do with the freed space. If you don't want to change the size of any existing Ubuntu partitions then you can certainly run GParted from within Ubuntu. 

Thanks for the reply.  Are there any limitations to doing it this way?  I imagine the extra space would show up sort of as a second hard drive.  But for Ubuntu system files and all (and program installations, as well?) would these have to go on the Ubuntu partition?

And also.... Idefix - is that at all a reference to "idée fixe?"

---

### Post by Idefix82 on 2008-10-06
I think if you simply format the partition as Ext 3 then it will just show up as another hard drive which you would have to mount before you can use it. You can make it mount automatically at start up or do it manually. It's a matter of two clicks in the file browser.

Alternatively, you can mount it as part of your file system. Eg if you want to use it as a music folder then you can first move everything from your existing Music folder to the new partition, then mount the new partition as /home/Music. It will now look as if the partition is just another folder in your hierarchy. You should backup the Music data before doing this, just in case.

I wouldn't temper in this way with system files that reside in any other folder apart from /home. If instead you want to use the extra space for software, say, then you have no choice other than expanding the root partition (or the /usr partition if you have one).

I hope all this makes sense, if not then feel free to ask.

Idefix is a reference to the dog from Asterix and Obelix: [http://en.wikipedia.org/wiki/Asterix]("http://en.wikipedia.org/wiki/Asterix")
Of course the authors of the comics did indeed intend it as a reference to "idée fixe" :)

---

### Post by le singe on 2008-10-28
so I haven't yet erased windows as I wanted to wait until I could back up some files.  Bumping this post with some additional info and a final few questions.

Reading through posts of other people who were also hoping to get rid of their windows partitions, I found the suggestion to post the output of a few terminal codes, to see how your partitions are actually set up.  Here they are:

sudo fdisk -l:
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8583    68942916    7  HPFS/NTFS
/dev/sda2            8584       14593    48275325    5  Extended
/dev/sda5            8584       14341    46251103+  83  Linux
/dev/sda6           14342       14593     2024158+  82  Linux swap / Solaris

df -h:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              44G   16G   26G  38% /
varrun                502M  116K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   56K  501M   1% /dev
devshm                502M   60K  501M   1% /dev/shm
lrm                   502M   39M  463M   8% /lib/modules/2.6.24-21-generic/volatile
gvfs-fuse-daemon       44G   16G   26G  38% /home/monkeychild/.gvfs

I really don't have much experience with partitions, and I am hoping that someone more knowledgeable than I might be able to tell me, based on my above hard drive partition information (I have only one hard drive), basically how I would go about deleting windows and allocating its space to Ubuntu.  I first installed windows, then Ubuntu, and so I'm not sure if that means that Ubuntu is running on a sub-partition of the windows NTFS partition, or...?  I realize that I have to boot from the live CD and use GParted - just not sure how intuitive the process is and whatnot.  Finally, once I have windows erased, I'd like to eventually try out Kubuntu or another KDE distribution as a dual boot, and so should I now set aside a partition onto which I can later install Kubuntu or something else.... or can I go ahead and give all of my hard drive to Ubuntu and later will a Kubuntu install sort out the necessary partition it needs?

Yeah I'm asking a lot of questions so my apologies if what I'd like to know is rather obvious.  I did some reading up on partitions but I've always found the forums more helpful than anything else.  Thanks to any further help!

---

### Post by le singe on 2008-10-28
so I haven't yet erased windows as I wanted to wait until I could back up some files.  Bumping this post with some additional info and a final few questions.

Reading through posts of other people who were also hoping to get rid of their windows partitions, I found the suggestion to post the output of a few terminal codes, to see how your partitions are actually set up.  Here they are:

sudo fdisk -l:
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8583    68942916    7  HPFS/NTFS
/dev/sda2            8584       14593    48275325    5  Extended
/dev/sda5            8584       14341    46251103+  83  Linux
/dev/sda6           14342       14593     2024158+  82  Linux swap / Solaris

df -h:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              44G   16G   26G  38% /
varrun                502M  116K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   56K  501M   1% /dev
devshm                502M   60K  501M   1% /dev/shm
lrm                   502M   39M  463M   8% /lib/modules/2.6.24-21-generic/volatile
gvfs-fuse-daemon       44G   16G   26G  38% /home/monkeychild/.gvfs

I really don't have much experience with partitions, and I am hoping that someone more knowledgeable than I might be able to tell me, based on my above hard drive partition information (I have only one hard drive), basically how I would go about deleting windows and allocating its space to Ubuntu.  I first installed windows, then Ubuntu, and so I'm not sure if that means that Ubuntu is running on a sub-partition of the windows NTFS partition, or...?  I realize that I have to boot from the live CD and use GParted - just not sure how intuitive the process is and whatnot.  Finally, once I have windows erased, I'd like to eventually try out Kubuntu or another KDE distribution as a dual boot, and so should I now set aside a partition onto which I can later install Kubuntu or something else.... or can I go ahead and give all of my hard drive to Ubuntu and later will a Kubuntu install sort out the necessary partition it needs?

Yeah I'm asking a lot of questions so my apologies if what I'd like to know is rather obvious.  I did some reading up on partitions but I've always found the forums more helpful than anything else.  Thanks to any further help!

---

### Post by le singe on 2008-10-28
Didn't mean to double-post - the server slowed down for a bit... can't find a way to delete the second post.

---

