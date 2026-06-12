---
title: "Kernel update question"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by FokkerCharlie on 2008-05-26
Hello, and good evening from Windy Cheshire!

The auto update feature installed a new kernel version a couple of hours ago, and it seems that I have successfully advanced to 2.6.24-17-generic.  However, the option to boot the previous version still exists (and works) in GRUB.  uname -r returns the appropriate versions (16 or 17, according to my GRUB selection), and both seem to work fine.

So, it looks like I have 2 kernels installed.  Is this a desirable situation?  Should I remove the older one?  If so, how?  Or perhaps I would just be better editing menu.lst for cosmetic effect?

And while we're at it, where can I find a list of the improvements that -17 brings?

Thanks!
Charlie

---

### Post by brommage on 2008-05-26
Don't worry about having multiple kernels installed, Charlie.  They take up very little space.  

A desirable solution to your problem might be to update your settings in /boot/grub/menu.lst to only show a boot prompt for the most recent kernel.

---

### Post by tgm4883 on 2008-05-26
That is how you want to have it (listing both kernels)  The new kernel should be the default, and if you had encountered any problems when booting it you could have easily reverted back to the old kernel.

---

### Post by FokkerCharlie on 2008-05-26
Thanks, chaps.

Have a good evening.

Charlie

---

### Post by philinux on 2008-05-26
You can install startupmanager from synaptic. You can tell it to display the number of kernels.

I would not uninstall previous ones in case of problems but SUM keeps grub menu clean. And you can always change it easily.

---

### Post by iansane on 2008-05-26
sorry to but in but when should one draw the line. There have been a lot of kernel updates in the last few months and everytime I get one for server, I have to install the one for Desktop too because I have ubuntu desktop and nvidia drivers which require the desktop kernel to build and install.

So everytime I get an update, I end up with server, server recovery, generic, and generic recovery. They build up quick and now grub fills my entire screen.

Is it safe to use synaptic to remove all but the newest and the last one?

I'm afraid if I remove them, something depending on one of them will fail.

---

### Post by iansane on 2008-05-26
> **philinux said:**
> You can install startupmanager from synaptic. You can tell it to display the number of kernels.

I would not uninstall previous ones in case of problems but SUM keeps grub menu clean. And you can always change it easily.

sorry, you answered my question while I was typing it.

---

### Post by philinux on 2008-05-26
You can also remove the older ones via synaptic.

---

### Post by wariskampar on 2008-05-27
Hello, i also face similar problem here. Update kernel using Update Manager last night but GRUB still use old kernel. How do I ensure UBuntu to use new kernel. I already installed StartUpManager(SUM), but can not see new kernel option in OS option.

---

### Post by brommage on 2008-05-29
> **wariskampar said:**
> Hello, i also face similar problem here. Update kernel using Update Manager last night but GRUB still use old kernel. How do I ensure UBuntu to use new kernel. I already installed StartUpManager(SUM), but can not see new kernel option in OS option.

run:

```
sudo update-grub 
```

It should update the menu.lst file to give you the most recent kernel on the boot prompt.

---

