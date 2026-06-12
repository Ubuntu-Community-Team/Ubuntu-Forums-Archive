---
title: "grub rescue error"
date: 2014-09-11
forum: New to Ubuntu
---

### Post by watson524 on 2014-09-11
Hi all,

I'm a very novice user. I know enough to get around but not necessarily to fix things so catastrophic as this. I have a machine with 2 internal HDs and 2 external. I THINK I'm on 10.4 (kept ignoring update notices due to life going on and things working fine as is). Shut down and unplugged machine for remodel in my home office and after moving the desk and needing to pull a file, I plugged it back in not 20 minutes later and booted up to the following:

error: hd0 read error.
grub rescue>

I immediately unplugged the external drives which is where I believe my most important data to be. hd0 should just be OS files but this sounds pretty bad. Is the drive toasted? What should my next steps be. I did an "ls" to see what would show up and I get the following:
(hd0) (hd0,msdos5) (hd0,msdos1) (hd1) (hd1,msdos1)

but have no idea what to do with that.

Any help would be greatly appreciated!!

thanks in advance!

---

### Post by watson524 on 2014-09-11
Small update. I'm thinking I have 12.04 at least because I looked on my external drive via another machine and it has a desktop-i386 ISO file and if I downloaded it I would have installed it.

Also I pulled both internal drives out (an 80GB that should be the OS drive) and a 320GB that I believe was blank but formatted. Through them in my external housing and tried to bring them up on another machine (windows, which worked fine with the other drives that were in there). I get nothing on either. Like it doesn't even see them. No "needs to be formatted" or anything. Seems odd that both internal drives would go. Unless they were specifically formatted for linux somehow? Where my external ones weren't since they were in the hot swap station. That would almost make more sense on how both won't do anything.

If I could figure out where my mail files are (I use thunderbird), I could almost abandon and build from scratch but I fear there's on the 80gb drive and I need those as it's mail archives going back many many years. I don't know what thunderbird calls them (like .PST in outlook) but I'll search and see. If that and what I think are my other documents are on the external drives, which I think they are since I usually keep docs separate from OS, then a rebuild seems to be the easiest thing unless someone has other suggestions.

---

### Post by JKyleOKC on 2014-09-11
> **watson524 said:**
> Small update. I'm thinking I have 12.04 at least because I looked on my external drive via another machine and it has a desktop-i386 ISO file and if I downloaded it I would have installed it.

Also I pulled both internal drives out (an 80GB that should be the OS drive) and a 320GB that I believe was blank but formatted. Through them in my external housing and tried to bring them up on another machine (windows, which worked fine with the other drives that were in there). **I get nothing on either. Like it doesn't even see them. No "needs to be formatted" or anything. Seems odd that both internal drives would go. Unless they were specifically formatted for linux somehow?** Where my external ones weren't since they were in the hot swap station. That would almost make more sense on how both won't do anything.

If I could figure out where my mail files are (I use thunderbird), I could almost abandon and build from scratch but I fear there's on the 80gb drive and I need those as it's mail archives going back many many years. I don't know what thunderbird calls them (like .PST in outlook) but I'll search and see. If that and what I think are my other documents are on the external drives, which I think they are since I usually keep docs separate from OS, then a rebuild seems to be the easiest thing unless someone has other suggestions.The failure could have been the disk controller portion of the motherboard on the original machine; that could cause both drives to be inaccessible. However that would not have made them unreadable on the other machine. Windows, however, does fail to recognize drives formatted for Linux, and at least the OS drive would have to have been formatted for Linux. 

If you have a Live CD or USB stick with which you installed Ubuntu originally, you can use it to boot the Windows machine (with the drives in question connected when you do so) into a Ubuntu session. Select the "Try" option rather than the "Install" and you will be able to investigate matters. If you then see on the desktop a drive named "80 GB" you can open it and should see a listing of the original OS file system. From there, open the HOME folder, and then the folder named the same as your login name.

If you get this far the drive itself is most likely good. When your home folder, the one with your name in the title bar of its window, appears, press CTRL and H at the same time to show hidden files. Among these files should be one with a name resembling your mail program; I use Thunderbird and the file is ".thunderbird" but your situation may be different. At any rate such a file should lead to your actual mail files, and it whould be relatively simple to copy them off to a flash drive for safekeeping while solving the original problem.

Hope this helps get you started on the way to fixing things. Keep us posted on your progress, and if you have any questions, ask them -- don't do anything likely to make matters worse until getting more help! Nothing you do from the Live CD session can hurt your hard drives, unless you explicitly command it to...

EDIT: Re-reading I notice that you, too, use tbird. In the ".thunderbird" file you'll find a folder with a name ending ".default" and in that folder is another named "Mail" which contains all of your messages. The path to mine looks like this:> /home/jk/.thunderbird/zwqgku0x**.default/Mail**/Local Folders/The Mail folder will have more folders, one for each account or local folder you have configured. These folders, in turn, contain your actual messages. Just drag the Mail folder's icon itself to a flash drive to save all your messages.

After re-installing everything, follow the same procedure to get to the ".default" folder of the new installation (the first part of its name will be different), and drag the "Mail" folder from the flash drive back into it to replace the mostly empty "Mail" folder created by the re-install. This should put everything, including your account settings, back into place.

---

### Post by watson524 on 2014-09-11
Thanks for the tips. I found this a few minutes ago [http://askubuntu.com/questions/415015/is-it-possible-to-pull-data-off-a-linux-hard-drive-using-windows-8-1](http://askubuntu.com/questions/415015/is-it-possible-to-pull-data-off-a-linux-hard-drive-using-windows-8-1) and was going to try it so it sounds like I'm going down the right path. Will keep you posted

---

### Post by stalkingwolf on 2014-09-11
mail files can be found here,
home > view> show hidden> thunderbird> default > mail

---

### Post by watson524 on 2014-09-11
possibly i've made some progress. booted off the usb and hit the try option (80GB HD did a lot more spinning that it did before which i took as a good sign). when i go to file manager it throws a rather long error message when i try to click on the "74 GB Volume" drive (so i see that as a good sign that it's at least there). 

Unable to access "74 GB Volume" 
Error mounting /dev/sdc1 at /media/ubuntu/e7de6203-2f5b-4fc1-a8cd-e452f7ba9b9: Command line mount -t "ext4" -o
"uhelper=udisks2,nodev,nosuid" "/dev/sdc1" "/media/ubuntu/e7de6203-2f5b-4fc1-a8cd-e452f7ba9b9" exited with non-zero exit status 32; mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
missing codepage or helper program, or other error 
in some cases useful info is found in syslog - try dmesg | tail or so

which is all greek to me.

---

### Post by watson524 on 2014-09-11
and actually, after i hit ok, i see files. and i hit ctrl-h and see more files. nothing that says thunderbird tho .cache, .config, .dbus, .local, etc. and then desktop, documents, downloads, etc. Wondering if maybe my OS is on the 320GB drive and like you said, the mobo controller crapped out. seems unlikely tho that i'd have put an OS on a 320gb drive....

---

### Post by watson524 on 2014-09-11
sorry you know what, i'm a moron, the reason i don't see what i'm looking for is because that file listing is coming from the "HOME" folder which isn't on the 74 GB drive. so I guess i'm back to that error message and whatever it means.

---

### Post by yancek on 2014-09-11
Unplugging a machine after properly shutting it down is not going to cause the error you reported in your initial post.
You indicated in an earlier post that you could not see your files from a Linux partition from windows.  That is expected behavior as windows is not even capable of recognizine a Linux partition and will not be able to read anything.  Generally, it will just show as unknown or unallocated space.  It isn't actually clear to me that these are Linux partitions?  Per your last post, which error are you referring to, the original error or the one in post 6?  If you can't boot your installed Ubuntu, use any Linux Live CD/flash drive and go to a terminal and run this command to get info to post here:  sudo fdisk -l(Lower Case Letter L in the command)  Have all of your drives attached before running it.

It might also be useful to indicate which windows you are using on this computer.

---

### Post by watson524 on 2014-09-11
Win 7 Home Edition. The error I'm stuck at is the one from post #6. Below is the fdisk output (/dev/sdd is the one with the issue), that's the one I have plugged in on the windows machine while booted into linux. /dev/sda is my Windows drive and /dev/sdb is the thumb drive that has the unbuntu on it.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe3102a4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   312578047   156185600    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 64.0 GB, 64019759104 bytes
75 heads, 35 sectors/track, 47633 cylinders, total 125038592 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x544d74f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2120   125038591    62518236    b  W95 FAT32

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003f769

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048   143736831    71867392   83  Linux
/dev/sdd2       143738878   156301311     6281217    5  Extended
/dev/sdd5       143738880   156301311     6281216   82  Linux swap / Solaris

---

### Post by JKyleOKC on 2014-09-11
> **watson524 said:**
> possibly i've made some progress. booted off the usb and hit the try option (80GB HD did a lot more spinning that it did before which i took as a good sign). when i go to file manager it throws a rather long error message when i try to click on the "74 GB Volume" drive (so i see that as a good sign that it's at least there). 

Unable to access "74 GB Volume" 
Error mounting /dev/sdc1 at /media/ubuntu/e7de6203-2f5b-4fc1-a8cd-e452f7ba9b9: Command line mount -t "ext4" -o
"uhelper=udisks2,nodev,nosuid" "/dev/sdc1" "/media/ubuntu/e7de6203-2f5b-4fc1-a8cd-e452f7ba9b9" exited with non-zero **exit status 32; mount: wrong fs type, bad option, bad superblock on /dev/sdc1**,
missing codepage or helper program, or other error 
in some cases useful info is found in syslog - try dmesg | tail or so

which is all greek to me.The fact that you could later see files such as ".config" indicates that you were almost certainly looking at a home folder since such files ought not exist anywhere else. The name of the file that would contain your mail files is ".thunderbird" (note the leading dot, which is what makes the file hidden from normal viewing). 

Most likely, though, you were seeing the home folder of the "Try" session from the USB, not the one from your drive. The extra spinning you mention is, unfortunately, not a good sign -- it usually means that the system is having serious problems trying to read data from the drive, and trying over and over until it either times out, or eventually succeeds. You might try the other drive shown as an icon in the file manager just in case you had put the home folder of your 12.04 installation on it.

The error message I highlighted above indicates that this 74-GB drive may well be totally unreadable, which could be very bad news for you. The "bad superblock" phrase means that one of the most critical parts of the disk's directory files has been damaged to the extent that the system can no longer recognize it, and without that part it's almost impossible to get to the actual data files. Backup copies of the "superblock" do exist and it's possible to restore from them, but any error in an attempt to do so can make the drive definitely unrecoverable so I hesitate to provide any directions for an attempt. If you can locate an experienced Linux user in your immediate area who's willing to come to your site and help, it would be worth trying. However even if the repair appears to be successful, the damage may easily be more widespread and still foil total recovery...

---

### Post by watson524 on 2014-09-11
This whole thing just makes me sick. Finding an experienced linux user in podunk PA is impossible. I had been looking at drive recovery places online tho I have no idea what they cost. Has anyone ever used them? I don't care about anything else on this drive really other than that darn email. Are there any users here that do this type of work that I could pay and send the drive to?

---

### Post by watson524 on 2014-09-11
I can't hope it would be as easy as this sounds??

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

---

### Post by oldfred on 2014-09-12
The first thing to try is fsck. That will try to fix file corruption that can occur if drive was not correctly shutdown or after something like a power failure. It may fix a bad block or two, but if drive is failing it will not fix that.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by watson524 on 2014-09-12
When I run 
sudo e2fsck -C0 -p -f -v /dev/sdd1 (for some reason now it's showing as sdd vs sdc that it originally did when I plugged it in)

I get 
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdd1
Could this be a zero-length partition?

in response. and then it goes back to a prompt

---

### Post by JKyleOKC on 2014-09-12
Duplicated post...

---

### Post by JKyleOKC on 2014-09-12
> **watson524 said:**
> This whole thing just makes me sick. Finding an experienced linux user in podunk PA is impossible. **I had been looking at drive recovery places online tho I have no idea what they cost. Has anyone ever used them?** I don't care about anything else on this drive really other than that darn email. Are there any users here that do this type of work that I could pay and send the drive to?Many of the places that advertise on-line are quite pricy; I've seen quotes as high as $1,000 to recover data from a drive. A local friend succumbed to one of the "ransomware" scams about a year ago and wound up with a Windows drive that appeared to be unusable; I found a local data recovery guru who did manage to fix his drive for a bit less than $200, which he was glad to pay to save years of family photos -- but your most recent "short read" error tends to confirm my pessimism.

There's a program called *testdisk* that can search for the partition tables on a problem drive, and will not write to the drive unless you specifically tell it to do so. The package includes a second program, *photorec*, that can recover any and all readable data -- but it runs for many hours, loses all filenames, and files usually come out in little chunks that you have to piece together by hand. I've used it to recover a few critical emails from a damaged drive, myself, but it took more than a week of nearly full time efforts to get back less than a month's worth of data before I gave up and decided to accept the loss of the rest. It's sorta like piecing together documents after they have gone through a shredder...

I'm glad to see that **OldFred** has jumped in here. Perhaps he will have some ideas that I've missed...

---

### Post by JKyleOKC on 2014-09-12
> **watson524 said:**
> I can't hope it would be as easy as this sounds??

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)If, and **only** if, the problem is actually just a bad superblock, then the procedure in your link can fix it (and is much simpler than the routine I mentioned earlier for repairing things). The call to e2fsck with "-n" simply reads the data; the "-n" argument tells it **NOT** to write anything out. If that gives you an error instead of listing the superblock backup addresses, then it's likely to be a lost cause -- but if it does give you the list, that final call with the "-b" argument has a chance of getting things back. The 145 comments reporting success indicates that it works well in at least some cases.

If it were my own data involved, I would give it a try. If you do, be sure to let us know how it comes out.

Good luck!

---

### Post by watson524 on 2014-09-12
To be honest, at this point I might easily pay $500 or more to get this darn data back...... Is testdisk worth trying to "prove" anything one way or the other? 

I ran sudo mke2fs -n /dev/sdd

and got the list of backups but when I tried each of them with sudo e2fsck -b block_number /dev/sdd I get 
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Invalid argument while trying to open /dev/sdd

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

which seems bad..... since it happened on every one.

Open to any and all ideas at this point

---

### Post by watson524 on 2014-09-12
To be honest, at this point I might easily pay $500 or more to get this darn data back...... Is testdisk worth trying to "prove" anything one way or the other? 

I ran sudo mke2fs -n /dev/sdd

and got the list of backups but when I tried each of them with sudo e2fsck -b block_number /dev/sdd I get 
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Invalid argument while trying to open /dev/sdd

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

which seems bad..... since it happened on every one.

Open to any and all ideas at this point

---

### Post by oldfred on 2014-09-12
I would also try testdisk, nothing to lose.

And I also have used photorec to recover some text files (my notes for what I post here). I had a backup but it was not current. As JKyleOKC says it is a long slow process. You have to have another drive to copy data to that has enough room. I think I had to let mine run overnight but the larger the drive the longer it takes. And you only get file extenstions. Since I had saved my text files many times, it also found all the deleted copies and I had to do many compares to try to find which was the most current. I now include a file name inside  every text file just in case, but also back up more frequently.

Some other tools, often best to make image copy of drive so you are not working on only copy and perhaps making things worse.
       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
      
 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

