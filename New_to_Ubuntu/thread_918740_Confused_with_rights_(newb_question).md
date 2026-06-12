---
title: "Confused with rights (newb question)"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by sezicoolcat on 2008-09-13
Hi all,
I have a main hard drive with Ubuntu Hardy Heron installed.
I am first time Linux user (although I have dabbled at work - a few odd commands that I have learnt parrot fashion, but only to do specific tasks)
I have introduced my old Windows hard drive on IDE2, becasue I have realised I need docs/pics etc off of it.

I see the drive on my desktop plus the 2nd partition on that second drive called "GAMES"

I cannot access these drives, when I do it asks me for a password. I don't remember setting a password on these drives and indeed if I had, it certainly wasn't using my ubuntu username...

I then got some sort of indication that its NTFS (I cannot remember if I installed XP as NTFS or FAT32) But I cannot boot my XP (virused bad)

I checked out the forum pages here. I typed in from Terminal a command to "mount" the drive. It came back with an error - needs to be "root" user or I suspect my permissions would not allow access.?

It also suggested editing a file called /etc/fstab as an option:
/dev/sda1	/media/disk-1	ntfs-3g	force		0	0

I typed that in - it won't save the file. Tells me only "root" user can do that.

I switched user - root password I left blank, as I never set that up, but it never worked.

I then went back to these forums. Found root is not available for Ubuntu.

I wonder then if anyone has any ideas how I can these drives seen in Ubuntu (mount into an external USB case and try and use like my USB card reader - that works fine?)

Any help would be nice. Sorry if this confusing to read - I am getting my head around all this Linux - coming from a MS background for the last 20 years in IT support.

Sarah

---

### Post by rraj.be on 2008-09-13
A warm welcome to Ubuntu :) :) :)


> **sezicoolcat said:**
> Hi all,
I have a main hard drive with Ubuntu Hardy Heron installed.
I am first time Linux user (although I have dabbled at work - a few odd commands that I have learnt parrot fashion, but only to do specific tasks)
I have introduced my old Windows hard drive on IDE2, becasue I have realised I need docs/pics etc off of it.

I see the drive on my desktop plus the 2nd partition on that second drive called "GAMES"

I cannot access these drives, when I do it asks me for a password. I don't remember setting a password on these drives and indeed if I had, it certainly wasn't using my ubuntu username...



It was pasword of your root acount of your linux account.

It is a security measure

> 

I then got some sort of indication that its NTFS (I cannot remember if I installed XP as NTFS or FAT32) But I cannot boot my XP (virused bad)

I checked out the forum pages here. I typed in from Terminal a command to "mount" the drive. It came back with an error - needs to be "root" user or I suspect my permissions would not allow access.?



some system command require you to be admin or root of the system.

To runa a command in root mode use 

```
sudo

```
in front of that command like this to mount the drive

```
sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1
```

> 
It also suggested editing a file called /etc/fstab as an option:
/dev/sda1	/media/disk-1	ntfs-3g	force		0	0


insteed of editing fstab you can use a GUI tool called NTFS-CONFIG

To install that type this command in terminal
```
sudo apt-get install ntfs-config
```

and try this

[https://wiki.ubuntu.com/ntfs-3g]("https://wiki.ubuntu.com/ntfs-3g")

> 
I typed that in - it won't save the file. Tells me only "root" user can do that.

try this

```
sudo gedit <filepath>
E.G. sudo gedit /etc/wvdial.conf
```
> 

I switched user - root password I left blank, as I never set that up, but it never worked.

I then went back to these forums. Found root is not available for Ubuntu.

I wonder then if anyone has any ideas how I can these drives seen in Ubuntu (mount into an external USB case and try and use like my USB card reader - that works fine?)

Any help would be nice. Sorry if this confusing to read - I am getting my head around all this Linux - coming from a MS background for the last 20 years in IT support.

Sarah

you can get all help here.

Please give your questions clearly and shortly to get better response. :)

---

