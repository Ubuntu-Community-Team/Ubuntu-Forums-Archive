---
title: "fstab mount error"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by muske on 2013-10-20
Hi,

a bit of an introduction as to what I am trying to do.
As will show clearly from what I am about to ask I am not a super-experienced linux user but I've got the basics in my fingers.

I had a server running ubuntu desktop 12.04.1 on it with an hda, but because I was not entirely pleased with how that worked I decide to start over running ubuntu server 12.04.3 and configure all of the things I need myself (thats how you learn right).
So I managed to do the basics (parted disks, install, set up users and rights, set up samba and shares to the home network and set up bind for DNS) and all of that works.

As I only have 2 servers (the "main" one I am setting up and a pi as mediacenter), this one basically functions as file server etc..etc.. a big do-it-all.
attached to the pi is a USB external disk which I want reachable on the server for maintenance of the files thereon.

I am mounting the disk on this server with CIFS and pointing to the DNS entry for the pi and its share (being the USB disk) like so
```
sudo mount -t cifs -o credentials=/home/muske/.pi_creds,id=1000 //pi.home.hb/media /var/media/pi
```

however when I try to do the same automounting using fstab it failswith a *mount error could not resolve address for ... *
this is what I used :
```
//pi.home.hb/media /var/media/pi cifs credentials=/home/muske/.pi_creds,id=1000 0 0
```

I am guessing it cannot resolve the DNS name during startup/mounting as bind9 is not running yet ?
it works when I put the (fixed) ip address of the pi in fstab (although it still gives me an error), but thats not my prefered solution ofc :)

I guess my question is: is my above assumption correct and should I be mounting on login instead of boot?
when reading [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently) I take it I should add noauto and do the mount in /etc/rc.local ?

any help is appreciated, just trying to understand cause and proper solution.

thanks

---

### Post by muske on 2013-10-20
I went along and made the change of adding noauto option ```
//pi.home.hb/media /var/media/pi cifs ***noauto,***credentials=/home/muske/.pi_creds,id=1000 0 0
```
and adding the following line in /etc.rc.local
```
mount /var/media/pi
```

it has done the trick, so problem solved :D

---

