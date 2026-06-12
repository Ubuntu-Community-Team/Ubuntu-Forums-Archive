---
title: "Changing Permissions"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Nazty_Nayt on 2008-07-13
Ok, is there away I can change the permissions on files that are marked as root?  I'm the admin/sudo user so I don't know why I can't.  Even using nautilus I still cannot do anything to files that are read only.  I just want to change the access to them so I can add what I need to, and take out what needs to be taken out.  Can anyone help me out here?

---

### Post by tjwoosta on 2008-07-13
browse to the directory the file is in, then do
```
sudo chmod 777 filename
```

(filename is obviously the filename)

more info here
[http://www.ss64.com/bash/chmod.html]("http://www.ss64.com/bash/chmod.html")

---

### Post by Bachstelze on 2008-07-13
> **Nazty_Nayt said:**
> Ok, is there away I can change the permissions on files that are marked as root?  I'm the admin/sudo user so I don't know why I can't.  Even using nautilus I still cannot do anything to files that are read only.  I just want to change the access to them so I can add what I need to, and take out what needs to be taken out.  Can anyone help me out here?

If you don't have access, that propably means you shouldn't. **Don't** [font="Courier New"]chmod[/font] it! What are you trying to do?

---

### Post by ibuclaw on 2008-07-13
What files are you wishing to modify?

Regards
Iain

---

### Post by Nazty_Nayt on 2008-07-13
I'm modding my PSP, just changing out a theme on it.  I do know what I'm doing.  Now it's under a removable disk which is named 43.0 MB Media so what would the Chmod be?

---

### Post by ibuclaw on 2008-07-13
I think best course of action then would be to either remount it with write permissions, or give your PSP device an fstab line.

Can you post the output of this command?
```
df -hT
```
Regards
Iain

---

### Post by Nazty_Nayt on 2008-07-13
Sure thing

```
:~$ df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext3    294G   57G  222G  21% /
varrun       tmpfs    439M  108K  439M   1% /var/run
varlock      tmpfs    439M     0  439M   0% /var/lock
udev         tmpfs    439M   68K  439M   1% /dev
devshm       tmpfs    439M  788K  439M   1% /dev/shm
lrm          tmpfs    439M   44M  395M  11% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon    294G   57G  222G  21% /home/naztynayt/.gvfs
/dev/sdf1     vfat    950M  892M   58M  94% /media/disk
/dev/sdg      vfat     41M   25M   17M  60% /media/disk-1

```

Not sure how to remount with write permissions though.

---

### Post by collinp on 2008-07-13
hmm, run sudo nautilus, that should give you read/write permissions for everything. The command will open a file browser in the root directory. Then navigate to your psp and do what you need to do, then remember to close the file browser once done. The command only gives you root access in that file browser, every thing else stays the same.

---

### Post by rushikesh988 on 2008-07-13
you can use nautilus   for it 


just be a root (type in terminal "su")
and open nautilus (type in terminal "nautilus "
then browse the files and change there permissions by right clicking on them

---

### Post by ibuclaw on 2008-07-13
try
```
sudo mount -o remount,rw,nosuid,nodev,uid=1000,utf8,umask=077 /dev/sdg
```

Regards
Iain

---

### Post by Nazty_Nayt on 2008-07-13
> **rushikesh988 said:**
> you can use nautilus   for it 


just be a root (type in terminal "su")
and open nautilus (type in terminal "nautilus "
then browse the files and change there permissions by right clicking on them

When I type SU it asks me to enter a password.  I enter my sudo password, and it says authentication failed.

BTW

> **tinivole said:**
> try
```
sudo mount -o remount,rw,nosuid,nodev,uid=1000,utf8,umask=077 /dev/sdg
```

Not sure what this did.  I'm still not able to change the permissions any.  It's just really frustrating, why would the admin not be able to change the permissions for a file type???

---

### Post by bodhi.zazen on 2008-07-14
> **rushikesh988 said:**
> you can use nautilus   for it 


just be a root (type in terminal "su")
and open nautilus (type in terminal "nautilus "
then browse the files and change there permissions by right clicking on them

This will not work with a default installation of Ubuntu.

Ubuntu uses sudo.

To get a root shell :```
sudo -i
```

To start a gui application (like bautilus) use gksu

```
gksu nautilus
```

When asked for a password, enter your user password, the same one you logged in with. You will not see text in the terminal as you type your password, this is normal, hit enter.

---

### Post by bodhi.zazen on 2008-07-14
> **Nazty_Nayt said:**
> Not sure what this did.  I'm still not able to change the permissions any.  It's just really frustrating, why would the admin not be able to change the permissions for a file type???

ownership and permissions of FAT partitions are set at the time of mounting.

See also :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Nazty_Nayt on 2008-07-14
> **bodhi.zazen said:**
> ownership and permissions of FAT partitions are set at the time of mounting.

See also :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Alright, I'm reading into this now, my PSP is a fat12.  I'll post back if I run into any problems.

---

### Post by Nazty_Nayt on 2008-07-14
Ok, all these guides I'm finding are for FAT32 filesystems, would there be a difference?  Also what is my mounting point, it seems like everyons is /dev/dsa1 however when I run the code it says device doesn't exist, am I supposed to create it manually?

---

### Post by aysiu on 2008-07-14
The instructions for FAT32 will work for FAT16 as well (I've never heard of FAT12 before, but I'd assume it's the same deal there, too).

As for the location of the drive, based on what you posted earlier ```
/dev/sdf1     vfat    950M  892M   58M  94% /media/disk
/dev/sdg      vfat     41M   25M   17M  60% /media/disk-1
``` it would appear it's /dev/sdf1 or /dev/sdg

---

### Post by Nazty_Nayt on 2008-07-14
Ok, well I guess I'm trying to label the mount now, I'm at step 6 of the guide to do so...
> drive i: file="/dev/sdg"
mtools_skip_check=1 

Then I try
```
mcd i:
```

In which I get
```
Drive 'I:' not supported
Cannot initialize 'I:'

```

](*,)

---

### Post by Nazty_Nayt on 2008-07-14
Ok, don't even worry about it, this is the most retarded thing I've ever had to deal with.  I'll just use my girls computer for all my stuff that "I the admin am not aloud to do."

---

### Post by mochiko on 2008-07-27
hey, 
i need to delete some files in my home folder, but i can't log into ubuntu right now, so i'm using the cd as a live session user and i can see my files in front of me but i can't delete them!

the problem is that i need to delete some stuff down to at least 90% and right now i've got like 97%. i can't delete my own files and i've tried rm and all that stuff and i wanna know how to change a folder's permission so i can delete it!

---

### Post by eightmillion on 2008-07-27
You need to use 'sudo rm'. Pay careful attention to what you're deleting though.

---

