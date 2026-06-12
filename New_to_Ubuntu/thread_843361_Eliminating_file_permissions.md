---
title: "Eliminating file permissions"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by lost4now on 2008-06-28
Is there a way to eliminate or get rid of file permissions?

I have nothing to hide, protect or that is worth the hassle of having to fight the whole file permissions thing. If a file is that important then I'll hide it on a CD or another drive. I copied a CD with several hundred pictures from different cameras. At first I couldn't even view them. It took several passes with chown and wildcards to finally view them all. Is there a way around this file paranoia.

Thanks.

---

### Post by hyper_ch on 2008-06-28
no

---

### Post by mcduck on 2008-06-28
The permissions are not there only for hiding stuff you don't want others tosee. They are one of the most important things that make Linux and Unix safe operating systems.

If your computer is connected to Internet, you definitely don't want to get rid of permissions. Not that getting rid of them would even be possible..

---

### Post by robertchahine on 2008-06-28
and permissions keep you away from changing some important folders like /etc and /boot ...
but if you want, type in terminal 
```
gksudo nautilus 
```
it will open nautilus in root mode, so you can view,delete move any file any folder you want.But be careful while doing that

---

### Post by lost4now on 2008-06-28
Thanks for the advice. This is about what I expected. It just seems like it is a lot easier to pull the inet plug when it isn't in use than to have to deal with a bunch of commands that let me screw things up worse than a hacker would.

---

### Post by hyper_ch on 2008-06-28
you normally shouldn't care at all about permissions as they are set right.

---

### Post by mcduck on 2008-06-28
Well, running "gksudo nautilus" would be exactly the same as having no permissions at all. So it's just as dangerous as the solution you wan ted in the first place, removing all protection from your system and allowing you to mess it up as badly and easily as you wish without giving any warnings..

(The only difference is that using "gksudo nautilus" _only_ the file manager will be that dangerous. Removing all permissions would make _every_ program just as dangerous. Lack of proper permissions is one of the ost important resons for security problems in Windows..)

---

### Post by aysiu on 2008-06-28
It sounds as if you're having some kind of mounting issues. Is this an NTFS drive? FAT32?

---

### Post by Canis familiaris on 2008-06-28
You need enable root and login as root. I'm sorry I cant post how to because it is against forums rules and I agree it is not a good idea as well.
These file permissions in Linux is for your own good.
If you want to change permission only for an NTFS drive, plz ask.

---

### Post by hyper_ch on 2008-06-28
what is root login needed for? sudo is enough

---

### Post by lost4now on 2008-06-28
The drives are ext3. I guess I could be satisfied with total access to the /home directory and usb drives. I don't want to mess with the program stuff

---

### Post by hyper_ch on 2008-06-28
well, you should have total access to /home/YOURUSER and you should also get access to the USB drives.

---

### Post by lost4now on 2008-06-28
Hyper you may have a million posts but you are wrong. If you copy off pictures or files from a CD or usb drive that was made on another machine you do not have access. At least I don't.

---

### Post by aysiu on 2008-06-28
> **lost4now said:**
> The drives are ext3. I guess I could be satisfied with total access to the /home directory and usb drives. I don't want to mess with the program stuff
Then changing ownership of those files to your username should do the trick.

More info here:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

If you run into problems, post the error messages back here.

---

