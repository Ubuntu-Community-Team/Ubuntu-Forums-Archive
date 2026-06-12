---
title: "What is mounting the automount path on boot?"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by quirino77 on 2012-07-21
My Ubuntu 12.04 64 bits, if configured with some automount paths.
When ot boots, one of the paths is being mounted (i do nothing).
How can i get what is making it be mounted on boot?
I had thought it could be "recent files". But i (think) disabled it. (Privacy, Record Activity -> off). I also added the path to don't record activity.

Also i had tried the command lsof, but couldn't identify any access on the path.

Thank's.

---

### Post by ajgreeny on 2012-07-21
I don't totally understand what you mean nor what exactly happens at boot, but partitions that mount at boot are usually mounted by the system file /etc/fstab, which can be edited as root if you need to make changes.

See 
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
and 
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by quirino77 on 2012-07-21
Just after GUI is loaded, when desktop is ready to be used, a network path is mounted and the nautilus opens this path (as if a flash drive is conected).

You are right about fstab. But this isn't the problem. This path if mounted by automount, not fstab.

Also, the path is mounted seconds after the boot. I believe mount points defined on fstab are mounted during the boot (before GUI is loaded).

Thank's for helping.

---

### Post by NikTh on 2012-07-21
> **quirino77 said:**
> Just after GUI is loaded, when desktop is ready to be used, a network path is mounted and the nautilus opens this path (as if a flash drive is conected).

You are right about fstab. But this isn't the problem. This path if mounted by automount, not fstab.

Also, the path is mounted seconds after the boot. I believe mount points defined on fstab are mounted during the boot (before GUI is loaded).

Thank's for helping.

Hi , 
you have right when you say " I believe mount points defined on fstab are mounted during the boot (before GUI is loaded)" . 
What is this path , that nautilus automatically open when you be , in Desktop Environment ? 

To disable automount option on nautilus you can open a terminal and give these 2 commands 
```
gsettings set org.gnome.desktop.media-handling automount "false"
gsettings set org.gnome.desktop.media-handling automount-open "false"
```

If this serve your needs . 

Regards

---

### Post by quirino77 on 2012-07-21
This path is on my automount configuration files. I want this path to be mounted automatically when i access it. I have others paths on configuration files than do not have this problem. Only one path is being mounted even if i do not access.

This do not work for me, since i want automount working. I just don't want it being mounted by itself when i won't use it.

As far i had read about it, the first line will disable automount. 
```
gsettings set org.gnome.desktop.media-handling automount "false"
```
Am i right?

But i will enjoy the second line.
```
gsettings set org.gnome.desktop.media-handling automount-open "false"
```
I suppose it will make Nautilus do not open a new window when a new path is mounted.

I could also use dconf, ok?

Is there a way to list what process is accessing each file? Maybe this could point me what is mounting the path.

---

### Post by NikTh on 2012-07-21
Hi , 
yes , you well-read and well understood . 
Those 2 commands will disable automount  and automount-open from nautilus. 
According to this 
> **quirino77 said:**
> Just after GUI is loaded, when desktop is  ready to be used, a network path is mounted and the nautilus opens this  path (as if a flash drive is conected).
i thought that second command (automount-open) would serve your needs. 

Maybe another solution would be to add this particular path , to etc/fstab with NO mount option , like 
**noauto** . 

Thanks

---

