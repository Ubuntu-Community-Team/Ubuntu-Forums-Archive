---
title: "Log in Failure"
date: 2014-03-10
forum: New to Ubuntu
---

### Post by Brad wilkinson on 2014-03-10
Hello,

This morning when I booted my 12.04LTS desktop it would not let me log in.

What happens is when I get to the screen to select user name and enter password, after entering the correct password it just blanks the screen and then brings you back to the log in screen again.

If you type in the wrong password it gives you the error message, so I know I am entering the correct password when I do.

I also have a "guest" account that has no password required, and when I tried to use that account it just loops back to the log in screen again.

I tried selecting different versions of the kernel from grub, both regular and recovery versions and that makes no difference.

Since the last Live disk I have is 10.10 it doesn't seem to play nicely with my DVD drive, so I couldn't open a Live session of Ubuntu.

So I went and bought a new HDD (and a 8-gig usb drive) then swapped out the misbehaving HDD for the new one and installed 10.10 on the new HDD (which is how I got to here).

Does anyone recognise this problem? I searched the forum titles for the same issue, and there seem to be a few similar, but they are usually for much older versions of Ubuntu.

I was thinking that my best bet would to be to make a Bootable USB drive for 12.04 and then swap the old HDD back in and see if I can fix things that way.

If it would help diagnose the problem I could also pop the misbehaving HDD in an external cradle before reinstalling.

My PC is a AMD Phenom II X6 1055 with 8G of ram and a AMD/ATI radeon 5850. No other peripherals other than the DVD drive.

I wasn't downloading or updating anything when I shut down.

Cheers,

Brad

---

### Post by Brad wilkinson on 2014-03-11
OK, so now I have a bootable USB stick with the latest 12.04 LTS iso image on it, and I know it works (it's how I got here this time).

However before I pull out my new HDD to put back the old misbehaving one, I booted onto the machine with the 10.10 HDD still in it, and I got a number of questions, like 'install in new partition', 'upgrade 10.10 to 12.04' and 'erase 10.10 and install 12.04'.

But there were no 'would youlike to repair the current os' options.

So can someone please tell me if the live CD will ask me about repairing the 12.04 on my old disk?

---

### Post by bapoumba on 2014-03-11
First make sure you are not running out of space in your misbehaving HD (/home, root, or other essential system partitions).
```
df -h
```

---

### Post by Brad wilkinson on 2014-03-11
Thanks for the reply bapoumba.

The misbehaving HDD had ~800Gb free space last time I checked (a few days before it went bad).

---

### Post by bapoumba on 2014-03-11
> **Brad wilkinson said:**
> Thanks for the reply bapoumba.

The misbehaving HDD had ~800Gb free space last time I checked (a few days before it went bad).

OK, fine with me, but just make sure _some_ particular partition is not running out of space (/boot may be if you have one for ex, or root if you have kept may kernels). The fact your guest user cannot log in leads to some problem with the system and not only with a particular user.

Some errors could help pinpoint the issue. Can your boot in one of the virtual terminals ?

---

### Post by Brad wilkinson on 2014-03-11
I could get to the login screen (GDM?) but from that point I was unable to do anything as I described in the first post.

So I don't know if I would be able to run a terminal session, as I would still have to log in, which seemed to be the problem I was having with the graphical connection.

EDIT 

As far as I know, the 12.04 install that is playing up is all by itself on a ~1Tb partition on a 2Tb drive. I didn't manually include different partitions for the various /directories, so unless that is part of the installation they should all have plenty of room. 

I never manually repartitioned it for different kernel versions, whenever they hit the repo's I just let synaptic/apt do its thing.

---

### Post by bapoumba on 2014-03-11
> **Brad wilkinson said:**
> I could get to the login screen (GDM?) but from that point I was unable to do anything as I described in the first post.

So I don't know if I would be able to run a terminal session, as I would still have to log in, which seemed to be the problem I was having with the graphical connection.

You'll have to check it from a live session i'm afraid then.

Here are the steps to chroot to a partition (up to step #5) [http://ubuntuforums.org/showthread.php?t=2193917&p=12877164#post12877164](http://ubuntuforums.org/showthread.php?t=2193917&p=12877164#post12877164)

Then you'll have to test your different partitions. As i'm not that comfortable with the chroot, I'll ping steeldriver to see if they can assist you.

---

### Post by steeldriver on 2014-03-11
Before trying a chroot environment, I'd suggest *trying* to log in at one of the non-GUI virtual terminals (Ctrl-Alt-F1 / Ctrl-Alt-F2 etc.) - the GUI session startup does a lot of extra stuff besides login so it's by no means a given that it won't work. If you can get in that way, we can look at the display manager log files to see if anything jumps out. It's certainly unusual for ALL logins to be affected - most often the problem is with a particular user's session / profile / home dir.

I don't have any experience with gdm (did you install gdm manually or is that a left-over from upgrading? the default for 12.04 is lightdm). Another possibility might be to install / switch to lightdm.

---

