---
title: "problem w/ user privilages"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by mustard greens on 2008-06-08
I am having trouble with the user privilages.  I have found and changed the user privilages on my computer, and yet I am having trouble unmounting the disc in my disk drive.  details says it is not in my permissions (administrator) and that it is only the permission of the secondary user.  again, I have changed all this in the user and groups app.  also, when I attempt to eject while in the secondary account it says disc is being used by some unnamed app.  I have gone through all the apps and all have been closed properly.  I am confused!

---

### Post by bodhi.zazen on 2008-06-08
Hard to tell the problem from your description. I do not know if the failure is in your permissions, a problem with open files, or a problem with mounting (hal).

To unmount the device / partition use sudo :

```
sudo umount -l /dev/xxx
```

change /dev/xxx to your device (/dev/sda1 or what have you).

You can not un-mount your root partition unless you are running from a live CD.

Other then that we need a little more information ...

---

### Post by cariboo on 2008-06-08
It sounds like you're trying things from a windows perspective. In linux in general you don't change user privileges. The user has complete control of everything in their home directory, but can only
execute programs, not change them. the proper way to do things is to change the file permissions. Check out his link:

 [http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/)

Now as to your problem. If you haven't screwed up things to badly, you should in a terminal be able to enter the following commad and eject your cd.

```
sudo umount /media/cdrom [enter]
eject [enter]
```

Good luck

Jim

---

