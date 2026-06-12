---
title: "How to boot Ubuntu 14 without straight to desktop/login screen?"
date: 2015-07-12
forum: New to Ubuntu
---

### Post by Navin81 on 2015-07-12
Hi everyone.  I just installed ubuntu 14 on my laptop.  Everything is working fine.  The only issue I have is that when I startup my laptop i have a boot menu option where I have to select Ubuntu, start with advanced option and some other choices?  It also has like a 10s timer where if I don't make a selection it will automatically boot up Ubuntu.
I am not dual booting any other OS on this machine.  It is just one HD with Ubuntu installed on it.  Is there a setting that will allow the Ubuntu OS to boot up to the desktop without have to wait at that selection screen?

---

### Post by yancek on 2015-07-12
It was my understanding that if Ubuntu were the only OS, no boot screen would show.  I've never had Ubuntu as the only OS so don't know from experience.  Hit the enter key when you see the screen and it will boot.  If you want to reduce the timeout, change the /etc/default/grub file, the line:  GRUB_TIMEOUT=10  Change the 10 to a smaller number.  Usually create problems for yourself later if you set it to zere.

---

### Post by Navin81 on 2015-07-12
Yea that was my understanding also.  I did a clean install from a windows 10 installation and I ended up with the boot screen.  It's just annoying to see it every time I boot up the laptop.  It's not a big deal but it just bugs me because I know it should not be there.  Wish there was a way to completely get rid of it.

---

### Post by thatsallurspaceships on 2015-07-12
Well you might aswell set timeout to zero but it is not recommended. Then you also should read this afterwards.
[http://ubuntuforums.org/showthread.php?t=1904617](http://ubuntuforums.org/showthread.php?t=1904617)
There are other ways to speed up boot-time, by disabling unneeded services (if it is necessar...), because grub menu might get useful to have the boot choice when things break.

---

### Post by Navin81 on 2015-07-12
So basically there is no way of getting rid of that boot menu without trying another clean install?

---

### Post by Bucky Ball on 2015-07-12
Yes, there is. Open a terminal and:

```
sudo nano /etc/default/grub
```

Then look for this section at the top of the file (yours will look different):

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
**GRUB_TIMEOUT=10**
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
GRUB_CMDLINE_LINUX=""
```

The line in bold, make it zero (do not change anything else in that file)

```
GRUB_TIMEOUT=0
```

Type control+x, 'y' to save and exit, then:

```
sudo update-grub
```

If you ever need to get back into the menu, hit shift (or it might have changed to escape) right after boot.

---

### Post by Navin81 on 2015-07-12
Thanks a bunch.  That did the trick.  This OS feels so strange to navigate around.  I like it but it's daunting to try and find fixes.  I guess that is only natural coming from a longtime windows user.  Thanks again for the help.

---

### Post by Bucky Ball on 2015-07-12
> **Navin81 said:**
> This OS feels so strange to navigate around.  I like it but it's daunting to try and find fixes.  I guess that is only natural coming from a longtime windows user.  Thanks again for the help.

That feeling is normal and will pass. :)

Once you're fixed, though, it pretty much stays fixed, especially with LTS releases, and it won't seem so daunting once you know your way around a bit. The learning curve certainly has its rewards.

On the point of Ubuntu releases, you are using 14.04 LTS? If you are using 14.10, I would either install 14.04 LTS (supported until 2019) or 15.04 (January 2016) as 14.10 is out of support in a week or so. 

There are other desktop environments that are more Windows like. I use xfce4 myself. You might like to try some others. You can try Xubuntu (which uses xfce4) for instance, by creating install media from Xubuntu .iso, booting from it and 'Try Xubuntu' without installing anything to the hard drive. A 'Try before you buy'. 

You might like to look at these DEs:

xfce4
lxde
razor qt
enlightenment
mate

Apparently Mate DE is very Windows like and Ubuntu-Mate is now officially supported both here and by Canonical. Good luck. 

(PS: I'm getting a bit/lot off-topic so could you mark this thread as solved (which doesn't close the thread but does help others - see the second link in my signature), and post a new thread in Desktop Environments for any questions/problems about them. ;))

---

