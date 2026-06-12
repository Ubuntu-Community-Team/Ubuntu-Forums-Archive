---
title: "Too many grub choices after 8.04 upgrade?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by vidus on 2008-04-25
So I decided to upgrade to 8.04 on my dual boot machine. I did the upgrade from the update manager inside 7.10.

Everyone went smoothly.. I think (I was sleeping). But then it started this Ubuntu memtest86+. It lasted about 3 hours before I finally got annoyed by the fan on the laptop and turned it off. Do I have to let this complete before running 8.04??

Also, wehn grub loads I am given more choices than I had with 7.10. The list is as follow:

Ubuntu 8.04, kernel 2.6.24-**16**-generic
Ubuntu 8.04, kernel 2.6.24-**16**-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-**14**-generic
Ubuntu 8.04, kernel 2.6.24-**14**-generic (recover mode)
Ubuntu 8.04, memtest86+
Other operating systems:
Microsoft windows xp home edition

What the heck are all these Ubuntu choices?? I only had the 2 choices before, regular and recovery..

I am confused.

---

### Post by indytim on 2008-04-25
It's because you've experienced a kernel upgrade.

The easiest thing to do is to:
1.  Make a copy of /boot/grub/menu.lst
2.  Edit the /boot/grub/menu.lst and comment out the old stuff
3.  Save and re-boot.

Note : You will experience this slight inconvenience on each kernel upgrade.  If you have multiple Lxs to boot to, you may want to check out the link in my signature for one possible remedy.

IndyTim

---

### Post by philinux on 2008-04-25
You could install startupmanager, one of the optional choices is how many kernels to display. It can be a lifesaver to have old kernels knocking around that work but say telling sum to display only one.

---

### Post by y-lee on 2008-04-25
> But then it started this Ubuntu memtest86+. It lasted about 3 hours before I finally got annoyed by the fan on the laptop and turned it off. Do I have to let this complete before running 8.04??


If the update went ok probably not. memtest just test your memory chips to be sure they are working right. You only need to run it when you want to check your memory to make sure it is working ok or if you are sure something is wrong and you suspect it is your memory.


> What the heck are all these Ubuntu choices?? I only had the 2 choices before, regular and recovery..



Ok this is nothing to worry about. Every time Ubuntu updates its kernel 2 more entries will be added to to grub. I always leave my last kernel and my latest kernel in my grub menu list (both normal and recovery). I do this in case If I have problems with the newest I can go back to the old (which i know works). Now when i end up with lots of kernel updates and a long grub menu list then I uninstall the older kernels using synaptic package manager. That should remove their grub entries. If if you don't want to uninstall them you can edit the grub menu list directly.

In your case when you boot up choose **Ubuntu 8.04, kernel 2.6.24-16-generic** which is the latest kernel use it for a couple of weeks and if everything is fine with it you can remove the other kernel if you wish. Post on the forums if you need help doing so if and when you decide.

---

### Post by IcemanV9 on 2008-04-25
That is perfectly normal. You have two kernels installed. If -16 causes the problem, then you can fall back to -14 until the fix is implemented for -16. If you don't have a problem with -16 and STILL want to remove -14. Then, you type in the terminal ...
```
sudo aptitude purge linux-image-2.6.24-14-generic
```
The grub will be updated automatically.

---

### Post by Oldsoldier2003 on 2008-04-25
> **IcemanV9 said:**
> That is perfectly normal. You have two kernels installed. If -16 causes the problem, then you can fall back to -14 until the fix is implemented for -16. If you don't have a problem with -16 and want to remove -14. Then, you type in the terminal ...
```
sudo aptitude purge linux-image-2.6.24-14-generic
```
The grub will be updated automatically.

+1  the best answer so far :) but honestly its always a good idea to keep a backup kernel in case you have issues. at the very least dont purge the old kernel immediately after an update because you may need a working kernel later due to unforeseen circumstances.

---

### Post by graeme2912 on 2010-10-03
thanks this will probably help later when I want to uninstall old versions

---

### Post by drs305 on 2010-10-03
For users who prefer GUI apps, no thread about removing kernels from the Grub menu can be considered complete (IMO) without a mention of Ubuntu-Tweak. It's a great app that allows a user to easily remove older kernels.

See the section "Removing older kernels" and specifically the Ubuntu-Tweak section of this thread for how to use Ubuntu-Tweak:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by slakkie on 2010-10-03
> **Oldsoldier2003 said:**
> +1  the best answer so far :) but honestly its always a good idea to keep a backup kernel in case you have issues. at the very least dont purge the old kernel immediately after an update because you may need a working kernel later due to unforeseen circumstances.

True, but you can always install an older kernel :)

eg, I now run the kernel from lucid-updates:

```

$ apt-cache policy linux-image-generic
linux-image-generic:
  Installed: 2.6.32.25.27
  Candidate: 2.6.32.25.27
  Version table:
     2.6.35.22.23 0
        300 http://archive.ubuntu.com/ubuntu/ maverick/main Packages
 *** 2.6.32.25.27 0
        995 http://archive.ubuntu.com/ubuntu/ lucid-updates/main Packages
        400 http://archive.ubuntu.com/ubuntu/ lucid-proposed/main Packages
        100 /var/lib/dpkg/status
     2.6.32.24.25 0
        995 http://security.ubuntu.com/ubuntu/ lucid-security/main Packages
     2.6.32.21.22 0
        995 http://archive.ubuntu.com/ubuntu/ lucid/main Packages
     2.6.31.22.35 0
        300 http://security.ubuntu.com/ubuntu/ karmic-security/main Packages
     2.6.31.14.27 0
        300 http://archive.ubuntu.com/ubuntu/ karmic/main Packages
     2.6.28.19.24 0
        300 http://security.ubuntu.com/ubuntu/ jaunty-security/main Packages
        300 http://archive.ubuntu.com/ubuntu/ jaunty-updates/main Packages
     2.6.28.11.15 0
        300 http://archive.ubuntu.com/ubuntu/ jaunty/main Packages

```

You can then issue the commands below to downgrade to a another kernel, eg the one from lucid from the release date. 

```

sudo aptitude install linux-image-generic/lucid
# or
sudo aptitude install linux-image-generic=2.6.32.21.22

```

Same goes for the kernel headers (replace image with headers and you are good).

But in general, you are right, keep the old kernel for a while and then remove it if you don't need it anymore.

---

