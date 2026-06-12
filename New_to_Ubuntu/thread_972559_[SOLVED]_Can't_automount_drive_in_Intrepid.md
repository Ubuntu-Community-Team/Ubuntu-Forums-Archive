---
title: "[SOLVED] Can't automount drive in Intrepid"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by zain3000 on 2008-11-05
I have an internal 120Gig drive partitioned as ntfs. I added the following line to fstab to get the drive to automount on startup:

/dev/sdb1 /media/SHARED ntfs defaults 0 1

This gave me NO problems in hardy, but for some reason in intrepid, it gives me the message "You are not privileged to mount the volume".

I even tried using this line of code:

/dev/sdb1 /media/SHARED ntfs users,defaults,umask=000 0 0

but it gave me the same message. I'm totally lost as to what to try next. Can someone please help me out? :confused:

Thanks

---

### Post by nhasian on 2008-11-05
in my /etc/fstab file i have:

```
/dev/sdb1	/media/DriveD ntfs defaults,umask=007,gid=46 0 1

```

---

### Post by zain3000 on 2008-11-06
> **nhasian said:**
> in my /etc/fstab file i have:

```
/dev/sdb1	/media/DriveD ntfs defaults,umask=007,gid=46 0 1

```

I tried that, but I got the same dialogue box: You are not privileged to mount..."

Grrr... I see no reason why this shouldn't work :(

---

### Post by sisco311 on 2008-11-06
post the output of:
```
sudo blkid
```

---

### Post by bumanie on 2008-11-06
Why not configure it via the ntfs configuration tool? Ntfs-config will automatically add it to /etc/fstab > sudo apt-get install ntfs-configThen go to Applications --> System Tools --> NTFS configuration tool. Fill out the window that appears - and you are done; an automounting, readable/writeable ntfs partition.

---

### Post by gandaran on 2008-11-06
> **zain3000 said:**
> I tried that, but I got the same dialogue box: You are not privileged to mount..."

Grrr... I see no reason why this shouldn't work :(
I can mount mine without problems by just adding this line to fstab

# /dev/sda2
UUID=9C24E6C324E69F8E /media/Storage        ntfs    defaults,umask=007,gid=46 0       1

in you case you have to change two things here, first *Storege* this is the mane of my windows xp drive D, it must be exactly the same has it is shown in windows, second, you must find the UUID number for your drive and replace it, use this command to get the UUUID number for your drive **sudo blkid**

---

### Post by zain3000 on 2008-11-07
> **sisco311 said:**
> post the output of:
```
sudo blkid
```

Here is the output of sudo blkid:

###@###:~$ sudo blkid
/dev/sda1: UUID="46522F6D522F6143" LABEL="VISTA" TYPE="ntfs" 
/dev/sda2: UUID="4d9f09dd-1516-4f31-a222-ee89a09b7b0b" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="9d75d55d-ce1b-4ecf-bd38-c983967499b3" 
/dev/sdb1: UUID="1C9CA4719CA4475C" LABEL="SHARED" TYPE="ntfs" 
####@###:~$

I'm reluctant to use ntfs-config because it should be required for a simple automount which worked perfectly fine in hardy... something else has to be wrong.

Thanks

---

### Post by gandaran on 2008-11-08
try adding these two lines to fstab, should work
> # /dev/sdb1
UUID=1C9CA4719CA4475C /media/SHARED ntfs defaults,umask=007,gid=46 0 1


---

### Post by zain3000 on 2008-11-09
Thanks for all the help, guys.

After trying a number of things, I finally found something that works.

Here's what I did...

i) Mount the drive manually
ii) Add this line to fstab: /dev/sdb1 /media/SHARED ntfs defaults 0 1
iii) Restart the computer, and voila, the drive is mounted.

Here's the weird thing... I have full read/write privileges on the drive itself, but I can't unmount/mount the drive without going through the terminal.

Ah well, I can live with that, as long as it automounts on startup.

Thanks again for all the help. I'm such a newbie :)

---

### Post by bruceleo on 2008-11-11
Yeah, it seems that intrepid remembers if the drive was mounted on the last restart. So after adding the line to fstab:
1. sudo mount -a
Once it's mounted, then restart.
As long as it's not unmounted it will auto-mount on startup.

---

### Post by bruceleo on 2008-11-17
Scratch that. It seems that it does it sometimes?!?
I need help now. It seems I have to do "sudo mount -a" every time I start up.
What's going on here?

---

### Post by BGFG on 2008-11-17
Hi Guys, 
Please review this post. hope it helps

[http://ubuntuforums.org/showthread.php?t=98576](http://ubuntuforums.org/showthread.php?t=98576)

---

### Post by nebileix on 2009-02-02
> **zain3000 said:**
> I have an internal 120Gig drive partitioned as ntfs. I added the following line to fstab to get the drive to automount on startup:

/dev/sdb1 /media/SHARED ntfs defaults 0 1

This gave me NO problems in hardy, but for some reason in intrepid, it gives me the message "You are not privileged to mount the volume".

I even tried using this line of code:

/dev/sdb1 /media/SHARED ntfs users,defaults,umask=000 0 0

but it gave me the same message. I'm totally lost as to what to try next. Can someone please help me out? :confused:

Thanks

Here's another easy GUI config method to share for auto-mounting of internal drive on startup. All the application to configure is install by default for intrepid.

> Press alt-F2 and run "polkit-gnome-authorization"
> goto storage->mount file from internal drive.
> under explicit authorizations, grant the user to have the right on console and active session.
> Press alt-F2 and run "gnome-session-properties"
> Add a new startup program using this command "gnome-mount -d <your device name here. *EXAMPLE _/dev/sda3_> <your mount point. *EXAMPLE _/media/DATADrive_>
> Mark sure that new startup program is checked and re-login to check.

Hope this could help.

Good Day..

---

### Post by Irmandos on 2009-04-20
> **bruceleo said:**
> Scratch that. It seems that it does it sometimes?!?
I need help now. It seems I have to do "sudo mount -a" every time I start up.
What's going on here?

21:56 ricardo ~ $  cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb5 :
UUID=80decf96-0fbb-4ad2-b662-dbda8072da05 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb6 :
UUID=2d14b664-1dc6-4d7a-b89d-82d0521cfe2c none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb1 /media/winC ntfs-3g defaults,locale=en_ZA.UTF-8 0 0
/dev/sda1 /media/winD ntfs-3g defaults,locale=en_ZA.UTF-8 0 0

---

