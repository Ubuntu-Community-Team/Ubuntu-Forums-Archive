---
title: "mount: unkown filesystem type 'iso9660'"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by teshiburu on 2013-07-18
Morning Ubuntu Forums, 

I am posting this here because I am unsure as to where I should post it. I have an Ubuntu 10.04.4 LTS VPS hosted by webfusion. That I have installed LXDE onto so that I may have a desktop environment for certain applications. However I am also trying to set this up as a game server, I have created an ISO of a game server that I am trying to run uploaded this onto my server following instructions found in a tutorial online, however when i execute the command 

```
mount -o loop1 UT99GOTY.iso m1
```

I get the error message 

```
mount: unkown filesystem type 'iso9660'
```

I have read on a few other forum posts about similar issues and people assisting on those forums have asked to see the contents of the /etc/fstab file well this is my fstab file's contents

```
proc  /proc         proc       defaults   0   0 
none /dev/pts     devpts    rw          0   0
```

can someone please assist me :(

many thanks in advance

---

### Post by dannyboy79 on 2013-07-18
you need to first create a directory to mount the iso in. does your instructions tell you to create a folder in a certain location? you choose m1 as the folder you want to mount the iso at but you're missing the slash BUT also m1 needs to be created and I wouldn't suggest creating the folder on the root level (example: /m1)

```
sudo mkdir /mnt/m1
```
then you can mount the iso to the iso folder located within the /mnt/ folder using this
```
mount -o loop UT99GOTY.iso /mnt/m1
```

then you can view the contents of the iso in the folder /mnt/iso

---

### Post by teshiburu on 2013-07-18
Danny thanks for the reply. 

I have done as you suggested and created the mnt directory and m1 directory using mkdir, and if I use the code you provided 

```
[COLOR=#000000][FONT=Ubuntu Mono]mount -o loop UT99GOTY.iso /mnt/m1[/FONT][/COLOR]
```

I get this error instead 

```
mount: Could not find any loop device. Maybe this kernel does not know about the loop device? (If so, recompile or 'modprobe loop' .)
```

whereas if i run the code 

```
[COLOR=#000000][FONT=Ubuntu Mono]mount -o loop1 UT99GOTY.iso /mnt/m1[/FONT][/COLOR]
```

I get the:

```
mount: unkown filesystem type 'iso9660'
```

message I do not know where I got the "loop1" part from?

---

### Post by dannyboy79 on 2013-07-18
can you link to the guide you're following? i am not familiar with working on a VPS of Ubuntu

---

### Post by teshiburu on 2013-07-18
> **dannyboy79 said:**
> can you link to the guide you're following? i am not familiar with working on a VPS of Ubuntu

[http://blog.opensecurityresearch.com/2013/03/unreal-tournament-99-server-on-ubuntu.html](http://blog.opensecurityresearch.com/2013/03/unreal-tournament-99-server-on-ubuntu.html)

---

### Post by dannyboy79 on 2013-07-18
doubt this matters but did you try with sudo as the commands shows?
```
sudo mount -o loop UT99GOTY.iso /mnt/m1
```

---

### Post by teshiburu on 2013-07-18
Yes I tried with and without sudo.

---

### Post by dannyboy79 on 2013-07-18
also probably doesn't matter but why are you using such an old version of Ubuntu? Even that guide shows using 12.04. I'd suggest waiting for others to come along and help as I am out of ideas. You did try this though didn't you?
```
sudo modprobe loop
```

---

### Post by teshiburu on 2013-07-18
> **dannyboy79 said:**
> also probably doesn't matter but why are you using such an old version of Ubuntu? Even that guide shows using 12.04. I'd suggest waiting for others to come along and help as I am out of ideas. You did try this though didn't you?
```
sudo modprobe loop
```


This gives this error.

```
WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/. 

FATAL: Module loop not found
```

---

### Post by dannyboy79 on 2013-07-18
something isn't right with your kernel. The loop kernel option has been compiled into the kernel since like Ubuntu 9 which is why you can't modprobe it, it's not a module, it's support to be built right into the kernel. You'll have to wait for someone else to help you OR ask on the webfusion forums maybe

---

