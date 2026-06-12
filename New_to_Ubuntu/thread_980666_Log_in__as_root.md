---
title: "Log in  as root?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by FNDII on 2008-11-13
I need to log in  as root to run this command

mount -t udf -o ro,unhide /dev/yourdevice /mountpoint 

I assume that it would be like this for me

mount -t udf -o ro,unhide /dev/media/cdrom1 /mountpoint 

So how do i log in as root? or a saw somewhere about a sudo root?


This is what I'm trying to do

If you copy the DVD's contents (cp -r) to your hard drive (with sudo, so you can read everything), then chmod everything in the directory you copied to to allow at least read to user, and chown it all to yourself, the install runs fine. No need to futz with your .wine.

---

### Post by alwayshere on 2008-11-13
sudo su

---

### Post by ad_267 on 2008-11-13
You can just put a sudo in front of the command.

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bscbrit on 2008-11-13
To use Root's permissions, you prefix the command with 'sudo' e.g.

```

sudo mount -t udf -o ro,unhide /dev/media/cdrom1 /mountpoint

```

It will ask you for your password - which is your usual log-on password, and if you have sufficient privileges it will run your command as if you are Root.  It will also remember your password (for a default of 5 minutes) so that if you have to issue a series of commands as sudo then it will only ask for your password the first time.  The user that was given during the installation setting up is given automatic sudo privileges, other users have to have the system administrator give them the privileges.

---

### Post by FNDII on 2008-11-13
sudo mount -t udf -o ro,unhide /dev/media/cdrom1 /mountpoint

when i paste this in the terminal is says  "/mountpoint does not exist". Should i have something else instead?

---

### Post by ad_267 on 2008-11-13
The mountpoint is where you want the drive to be mounted. You have to make sure this is an empty directory.

Eg say you want to mount the cd at /media/mycd, then you first need to do
```
sudo mkdir /media/mycd
```
And then to mount it:
```
sudo mount -t udf -o ro,unhide /dev/media/cdrom1 /media/mycd
```

Where you want to mount it depends on what you're doing. /media is where Ubuntu will mount removable drives by default so it's usually a good idea to stick it there.

---

### Post by FNDII on 2008-11-13
I did the first code but the 2nd one gave me an error


 special device /dev/media/cdrom1 does not exist

---

### Post by stephanvaningen on 2008-11-13
/dev/media/... should be /media I believe

---

### Post by FNDII on 2008-11-13
i took out the /dev

sudo mount -t udf -o ro,unhide /media/cdrom1 /media/mycd

when I used that I got this

/media/cdrom1 is not a block device

---

### Post by AndyCee on 2008-11-13
The command you're trying to use seems to be to mount your CD-ROM. In Ubuntu, CD's are mounted automatically. (Look around in /media )

If you're certain you need to mount it manually, you don't actually want /media/cdrom1 - rather, /dev/scd0.

ie.

sudo mount -t udf -o ro,unhide /dev/scd0 /media/mycd

---

