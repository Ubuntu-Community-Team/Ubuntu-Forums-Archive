---
title: "Help!  I changed the xorg.conf file and now my mouse doesn't work"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by hellodoggie on 2008-06-19
Hello.

I changed the xorg.conf file and now my mouse doesn't work.  I am contemplating reinstalling the OS.  Can someone give me a step by step method on how to restore my mouse to work?:confused:

---

### Post by mohammadrizki on 2008-06-19
have you tried to reconfigure xserver using sudo dpkg-reconfigure xserver-xorg?

> sudo dpkg-reconfigure xserver-xorg

---

### Post by iaculallad on 2008-06-19
Open your terminal and browse your /etc/X11 directory. You should see a file named xorg.conf~ (If it exist)

```
cd /etc/X11
sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```


Then restart your GDM.

---

### Post by stairwayoflight on 2008-06-19
I know this won't seem to help you solve your immediate problem, but in future remember it is good to back up files before changing them. You could try for example:
sudo cp -p /etc/X11/xorg.conf /etc/X11/xorg.conf.old

That will give you a backup and you will know where to find it should you need to restore it.

---

### Post by iaculallad on 2008-06-19
> **stairwayoflight said:**
> I know this won't seem to help you solve your immediate problem, but in future remember it is good to back up files before changing them. You could try for example:
sudo cp -p /etc/X11/xorg.conf /etc/X11/xorg.conf.old

That will give you a backup and you will know where to find it should you need to restore it.

Actually, Ubuntu does that automatically when you try to edit "system" files. It automatically create a duplicate copy of the "system" file you're trying to edit (w/c you have to save afterwards) and appends the tilde sign (~).

-Backing up would be a good idea before messing with important files.

---

### Post by hellodoggie on 2008-06-19
Worked like a charm.  Thanks!

> **iaculallad said:**
> Open your terminal and browse your /etc/X11 directory. You should see a file named xorg.conf~ (If it exist)

```
cd /etc/X11
sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```


Then restart your GDM.

---

### Post by forestpixie on 2008-06-19
> Actually, Ubuntu does that automatically when you try to edit "system" files. It automatically create a duplicate copy of the "system" file you're trying to edit (w/c you have to save afterwards) and appends the tilde sign (~).

Gedit might do that but nano, for instance needs to be told to do it. 

I would also suggest that it is much better to get into the habit of backing up a file before you edit it, after all it's quite easy to do.

---

