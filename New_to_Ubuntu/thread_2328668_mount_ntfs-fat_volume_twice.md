---
title: "mount ntfs-fat volume twice?"
date: 2016-06-23
forum: New to Ubuntu
---

### Post by fahid2 on 2016-06-23
Good Day everyone,

Short Question:
Can I mount one NTFS or FAT volume twice at two different mount point, with different of same options?


Long Question:

[B]OS: Xubuntu 16.04
[/B]
**Disks in Computer:** 
[LIST=1]
[*]120GB SSD (OS Disk)
[*]3TB NTFS (mounted through fstab at /media/3tb)
[*]1TB FAT (mounted through fstab at /media/3tb)
[/LIST]

**Intended Uses of subject PC:**
[LIST=1]
[*]LAMP Webserver
[*]File Server from Internet through [Owncloud]("http://owncloud.org")
[*]MiniDLNA Server
[*]SSH Server
[*]Time to Time usage as normal Computer through XRDP
[/LIST]

until this point all is OK.

Owncloud is installed at **/home/cloud/public_html** as user cloud
My Owncloud user-data dirctory is **/home/cloud/public_html/data/user/files/** 

I want to be able access my 3TB drive from Internet through Owncloud but problem is that the drive is mounted outside of my OC-user-data directory and hence I can't access it through Owncloud.

In order to access it through Owncloud I need to mount my 3TB Disk at **/home/cloud/public_html/data/user/files/3tb **and it works, but when I do this, MiniDLNA can't use it anymore because of permission issues nor can I use it from the Desktop.
In order to cope with this I tried the following: 
[LIST]
[*]chmod **/home/cloud** (and all sub-dirs) to 0755
[*]point miniDLNA to use **/home/cloud/public_html/data/user/files/3tb**
[*]created a link on desktop to **/home/cloud/public_html/data/user/files/3tb**
[/LIST]

all started working, but as I restarted the computer, somehow chmod value of **/home/cloud/public_html/[COLOR=#ff0000]data[/COLOR]/user/files/3tb **directory was changed automatically to 0770. Hence creating a permission issue for MiniDLNA and Desktop access.

If I mount at **/home/3tb**, I can't access the drive through Owncloud
If I mount at **/home/cloud/public_html/data/user/files/3tb**, MiniDLNA and Desktop access is broken

So I was thinking if I can mount the 3rb disk at both points, it is likely to solve the problem. Can I somehow do that?

---

### Post by HermanAB on 2016-06-23
I think you should make a soft link with ln -s

---

### Post by fahid2 on 2016-06-23
Problem with Owncloud - It doesn't cares about links!!

But seems like I have get it to work by kind of mounting the disk twice
 ```
sudo mount --bind /media/3tb /home/cloud/public_html/data/user/files/3tb
```

seems to work so far, but I will now put it in the fstab file and go through restarting and other test to see if keeps working, I hope it will

---

### Post by fahid2 on 2016-06-23
adding to fstab causes a Boot Time Error and won't let the computer boot unless you interact with it directly. so don't add that to fstab, these are entries I tried adding in fstab
```
mount --bind /media/3tb /home/cloud/public_html/data/user/files/3tb

--bind /media/3tb /home/cloud/public_html/data/user/files/3tb

/media/3tb /home/cloud/public_html/data/user/files/3tb
```

none worked for me.

so here is what I finally did, I added a new cron job to execute as **root** at boot time the command **mount --bind /media/3tb /home/cloud/public_html/data/user/files/3tb**, and all is working fine, across multiple reboots there haven't been any issues at least so far.

And since everything seems to be working fine, I will mark the thread as solved, but if anything unexpected turned up, I will come back to this thread.

---

