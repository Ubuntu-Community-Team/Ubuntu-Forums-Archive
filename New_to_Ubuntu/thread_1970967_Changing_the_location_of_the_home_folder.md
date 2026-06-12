---
title: "Changing the location of the home folder?"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by Zane Pepper on 2012-05-01
I am currently setting up a dual boot system with Ubuntu and Win7. I am  planning on having the 1 partition for Ubuntu, 1 for Win7 and 1 for all  my data. I was wondering how I would go about moving the folders inside  the home directory (downloads, documents, music, ect.) on to the data  partition. I know with Windows I would just go to properties on the  folder and change the location directory, but I am confused on how I  would go about it with Ubuntu.

---

### Post by oldfred on 2012-05-01
Welcome to the forums.

I use a ext3 data partition that has all my data folders from /home plus a few. I also have a NTFS shared data partition but only link a few things in. My Firefox & Thunderbird profiles are in my NTFS partition also but I use profile.ini to redirect to the profiles in the NTFS data partition.

You have to create a mount point, add that mount into fstab to permanent have it and link folders from that into /home.

I use shared as my name, it can be anything.
#find your UUID
sudo blkid
mkdir /mnt/shared
cp /etc/fstab /etc/fstab.backup
# my partition is sdc2 which has this UUID, you have to use yours and add this to fstab.
gksudo gedit /etc/fstab 
```
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /mnt/shared  ntfs-3g   defaults,uid=1000,nls=utf8,windows_names   0  0 

```# Verify no errors in fstab & remount with new mounts
mount -a

# I am not sure this does much as NTFS does not support permissions and the fstab really controls it.
chown $USER:$USER /mnt/shared
chmod 777 /mnt/shared

# for every folder in your shared that you want in /home, do this from /home/$USER which is you.
mv Music oldMusic
ln -s /usr/local/fred/data/Music

More explanation:
Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

If you want to share Firefox or Thunderbird profiles, this is really for both:
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by Zane Pepper on 2012-05-02
Holy crap that looks confusing, I am sure it will make more sense when I am actually doing it. I still have about 4 hours on the data backup before I can start though. Thank you for all the info.

---

### Post by Zane Pepper on 2012-05-04
Can anyone explain things a little more noob friendly to me? I can't seem to make heads or tails from oldfred's post. No offence oldfred, I am sure you did a great job explaining, it is just beyond my experience level with Linux. I am not sure what the # signs are for either.

Anyway, where I am at right now is, I have a partition with Windows on it, one with Ubuntu and a Data partition, I was able to link the Documents, Music, Pictures, ect. to the Data partition in windows just fine, but I can't figure it out with Ubuntu. I used a program called "NTFS Configuration Tool" (or something along those lines) to have my NTFS Data partition mount with the Ubuntu system. I am not sure this was the right or best way to do it, but like I said, I don't know my way around Linux that well yet. Any help is appreciated, but please try to keep it as simple as possible so I can understand better.

---

### Post by r-senior on 2012-05-04
I've been using Linux for 15 years and I had to read it a couple of times! :-k

If you have your data partition mounted, you've probably done most of it. Do you know where it is mounted in Ubuntu? It will probably be a path something like /mnt/ntfs.

---

### Post by coffeecat on 2012-05-04
> **Zane Pepper said:**
> I used a program called "NTFS Configuration Tool" (or something along those lines) to have my NTFS Data partition mount with the Ubuntu system.

Ah, the dreaded the ntfs-config, an application unmaintained since it was first developed years ago and still lurking in the repos. Sometimes it does a passable job, sometimes not. Let's see whether it has or not for you. Please open a terminal and post the output of these commands:

```
cat /etc/fstab
sudo blkid
sudo fdisk -lu
mount
ls -l /media
```

You can highlight the output of the output, right-click and copy to paste it into your post. Please post the output between [noparse]```
 and 
```[/noparse] tags to retain formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

If your data partition is being mounted properly, it's very easy to create symlinks (more-or-less equivalent to Windows' shortcuts) to your home folder, but let's check it is being mounted properly first.

---

### Post by Zane Pepper on 2012-05-04
> **r-senior said:**
> I've been using Linux for 15 years and I had to read it a couple of times! :-k

If you have your data partition mounted, you've probably done most of  it. Do you know where it is mounted in Ubuntu? It will probably be a  path something like /mnt/ntfs.

Not sure where it is mounted, I will have to check tomorrow though. I need to get to bed and I am currently restoring my files from my backup and I am booted into windows right now.

> **coffeecat said:**
> Ah, the dreaded the ntfs-config, an application unmaintained since it was first developed years ago and still lurking in the repos. Sometimes it does a passable job, sometimes not. Let's see whether it has or not for you. Please open a terminal and post the output of these commands:

```
cat /etc/fstab
sudo blkid
sudo fdisk -lu
mount
ls -l /media
```You can highlight the output of the output, right-click and copy to paste it into your post. Please post the output between [noparse]```
 and 
```[/noparse] tags to retain formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [IMG]http://ubuntuforums.org/images/editor/code.gif[/IMG] button in the message toolbar.

If your data partition is being mounted properly, it's very easy to create symlinks (more-or-less equivalent to Windows' shortcuts) to your home folder, but let's check it is being mounted properly first.

Wow, really? I had no idea it was so outdated and non-maintained. Sorry, I was not sure anyone was going to respond, so I am currently logged into windows and restoring the files from my backup. I will post the results though tomorrow after I get out of bed.

---

### Post by nothingspecial on 2012-05-04
The main PC in my house has an ntfs partition and the Music and Pictures folder are mounted in my wife's home

First the partition itself is mounted at boot using /etc/fstab like this


```
LABEL=Stuff /media/Stuff ntfs-3g defaults,en_GB.utf8 0 0
```

I have used a label instead of the uuid for readability

Then further down the fstab file we bind the Music and Picture folder to her home directory like so

```
/media/Stuff/Music/ /home/suzie/Music  none  bind
/media/Stuff/Pictures/ /home/suzie/Pictures  none  bind

```

I hope I have not confused the issue further

---

### Post by oldfred on 2012-05-04
The # are comments, so they are not commands to be run.

I like nothingspecial's suggestions. I still plan to convert to using labels and I think we do not suggest or use labels as much as we should. It does make it less confusing, but you have to label your partition. The use of bind is also recommended by many if connecting computers on a network. I do not so my linking works.

Post the output that coffeecat suggested and whoever is one line can help you.

---

### Post by Zane Pepper on 2012-05-04
> **nothingspecial said:**
> The main PC in my house has an ntfs partition and the Music and Pictures folder are mounted in my wife's home

First the partition itself is mounted at boot using /etc/fstab like this


```
LABEL=Stuff /media/Stuff ntfs-3g defaults,en_GB.utf8 0 0
```I have used a label instead of the uuid for readability

Then further down the fstab file we bind the Music and Picture folder to her home directory like so

```
/media/Stuff/Music/ /home/suzie/Music  none  bind
/media/Stuff/Pictures/ /home/suzie/Pictures  none  bind

```I hope I have not confused the issue further

 I don't have permission to modify the fstab file, how do I get permission to do so?

---

### Post by coffeecat on 2012-05-04
> **Zane Pepper said:**
> I don't have permission to modify the fstab file, how do I get permission to do so?

Use this to edit fstab:

```
gksu gedit /etc/fstab
```

But don't do that until you've posted the outputs I suggested. nothingspecial's bind lines are a good way of linking your data partition to your home folder. The symlinks I mentioned constitute a different but valid way for the same end. But it's best if we see that output first.

---

### Post by Zane Pepper on 2012-05-04
> **coffeecat said:**
> Use this to edit fstab:

```
gksu gedit /etc/fstab
```But don't do that until you've posted the outputs I suggested. nothingspecial's bind lines are a good way of linking your data partition to your home folder. The symlinks I mentioned constitute a different but valid way for the same end. But it's best if we see that output first.

 Whoops, I forgot you wanted me to run those. Well, I was able to edit it and I modified the fstab file, now my folders are linked like I wanted. I did back up the fstab file to my documents before I modified it, but it seems to be missing now. I guess when I binded the folders together it deleted it? I would have restored it, but now I can't. Do you want me to run them anyway?

---

### Post by Zane Pepper on 2012-05-04
Here is the output.

```
zane@zane-Satellite-L305:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=cc4f806c-283b-4968-b6f7-56a0ad933434    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda7 :
UUID=2aa9cb58-1a85-4cb5-919a-4c3d17ec8ef4    /home    ext4    defaults    02
#Entry for /dev/sda4 :
LABEL=Data /media/Data ntfs-3g defaults,en_GB.utf8 0 0
#Entry for /dev/sda6 :
UUID=caa230eb-4614-45c8-8d82-d3e0a8dbb05d    none    swap    sw    0    0

/media/Data/Documents /home/zane/Documents none bind
/media/Data/Downloads /home/zane/Downloads none bind
/media/Data/Music /home/zane/Music none bind
/media/Data/Videos /home/zane/Videos none bind
/media/Data/Pictures /home/zane/Pictures none bind
```


```
zane@zane-Satellite-L305:~$ sudo blkid
sudo: /etc/sudoers is mode 0777, should be 0440
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin
```


```
zane@zane-Satellite-L305:~$ sudo fdisk -lu
sudo: /etc/sudoers is mode 0777, should be 0440
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin

```
I think the 0777 bit is from me modifing the permissions with a code I found online so I could edit the files in /etc/

```
zane@zane-Satellite-L305:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda7 on /home type ext4 (rw)
/dev/sda4 on /media/Data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/media/Data/Documents on /home/zane/Documents type none (rw,bind)
/media/Data/Downloads on /home/zane/Downloads type none (rw,bind)
/media/Data/Music on /home/zane/Music type none (rw,bind)
/media/Data/Videos on /home/zane/Videos type none (rw,bind)
/media/Data/Pictures on /home/zane/Pictures type none (rw,bind)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/zane/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=zane)
```


```
zane@zane-Satellite-L305:~$ ls -l /media
total 4
drwxrwxrwx 1 root root 4096 May  4 05:10 Data

```

---

### Post by coffeecat on 2012-05-04
Before we go any further.

> **Zane Pepper said:**
> 
I think the 0777 bit is from me modifing the permissions with a code I found online so I could edit the files in /etc/

Have you given 777 permissions to any system files apart from /etc/sudoers? If you have given 777 permissions to more than a few files, you have effectively broken your system. And as for an online howto that tells you to give 777's to files in /etc so that you can edit them - I am speechless! :(

Have a look here:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Boot into recovery mode and case 3. But this will only do for false permissions on /etc/sudoers.

---

### Post by Zane Pepper on 2012-05-04
> **coffeecat said:**
> Before we go any further.



Have you given 777 permissions to any system files apart from /etc/sudoers? If you have given 777 permissions to more than a few files, you have effectively broken your system. And as for an online howto that tells you to give 777's to files in /etc so that you can edit them - I am speechless! :(

Have a look here:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Boot into recovery mode and case 3. But this will only do for false permissions on /etc/sudoers.

I applied it to the whole /etc/ directory. I think I will just reinstall Ubuntu and start over, if like you said, I broke my system.

---

### Post by coffeecat on 2012-05-05
> **Zane Pepper said:**
> I applied it to the whole /etc/ directory. I think I will just reinstall Ubuntu and start over, if like you said, I broke my system.

Whether you applied 777 permissions to just the folders and files in /etc, or recursively to the whole of /etc, repairing that would be a task of such time-consuming magnitude, that I doubt it's feasible. I'm sorry you had to learn the potentially dangerous power of terminal commands run with sudo the hard way. Good luck with the re-install, and don't hesitate to post if you need help with setting up your data partition.

The method nothingspecial posted for binding folders in your data partition to your home folder is a very elegant way of doing things, but for the record I'll post details of setting up symlinks entirely using the GUI. That gives you a choice. Most people use the ln command in the terminal for creating symlinks, but there is a GUI way. Let's say there is a folder called "Projects" in your data partition.

1 - Open a nautilus (file browser) window for each of your home folder and data partition.

2 - Right-click on the Projects folder in your data partition and choose "Make link". A symlink (folder with an arrow symbol) appears called "Link to Projects".

3 - Drag and drop the Link to Projects folder into your home and then delete the Link to Projects folder in the data partition.

4 - You can rename "Link to Projects" to just "Projects" with a right-click if you want. Repeat for any other folders you need symlinks for. If you are symlinking Music, Pictures, etc, you'll need to delete the folders with those names in home first.

---

### Post by Zane Pepper on 2012-05-05
> **coffeecat said:**
> Whether you applied 777 permissions to just the folders and files in /etc, or recursively to the whole of /etc, repairing that would be a task of such time-consuming magnitude, that I doubt it's feasible. I'm sorry you had to learn the potentially dangerous power of terminal commands run with sudo the hard way. Good luck with the re-install, and don't hesitate to post if you need help with setting up your data partition.

The method nothingspecial posted for binding folders in your data partition to your home folder is a very elegant way of doing things, but for the record I'll post details of setting up symlinks entirely using the GUI. That gives you a choice. Most people use the ln command in the terminal for creating symlinks, but there is a GUI way. Let's say there is a folder called "Projects" in your data partition.

1 - Open a nautilus (file browser) window for each of your home folder and data partition.

2 - Right-click on the Projects folder in your data partition and choose "Make link". A symlink (folder with an arrow symbol) appears called "Link to Projects".

3 - Drag and drop the Link to Projects folder into your home and then delete the Link to Projects folder in the data partition.

4 - You can rename "Link to Projects" to just "Projects" with a right-click if you want. Repeat for any other folders you need symlinks for. If you are symlinking Music, Pictures, etc, you'll need to delete the folders with those names in home first.

I am not too upset I broke it, I learn best from trial and error. I got a fresh install running now and I have my Data partition mounted using nothingspecial's method, editing the fstab file the right way (how you told me). Everything seems to be working fine, no errors and what not. Thank you for your alternate method of doing it, I will try that out next time I have to re-set-up my system.

Thank you everyone for your help, I really appreciate it.

---

### Post by Zane Pepper on 2012-05-05
New question, I noticed that when I delete a file on my NTFS Data partition it deletes it fully and will not send it to the recycle bin. Is there any way to fix this?

---

### Post by coffeecat on 2012-05-05
> **Zane Pepper said:**
> New question, I noticed that when I delete a file on my NTFS Data partition it deletes it fully and will not send it to the recycle bin. Is there any way to fix this?

Yes, you need a "uid=1000" or the uid of your account (which is almost certainly 1000) in the mount options in your /etc/fstab line for the ntfs partition. Based on what you posted before, I guess you have "defaults,en_GB.utf8" at the moment. If you change this to "defaults,en_GB.utf8,uid=1000" trashing a file should send it to your trash. If you need help, post the contents of your /etc/fstab file from your new system.

I'd suggest one other thing too. Try this:

```
defaults,en_GB.utf8,uid=1000,windows_names
```

The windows_names option ensures that Microsoft forbidden characters (such as : ) don't get written in filenames. Some characters which Microsoft disallows are permissible in Unix and Linux will happily use them in filenames when writing files to NTFS filesystems. Strangely, ntfs will happily accept them and display them so long as you are using Linux. Problems start when you try to see the files in Windows which gets quite flummoxed by them. :)

---

### Post by Zane Pepper on 2012-05-05
> **coffeecat said:**
> Yes, you need a "uid=1000" or the uid of your account (which is almost certainly 1000) in the mount options in your /etc/fstab line for the ntfs partition. Based on what you posted before, I guess you have "defaults,en_GB.utf8" at the moment. If you change this to "defaults,en_GB.utf8,uid=1000" trashing a file should send it to your trash. If you need help, post the contents of your /etc/fstab file from your new system.

I'd suggest one other thing too. Try this:

```
defaults,en_GB.utf8,uid=1000,windows_names
```The windows_names option ensures that Microsoft forbidden characters (such as : ) don't get written in filenames. Some characters which Microsoft disallows are permissible in Unix and Linux will happily use them in filenames when writing files to NTFS filesystems. Strangely, ntfs will happily accept them and display them so long as you are using Linux. Problems start when you try to see the files in Windows which gets quite flummoxed by them. :)

Here is the contents of my fstab file.
```
zane@zane-Satellite-L305:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=dc776db0-d433-4d43-bda2-9819280b7cb5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=acfec264-1e34-40c6-b04d-ad37762de839 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=caa230eb-4614-45c8-8d82-d3e0a8dbb05d none            swap    sw              0       0

# Custom modifications
LABEL=Data /media/Data ntfs-3g defaults,en_GB.utf8 0 0

/media/Data/Documents/ /home/zane/Documents  none  bind
/media/Data/Downloads/ /home/zane/Downloads  none  bind
/media/Data/Music/ /home/zane/Music  none  bind
/media/Data/Videos/ /home/zane/Videos  none  bind
/media/Data/Pictures/ /home/zane/Pictures  none  bind
```

---

### Post by coffeecat on 2012-05-05
First, check that your uid is 1000 with this terminal command:

```
id
```

If yours is the first created account, then it will be. If you are running more than one account, then things get complicated. Change this in /etc/fstab:

```
# Custom modifications
LABEL=Data /media/Data ntfs-3g defaults,en_GB.utf8 0 0
```

To look like this (I've added a few spaces between some of the fields - it's easier to read that way):

```
# Custom modifications
LABEL=Data     /media/Data     ntfs-3g     defaults,en_GB.utf8,uid=1000,windows_names     0 0
```

---

### Post by Zane Pepper on 2012-05-06
> **coffeecat said:**
> First, check that your uid is 1000 with this terminal command:

```
id
```If yours is the first created account, then it will be. If you are running more than one account, then things get complicated. Change this in /etc/fstab:

```
# Custom modifications
LABEL=Data /media/Data ntfs-3g defaults,en_GB.utf8 0 0
```To look like this (I've added a few spaces between some of the fields - it's easier to read that way):

```
# Custom modifications
LABEL=Data     /media/Data     ntfs-3g     defaults,en_GB.utf8,uid=1000,windows_names     0 0
```

Ok, I my id was 1000 and I did the changes you said with out problem. Now when I delete something it makes a folder called .Trash-1000 and puts the file in there, but not in the normal trash bin. Is there any way to have it appear in the normal trash bin on the launcher?

---

### Post by coffeecat on 2012-05-06
> **Zane Pepper said:**
> Ok, I my id was 1000 and I did the changes you said with out problem. Now when I delete something it makes a folder called .Trash-1000 and puts the file in there, but not in the normal trash bin. Is there any way to have it appear in the normal trash bin on the launcher?

That's how it works - it does appear in your launcher trash bin. If you delete something in your home folder, it gets moved to ~/.local/share/Trash/files/. In your data partition, a deleted file gets moved to .Trash-1000/files/. Both, though, will cause the trash icon in the launcher to show crunched up paper. If you delete files from both your home folder and from the data partition, you'll see them all mixed up when you open a file browser window from the trash icon. That's all by design and is analogous to the way Windows does things with a $RECYCLE.BIN folder (which is hidden in Windows) in each partition, but all deleted files from whichever partition appearing in the graphical recycle bin when you open an Explorer window.

If you use USB drives and delete things, you'll find them in .Trash-1000 folders in the USB drive, not physically in your home folder, but they still appear in your graphical trash. MacOS does exactly the same thing except it calls the hidden trash folder .Trashes (if I remember correctly).

---

### Post by Zane Pepper on 2012-05-06
> **coffeecat said:**
> That's how it works - it does appear in your launcher trash bin. If you delete something in your home folder, it gets moved to ~/.local/share/Trash/files/. In your data partition, a deleted file gets moved to .Trash-1000/files/. Both, though, will cause the trash icon in the launcher to show crunched up paper. If you delete files from both your home folder and from the data partition, you'll see them all mixed up when you open a file browser window from the trash icon. That's all by design and is analogous to the way Windows does things with a $RECYCLE.BIN folder (which is hidden in Windows) in each partition, but all deleted files from whichever partition appearing in the graphical recycle bin when you open an Explorer window.

If you use USB drives and delete things, you'll find them in .Trash-1000 folders in the USB drive, not physically in your home folder, but they still appear in your graphical trash. MacOS does exactly the same thing except it calls the hidden trash folder .Trashes (if I remember correctly).

That is not what it is doing though. If I go into, lets say, my Music folder directly from my Data partition and delete something it shows up in the recycle bin like it is supposed to. If I get to Music by going through Home and delete a file, it ends up deleting the file but it does not show up in the recycle bin. Instead, it makes a new .Trash folder in the Music folder and moves the file there. It is really annoying.

Do you think it may have something to do with how I binded the folders together in the fstab file?

---

### Post by coffeecat on 2012-05-07
> **Zane Pepper said:**
> 
Do you think it may have something to do with how I binded the folders together in the fstab file?

Possibly. That's an interesting observation. I'll do some investigation and post back later - possibly not for a few hours. I need to try something on my machine with a NTFS data partition which I'm not using at the moment.

---

### Post by coffeecat on 2012-05-07
I forgot that I had a spare ntfs partition on my main machine! Experiment done.

You are right - it's the bind method that's causing the problem. If you create symlinks, however, in the way I described and remove the bind lines, the issue goes away and deleting files works as it should with deleted files sent to .Trashes-1000 in the root of the NTFS filesystem.

There is one aesthetic disadvantage which is easily overcome. Take the Music folder for example. The default Music folder has a special folder icon to distinguish it from others. Ditto Videos, and so on. If you delete your default Music folder and replace it with a symlink folder, the icon for the symlink folder is a generic symlink one with a curved arrow. If you want to change this, have a look here:

[http://askubuntu.com/questions/79110/how-can-i-assign-custom-icons-to-folders](http://askubuntu.com/questions/79110/how-can-i-assign-custom-icons-to-folders)

The folder icons you will need are in /usr/share/icons/Humanity/places/48/.

---

### Post by Zane Pepper on 2012-05-07
> **coffeecat said:**
> I forgot that I had a spare ntfs partition on my main machine! Experiment done.

You are right - it's the bind method that's causing the problem. If you create symlinks, however, in the way I described and remove the bind lines, the issue goes away and deleting files works as it should with deleted files sent to .Trashes-1000 in the root of the NTFS filesystem.

There is one aesthetic disadvantage which is easily overcome. Take the Music folder for example. The default Music folder has a special folder icon to distinguish it from others. Ditto Videos, and so on. If you delete your default Music folder and replace it with a symlink folder, the icon for the symlink folder is a generic symlink one with a curved arrow. If you want to change this, have a look here:

[http://askubuntu.com/questions/79110/how-can-i-assign-custom-icons-to-folders](http://askubuntu.com/questions/79110/how-can-i-assign-custom-icons-to-folders)

The folder icons you will need are in /usr/share/icons/Humanity/places/48/.

It works perfect with symlinks, thank you for all the help you have given me. Everything seems to be working perfect now. The icons don't bother me, they look the same except they have a little arrow on them.

---

