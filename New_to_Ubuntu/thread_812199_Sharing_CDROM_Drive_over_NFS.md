---
title: "Sharing CDROM Drive over NFS"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by bungledoe on 2008-05-29
Hi all,

I've got a PopCornHour networked media tank player ([www.popcornhour.com](www.popcornhour.com)) on my home network and I want to be able to access the cdrom drive of my Hardy Heron box from this device.

The PopCornHour will support various different sharing protocols such as NFS and SMB but NFS gives the best performance. I've already created a NFS share for a folder in my /home/bungle which I use for streaming media from the Ubuntu box to the PopCornHour. This works really well. I'd really like to be able to connect to the cdrom drive to avoid the need to have a separate dvd player.

I know I could rip the DVDs to an iso image and use that but I'd like to be able to just insert a DVD into the Ubuntu box and then connect to it from the PopCornHour to save on the hassle of ripping it to an iso.

I've tried sharing the cdrom through NFS and I'm told much my to my unhappiness by Ubuntu that the cdrom drive does not support NFS export.

Anyone out there with any skills that can help me out and try to get this resolved? Would be much appreciated.

Thanks

Bungle

---

### Post by pdwerryhouse on 2008-05-29
It should just be a matter of putting something like this in your /etc/exports file:

/cdrom          10.1.10.0/255.255.255.0(ro)

Obviously substitute your network range where I have put "10.1.10.0".

You'll need to have the nfs-kernel-server and portmap packages installed, and running. Once you've edited the exports file, run:

exportfs -a

To check if it is working, then from another server, run:

showmount -e your.host.name

---

### Post by neurostu on 2008-05-29
One thing you could try is using SSHFS to mount the directory where the cdrom drive is mounted.

on computer A insert a CD. It then will be mounted somewhere like /media/cdrom
on computer B run SSHFS 

```

user@computerB$ sshfs user@computerA:/media/cdrom/  /media/localMountDir

```
That will then mount the remote directory like a local directory.  Anytime you insert media into computer A and it mounts it to /media/cdrom you will be able to read it from computer B from /media/localMountDir

---

### Post by bungledoe on 2008-05-29
Hi,

Thanks to you both for your replies. I'll try what you have recommended and let you know how I get on.

Nice one.

Cheers

---

