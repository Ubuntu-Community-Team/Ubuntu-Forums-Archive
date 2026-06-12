---
title: "Ubuntu &amp; QNAP 109Pro NAS"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by mtonsbeek on 2008-05-04
Has anyone got some sensible advice on how to link up to a QNAP 109Pro NAS, which incidentally I believe runs Linux?

It seems invisible on my network whilst all other (Windows) computers do show up.

Thanks.

---

### Post by Paqman on 2008-05-04
I use a TS-209 at home. They do run Linux, but because they're designed to work with a Windows network they actually use Samba. You can just treat it like connecting to a Windows machine
 
Follow the instructions in [this thread](http://ubuntuforums.org/showthread.php?t=288534) and you'll have no problems.

However, since you've got the "pro" version, you can also use Linux's own NFS protocol instead of SMB/CIFS.

Take a look at [this thread](http://forum.qnap.com/viewtopic.php?f=11&t=2423) on the Qnap forums. Sounds like you'll need the package nfs-common.

---

### Post by mtonsbeek on 2008-05-04
> **Paqman said:**
> I use a TS-209 at home. They do run Linux, but because they're designed to work with a Windows network they actually use Samba. You can just treat it like connecting to a Windows machine
 
Follow the instructions in [this thread](http://ubuntuforums.org/showthread.php?t=288534) and you'll have no problems.

However, since you've got the "pro" version, you can also use Linux's own NFS protocol instead of SMB/CIFS.

Take a look at [this thread](http://forum.qnap.com/viewtopic.php?f=11&t=2423) on the Qnap forums. Sounds like you'll need the package nfs-common.

I have read the threads you quote and unfortunately feel a little out of my depth. I have now got nfs-common installed but am unsure about the rest. 

I can however ping it, and even get into the NAS by using its IP address so Linux knows it is there but I still cannot see it under Places > Network.

---

### Post by Paqman on 2008-05-05
> **mtonsbeek said:**
> I have read the threads you quote and unfortunately feel a little out of my depth. I have now got nfs-common installed but am unsure about the rest. 

I can however ping it, and even get into the NAS by using its IP address so Linux knows it is there but I still cannot see it under Places > Network.

I've not used NFS, but I can guarantee that if you follow the step-by-step instructions for using CIFS in that thread, you will get your shares mounted.

I have to mount them by the NAS's IP address. The thing about that is that if your router dynamically assigns IP addrress using dhcp, then you'll have to go into the router control panel and set the NAS to have a static IP. Which is not hard.

By way of example, I mount my Qmultimedia folder with this line in my fstab:
```

//192.168.0.4/Qmultimedia    /media/Qmultimedia        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777

```
Mounting it in your /media folder put the icon on your desktop. If you don't want that you can mount it in /mnt.

---

### Post by Edk on 2008-06-24
Hope I can piggy-back on this one please!  I am tearing my hair out!!

Thanks for the help here.  I have read the entries but am still having real problems.

1.  I run Hardy Heron and have nfs-common installed - perhaps not relevant

2.  I want to mount //192.168.0.9/Public to /mnt/qnap

3.  As root I created /mnt/qnap

4.  Permissions of qnap are: 

drwxr-xr-x  2 edward root 4096 2008-06-18 19:20 qnap

5.   I have tried this command:
sudo mount -t cifs //192.168.0.9/Public /mnt/qnap -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

and this command:

mount -t nfs 192.168.0.9:/Public /mnt/qnap


The qnap mounts and is accessible via the terminal.  Most of the files at the first level are permissions nobody/nogroup

6.  If I navigate to /mnt/qnap using Nautilus I can see the files BUT even if I do mothing, after a few seconds, Nautilus greys out, locks up and I have to kill it off.  Fairly useless!

7.  The same happens if I mount at /home/edward/qnap

8  I had a bit more success with:
sudo mount -t cifs //192.168.0.9/Public /mnt/qnap -o username=edward,password=edward,iocharset=utf8,file_mode=0777,dir_mode=0777

At least nautilus was useable, BUT if I created a folder under one of the root folders, the new folder has an Owner of 501 (!) with full access, and Group Users with Access only, and Others folder access - Access files

This is not much use to create files/folders!!

Has anyone any ideas as it seems daft that I cannot mount one Linux box to another!  Please be simple as I am still learning!

Thanks in advance

Ed

---

