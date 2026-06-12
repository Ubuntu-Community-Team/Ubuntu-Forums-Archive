---
title: "Check Nvidia driver version"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by jbrown96 on 2008-07-15
How do I check which version of the nvidia drivers are in use? I know I'm using the proprietary driver but am unsure which version number.

thanks.

---

### Post by overdrank on 2008-07-15
> **jbrown96 said:**
> How do I check which version of the nvidia drivers are in use? I know I'm using the proprietary driver but am unsure which version number.

thanks.

HI and you can view it in the nvidia settings. Use the alt F2 keys and enter ```
gksu nvidia-settings
```

---

### Post by jbrown96 on 2008-07-15
Is there a way to do it without installing nvidia-settings? Perhaps via command line?

---

### Post by overdrank on 2008-07-15
> **jbrown96 said:**
> Is there a way to do it without installing nvidia-settings? Perhaps via command line?

```
dpkg -l | grep nvidia

```

---

### Post by sdennie on 2008-07-15
This should work from the command line:

```

nvidia-settings -q NvidiaDriverVersion

```

And this should work without needing nvidia-settings

```

grep -i "x driver" /var/log/Xorg.0.log

```

---

### Post by jbrown96 on 2008-07-15
Thanks for the help. I seem to have caused a new problem. I had the nvidia drivers that ubuntu installs (169.12). I downloaded the new drivers (173.14.09) from Nvidia and installed them. However, now I have two problems. First, the x server does not automatically start. It's not much of a problem, but I would like to fix it. Second, I can't start the x server at all. There are several error messages, but it seems to be an installation error. The most important part of the message is > Error: API mismatch: the NVIDIA kernel module has version 169.12, but this NVIDIA driver component has version 173.14.09. Please make sure that the kernel module and all NVIDIA driver components have the same version. It references a log file that I could not attach because it's too large, and it doesn't seem to be of any help - it's just memory locations where resources were unavailable.

Could someone help me update the kernel module?

I tried installing a the same version but from a new download, and now the error says that the mismatch is 71.86.04 and 173.14.09, respectively.

---

### Post by sdennie on 2008-07-15
Try this link: [http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2](http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2).  And possibly re-install the downloaded drivers before rebooting.

---

### Post by jbrown96 on 2008-07-15
> **vor said:**
> Try this link: [http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2](http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2).  And possibly re-install the downloaded drivers before rebooting.

This didn't work. However, I did get X working with ```
dpkg-reconfigure xserver-xorg
```. I am getting a new error, which may have something to do with a lack of X starting automatically. I recently downloaded the new alpha of Amarok2. I mistakenly uncompressed it in my home folder. It created a lot of files, and I haven't been able to move them because Dolphin keeps crashing. I think the error has something to do with all those files. The error says > @@@ToBeReplacedByDesktopBase@@@; it is in a KDE dialog box, so X must start then fail. I am then dumped to a terminal login, but I can start X with ```
startx
```.

I uninstalled everything related to Nvidia and was going to try to install the drivers from scratch. The hardware manager does not seem my card anymore, and I cannot install the Nvidia driver. I tried with and without the modification to /etc/default/linux-restricted-modules-common.

---

