---
title: "Linking back to /home"
date: 2014-01-24
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-01-24
12.04 is installed on a SSD

I have unpacked my tarball into the second drive (a HDD) on this computer on sda6 and here is output from "mount"

```
robert@robert-HP:/media/Data/tmp/home/robert/Desktop$ mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb2 on /home type ext4 (rw)
/dev/sdb3 on /boot/efi type vfat (rw)
gvfs-fuse-daemon on /home/robert/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=robert)
/dev/sda7 on /media/7edaadf6-ebbd-4b9e-acc4-5e12e09213b0 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sda6 on /media/Data type ext4 (rw,nosuid,nodev,uhelper=udisks)

```

Please see the final line of the above. Under /media/Data are /tmp/home/robert/Desktop:

robert@robert-HP:/media/Data/tmp/home/robert/Desktop$ ls
aclk.desktop                                  
Backups                   
Chrome Bookmarks 101109   
chromium-browser.desktop  
Computer-Various          
Current-Various                           
google-chrome             
House Concerts            
How-To's & ThingsToKnow
Linux Stuff
Misc
Music & Audio
Property
SusieStuff
UserData

I am ready to take the next step, which, in my mind, is linking or binding (or another method) the folders and files above back to /home/robert so that the directories and files in the list above show on my desktop (ie, what I see when the computer boots up), just as if they actually existed in /home/robert/Desktop. Otherwise, I could just put a shortcut on the desktop to "Destktop" at  Data/tmp/home/robert/Desktop

So first question: Is this possible?

Second question: Can I do this by linking or binding or is there a better method? I had originally thought to have sda6, mounted as /home, but was persuaded by OldFred's idea of just linking these directions back to home. The idea being that as hidden files in /home change from time to time, that these data files remain independent and unchanged. This would allow a different version of linux to be installed in a different partition on the SSD and also access those files, again allowing that install's hidden files to change without changing the data files. (I.e., as opposed to mounting sda6 as /home and hidden files would be subject to change caused by more than one install. Hope I (a) understand this and (b) am not being confusing here.)

Third question: As I wrote that last sentence, it occurs to me that for each link to 12.04, there would need to be a link to each other install (if any). Can there be multiple links to the same directory?

Fourth question: Is there any reason to have the /desktop at the end of this long string: 

Data/tmp/home/robert/Desktop

I think it can just as easily be

Data/Desktop by moving Desktop directly under Data and then deleting /tmp/home/robert/ . Have I got this right? (I know this is a very elementary question, but I have been a long time getting this far and don't want to blow it up.)

---

### Post by oldfred on 2014-01-24
When I moved my /home to my data partition, I just kept each folder at top level. And I mount in /mnt/data. The only reason I use /mnt over /media is that /media may show again with underscore at end of name in the left panel of Nautilus, but not work as already mounted.

I link in every install. And since I often install the new version several times, I found I was repeating many mount entries over & over or time for a script. I just copied my history to a text files and converted that to a script with a little editing. I also have same configuration of mounts on my laptop and copy data to laptop when travelling so I have the same data.

Not sure about the easiest way to change mount or if you can mount at the deeper level. I would expect so, but have not tried that.

I also stopped using spaces in any folder or file name with Linux as that can create issues. You have to modify commands to quote or escape the space. It just is easier to use under_score, CamelCase, or justonename.

If not moving folders to top level, you can just experiment for making mount permanent in fstab.

All these commands will need sudo, as I am copying from my script.
mkdir /mnt/data
chown $USER:$USER /mnt/data
#chmod 777 /mnt/data
#The big "X" will also not make files executable unless they were executable to begin with.Morbius1
chmod -R a+rwX /mnt/data

mv Music oldMusic
ln -s /mnt/data/..../Music  #where ... is the rest of you path

To see links you have created.
 Show links
find /home -type l
ls -lah | grep ^l

You can use rm command to remove links, but as with any deletion be careful. And with links do not mix link with actual path to data. I converted my actual data to a link once and lost all the data.

---

### Post by Odyssey1942 on 2014-01-24
Hello OldFred,

Thank you for your customary erudite reply. This gives me a lot to consider with respect to linking and it looks very helpful indeed.

Linking or binding or whatever are likely among my "how" options once I have determined where I want to go. As set out in the OP, there are four questions that I need to find answers to before I then consider the "how".

I have not yet responded hoping that others will weigh in with answers to the four questions. Additional input will be most welcome.

---

### Post by varunendra on 2014-01-25
> **Odyssey1942 said:**
> ..so that the directories and files in the list above show on my desktop (ie, what I see when the computer boots up), just as if they actually existed in /home/robert/Desktop.
....
So first question: Is this possible?
Yes it's possible. Quite easily if you can change the filesystem of /dev/sda6 to NTFS, also easy with EXT4 as long as it remains a single user system, but slightly tricky if the filesystem remains EXT(2/3/4) and is going to be a multi-user system.

**Advantage of changing to NTFS :** you'll be able to access the partition from Windows which you are dual-booting with (but make sure '[FastBoot]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")' is turned off in Windows, else any changes made to the files on that partition from linux will be lost when you boot to Windows 8).

**Downside of changing to NTFS :**
**1)** Writing to the partition from Linux will become much slower compared to EXT partitions. This is because the linux driver for ntfs is not as efficient as the native windows driver for it. Still, the speed should remain above 34 MB/s (as personally noticed by me many times).
**2)** Fragmentation problem, making the read/writes further slow in case the data on the partition is frequently written/modified. Arguably, linux filesystems almost never suffer from this problem.

**_How to Mount a Folder (Source) Inside Another Folder (Mount Point)_:** ..so that your source folder's contents appear in the Mount-point as if they were right there.

You can use the mount command's "--bind" option, or a "bind" mount in fstab file to achieve this. Please note that in every kind of mounting, the previously existing contents of the mount point disappear (not deleted, just not visible or accessible anymore) as long as the mounting is in effect, and instead it starts showing the contents of the target which is mounted there. The permissions of this mount point become the same as the permissions of the source, or as specified by the mounting options.

Without going in the mumbo-jumbo of details (unless you are interested and ask for them), here's an example of what should do what you want -

[indent]**Test before making things permanent -**
```
sudo mount --bind /media/Data/tmp/home/robert/Desktop Desktop
```
Now click on your Desktop, and press "F5" to refresh it. You should see the contents of your extracted Desktop folder, while any existing contents will disappear. This would be a "Test Successful". To get your previous desktop back -
```
sudo umount Desktop
```
..followed by another refresh.

Now, considering what oldfred mentioned about mount-points within /media, and I agree too, the following steps include removing the current custom mount point (/media/Data) from your /etc/fstab file (if it exists there and I assume it does), and replace it with a more suitable entry.

**1)** First, backup your current fstab file, just in case something is messed up and you need to return to original state -
```
sudo cp /etc/fstab /etc/fstab.bak
```

**2)** Now open the fstab file with root privileges -
**Alt-F2 > gksu gedit /etc/fstab**

**3)** Remove or comment out your current entry for the custom mountpoint (/dev/sda6), and instead add these lines at the end of your /etc/fstab file -
```
/dev/sda6	/mnt/Data	ext4	defaults	0	0
/mnt/Data/tmp/home/robert/Desktop	/home/robert/Desktop	none	bind
```
Proofread, save and close the file.

I have used the mount point /mnt/Data instead of /media/Data assuming we don't want an unnecessary icon on our desktop/filemanager when we are going to access it all from within our home. So it is not necessary, just one of the recommended ways.

It is also highly recommended to use the partition's UUID instead of its logical ID (/dev/sda**X**) because logical ID may change in certain situations, while UUID remains the same unless manually changed. An example entry with UUID -
```
UUID=e9eda802-77d1-4215-8f7f-185955149a97	/mnt/Data	ext4	defaults	0	0
```

**4)** You can create similar **'bind'** entries for other directories inside your extracted folder (tmp), specifying different mount points within your home. Probably a mount point for 'tmp' itself. You can also use a mixture of bind mounts and links as suitable. For example, to create a link to the /mnt/Data inside your home (so that you can access the whole partition from within your home) -
```
ln -s /mnt/Data
```
Although if you haven't already done this, you may have to take ownership of the mounted partition to have read/write access on it. Exactly as suggested in your previous thread [here]("http://ubuntuforums.org/showthread.php?t=2201318&p=12909074#post12909074").

**IMPORTANT:** The order of the entries in the /etc/fstab file are important, as mentioned in its man page ("man fstab") -
> The order of records in fstab is important because **fsck(8)**, **mount(8)**, and **umount(8)** sequentially iterate through fstab doing their thing, though  at boot time **mountall(8)** may process the file out-of-order when it believes it is safe to do so.[/indent]

So, assuming you want to mount each of these from the extracted folder (/mnt/Data/tmp/) - Desktop, Documents, Downloads, Music, Pictures, Videos..., **PLUS** a separate mount point for the whole partition itself (/mnt/Data) - into the folders of same name in your actual home, this should be what your /etc/fstab file look like *(leave the existing default entries to what they currently are, change the example UUID to what your /dev/sda6 has)* -
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3d062b75-d99d-4e0f-9219-ed3422d850da /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=7fd7d687-5957-4669-a88f-1c78c09cdd6c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

[COLOR="#FF0000"]# manually added by robert
[B]UUID=e9eda802-77d1-4215-8f7f-185955149a97	/mnt/Data	ext4	defaults	0	0
/mnt/Data	/home/robert/Data	none	bind[/B]
/mnt/Data/tmp/Desktop	/home/robert/Desktop	none	bind
/mnt/Data/tmp/Documents	/home/robert/Documents	none	bind
/mnt/Data/tmp/Downloads	/home/robert/Downloads	none	bind
/mnt/Data/tmp/Music	/home/robert/Music	none	bind
/mnt/Data/tmp/Pictures	/home/robert/Pictures	none	bind
/mnt/Data/tmp/Videos	/home/robert/Videos	none	bind[/COLOR]
```
**[COLOR="#FF0000"]A word of Caution ![/COLOR]**
While testing this in a Virtual Machine here (just two custom entries - the partition, and a folder inside it), I didn't even create the mount points, they were automatically created on reboot. Also, I have rebooted the virtual machine more than 10 times since the test, and the fstab is working as expected every time. BUT, considering this part of the fstab man page -
> though  at boot time **mountall(8)** may process the file out-of-order when it believes it is safe to do so.
.. you may wish to check [this post]("http://ubuntuforums.org/showthread.php?t=2192848&p=12870240#post12870240") out, as [earlier suggested]("http://ubuntuforums.org/showthread.php?t=2200667&p=12906243#post12906243") by oldfred in one of your previous threads.

If it is going to be a multiuser (or multi-linux-os) system, and you also want the data to be accessible from Windows, it is best to change the partition type to NTFS (with 'Fast Boot' off in win 8). You then only have to change "**ext4**" to "**ntfs**" in the partition mounting line in fstab, and don't have to worry about permissions. Otherwise, you *may* have to consider adding permission options in the fstab line, with a couple of added tricks as mentioned in this wiki page : [https://help.ubuntu.com/community/Bindfs-SharedDirectoryLocalUsers](https://help.ubuntu.com/community/Bindfs-SharedDirectoryLocalUsers)

To see why those added tricks are needed (creating a group, specifying permissions), read [this post]("http://ubuntuforums.org/showthread.php?t=1675381&p=10397228#post10397228") by Morbius1 (also recommended by oldfred earlier).

> Second question: Can I do this by linking or binding or is there a better method?
Linking is easier, binding a bit more work.
But binding has the advantage that you can do the mounting at folder level, and control the permissions at mount point. Besides, it makes the data appear more naturally (as if it exists in the mount point itself), and that is probably what you like more.

> Third question: As I wrote that last sentence, it occurs to me that for each link to 12.04, there would need to be a link to each other install (if any). Can there be multiple links to the same directory?
As far as I know, there is no limit to the number of symlinks, but you'll have to maintain them manually and individually. For example, if you change the name or move one of the targets, you'll have to manually and individually fix all the existing links to it. The same applies to 'bind' method also - you'll have to modify the fstab entries manually if you rename/move source directories.

> Fourth question: Is there any reason to have the /desktop at the end of this long string: 

Data/tmp/home/robert/Desktop

I think it can just as easily be

Data/Desktop by moving Desktop directly under Data and then deleting /tmp/home/robert/
No problem as long as you have write access on ..../Data. If not, you'll have to move using **sudo**, but that shouldn't affect the permissions on Desktop ('mv' preserves permissions, 'cp' changes them to current user's).

Hope I didn't miss anything, nor confused things. If I did, please ask whatever you need to know or be clarified. :)

---

### Post by Odyssey1942 on 2014-01-25
Varun, What a complete and clear reply. If every question on this forum got such a response, Microsoft might go out of business as ex-MS'ers flooded to Ubunutu. You have a real talent for this.
> also easy with EXT4 as long as it remains a single user system, 

1) This is my wife's computer and so 99.999%, maybe 100%, of the time will be a single user system. The only other person to either access it via lan or at the keyboard will be me, and if the latter, under her log-on. Also, this is a brand-new (and not yet really run-in user tested) so there is nothing on the desktop that needs to remain there.

And I prefer EXT4 as it is the preferred fs for Ubuntu and the less I have that has any connection with MS, the better. Having said that, the reason that I might access it over the lan would be to pull a file to my computer, also a 12.04, or push one to her, so again I don't think I need to switch to NTFS. But if I am missing anything in this, please comment.

Also, does "single user system" mean quite literally only one user for log-on purposes. I always set up each computer with an alternate user with the same name on every computer using the same very complex password. This is a JIC user so that if something goes pear shaped with my usual log-on, I have a fall-back. So far have never needed to use it on an Ubuntu computer (although occasionally in Win computers).  Should I not do this anymore to avoid whatever issues might be implicit in a "non-single user system"? I assume that the better name for a "non-single user system" is "multi-user", but in the context of this discussion, thought I should ask for confirmation.

2) If accessed from my computer over the lan, I assume that I should use her log-on to keep it a "single user system", but if in error and I can sign in otherwise, please advise.

3) Further on this: > If it is going to be a multiuser (or multi-linux-os) system, and you also want the data to be accessible from Windows, it is best to change the partition type to NTFS (with 'Fast Boot' off in win 8). Having dealt with multi-user above, the next item is "multi-linux-os". Does this not negate the whole advantage that OldFred speaks of and I mentioned in the OP? > The idea being that as hidden files in /home change from time to time, that these data files remain independent and unchanged. This would allow a different version of linux to be installed in a different partition on the SSD and also access those files, again allowing that install's hidden files to change without changing the data files. (I.e., as opposed to mounting sda6 as /home and hidden files would be subject to change caused by more than one install.  Or am I misunderstanding your caution here?

4) One possibility that we haven't considered is if she wants to access the Windows computer that sits between us which is used primarily for scanning, her Photoshop stuff, and will be used in future to access iTunes so that she can manage songs on her iPod. In particular she will want to bring files from that computer (currently XP, but soon to be Win 7) to hers. The middle computer's file system will of course be NTFS. Is this going to be a problem in the context of the above?

5) I think I am understanding your code and Morbius's post except this:

> sudo mount --bind /mnt/data/Music /home/morbius/Music He was speaking of binding data on another HDD (Ryan has the HDD mounted at /mnt/data/music). > I have a second hard drive that is 2 TiB that is mounted to /mnt/data currentlyIs the entire 2Tb mounted? And does the later "binding" alter this somehow?

I find this confusing. Why mount data if the next thing you do is make it available by binding it as he sets out? This question doubtless shows how little of this I understand, but hopefully a better understanding of this point will help to remove one more black dog. If you find my #5 confusing so far, you're not alone. I have re-written it several times.

Also: ```
mount --bind /mnt/data/Music /home/morbius/Music
mount --bind /mnt/data/Downloads /home/morbius/Downloads
mount --bind /mnt/data/Movies /home/morbius/Movies
end script
``` How would you rewrite one of the mount lines above using a sample UUID given the mount question above?

I'm out of time right now, so will go ahead and post this, even though I am not satisfied with some of it, especially #5. I know I will have add'l questions about the code to incorporate the "start on stopped mountall" bit, but later on that. Maybe the questions that this post raises in your mind about what I am trying to say will help me clarify my thinking. Thanks again.

---

### Post by oldfred on 2014-01-25
In this link Morbius1    mounts with fstab and then binds with auto scripts after mount - post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

I have never used bind, so not familiar with that.

If multiuser system then better to create groups with separate mounts and assign permissions & ownership by group. 

If you do not have Windows on your wife's PC, I would not use NTFS. Just like Ubuntu runs  fsck every 40 or 60 reboots, you need to run chkdsk on NTFS. Without Windows that can be difficult. You at least then need a Windows repair flash drive and use that occasionally.

To share with another Windows computer, you can use Samba. I shutdown Windows, and my two computers share with NFS. Even when running Windows XP on laptop and desktop, I found it easier to install Ubuntu on both systems and use NFS to copy data to NTFS data partition on laptop from NTFS partition on desktop. Every update to Windows XP, firewall or security seemed to reset Samba in Windows so I was constantly reconfiguring it. I gather it is a bit easier now. Morbius1 has many posts on that issue. It is important not to mix the two methods.
[http://ubuntuforums.org/showthread.php?t=1375183](http://ubuntuforums.org/showthread.php?t=1375183)  Morbius1
The two ways you can share folders are Nautilus-Share ( or Simple Sharing ) and "Classic Samba".

---

### Post by Odyssey1942 on 2014-01-25
Thanks for more good food for thought and a few lookups (e.g. NFS) for me.

In the referenced thread, which I am glad you mentioned as I forgot to ask before, Morbius said:
> Let's say you have a folder in the second partition labeled Music. To temporarily bind that directory to your Music directory you can run the following command:
```
sudo mount --bind /mnt/data/Music /home/morbius/Music
```
I still am not clear in my mind exactly what a mount is. I have some comfort that I know what it accomplishes (tells computer where to find something) Can anyone think of a non-computer analogy which would help me understand? Ideally a nuts and bolts (i.e. physical) analogy.

Morbius refers to a folder in the second partition, but doesn't say on which drive (Ryan does not mention partitions on the HDD). Also since the second partition on Ryan's SSD is root, I am understanding from what Morbius said is that (hypothetically) there is on the second partition on the HDD a directory labeled Music. Would that be correct?

If so, then as I understand it, the effect of the code above is that the files in Music on the second partition of the HDD appears in Ryan's /home directory (just as if they were actually located there) and this courtesy of the mount point at /mnt/data which links the two together. Is this correct?

My questions above are to anybody, not specifically OldFred as I know he likely will not answer them directly, but generally (just as above).

And again my apology for asking such basic questions, but I absolutely know that a house built on a weak foundation will have lots of problems. I am trying to build my foundation with such questions. (I.e., I am a Beginner.)

Last edited by Odyssey1942; 1 Minute Ago at 10:51 AM. Reason: posted to wrong thread

---

### Post by oldfred on 2014-01-25
In my post #2 I left out the mount command as I always auto mount with fstab. Generally you create a mount point, and mount a partition to that mount point. Then you can see the folders like Music or documents inside that mount. When you make the mount you can call it anything where in Windows it is just d:. So if you have one partition with just music you can make it /mnt/Music as a mount point or /media/Music. Or like I have a data partition with many folders. Then I mount /mnt/data and link each folder. Or you can bind each folder.

Mount may go back to the old mainframe days. Then you did not have a hard drive, but tape drives. So you told system you mounted tape a to a physical tape device.

Lots of reference info:
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

You can manually mount. But if auto mounted with Nautilus you have to unmount it first.
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data

This only applies to Linux formatted data partitions, NTFS only can be set with defaults when mounted.
Set permissions:
      sudo chmod -R a+rwX,o-w /mnt/data
Set ownership
sudo chown -R $USER:$USER /mnt/data
Once ownership & permissions are set for your data, you should not have to run those again, if remounting.

Note that you should never run the -R or recursive parameter on anything other than your data partitions. If run on a system partition you will have to reinstall to get correct ownership and permissions back.

---

### Post by varunendra on 2014-01-25
> **Odyssey1942 said:**
> ..the reason that I might access it over the lan would be to pull a file to my computer, also a 12.04, or push one to her, so again I don't think I need to switch to NTFS. But if I am missing anything in this, please comment.
No, I don't think we are missing anything, except that I thought it is going to be a dual boot with Windows 8. But even in that case switching to NTFS is not necessary, just recommended for sake of simplicity.

> Also, does "single user system" mean quite literally only one user for log-on purposes. I always set up each computer with an alternate user with the same name on every computer using the same very complex password.... Should I not do this anymore to avoid whatever issues might be implicit in a "non-single user system"?
The other user is not going to cause any complexities. The worst that can happen would happen to that 'other' user account, and that 'worst happening' is that they would only have 'read-only' access to the partition/its data (unless you perform the additional steps mentioned on the wiki page I linked to). I'm sure that is such a remote possibility, and so insignificant for you that you don't care. :)

> 2) If accessed from my computer over the lan, I assume that I should use her log-on to keep it a "single user system", but if in error and I can sign in otherwise, please advise.
I don't have enough practical experience with network sharing on Linux to be able to give any sound advice. What I can think or assume can be confusing. So I have nothing to add to what oldfred already mentioned about sharing. But based on my little network sharing experience (very little in fact), I don't think multiple users are ever going to be much of a problem. After all, Linux/Unix was designed to be a multiuser system. It is just the security concerns that makes the rights and permissions very discrete at access level, but everything is doable at any time when required.

> 3) Further on this:  Having dealt with multi-user above, the next item is "multi-linux-os". Does this not negate the whole advantage that OldFred speaks of and I mentioned in the OP?  Or am I misunderstanding your caution here?
Nothing really negates that. The 'Mounting' of the data partition directly in home will cause it to also bear the OS - specific user-configuration files, which would change depending upon the variations of OS and program versions, thus possibly causing problems at some point. The advantage he mentioned about linking over mounting is that these user-configuration files in the latter case would stay in their own separate home directories, while the users still being able to access the data using the links. Binding also allows that, just feels more natural and allows more control over permissions.

The problem that I (originally Morbius1) mentioned about linking is that while it is easy, by default it will access and save files with the default user permissions, and these permissions applicable to one user in one OS *may not* be same for the same user in the other OS (because even though the user names may be same, their UID/GIDs may be different by which their access rights are decided). The same problem will also arise in the simple 'bind mounting' type setup I proposed, but when (and if ever) it happens, it can be easily resolved by some added mounting options in fstab. It won't be that easy with linking.

And since these advanced permission bits don't exist in NTFS filesystem, there is no possibility of any such issues on it at all. That doesn't mean I am advocating NTFS (I stay away from NTFS as much as possible). While it is simpler for sharing, which is usually a one-time extra work, it will have permanent performance issues with Linux as pointed out earlier (speed, fragmentation, maintenance etc.). The point of having it only holds if the system is going to be a dual boot with Windows. Even in that case you can use Linux filesystem driver tools like EXT2FSd to access the partition from windows while keeping it EXT2/3/4, but that is not recommended as it opens the Linux partitions to same vulnerabilities (when accessing them from windows) that usually Windows suffers from (corruption caused due to crashes, viruses etc.).

> 4) ....In particular she will want to bring files from that computer (currently XP, but soon to be Win 7) to hers. The middle computer's file system will of course be NTFS. Is this going to be a problem in the context of the above?
Never. NTFS is only simpler, not a problem for Linux. The access permissions would only be needed to setup at sharing configuration level, and there would be nothing to worry about at filesystem level.

> 5) I think I am understanding your code and Morbius's post except this:

 He was speaking of binding data on another HDD (Ryan has the HDD mounted at /mnt/data/music). Is the entire 2Tb mounted? And does the later "binding" alter this somehow?
The entire 2TB was mounted at mount point "/mnt/data", thus making the data on the partition accessible (in /mnt/data). The 'bind' mounts thereafter were mounting the folder "music" on it to another mount point (the user's home/music). You can't mount a folder with mount if you can't access it first. So the traditional mounting is necessary before you can use binding.

The main differences are that the traditional mounting can't be done at folder level (only at block device level, which means the whole partition), and advanced permission control is not possible with it. The bind mount allows these extra capabilities, but it needs to access the source folders first for which it relies on the traditional mounting.

Hence in binding, the mounting is done in two parts - **1)** You mount the block device (a partition, a disk or some other storage device or file that can be treated as these) to be able to access the data on it. **2)** You use 'bind' to further mount this whole mount-point, or more discretely, the accessible directories in it with more control over permissions at its own specified mount-points. These mount points can be different other directories in your root hierarchy, or the traditional mounting's mount point itself (thus the folder mounting over itself - may sound silly, but having this capability has the advantage of more control over permissions that the traditional mounting couldn't allow).

> I find this confusing. Why mount data if the next thing you do is make it available by binding it as he sets out?
Mount it to make the data on the 'Device' (which you are mounting) accessible first, only then you can use bind to make the data available at more discrete level, with more control over permissions. To be able to access the source data, mounting is necessary. You don't need binding (or linking) if you are happy with accessing the whole data at its mount point (**/mnt/data** in our example).

> Also: ```
mount --bind /mnt/data/Music /home/morbius/Music
mount --bind /mnt/data/Downloads /home/morbius/Downloads
mount --bind /mnt/data/Movies /home/morbius/Movies
end script
``` How would you rewrite one of the mount lines above using a sample UUID given the mount question above?
You won't, you can't. These are bind mounts, mounting directories not a block device. The UUID is a property of block devices (e.g., the partition), not of files/folders. UUID can (and should) be used at initial mounting of the device. In a bind mount (or simply - 'Binding'), you are mounting (binding) the already accessible directories, not the device that is holding them.

Feel free to rebuke me if I made anything more confused (for example, I now feel that it was wrong to use the word 'bind mount' over and over. Using the word 'binding' could possibly have avoided some confusion). :)


**[SIZE=3]PS:[/SIZE]**

I started this post yesterday, fell asleep, and now noticed the further posts 'After' I started this one :P
I'll try an analogy you asked for -
> I still am not clear in my mind exactly what a mount is. I have some comfort that I know what it accomplishes (tells computer where to find something) Can anyone think of a non-computer analogy which would help me understand? Ideally a nuts and bolts (i.e. physical) analogy.
Apart from the tape-drive explanation of oldfred, you may consider an unmounted partition (or disk or any storage device) like the old gramophone record, or a modern optical disc (CD/DVD). You know that they *may* have something on them (a song, or dialogues, or nothing...), but you can actually access their contents only after putting them in the correct device that can 'read' them (a gramophone, or a DVD player). So these items have everything on them, but its meaningless until you put (mount) them in their respective correct devices.

Now consider putting a gramophone record in a CD player or a CD on a gramophone machine. You 'Mounted' them, but not in their respective correct places, so the machines won't know what to do with the disks. If you tried hard, you'll end up with a neatly 'scratched' CD and possibly a melted gramophone record (if the laser tried 'really hard'). ;)

Same is the case with mounting filesystems. If you mount an NTFS partition with and EXT driver, it won't find anything on it. Do it the opposite way and the result will be the same - nothing. Force mounting (if possible at all) a device with a wrong driver may cause a corrupted filesystem (a scratched CD), if the mounting or actions afterwards involved 'writing' to the filesystem.

Therefore the mount command tries to determine the filesystem type (if not explicitly specified) and use a correct driver for mounting. If it can't determine the filesystem, or if the required driver is not available, it will simply give up with a relevant error message.

Actually, there can be an interesting and a long discussion about mounting, but I hope the above clarifies its fundamental purpose and nature.

Also -
> If so, then as I understand it, the effect of the code above is that the files in Music on the second partition of the HDD appears in Ryan's /home directory (just as if they were actually located there) and this courtesy of the mount point at /mnt/data which links the two together. Is this correct?
Absolutely correct ! Once something is mounted, and you know and can access the mount point, it makes no difference where the data physically resides.

---

### Post by Odyssey1942 on 2014-01-26
I believe I got all of that, so much so that I have no questions about your explanation. And I do not find bind-mount confusing at all now that I (finally) have a clear idea about what the partition mount is actually doing. The analogy was good. Very helpful, (BTW, I had never thought about the fact that mount is only for devices, more specifically that it cannot be used at folder level. In retrospect, cannot imagine how I missed it. Just did.)

The only question that I have now is to clarify that hers is indeed a dual boot with Win 8 and to ask what impact that might have on the mounting and bind-mounts plan that now seems to be the way to go?

While it will be a dual boot machine, I plan to do all the hand holding necessary to enable everything she wants to do, done in 12.04 so that she never wants/needs to boot into Windows 8 (which she hates anyway so she will be patient). After all, there will be the Win 7 computer in between that she can turn to (and must for certain programs like iTunes). Worse comes to worse, she can sneaker-net files from the EXT4 partition onto a thumb drive and move them to the Win 7 machine.

I recognize that she can run itunes in wine, but I know nothing about it and do not want to introduce yet another level of complexity to the 12.04 system. She is nervous enough.

You may respond that the Win 8 makes the plan much more complicated, and if so, then I will want to consider a plan B. Not sure what that might be ("disabling" the grub loader so that Win 8 cannot be booted, or ???) so please give that some thought as a fall-back.

Thanks again for such a great answer.

---

### Post by varunendra on 2014-01-26
First of all, I would like to clarify that almost all of what I have suggested is nothing but the knowledge that came from oldfred's posts and the links he provided. I personally knew nothing about binding until I read the posts of Morbius1 that he linked to. I followed links, read them, seemed interesting, did some experiments and posted what I found.

So basically, almost everything of whatever I have proposed is actually just a presentation of information that was originally provided by oldfred to you. So all thanks goes to him, including mine for giving me something new to play with. :)

> **Odyssey1942 said:**
> The only question that I have now is to clarify that hers is indeed a dual boot with Win 8 and to ask **what impact that might have on the mounting and bind-mounts plan** that now seems to be the way to go?
Nothing.

When you are running Ubuntu, the whole windows installation is nothing but some files/directories lying aside on a different partition that you don't need to worry about.

When you are running Windows, it won't even see the EXT partitions (Ubuntu or the data partition, since both are on EXT4 partitions), so can't do any harm to it.

*IF* you ever decided to change the data partition to NTFS, or use EXT2/3/4 driver programs (like ext2fsd) on windows to access the ext partitions, only then there would be a little concern, and that would be to make sure that you don't intentionally or accidentally change the folder names or their locations from windows (plus, make sure Fast Boot is disabled, as being said many times by now, hope you don't mind me repeating it). This caution applies to Ubuntu also. If you changed the folder names/locations on the Data partition, you will need to manually correct the associated linkings/bindings.

> You may respond that the Win 8 makes the plan much more complicated
I honestly don't see any complications ahead. But I'll wait for a more experienced answer, obviously coming from the actually experienced person - oldfred. O:)

---

### Post by oldfred on 2014-01-26
Windows 8 has always on hibernation or fast boot. You must turn that off or you may have issues.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

I do not know Window 8 as my last Windows was XP and I essentially shut it down 2 years ago. But I started sharing a NTFS data partition. Originally using XP and trying to learn Ubuntu, my wife would want to check email and we had to reboot. And of course rebooting into Windows is a long process. Then I learned you can share the Thunderbird and Firefox profiles in a shared NTFS data partition. Those are not shared with links but with edits to profile.ini. Then I only had to boot Windows for that one app that I had used since DOS days and  was not ready to use the Linux not really equivalent. 

I would have a shared NTFS data partition as it is best not to write into the Windows system partition, reading is ok. I prefer smaller system partitions for both Windows and Linux and large data partitions. Very slight performance improvement as system data is closer together on drive so drive may be a bit quicker. Trade-off is that unused space is not shared. Default of just / (root) means all unused space can be used by system or data. But with new drives being very large a little extra in / , still leaves lots of space for data. 

My wife does not use iTunes. Not sure how well that works. She does everything on iPhone and iPad on those devices. I do back up photos to Ubuntu data partition and then to DVDs from iPhone. She uploads photos directly from the Windows version of Picasa running in .wine to Shutterfly.

---

### Post by DuckHook on 2014-01-26
...an insanely useful thread. One I'm filing away as a keeper subscription.

---

### Post by Odyssey1942 on 2014-01-26
Varun, Very considerate of you to credit OldFred for his valuable original work and contributions that you leaned on in composing your answers. I am in awe of OldFred, even though I usually only glean a little from each of his posts. He clearly has an exceptional grasp of this stuff, and yet has the modesty to say so when he does not.

But don't sell yourself short in this. Each time you post, I make significant strides in reaching my objective with the project. Thank you for all the time and thought you put into it.

That DuckHook, like me, found it enormously helpful is a tribute to both of you.

---

