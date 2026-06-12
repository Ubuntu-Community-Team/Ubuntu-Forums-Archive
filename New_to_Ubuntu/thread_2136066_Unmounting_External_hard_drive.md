---
title: "Unmounting External hard drive"
date: 2013-04-16
forum: New to Ubuntu
---

### Post by Ant01 on 2013-04-16
I've mounted a external hard drive on my new installation of Ubuntu 12.04 and I've corrupted something as I can start the machine with the external hard drive, I get some error about Grub error reading the drive. When I boot up without the drive it tells me that its missing media/External do I want to wait skip or manually change settings.

Is there a way I can unmount the media drive, I tried using sudo unmount media/External but it says command not understood?

:confused:

---

### Post by ibjsb4 on 2013-04-16
You of course could edit fstab manually, but I just use "pysdm"

---

### Post by The Cog on 2013-04-16
Check the spelling of umount. It's umount, not unmount - second letter is 'm'. Why they chose to spell it that way is a mystery to me.

I can only imagine complaining about missing media/External if it's listed in /etc/fstab as an automatically mounted drive. Oh, and it's probably best to put a slash in front of media/external:
```
umount /media/External
```

---

### Post by Ant01 on 2013-04-16
My bad I misspelled it, the problem I have now is it doesn't see the mounting as I have to skip it on boot up and if I try connecting the external drive I get a Grub error. I think I have to edit something in Grub but have no idea...

---

### Post by Cheesehead on 2013-04-19
Please us the *exact* grub error. Or post a clear photo of it.
The error message has meaning.

---

### Post by ibjsb4 on 2013-04-19
[http://ubuntuforums.org/showthread.php?t=2136964](http://ubuntuforums.org/showthread.php?t=2136964)

---

