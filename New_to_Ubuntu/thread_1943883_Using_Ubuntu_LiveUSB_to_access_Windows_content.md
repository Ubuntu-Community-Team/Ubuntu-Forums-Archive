---
title: "Using Ubuntu LiveUSB to access Windows content"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by Mynxenoa on 2012-03-20
My hard drive is going to hell, I can hear the clicking sounds which means that its soon to fail and I need to back up the data. I remember when I used to use Ubuntu in the past that it would allow me to access Windows files and copy the image (non-bootable) but it would keep the data intact. I'm hoping someone can teach me how to do this again rather than me clicking around in circles looking for Windows related files.

---

### Post by dmouck on 2012-03-20
You should hopefully be able to see your hard drive in Nautilus. IF you do, click it and it should mount. If you are using Vista or Windows 7, your data will be in C:\Users\<username> . To be safe, backup everything in that folder. But if you don't have a lot of disk space to backup to, grab your Desktop, Documents, Pictures, Videos, Music. If you use internet explorer, grab the Favorites folder as well.

---

### Post by dolphin194 on 2012-03-20
> **dmouck said:**
> You should hopefully be able to see your hard drive in Nautilus. IF you do, click it and it should mount. If you are using Vista or Windows 7, your data will be in C:\Users\<username> . To be safe, backup everything in that folder. But if you don't have a lot of disk space to backup to, grab your Desktop, Documents, Pictures, Videos, Music. If you use internet explorer, grab the Favorites folder as well.

Exactly. If you are recovering XP, it will be in C:\Documents and Settings\<username>

---

### Post by Mynxenoa on 2012-03-20
Nautilus?

I'm not aware of what that is, can I try to sudo get-apt Nautilus?

---

### Post by snowpine on 2012-03-20
Nautilus is the default File Manager for Ubuntu. 

If you are using a different Ubuntu "spin" then you will have a different file manager (Thunar for Xubuntu, PCManFM for Lubuntu, etc) but the principle will be the same.

---

### Post by Mynxenoa on 2012-03-20
Well here's what I got going on right now. I booted the computer and the device I want to take the data from has been mounted as 'OS' and my live cd has been mounted as well. However, I cannot access the files on the OS mount because of the permissions only allow me to create and delete files and not view them. What can I do to get root / superuser access and all permissions to this machine and hard drive?

---

### Post by NikTh on 2012-03-20
> **Mynxenoa said:**
>  What can I do to get root / superuser access and all permissions to this machine and hard drive?
Hi ,
You can open nautilus with root privileges . Open a terminal and write
```
sudo nautilus
```

---

### Post by winh8r on 2012-03-20
> **NikTh said:**
> Hi ,
You can open nautilus with root privileges . Open a terminal and write
```
sudo nautilus
```
 

You should use 

```
gksu nautilus
```

for this.

---

### Post by mastablasta on 2012-03-20
another option is to create an image of the drive (hwich should be bootable). to do this you can use clonezilla (ubuntu and debian based) or you can use a bit more user friendly and perhaps with a bit  less features Redobackup (ubuntu based).

---

### Post by NikTh on 2012-03-20
> **winh8r said:**
> You should use 

```
gksu nautilus
```for this.

I think its the same for a LiveUsb. Isn't it ?
Its not a regular account.

---

### Post by wildmanne39 on 2012-03-21
Hi you can also use```
sudo -i nautilus
```it opens the root file browser window in the live cd, no password required.

---

### Post by mastablasta on 2012-03-21
> **NikTh said:**
> I think its the same for a LiveUsb. Isn't it ?
Its not a regular account.
 
gksu is just graphical sudo (i.e. sudo for GUI programmes)

---

