---
title: "User and group management for shared directories"
date: 2016-11-06
forum: New to Ubuntu
---

### Post by dimitrib on 2016-11-06
Hi,


Until 2 years ago I was using Windows and since my switch on my desktop pc didn't have to login in Windows once so I'm happy Ubuntu has given me a nice alternative for Windows.


Before today, I only used the system for myself.


Today I wanted to install Ubuntu 16 on a laptop with 2 accounts; I'll list my demands:
* Account 'user1' is the account I installed the OS with. Security should be minimal, as little passwords as possible; if for security measures against hacking or whatever, I'm willing to enter my password for some critical stuff but I want the system to be as accessible as possible. On login I don't want to fill in a password nor do I want to fill in a keyring password on login or for every action I'm doing ...
* Account 'user2' has his own preferences (english / other language, applications, shortcuts etc.) but the system should be even more accessible for him. On startup, this account should start, as little possible number of password. He just wants to browse and surf a little bit with as little annoyances as possible.
* The data partition should be completely accessible by both accounts and guest accounts.


Quite easy demands, I thought ... after hours of work and searching google and forums:

[LIST]
[*]Data partition was not accessible by user2; only by user root ... so I needed to change the rights for the data folder
```
sudo chown :users /media/user1/data # to make the directory owner of group users
sudo chmod 770 /media/user1/data # to make the directory readable and writeable by group users and not by 3d parties
sudo chmod g+s /media/user1/data # to make new files and folders inherit permissions
```
[*]Oh do not forget to add   user2 to users
```
sudo useradd -a -G user2 users
```
[*]Things going through my head while searching and trying this - ranting: why isn't there an easy gui option for all this? Why should I bother finding shell commands for basic access for a folder? Why isn't something like this done by default? How hard can it be ... sigh ... Does someone really want to create a user without any rights at all?
[/LIST]

I still have following problems:

[LIST]
[*]On startup account 2 is logged in; nice; but upon accessing my data partition I'm greeted with "Authenication is required to mount <disk name> (DEV/ssa3)": ... password for user1.
...
Why do i get a password request for user 1 while I'm user 2??
[*]I swith to user 1. No password asked; nice. Click in Nemo on Devices/data: accessible: ok ... via cmd to /media; in this directory 2 other directories: user1 and user2
```
ls -al /media/user1 # data
ls -al /media/user2 / # empty
```
[*]Swith to user2: in Nemo try to access data gain: same password request for user1 ... ok i'll fill in my password for user1 ... ok ... files are viewable ... now when i check properties of data I can see /media/user2
[*]Let's go back to user1; In Nemo click on devices data: notice "could not display /media/user2/data" ...wtf it seems really my personnal mount is linked between accounts ... unmount ... request for password ... ok; mount again ah I can view my files again!
[*]Swith to user2: awww I can't view my files anymore
[*]and again ...
[*]Next if I startup and go to user1 account and access my data partition, after that switch to account user2 I get the message "Can not display '/media/user1/data'"
So apparently somehow my mount in user2 is linked to the mount in user1? Why isn't /media/user2/data mounted? ...
[*]Even on reboot I get asked for a password again to access the shared directory ...
[/LIST]

So it seems I can't access my data partition on 2 accounts without unmounting and mounting and filling in password because it somehow is linked cross accounts?


In another post I read I should mount /media/data to for exampe /dev/sda3; that worked but after a switch the same happened as before ... the mount disappears and it added to the user media again.



Long story short; is there a simple tutorial / guide / explanation how to add 2 users and let them both use a shared partition?


Conclusion for now: I'll just use 1 admin account; why bother with frustration about seemingly simple stuff ... sigh.

Thanks in advance for help.

---

### Post by Morbius1 on 2016-11-06
Believe it or not you didn't provide enough information to answer the question. If you want someone to help you provide the output of the following commands:

```
sudo blkid -c /dev/null -o list
```
```
cat /etc/fstab
```

---

### Post by dimitrib on 2016-11-06
[HR][/HR]Thanks for the quick response.


sudo blkid -c /dev/null -o list
device                                         fs_type         label            mount point                                        UUID
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                                      ext4                             /                                                  77a55ff4-76f5-4098-86a0-1b9bf446003c
/dev/sda3                                      ext4            data             /media/user1/data                                b9834bd7-c02e-4226-9543-7721341f871f
/dev/sda5                                      swap                             [SWAP]                                             9f09571c-2531-4a93-b651-d21132fe5c5e




cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=77a55ff4-76f5-4098-86a0-1b9bf446003c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9f09571c-2531-4a93-b651-d21132fe5c5e none            swap    sw              0       0

---

### Post by Morbius1 on 2016-11-06
Have the partition automount at boot would be the first step:

Unmount the partition:
```
sudo umount /media/user1/data
```
Create a mount point:
```
sudo mkdir /media/data
```
Edit /etc/fstab and add the following line at the bottom of the file:
```
UUID=b9834bd7-c02e-4226-9543-7721341f871f /media/data ext4 defaults 0 2
```
Mount the partition using:
```
sudo mount -a
```
Make sure it's mounted by going to /media/data in your file manager.

All of your chmod'ing and such should carry over to the new mount point but if for some reason it didn’t just redo it against /media/data.

Gatta Go ........

---

### Post by dimitrib on 2016-11-06
Xaxaxa that's why i love Ubuntu and the community; solutions can be so easy but you need to have the right command / do the right thing.

Did as you told; switched accounts; rebooted; everything works as I wish (for now).

Thanks a lot Morbius1!

---

