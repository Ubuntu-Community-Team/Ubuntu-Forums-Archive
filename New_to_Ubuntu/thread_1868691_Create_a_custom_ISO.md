---
title: "Create a custom ISO"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by DaimyoKirby on 2011-10-24
Hi there.
I believe (correct me if I'm wrong) that you need an iso to create a livecd, and that the livecd is based on this iso.

Is there a way to create an iso of my current desktop setup, like taking a picture of my panels, settings, installed applications, etc., and package it into a single iso file I can use to create a startup disk?

---

### Post by haqking on 2011-10-24
> **DaimyoKirby said:**
> Hi there.
I believe (correct me if I'm wrong) that you need an iso to create a livecd, and that the livecd is based on this iso.

Is there a way to create an iso of my current desktop setup, like taking a picture of my panels, settings, installed applications, etc., and package it into a single iso file I can use to create a startup disk?

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

or re-linux which is a fork of remastersys

You could also if you want an exact copy take a clone using clonezilla, but cloning it back depends on destination size of HDD and you may have issues if the hardware has changed

---

### Post by DaimyoKirby on 2011-10-24
Ok, I downloaded re-linux, and I immediately ran into an error during installation.

I entered the code:
```
sudo cp -R usr etc /
```
like the installation instructions told me to do, and I got some errors:
```
sudo cp -R usr etc /
[sudo] password for alden: 
cp: cannot stat `usr': No such file or directory
cp: cannot stat `etc': No such file or directory
```

Why is it telling me this? Or am I supposed to be running this code while in my Relinux folder, where I extracted the .tar.gz file?

---

### Post by haqking on 2011-10-24
> **DaimyoKirby said:**
> Ok, I downloaded re-linux, and I immediately ran into an error during installation.

I entered the code:
```
sudo cp -R usr etc /
```
like the installation instructions told me to do, and I got some errors:
```
sudo cp -R usr etc /
[sudo] password for alden: 
cp: cannot stat `usr': No such file or directory
cp: cannot stat `etc': No such file or directory
```

Why is it telling me this? Or am I supposed to be running this code while in my Relinux folder, where I extracted the .tar.gz file?
 [s]you need to specify paths.

etc is /etc usr is /usr

you need to specify where things are

as for re-linux i dont know i have never used it, i am sure there is instructions there somewhere[/s]

I just downloaded it it wants you to copy the extracted folders, so you need to do it from within the extracted folder, use nautilus or specify the paths

---

### Post by DaimyoKirby on 2011-10-24
umm...what?

I tried running the command from the folder where I had extracted the files, and everything seemed to run fine.

Is that what you said?

---

