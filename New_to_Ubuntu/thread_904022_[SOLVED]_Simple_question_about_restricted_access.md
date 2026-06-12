---
title: "[SOLVED] Simple question about restricted access"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by yessirsir on 2008-08-28
i have just installed ubuntu on MY computer, but everything is restricted, i cannot even access my second HD or launch an app that i just compiled because it is saved in one of the root folders, it tells me i don't not have the privilege.

Like can i be the judge about that :S ? this is my own computer and no one else lives here. besides, im not the kind of guys who goes and delete just whatever. 

Ok this can be good feature for security ...for those who want to be paranoid about it, but hey, im not. 

 Can i just unlock access to my own computer and start actually using it ...or i have no choice to look at it only :S

---

### Post by bruce89 on 2008-08-28
> **yessirsir said:**
> i have just installed ubuntu on MY computer, but everything is restricted, i cannot even access my second HD or launch an app that i just compiled because it is saved in one of the root folders, it tells me i don't not have the privilege.

There are a few questions here. What folder is it in? Why is it there?

> **yessirsir said:**
> Like can i be the judge about that :S ? this is my own computer and no one else lives here. besides, im not the kind of guys who goes and delete just whatever. 

Ok this can be good feature for security ...for those who want to be paranoid about it, but hey, im not. 

 Can i just unlock access to my own computer and start actually using it ...or i have no choice to look at it only :S

It's best not to. There is usually no need to modify files outside your own home directory (except config files in /etc perhaps).

---

### Post by nicedude on 2008-08-28
yes you can but no one is supposed to tell you how in the forums and for good reason as new users will break their system in very short order as well as it is a huge security risk even if you are the only physical user if you use the Internet. 90% of all software runs without wanting you to be root while any system configuration or software that could harm the system requires root. The program you built from source wants root because you put it in the root folder when you installed it, instead try making a folder called custom in your home folder for your user name and then put any source code directories in there and compile them and then install using "sudo make install" and that will work just fine. Please just take my word for it that Ubuntu is designed for you not to run as root, you can do it but I promise you that you will be sorry later.

Hope this helps you out and welcome to Ubuntu

---

### Post by yessirsir on 2008-08-28
well, if there is no need to , how come i cannot acces my own stuff pratically anywhere ..

Like for starter, i cant access my second hard drive, there is not even a os instaled there, now why would it be dangerous to deleted videos , music , pics  and docs ?

Isnt there a way to keep locked only the files crutial to the OS and grant acess to the rest ?

and i dont see what could be worst than having to format in case i get really stupid and delete what should not be ? 

i would just want to stop have to look 3 hours on all sorts of forum everytime i try to do something u know, i dont have that kind of free time unfortunately. 

Its too bad but, if i cant gain access to my own computer , i will have no choice but to de-install this OS cause i really have like 2 or 3 hours a week for myself and looking about how to gain access to my stuff on forums is not the most interesting thing ...no offense


Edit: alright , i understand about internet security ...and i think you are right aboutthat one, but could i at least have access to my extra hard drive ? i see it in the places scroll down menu, but i click and then .....bump...get a message that i do not have privilege


When i compiled my app, i did it in the folder i created on my desktop, and it got , somehow , in the root folder at the end of the process. im not yet experianced enough to tell the compiler where to save after it finished. so i figured it was its default saving path location or somthing.


Thanks for welcoming me btw

---

### Post by bruce89 on 2008-08-28
> **yessirsir said:**
> well, if there is no need to , how come i cannot acces my own stuff pratically anywhere ..

Your stuff should only be in your own home folder (or another drive).

> **yessirsir said:**
> Like for starter, i cant access my second hard drive, there is not even a os instaled there, now why would it be dangerous to deleted videos , music , pics  and docs ?

This is a case of it being mounted wrongly. Someone else can say what to do.

---

### Post by nicedude on 2008-08-28
I am so sorry we are taking up your free time, I guess you don't consider that we are using our free time to try and help you for free. And I also hate when people threaten to go back to Windows if someone can't solve their problems for them. Ubuntu is not hard and it is super easy to access any storage device that is connected to your PC there is only a few commands involved to do any of it as well as scripts like pysdm that even do it for you.

 I have never said this before in these or any other forums but I think maybe you would be better served with windows as learning anything seems to be a stumbling block for you.

---

### Post by yessirsir on 2008-08-28
I lwouldnt need help if it was not locked ........

my point was not that i dont like that u help . my point was that i want to learn about somehing else than this very topic. 

i think if i want to ruin my pc , its my choice, and besides its the best way to learn ...by making mistake dont you agree ?

anyway im not trying to start a fight here im just hoping to read about other things about ubuntu which i greatly appreciate btw.

---

### Post by nicedude on 2008-08-28
It is not locked you are expected to use a regular user mode and use sudo or provide password when needed to do administrative tasks. If you google how to login to Ubuntu you can find out how to make a root password and login as ROOT and you will break your system in less than a week and I would bet $100 on that. I would explain to you how to mount your hard disk but I don't have the time right now.

---

### Post by yessirsir on 2008-08-28
it is mounted. i know how cause i searched.sorry but for me it is hard cause i just begin i was also very surprised that i need to do things like command and mount ...etc , which a beginner cant find it easy. i just needed to login root access which acould have taken 3 second to say in the first place, i didnt mean to force any1 to answer or feel offended becuase i have less time then some others ..., Thank you

---

### Post by nicedude on 2008-08-28
So go google and learn how to log in as root so you can break your PC like you seem to want to. There is a reason why no one here is supposed to say how to do it, because it is never needed and you will break your system very quickly on top of it not being needed. There are many kinds of Linux in the world and allot of them are made to be logged into as root so you might want to look around. You don't need to login as root to mount and use disks you just need to use sudo with the mount command to give your user root permissions. 

By all means though don't believe me and go do as you please since I have a feeling you will anyway, but like I said you will have to figure it out via Google since there is a rule here not to tell people how to do what you are asking and it is a good rule.

---

### Post by tommcd on 2008-08-28
Yessir,
Is the 2nd hard drive an internal drive or an external one? What directory is it mounted to?
Can you post the output of
```
cat /etc/fstab
```
and
```
sudo fdisk -l
```
To gain access to the 2nd drive you can probably do it with chown command. For example, if your 2nd hard drive was mounted in /media/drive then you could cd into the /media directory and run:
```
sudo chown -R your_username:users drive/
```
This will give your username read and write permission to all folders on the drive.

---

### Post by yessirsir on 2008-08-28
after typing this command cat /etc/fstab

i got this 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=884ad957-f296-4a93-b4b2-d1d821398ba4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7183c8af-2431-40e1-aa71-292d87399c6e none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
 

and after that one sudo fdisk -l


i got 

255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ca0c111

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7193    57777741   83  Linux
/dev/sda2            7194        7476     2273197+   5  Extended
/dev/sda5            7194        7476     2273166   82  Linux swap / Solaris

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd67dd67

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19929   160079661    c  W95 FAT32 (LBA)

> sudo chown -R your_username:users drive/

This will give your username read and write permission to all folders on the drive. 

oh i think this will let me use my system as i wanted it right? like, the next time i see restricted access i can use that command in the same folder and it will never tell me restricted access again ? 

(i wont come back here to complain if i break something , no need to worry :))

im not sure if i got that part of the command right tho (your_username:users drive/)  shouldnt it be username: password ,so it remembers the password and have always root access there in the future ? 

i tryin the "man" command to display about chown just now ...hmm , but im not sure if this is the result ill get

---

### Post by tommcd on 2008-08-28
Your 2nd hard drive /dev/sdb does not seem to be listed in your fstab. Is the 2nd drive internal or external? Is the drive mounted? And what directory is it mounted to?

It looks like the 2nd drive is a Windows drive, correct? The file system is W95 FAT32.
To add it to fstab first backup your fstab for safety
```
sudo cp /etc/fstab /etc/fstab.bak
```
Then run ```
gksudo gedit /etc/fstab
```
Add a line for the 2nd hard drive like this
```
/dev/sdb1 /media/drive vfat defaults 0 0
```
This assumes that the 2nd hard drive is mounted on /media/drive. You can make any mount point (preferably in /media) that you want. If media/drive (or whatever you want to call it) does not exist, you can make it with 
```
sudo mkdir /media/drive
```
You can then reboot and the drive should mount automatically.

[QUOTE=
im not sure if i got that part of the command right tho (your_username:users drive/)  shouldnt it be username: password ,so it remembers the password and have always root access there in the future ? 
[/QUOTE]

No. That part of the chown command is for user_name:group_name. So since my username is tom I would run
```
sudo chown _R tom:users /media/drive
```

You should not use chown on just anything. For a 2nd hard drive that just has data on it then it's fine. But don't just chown anything on your system that normally should be owned by root, which is pretty much anything outside of your /home directory.

---

### Post by yessirsir on 2008-08-28
Yes this is an internal drive and it is mounted. 

it is mounted here 
filesystem/media/M-SPACE


i cannot access it due to permission so i tried your command 

in terminal like this:

[HTML]root@HomePC:/media# sudo chown -R yessirsir:users /media/M-SPACE
[/HTML]

but all i get is a buch of line pratically saying the same thing ..like this :


changing ownership of `/media/M-SPACE/ Operation not permitted

so i am not permited to do the command to permit me the access ...hmmm its confusing :S

---

### Post by nicedude on 2008-08-28
Try using pysdm to mount it for you and allow you as a user to use the drive, its a GUI based python script that is just for mounting stuff without you having to learn how to mount things via the command line. First log back in as a user instead of using that root prompt and then use these 2 commands to install the program and then to run it.


COMMAND TO INSTALL IT

sudo apt-get install pysdm

COMMAND TO OPEN IT

sudo pysdm

then just select the drive you want to use and press mount and it will remount it and you can then use it.

---

### Post by cariboo on 2008-08-28
You won't be able  to change the ownership, but you can change the read/write permissions on your mount point try:

```
sudo chmod -R 777 /media/M-SPACE
```

That should give you access to your data.

Jim

---

### Post by tommcd on 2008-08-29
> **cariboo907 said:**
> You won't be able  to change the ownership, but you can change the read/write permissions on your mount point try:
```
sudo chmod -R 777 /media/M-SPACE
```
That should give you access to your data.
Jim

Cariboo,
I don't understand why he cannot change ownership with chown. Do you know why?

Yessir,
Try the chmod command that Cariboo gave. Also try the chown command with sudo, but without loging in as root. The root account in Ubuntu is not recommended. So login as a regular user and try the chown command again. I don't know if that will enable it to work, but it's worth a shot.

---

### Post by yessirsir on 2008-08-29
using what nicedude proposed worked! thank you i can use my computer.

I can also try the chmod command but i think its best not now since i can access my files right ?

Although, the sudo chown seemed useful it would be nice to know what Cariboo has to say about changing the ownership.

---

