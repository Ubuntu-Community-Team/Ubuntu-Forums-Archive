---
title: "Please help me edit my GRUB menu"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by KevNice on 2008-10-28
I've had Ubuntu for about a year on this computer, so it includes various updates. I thought old versions would delete as the new was installed, but that is not the case. Here is what my GRUB menu looks like:
```

[B]Ubuntu 8.04.1, kernel 2.6.24-21 generic

Ubuntu 8.04.1, kernel 2.6.24-21 generic (safe mode or somesuch)[/B]


Ubuntu 8.04.1, kernel 2.6.24-19 generic

Ubuntu 8.04.1, kernel 2.6.24-19 generic (safe)

Ubuntu 8.04.1, kernel 2.6.24-18 generic

Ubuntu 8.04.1, kernel 2.6.24-17 generic

Ubuntu 8.04.1, kernel 2.6.24-16 generic

Ubuntu 8.04.1, kernel 2.6.24-14 generic
[B]
memtest 

Windows XP
Windows Vista
Some other thing that I need[/B]
```

Due to the fact that I have mild OCD with regards to clutter, and the fact that the other version are taking up disk space, I would like to delete all the other versions. I have BOLDED everything that I want to keep.

How do I go about cleaning this up?

---

### Post by Xiong Chiamiov on 2008-10-28
There is a graphical grub editor in the Ubuntu repositories, although I have no idea what it's called or how well it works.


First, let's make a backup:
```

cd /boot/grub
sudo cp menu.lst menu.lst.bak

```
To edit it manually, you'll need to edit the file with your favorite text editor:
```

gksudo gedit /boot/grub/menu.lst

```
or
```

sudo nano /boot/grub/menu.lst

```
All the top of the file are just options.  Scroll to the bottom and delete the entries you don't want.  Reboot.

BTW, one of the options you can change in there is to have old kernels removed.  You'll have to look for it yourself, and probably uncomment the line.

---

### Post by Idefix82 on 2008-10-28
Type in
```
sudo cp /boot/grub/menu.lst menu.lst.bac
gksudo gedit /boot/grub/menu.lst
```

and find at the end of the file the entries that you want to delete. They look something like
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,7)
kernel		/vmlinuz-2.6.24-19-generic root=UUID=cd29e314-6005-4acd-bf45-06b3fcee5c23 ro quiet splash
initrd		/initrd.img-2.6.24-19-generic

```

Go ahead and delete these entries. To be sure, reboot and see if all the remaining entries boot fine and that you haven't deleted anything wrong. If everything looks fine then go into Synaptic and uninstall the kernels that you don't want to keep.

---

### Post by ashmew2 on 2008-10-28
> 
There is a graphical grub editor in the Ubuntu repositories, although I have no idea what it's called or how well it works.

I think its called grubconf!

---

### Post by ashmew2 on 2008-10-28
I think he wanted to remove the older kernels from disk as well.
Check out :
[http://ubuntuforums.org/showthread.php?t=22812](http://ubuntuforums.org/showthread.php?t=22812)

To remove from grub menu , you need to edit /boot/grub/menu.lst
```

sudo gedit /boot/grub/menu.lst
```

Just remove the entries of kernels you already removed :)

---

### Post by Nepherte on 2008-10-28
Ubuntu doesn't remove the older kernel versions when a new one is installed. The reason is that when a new one breaks your system, you can still use the older one. If the latest one works for you, you can safely remove the other ones. In synaptic search for linux-headers and linux-image, look carefully at the version number and remove the ones you don't need.

---

### Post by soloman498 on 2008-10-28
Try this thread 

[http://ubuntuforums.org/showthread.php?t=898253](http://ubuntuforums.org/showthread.php?t=898253)

---

### Post by KevNice on 2008-10-31
Thanks for your help guys. It looks nice and clean now and I have an extra GB of space to play with :)

---

