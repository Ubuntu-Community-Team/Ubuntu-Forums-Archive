---
title: "How to hide second HDD from the Unity panel?"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by kramer65 on 2012-03-21
Hello,


I've got a second internal harddrive which I automatically boot at startup. Where it normally used to appear on my desktop, it now appears on the unity panel. I always used to [hide it]("http://www.techdrivein.com/2011/06/how-to-hide-mounted-drives-from-ubuntu.html") from the desktop, to prevent clutter.

Does anybody know how I can hide my second harddrive from the Unity panel?

All tips are welcome!

---

### Post by ajgreeny on 2012-03-21
I do not use unity, but in gnome 2 you could stop volumes appearing on the desktop by mounting the partition at /mnt instead of /media.

I have no idea about unity's behaviour in this situation, but it is worth a try, I think.

---

### Post by jerome1232 on 2012-03-21
> **ajgreeny said:**
> I do not use unity, but in gnome 2 you could stop volumes appearing on the desktop by mounting the partition at /mnt instead of /media.

I have no idea about unity's behaviour in this situation, but it is worth a try, I think.

I believe it's the same, at least I have volumes mounted at /dos, /windows, and /backup, none of which show up in my panel.

---

### Post by kramer65 on 2012-03-21
> **ajgreeny said:**
> I do not use unity, but in gnome 2 you could stop volumes appearing on the desktop by mounting the partition at /mnt instead of /media.

I have no idea about unity's behaviour in this situation, but it is worth a try, I think.

Alright. Thanks for the tip. I am a bit lost in how to do this. In order to auto mount I simply followed [this guide]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") and did the following:
```
ls -al /dev/disk/by-uuid/
```
and then I added the following to my startup applications:
```
/usr/bin/udisks --mount /dev/disk/by-uuid/d3f5cd57-b706-417b-9e16-2b4fc510fc6a
```

Any idea how to change the disk to /mnt instead of /media? (even though I have a lot of posts I am often still quite a noob.. :-$)

---

### Post by mcduck on 2012-03-21
> **kramer65 said:**
> Alright. Thanks for the tip. I am a bit lost in how to do this. In order to auto mount I simply followed [this guide]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") and did the following:
```
ls -al /dev/disk/by-uuid/
```
and then I added the following to my startup applications:
```
/usr/bin/udisks --mount /dev/disk/by-uuid/d3f5cd57-b706-417b-9e16-2b4fc510fc6a
```

Any idea how to change the disk to /mnt instead of /media? (even though I have a lot of posts I am often still quite a noob.. :-$)
As far as I knwo you can't do it that way, instead you need to configure the drive in /etc/fstab (which is a better way to automatically mount drives anyway, as it gives you better control, and mountiong happens at boot time, even before you log in (or actually regardless of if you log in or not...)

Here's a decent guide to using fstab: [http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by ajgreeny on 2012-03-21
Just back up fstab with ```
sudo cp /etc/fstab /etc/fstabbak
``` then edit /etc/fstab with command ```
gksu gedit /etc/fstab
```and add a line like 
```
UUID=d3f5cd57-b706-417b-9e16-2b4fc510fc6a /mnt/disk2           ext4    defaults        0       2
``` You can call **disk2** whatever you want, but make the folder first with command ```
sudo mkdir /mnt/disk2
```

---

### Post by NikTh on 2012-03-21
> **kramer65 said:**
> Hello,


I've got a second internal harddrive which I automatically boot at startup. Where it normally used to appear on my desktop, it now appears on the unity panel. I always used to [hide it]("http://www.techdrivein.com/2011/06/how-to-hide-mounted-drives-from-ubuntu.html") from the desktop, to prevent clutter.

Does anybody know how I can hide my second harddrive from the Unity panel?

All tips are welcome!

Hi , 
For Unity i think that tool will do your "job" --> [MyUnity]("http://www.omgubuntu.co.uk/2011/12/unity-tweak-tool-myunity-gets-new-look-coming-to-ubuntu-software-centre/") 

[IMG]http://img163.imageshack.us/img163/7924/screenshot20111211at215.jpg[/IMG]

---

