---
title: "[SOLVED] Frustration"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2008-05-30
Here is my situation.

I am trying to use Amarok, gtkpod, or ANY other music transfer device to work with my 80G IPod Classic. Since Ive started using Linux, it is the only thing I just cannot do at all. I cannot get it to sync. Ive gotten close a few times but I think I figured out whats wrong and Im totally stuck so if anyone knows how, help me please.

From what I gather, when you connect the IPod with a USB cable it should automount and pop-up on the desktop. 

It does this.

Problem is, Amarok and gtkpod tell me it is unmounted. I tried to direct it to the mount point ( /media/ipod ). The 2 programs tell me that mount point doesn't exist.

I tried this code to create the mount point manually (as per advice of a friend of mine).

```
sudo ln -s /media/ipod /mnt/ipod
```


I got back an error from terminal saying that /media/ipod was not a directory. So I made one.

```
mkdir /media/ipod
```



I tried it all over again and Amarok still tells me it is unmounted. So what I did next was right click on the IPod icon that shows up on the desktop when you connect it and clicked on "Properties". I tabbed over to drives and the mount point was blank. I tried to enter "/media/ipod" there but that didnt work either.

I'm stuck and I don't have a clue what to do from here. :confused:

---

### Post by TenPlus1 on 2008-05-30
I have a friend who uses Floola to access his iPod and it works perfectly:

[http://www.getdeb.net/app/Floola](http://www.getdeb.net/app/Floola)

but if you still have problems, here's a link that may help:

[http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu](http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu)

---

### Post by kpkeerthi on 2008-05-30
Connect you iPod and run this command in a terminal
```
mount
```

That should tell you where your iPod is mounted. Use this mount point to configure Amarok, gtkpod. If can't figure out, post the output of the command here for us to help you out.

---

### Post by Bigtime_Scrub on 2008-05-30
> **kpkeerthi said:**
> Connect you iPod and run this command in a terminal
```
mount
```

That should tell you where your iPod is mounted. Use this mount point to configure Amarok, gtkpod. If can't figure out, post the output of the command here for us to help you out.

This was the output:

gary@gary-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-17-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/gary/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gary)
/dev/sdb1 on /media/KONG'S IPOD type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

---

### Post by kansasnoob on 2008-05-30
I believe my daughter uses xmms2 for her Ipod mini and I'm fairly certain it auto mounts. It's quite similar to Winamp in general appearance.

---

### Post by Bigtime_Scrub on 2008-05-30
> **kansasnoob said:**
> I believe my daughter uses xmms2 for her Ipod mini and I'm fairly certain it auto mounts. It's quite similar to Winamp in general appearance.

I thought XMMS is just a music player. I checked their website and they made no mention of being able to sync and transfer files to a portable device.

---

### Post by kpkeerthi on 2008-05-30
> **[COLOR="Red"]/dev/sdb1 on /media/KONG'S IPOD[/COLOR]** type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1 000,utf8,umask=077,flush)

**/media/KONG'S IPOD**

---

### Post by Bigtime_Scrub on 2008-05-30
> **kpkeerthi said:**
> **/media/KONG'S IPOD**

That's it! OMG Thank you so much. I've been trying to get this to work for a month and that little thing fixed it! I got songs to transfer finally. I was using the wrong mount point. When I used the one you said it worked without a hitch. Thank you so much.

---

