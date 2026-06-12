---
title: "Getting Thunderbird to work in Ubuntu and Windows"
date: 2014-06-14
forum: New to Ubuntu
---

### Post by Middo on 2014-06-14
Hi All,

I have recently installed Ubuntu as a dual boot with Windows 7.  The Ubuntu is worrking well, but I wanted to be able to use Thunderbird data in both Windows and Ubuntu.  From what I can see, I need to mount the windows partition first, but I have followed a couple of tutorials and can't seem to do this.  One tutorial said to make a directory called /mount/WindowsDrive, but when I tried, it did this:

middleton@middleton:~$ mkdir /mount/WindowsDrive
mkdir: cannot create directory ‘/mount/WindowsDrive’: No such file or directory

I was trying to follow the tutorial from here:

[http://www.computerandyou.net/2011/05/how-to-mount-a-windows-partition-on-linux-automatically-on-each-start-up/](http://www.computerandyou.net/2011/05/how-to-mount-a-windows-partition-on-linux-automatically-on-each-start-up/)

which came from the thread on using Thunderbird here:

[http://ubuntuforums.org/showthread.php?t=1840521](http://ubuntuforums.org/showthread.php?t=1840521)

Doing stuff in terminal is new to me, so I may be doing something wrong which is obvious to others.  I would be grateful for any help.

---

### Post by vanadium on 2014-06-14
You can now use the "Disks" utility to configure your Windows partition so that it is automatically mounted during startup. Once this is done, you can have the Thunderbird version in Ubuntu use the same configuration folder as your Windows version of Thunderbird merely by linking that folder in Ubuntu to the folder in Windows. Some caveats

1) Make sure you keep the ntfs partition "clean" before using Ubuntu. This means that you must fully shutdown Windoew before going to Ubuntu (no hibernate).
2) Make sure you use the same version of Thunderbird under both systems (may not be a real issue usually, but just to be safe).

---

### Post by SeijiSensei on 2014-06-14
> middleton@middleton:~$ mkdir /mount/WindowsDrive
mkdir: cannot create directory &#8216;/mount/WindowsDrive&#8217;: No such file or directory

There is no "/mount" directory.  Probably what you read was referring to the "/mnt" directory, a staple of Unix systems for decades.  However, even if you tried to create "/mnt/WindowsDrive" using the command above, it would have failed.  Only the "root" or administrative user can create directories on most of the system.  Users can create directories in their home directory, /home/username, and in /tmp.  Otherwise you need root privileges using the program called sudo like this:
```
sudo mkdir /mnt/WindowsDrive
```
You'll be prompted to enter your password to authenticate.

I have a Windows partition mounted as /windows.  I prefer lower-case and shorter directory names since I spend a lot of time typing at the terminal.

---

### Post by oldfred on 2014-06-14
Also better not to use the Windows system partition. The Linux NTFS driver exposes all the normally hidden files & folders and Windows just does not like too much activity in its system.
But creating another NTFS partition and moving Firefox & Thunderbird profiles to that data partition then lets you set Windows system as read only and NTFS data as read/write.

I share a NTFS partition with Windows XP since 2006 (actually then it was FAT32, but changed to NTFS in 2009).

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

I add a entry in fstab.
New fstab entry with NTFS shared partition
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657 /mnt/shared ntfs-3g defaults,uid=1000,nls=utf8,windows_names 0 0

I link mnt/shared into /home so it is easy to access. From my home:
ln -s /mnt/shared

Then you have to start Thunderbird once to create a default, but then edit the profile to use the profile in the shared partition. I created a folder called mozilla in my shared and under mozilla I have both thunderbird & firefox folders where the profiles are.
> [General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/home/fred/shared/mozilla/thunderbird/profiles/lyu25irb.default
Default=1


---

### Post by Middo on 2014-06-15
Thanks for the replies.  When I used the disks utility, I found that the windows drive was already mounted.

So I deleted Thunderbird from Windows, reinstalled it, and it seemed to work.  I copied the profile so that Ubuntu uses the windows profile.  So far so good, it sends and receives emails

But, ever time I go into Ubuntu, Thunderbird tells me it cannot find the profile.  I copy and past the exact same path into the profile.ini file, deleting the old one, and it works fine.  Any ideas?

---

### Post by oldfred on 2014-06-15
Do you have your partition mounted by fstab so it will always be mounted when you reboot?

post fstab & profile.ini

---

### Post by Middo on 2014-06-16
OK,

I hope I am doing this correctly.  It is actually quite hard to find how to get the fstab listed as a noob.  I got the following, and I hope it helps:

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=b73f2fe7-f5c7-43bb-a8da-e72b46471bbb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e4af7ade-a843-42e0-8d78-a2bfa42d3730 none            swap    sw              0       0


and the profiles.ini file says:

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/media/middleton/D23A802F3A801321/Users/Ian Middleton/AppData/Roaming/Thunderbird/Profiles/g18fzuev.default


If I copy the path from the profile file on the windows side, and repaste it, it looks exactly the same, but now Thunderbird can start.  So confused at the moment about it.

---

### Post by oldfred on 2014-06-16
You do not have a permanent mount in fstab, so you have to manually mount the location with profile for Thunderbird to be able to see it.
By looking for location to copy it into your profile.ini, you are mounting it and then it works.

You need to create a permanent mount. And each partition can only be mounted once. One advantage of Linux is you use a name or label for your mounts that can mean something as opposed to just d: or e:.

Better to create a shared NTFS data partition. Windows does not like too much activity inside its system partition. You cannot hibernate either way. Also the Linux NTFS driver exposes all the hidden files & folders.

If you mount in /media you may see two entries in Nautilus, a second one with a underscore at the end that does not work. If you mount in /mnt it will not be shown in Nautilus except by drilling down thru system.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mout to.
[http://ubuntuforums.org/showthread.php?t=2227574](http://ubuntuforums.org/showthread.php?t=2227574)

    
 For ntfs UUID shown is example only see below:
```
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:


 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD

      
 ** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab


 ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

Example for read only mount:
Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862](http://ubuntuforums.org/showthread.php?t=2043862):
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0

UUID is prefered method to mount as that rarely changes, where drive order may change more often.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Middo on 2014-06-21
Thanks Old Fred, I have now got it to work.  It took me a while to realise that I didn't have the necessary software to do the "gksu gedit" type command.  I have mounted the windows drive in fstab.  I know this is a little dangerous, but I never hibernate my windows, and am only using the thunderbird files at the moment.  Next is onto my music and pictures.

---

