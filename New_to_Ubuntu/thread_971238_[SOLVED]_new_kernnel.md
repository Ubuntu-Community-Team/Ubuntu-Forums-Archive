---
title: "[SOLVED] new kernnel"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by pgte3 on 2008-11-04
I have downloaded an new kernel via the update manager. How do I begin using it? My old kernel still appears in my grub menu.

Also, how can I tell how many kernels have been downloaded and are available on my Ubuntu install?

---

### Post by drs305 on 2008-11-04
For new users I strongly recommend using a gui-based app called StartUp-Manager. It will let you set the default OS and/or kernel, what to do when new kernels become available, how long to display the menu and much more. And you don't have to manually edit /boot/grub/menu.lst

To install:
```
sudo apt-get install startupmanager
```
To run:
System, Administration, StartUp-Manager

To set the default kernel (or OS), set it on the main "Boot Options" tab.

The app can also set how many kernels you see on the menu. It can hide unused ones but will not remove them from your machine.

Here is a tutorial link to StartUp-Manager:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by pgte3 on 2008-11-04
Thanks for the tip. Synaptic says that I have two Linux kernels installed, 2.6.24-19 and 2.6.24-24. I do not see how select a kernel using Startup-manager?

---

### Post by drs305 on 2008-11-04
> **pgte3 said:**
> Thanks for the tip. Synaptic says that I have two Linux kernels installed, 2.6.24-19 and 2.6.24-24. I do not see how select a kernel using Startup-manager?

On the Boot Options page, in the middle is the 'Default operating system'. If you click on it, you will see the available kernels. Select one.

---

### Post by pgte3 on 2008-11-04
I took a look at this when I first installed Startup-manager. I only see 2.6.24-19 not 2.6.24-24.

Maybe I need to update menu.lst if I want to change kernels?

When a new kernel is available for install how does Ubuntu handle it, is the new kernel downloaded and installed, but it is up to me to do something to begin using it?

---

### Post by snova on 2008-11-04
When a new kernel is installed, I am quite certain that Apt changes things so that it becomes the default. You do not need to do anything.

The old kernel still appears because it is Apt policy not to remove old ones in case the most recent one fails somehow. You can remove them manually via the package manager.

---

### Post by drs305 on 2008-11-04
> **pgte3 said:**
> When a new kernel is available for install how does Ubuntu handle it, is the new kernel downloaded and installed, but it is up to me to do something to begin using it?

It is decided by what is in /boot/grub/menu.lst when a new kernel is introduced. Specifically, it is the section below.

On the Advanced tab of Startup-Manager there is a section "Automatically update the default boot option'. It changes this section of menu.lst:
```

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

```
If you wanted grub to automatically use a new kernel, this entry should be *true*. I do not remember what the default setting is. It is possible this has to be ticked in StartUp-Manager before it displays in either the menu.lst or SUM options although I don't recall that being necessary. 

At this point, perhaps it would be best if you just posted your menu.lst so we can take a look at it:

```
cat /boot/grub/menu.lst
```

---

### Post by sdennie on 2008-11-04
As snova said, on a new kernel install, the script "update-grub" is automatically run.  This functionality happens at the package level (and configurable with /etc/kernel-img.conf and /etc/kernel.d) for all kernels built "the Ubuntu way" (probably more accurately, "the Debian way" but, I've not built Debian kernels).  Anytime you install a kernel .deb, it will run update-grub and add that kernel to grubs list unless you've turned that off in /etc/kernel-img.conf.

By default, /boot/grub/menu.lst has the default kernel set to the first kernel in the list of kernels.  Because new Ubuntu kernels always increase in version number (and therefore appear higher in the list), this should mean that you should never have to conscientiously do anything on kernel updates because you will always boot into the newest kernel.

@drs305: I actually don't know what "updatedefaultentry" does.  By default it is set to "false" and I use it with "false" but, I use "savedefault=true" and have manually set "default saved" at the top of /boot/grub/menu.lst.  This makes grub remember the last kernel I used and boot into it regardless of what number it is in the kernel list.

---

### Post by drs305 on 2008-11-05
pgte3, 

How did you install the 2.6.24-24 kernel? You say you used update manager but I can't find the -24 kernel in any of the 'official' ubuntu repositories. I believe the latest supported kernel is 2.6.24-21.

If you would like to use -21, you can open synaptic, select "linux-image" (with nothing else). Selecting 'linux-image' will always install the latest generic linux kernel image, so you don't have to append the version number to install it.

Installing the -21 kernel version via this method should introduce it to your grub menu.lst and also make it available via StartUp-Manager.

If you really want to try to use the -24 kernel, you might try marking it for reinstallation and see if that gets it into the grub menu or StartUp-Manager.

---

### Post by pgte3 on 2008-11-05
Thanks for the posts, they were helpful. I think I have enough information to move on.

Thanks, pgte3

---

