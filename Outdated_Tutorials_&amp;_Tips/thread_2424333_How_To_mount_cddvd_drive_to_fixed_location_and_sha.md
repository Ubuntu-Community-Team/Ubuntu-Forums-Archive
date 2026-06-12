---
title: "How To mount cd/dvd drive to fixed location and share it"
date: 2011-08-18
forum: Outdated Tutorials &amp; Tips
---

### Post by mrkazoodle on 2011-08-18
Hi,

I wanted to share a cd/dvd drive over my network but couldn't pull the trick off by enabling the share option in its properties dialog, I then started digging a little deeper and as I couldn't easily find a solution, I decided to give back to the community what I learned :)

_**First of you need your cd/dvd to be mounted on a fixed location:**_

edit /etc/fstab

```
sudo gedit /etc/fstab
```

and add the following line (at the bottom) in order to mount the drive automatically to /media/dvd

```
/dev/dvd  /media/dvd  auto  user,noauto,exec,utf8  0  0
```

Next you have to make sure that the folder you are mounting the drive to exists and therefore create it

```
sudo mkdir /media/dvd
```

This does the trick, now cds/dvds will be mounted always be mounted to the same location, they will still show up on your desktop and there it will still carry its volume name.

**_Sharing the drive over the network:_**

Now the drive has it own folder, it can be treated as one. So you share it like you'd share any other folder of which you aren't the owner. (For new people: your user account only owns the folders in your home folder, you don't (normally) have the rights to share folders you don't own)

**GUI**

If you don't have this program already, install it. It is a handy program for configuring samba.

```
sudo apt-get install system-config-samba
```

I found a good tutorial on the program [_[COLOR="Blue"]HERE[/COLOR]_]("http://www.liberiangeek.net/2010/07/mountmap-ubuntu-10-04-lucid-lynx-cddvd-drive-windows/"), it even has pictures ;), it'd be foolish not to refer you to it.

**Command line**

Add this to /etc/samba/smb.conf (you can see an example which looks pretty much like this at the end and it looks pretty much like what I've been saying here)

```
[cdrom]
   comment = Samba server's CD-ROM
   read only = yes
   locking = no
   path = /media/dvd
   guest ok = yes
```

That's it! Enjoy :)

---

