---
title: "[SOLVED] Installing second internal hard disk"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by ubalderdash on 2008-09-02
I have just installed a second internal hard disk on my computer running Ubuntu 8.04 i386. This disk appears on my desktop and I have been able to "mount" it (???). I then assumed it would be an easy matter to delete some remaining files from a Windows installation. However it seems I am not the "owner" of the disk and it belongs to someone called "root"! I tried to log in as "root" but his password is obviously not the same as mine. Now this hard disk really does belong to me and I would like to recover the power to delete my old files.

Can anyone help please?

---

### Post by nitro_n2o on 2008-09-02
Assuming that you have sudo access then try 

sudo chown -R yourUserName /path/to/your/disk

---

### Post by halitech on 2008-09-02
check here
[http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+ext3](http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+ext3)

if it's fat32, check here
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by ubalderdash on 2008-09-02
Hey! Who's "sudo"?

I guess I must be something less than an Absolute Begginer...

---

### Post by halitech on 2008-09-02
> **ubalderdash said:**
> Hey! Who's "sudo"?

I guess I must be something less than an Absolute Begginer...

sudo isn't a person, its a command to tell Ubuntu to give you permission to run as root (superuser do) on a per command basis. It will ask you for your password and then as long as you are the main user and have admin rights it will do what you tell it to do

---

### Post by prshah on 2008-09-02
> **ubalderdash said:**
> I have just installed a second internal hard disk on my computer running Ubuntu 8.04 i386. This disk appears on my desktop and I have been able to "mount" it (???). 

How did you mount it? You should use pmount or gnome-mount to mount it properly. I suggest pmount.

Open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo apt-get install pmount
``` to (duh!) install pmount. Now give the command```
pmount sdb1
``` (Note no sudo); replace sdb1 with whichever partition id you want to mount. 

To unmount, use ```
pumount sdb1
```

To use pmount, the user must be a member of plugdev group (which by default all users created during installation are.)

This will mount the device with related permissions. If you want to make it permanent, you will have to edit your /etc/fstab file and put in the proper settings. To know more about this, post the outputs of the following commands```
cat /etc/fstab
sudo fdisk -l
mount
sudo blkid
```

---

### Post by ubalderdash on 2008-09-02
I mounted (whatever that means) the disk by right clicking on its icon and choosing the mount option. This allowed me to access the contents of the disk but not to delete the unwanted files.  
Your dos type commands refer to url addresses, but I have not yet discovered where these can be found and the only name I have for the disk is the one that appears on the desktop i.e. "118.5 GB Media". There is no drive letter shown or anything vaguely similar like the suggested sdb1.

Installing this disk and running it was expected to be a very simple task as indeed the mechanical part was. What I really didn't expect, was that the running of it should be such a nightmare and excite so many varying opinions.

---

### Post by fballem on 2008-09-02
> **ubalderdash said:**
> I mounted (whatever that means) the disk by right clicking on its icon and choosing the mount option. This allowed me to access the contents of the disk but not to delete the unwanted files.  
Your dos type commands refer to url addresses, but I have not yet discovered where these can be found and the only name I have for the disk is the one that appears on the desktop i.e. "118.5 GB Media". There is no drive letter shown or anything vaguely similar like the suggested sdb1.

Installing this disk and running it was expected to be a very simple task as indeed the mechanical part was. What I really didn't expect, was that the running of it should be such a nightmare and excite so many varying opinions.

It's not an actual nightmare - just a different way of looking at things.

[LIST=1]
[*]In Windows, the assumption is that the logged in user is the administrator. So, that user has automatic access to any resources connected to the computer - including the second hard drive.
[*]Linux does not assume that the logged in user is an administrator. On some distributions of Linux, you can log in a a root user. This is discouraged unless you are doing some specific system activity. In Ubuntu, by default, root login is not allowed. Instead, Every resource has an 'owner' and that 'owner' can set up access rights. If you want to change them, then you have to issue a 'superuser do' command (or sudo for short).
[*]This is a security feature, and is part of what makes Linux more secure than Windows.
[*]It does mean, however, that when you add some hardware (like a second disk), you may need to do some work to make it available to you.
[*]The other posters are trying to find the easiest way to help you - but please remember that this is not Windows and it is a little different.
[*]My experience is that I have finally gotten comfortable with ubuntu after about a month - but I'm not an expert and I still come into the forums for some pretty basic newbie questions. I find it helps to have a sense of humour and to let people know that you're a newbie. The explanations get a little more detailed.
[*]And in case no one else has told you - welcome! You may find, if you give ubuntu a chance, that this will be a good experience for a variety of reasons. As with anything new, however, there will be some short term pain - but think of the long term gain!
[/LIST]

As for the options:

[LIST]
[*]Right clicking to mount is perfectly acceptable. The term 'mount' comes from the old days when all data was stored on tape and the tapes had to be physically mounted on the tape reader in order to be used by the computer. I don't know if you have any experience with networks in a Windows environment, but if you do, then think of 'mount' as the same process you need to go through to log on to a network and use any drives that are there. In Windows, because of the assumption that the logged in user should have access to anything attached to the computer, you don't actually have to mount the drive - but Linux is different.
[*]Halitech's first post includes a link to a site that will allow you to permanently mount the second drive so that you don't have to mount it. If it's a Windows drive, it is likely an NTFS drive.
[*]The commands in prshah's post, and the output from those commands, are intended to provide him/her with sufficient information to guide you further. Just to manage expectations, the /etc/fstab file is used to identify the file system - and everything to do with storage is considered part of the file system. To enter the commands, you will have to use a Terminal. This may be accessed from Applications | Accessories, assuming that you are using ubuntu.
[/LIST]

My suggestion would be to try the commands in prshah's post - the intent is to find out exactly what you have in order to find the best solution to your problem.

As for 'sdb1', it is a name for a partition. I've attached a screenshot showing my one hard disk, which contains three partitions. All hard drives are partitioned in order to be usable in Linux. If I had a second hard disk, then the partitions would be sdb1, etc.

prshah: Once you have what you need, may I suggest that you use 'gksudo gedit /etc/fstab' to edit the /etc/fstab file. It's easier for someone coming from Windows to use.

Hope this helps,

---

### Post by prematurebaby on 2008-09-02
sudo is the safer way to do root privileges

---

### Post by ubalderdash on 2008-09-02
Many thanks for all your efforts and the time you have all spent with a total ignoramous! As it happens, another Ubuntu user contacted me 'off-thread' and led me to a Ubuntu community site where the process was explained in detail and proved to be very easy and almost entirely code free!
Back in the seventies I had to use dos but hey, time has moved on since then and I'm far too old to start over again...

---

### Post by fballem on 2008-09-02
> **ubalderdash said:**
> Many thanks for all your efforts and the time you have all spent with a total ignoramous! As it happens, another Ubuntu user contacted me 'off-thread' and led me to a Ubuntu community site where the process was explained in detail and proved to be very easy and almost entirely code free!
Back in the seventies I had to use dos but hey, time has moved on since then and I'm far too old to start over again...

Could you please post that site here? It makes it easier for others who may encounter the same problem.

Thanks, and glad that it worked out!

---

### Post by warped0ne on 2008-09-02
Yes, please post the site. I'm having the exact same problem :(

---

### Post by warped0ne on 2008-09-02
Never mind, this command worked. 

sudo chown -R username /media/disk

However, for an absolute beginner, you might want to tell them they need to have their drive mounted before running that command and they will need to unmount and mount it again before the affects will take place.

---

### Post by Onso on 2008-09-09
Hi. when I run sudo chown -R username /media/Media Two
it says to me that there's no such file or directory
The name that shows up on my Drive on the desktop when I mount it is Media Two
and in the File Browser it says it's location is /media/Media Two. But I still get no such file or directory.
What am I doing wrong?

---

### Post by halitech on 2008-09-09
if there is a space in the name, this should work

```
sudo chown -R *username* /media/Media\ Two
```

the \ after Media tells it to include the space

---

