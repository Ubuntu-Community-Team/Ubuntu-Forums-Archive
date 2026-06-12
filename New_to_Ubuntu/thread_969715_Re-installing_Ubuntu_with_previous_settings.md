---
title: "Re-installing Ubuntu with previous settings"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by ubalderdash on 2008-11-03
My PC is an ACER Aspire T180 with Nvidia GeForce integrated graphics and 4Go of Corsair DDR2 RAM

I've only been using Ubuntu for a few weeks but was excited by the new and "Recommended" upgrade to the Intrepid Ibex. All went as planned until the computer rebooted; it goes past the first Ubuntu logo splash screen but then goes black with five lines of text ending with...
"Running local boot scripts (/etc/rc.local)"

I've spent the entire weekend trawling through forums but although this problem is evidently not unusual it would appear to be insurmountable as far as my Nvidia Geforce 6100 video card is concerned.

However, not wishing to change my PC yet I wonder if anyone can help me to get back into my original 8.04 version and recover all my files and settings?

---

### Post by Bölvaður on 2008-11-03
*deleted* double post

---

### Post by Bölvaður on 2008-11-03
this is fairly easy.

Lets just look at where the settings are kept: **/home**
This is the place where all your personal data are probably also kept.

So somehow you have to have the same /home in the new installation. There are many ways to do that, depending on your situation and what you are trying to do exactly.

One way to do this is:

1. Get portable harddisk drive and connect to your computer.
2. Get some live cd.
3. Boot up of the live cd
4. Copy your /home to the portable hard disk drive
5. Make sure the data are on there (because _you do not want to lose any data_) and then disconnect the portable harddisk
6. Install Ubuntu 8.10 as a fresh install (over the existing one)
7. Place the old /home from the portable harddisk over the new /home (placing all old data and settings into the new os)

You might need to change owner of the files and folders:

change user: chown username /home
change rights: chmod 766 /home   (you may need to read more about this command and take 10 minute course in binary&#8594;decimal)

I guess you can do all that by running the file manager as root.
Press: Alt+F2
type:  gksu nautilus
And then you can change users and rights like you want.


The easiest way is to keep the same settings is to have separate /home partition that you just mount unchanged to your new installation (chose it during the installation in manual when picking how to do the partitions)

---

### Post by ubalderdash on 2008-11-03
Thanks Bölvaður, I'm going to try this and will get back to you later.
The first part sounds easier than the second part, but let's see how far I get first :-)

---

### Post by ubalderdash on 2008-11-04
Bölvaður, After copying the first "Home" file I realized it did not contain my files. I returned and managed to find my real "Home" folder but could not copy it as I am, apparently, not the owner. Although you mention changing the owner and the owner's rights, I do not feel so competent about doing this. Particularly as you suggest I should read up on it first. Can you suggest anywhere that might have a tutorial on this subject?

---

### Post by handydan918 on 2008-11-04
This is an excellent example of the benefits of putting /home on it's own partition. 
Just get your old /home copied off the disk to some safe medium, cd/dvd, flashdrive, whatever, and reinstall. Then you can simply copy the old /home onto the current /home and do whatever renaming, chowning is needed. 
Note: chowning something as a user will obviously require the use of sudo...

---

### Post by tarps87 on 2008-11-04
Possibly a quick solution, instead of copying the /home folder try copying the folder /home/username this should have the same outcome.

Also to copy you should only need to do ```
chmod a+r /home
```
If the user you create on the new installation has the same name you will not need to change the owner of the folder (chown)

I don't know of an good tutorials on chown but```
man chown
``` will tell you about the command. You can try making a couple of folders and changing the permissions of them, as long as you **do not** use the command sudo (this will give you root privileges) you will not break the system.

The basics on chmod:

```
chmod a+r filename
```
a = all
can also be:
u = user/owner
g = group
o = other

+ = add permissions
- = remove permissions

r = read permissions
can also be:
w = write permissions
x = executable permissions

The basics on chown:

```
chown user:group filename
```

user: is the name of the user that will own the folder/file
group: is the name of the group will own the folder/file (usually the same as the users name)
filename: the file or folder name to change the owner of

---

### Post by Dojan5 on 2008-11-04
The best thing would be to reinstall Ubuntu.
> **Bölvaður said:**
> 
1. Get portable harddisk drive and connect to your computer.
2. Get some live cd.
3. Boot up of the live cd
4. Copy your /home to the portable hard disk drive
5. Make sure the data are on there (because _you do not want to lose any data_) and then disconnect the portable harddisk

Just to make a note to the future:
If you don't have any external drive, you can shrink the partition and create a new partition.

Another thing regarding partitioning, when installing Ubuntu, make two partitions. Make one that is mounted as / and another that is mounted as /home, that way you won't loose your files unless you check the format button upon next install.

---

### Post by ubalderdash on 2008-11-05
I came to "Absolute Beginner Talk" because I hoped to find simple answers aimed at Ubuntu novices who don't yet understand all that 'Silly Stuff'. Yet again I became lost in all the silly stuff but eventually found the solution on another, non ubuntu, forum.

All I had to do to solve all my increasing worries was to re-install Windows XP SP3. Now, at least, I can get back to work and stop wasting time in undeveloped and buggy software.

---

### Post by tarps87 on 2008-11-05
I do not think installing xp is the solution to your question:
"However, not wishing to change my PC yet I wonder if anyone can help me to get back into my original 8.04 version and recover all my files and settings?"
Installing xp will remove all your files.
Your problem is probably not due to "undeveloped and buggy software" it is down to the graphic manufactures being reluctant to support open source OS.
Bölvaður solution is a simple solution and following the commands would do exactly what you wanted. The explanations were provided as you asked for them.
Remember everyone here are volunteers and are only trying to help

---

