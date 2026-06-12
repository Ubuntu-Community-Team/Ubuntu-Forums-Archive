---
title: "Reformat hard drive to use as storage"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by K-D on 2008-07-14
I have recently taken the plunge into Ubuntu.

I have two internal hard drives and I tried installing Ubuntu on the larger one but for some reason it was giving me an error message on boot up of:

verifying dmi pool data.....

mbr error

as I had another (smaller hd) I thought I would have a go at installing Ubuntu on that and try accessing the other drive once I got up and running.  So far so good......however now I am trying to format the larger drive it has restricted access.  I presume this is due to me setting up security on my first install. 

any suggestions on how I can reformat the larger drive as I am stuck and don't really know what i'm doing.


Cheers

---

### Post by OffAxis on 2008-07-14
you can use gparted to format the drive (it has a graphical interface, nice and easy)
it's on the liveCD or

```
sudo apt-get install gparted
```

---

### Post by K-D on 2008-07-14
I have used G parted but it won't let me format the drive for some reason it won't et me touch the 188g free space..

---

### Post by OffAxis on 2008-07-14
then I'd go with a bootable hard drive utility disc. If you can't find the one that came with your drive you can download it off the manufacturer's website.
That should let you erase, clone, or copy the drive.

if you have trouble finding the software on the manufacturer's site you can roll with the ultimate boot cd
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by K-D on 2008-07-14
Thanks for that!

I have managed to wipe the hard drive clean:)

The only probelm now is I can't detect the drive.  It appears in the devices searched for in GParted but I cannot access it for storage?

This could well be me being stupid but any ideas would be great!

---

### Post by paul101 on 2008-07-14
well, if you've wiped the hdd you've prob not formatted it to your preferred file system??



... unless i'm very much mistaken

---

### Post by K-D on 2008-07-15
I formatted it to ext3 and it has now appeared once I rebooted the comp!

I have to changed the access level but thank you very much for your help!:guitar:

---

