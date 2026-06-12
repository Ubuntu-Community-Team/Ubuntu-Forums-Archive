---
title: "remove folder mount from devices in nautilus"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by alpineedge3 on 2012-07-17
How do I remove the "Documents on" item in the devices list? remove is disabled in the right-click menu.

[http://i.imgur.com/ZgbX2.png](http://i.imgur.com/ZgbX2.png)

I'm getting a mounting error because the folder doesn't exist anymore. Thanks.

---

### Post by Jacobonbuntu on 2012-07-17
> **alpineedge3 said:**
> How do I remove the "Documents on" item in the devices list? remove is disabled in the right-click menu.

[http://i.imgur.com/ZgbX2.png](http://i.imgur.com/ZgbX2.png)

I'm getting a mounting error because the folder doesn't exist anymore. Thanks.


I think "documents on" is not the whole sentence, if you increase the left section, there will be someting like "documents on this or that disc". I don't know, but I guess your fstab file is linking to this folder somehow, that causes trouble on startup.  removing the link will stop the error. open the fstab file with gksudo gedit /etc/fstab BUT if you are not sure what to do, please ask; the fstab file is a rather sensitive file.

---

### Post by alpineedge3 on 2012-07-17
the title is just "Documents on", i assume it was a child folder of the unnamed device above it that mounts ok. 

when i click on the "Documents on" item, I get a "Lockdown error -17" message box. 

I tried to make a Documents folder on the device to see if the link would work then, but no luck.

i don't see it in my fstab file either:

```


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=edf...445 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=56b...dd0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```

---

### Post by Jacobonbuntu on 2012-07-18
> **alpineedge3 said:**
> the title is just "Documents on", i assume it was a child folder of the unnamed device above it that mounts ok. 

when i click on the "Documents on" item, I get a "Lockdown error -17" message box. 

I tried to make a Documents folder on the device to see if the link would work then, but no luck.

i don't see it in my fstab file either:

```


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=edf...445 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=56b...dd0 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```

....That is weird!
I think it must be a bug or something. The only thing I can find on the internet on "Lockdown error 17" is about connecting Iphones....
just a wild idea, but there must be a link to the not -existing device in /media. Can you remove that one?
anyone else an idea?

---

### Post by audiomick on 2012-07-18
> **Jacobonbuntu said:**
> anyone else an idea?

If you can definitely associate the broken link with a particular device, plug that device back in and unmount it cleanly. I had a similar thing ages ago where that worked, I think.


One other thing: you say that remove is disabled in the right click menu. What about a left click on the "eject" symbol next to the entry?

---

