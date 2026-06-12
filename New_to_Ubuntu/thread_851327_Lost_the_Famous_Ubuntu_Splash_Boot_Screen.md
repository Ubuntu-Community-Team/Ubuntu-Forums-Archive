---
title: "Lost the Famous Ubuntu Splash Boot Screen"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by bobnutfield on 2008-07-06
Hello Everyone,

I posted this back in May in the INSTALLATION forum, but was never able to find a solution and this one has me stumped. I wanted to install a second distro on my laptop where Hardy is my main OS. I needed something I thought would be a little more stable until Hardy gets a little more mature. So, I added an extended partion and installed Slackware, never touching the partition that Hardy is installed on.

After the Slackware install, Hardy no longer has the famous moving bar (splash screen) during boot-up. It boots up OK and gets me to the login screen, but totally in text mode. But, it shuts down WITH the nice little bouncing bar. I really feel more comfortable having the splash screen, for both boot and shutdown.  I know that this is a function of the boot entries in menu.lst, and it was not changed at all, other than to add the entry to boot Slackware.  "quiet splash" is still in the boot line for Hardy.

Anyone have any ideas how to restore this? The menu.lst still has the splash entry in the boot line.

Any replies appreciated.

---

### Post by jimbob on 2008-07-06
This worked for me sometime ago:

sudo apt-get remove ubuntu-artwork-usplash
sudo apt-get install --reinstall usplash

You may have to regenerate initrd.img also.

---

### Post by sayakb on 2008-07-06
Shouldn't it be **ro quiet splash** at the boot line.
Anyway, also try startup manager
```
sudo apt-get install startupmanager
```

---

### Post by caljohnsmith on 2008-07-06
I think you may have the exact same type of problem I had, and it has to do with your UUIDs changing when you added the extra partition. See this thread for the details, and how to fix it:
[http://ubuntuforums.org/showthread.php?t=828578](http://ubuntuforums.org/showthread.php?t=828578)
Before uninstalling and reinstalling your splash screen, I would recommend you at least check whether your UUIDs are consistent as detailed in the thread above, because if that is your problem, then uninstalling/reinstalling the splash screen won't help in this case.

---

### Post by bobnutfield on 2008-07-06
Jimbob--Thank you, I will try that.  I have not tried uninstalling and reinstalling yet.

LinuxIsInnovation--Thank you for the reply.  I already have StartUpManager installed and have tried using that to restore the splash screen, but no dice that way.

In the end, it is not earth shaking if I cannot restore it as everything else works find.  I get to the login window with no problems.

---

### Post by Fixman on 2008-07-06
> **bobnutfield said:**
> Hello Everyone,

I posted this back in May in the INSTALLATION forum, but was never able to find a solution and this one has me stumped. I wanted to install a second distro on my laptop where Hardy is my main OS. I needed something I thought would be a little more stable until Hardy gets a little more mature. So, I added an extended partion and installed Slackware, never touching the partition that Hardy is installed on.

After the Slackware install, Hardy no longer has the famous moving bar (splash screen) during boot-up. It boots up OK and gets me to the login screen, but totally in text mode. But, it shuts down WITH the nice little bouncing bar. I really feel more comfortable having the splash screen, for both boot and shutdown.  I know that this is a function of the boot entries in menu.lst, and it was not changed at all, other than to add the entry to boot Slackware.  "quiet splash" is still in the boot line for Hardy.

Anyone have any ideas how to restore this? The menu.lst still has the splash entry in the boot line.

Any replies appreciated.

```
 gksu gedit /boot/grub/menu.lst 
```
Search for the Ubuntu entry and add "quiet splash" at the end.

---

### Post by peacewithall on 2008-11-02
> **LinuxIsInnovation said:**
> Shouldn't it be **ro quiet splash** at the boot line.
Anyway, also try startup manager
```
sudo apt-get install startupmanager
```

After my failed experimentations at adding a new boot screen (and totally losing the default boot screen), not only did this help me get my boot screen back, but also all the boot screens that I was trying to use. I think what did it was the option to adjust resolution, when I first installed Intrepid Ibex my boot screen was stuck at 640x480, now I have it at 1280x1024.

Any way it worked and thanks for sharing as always everyone :) .

---

### Post by shane2peru on 2008-11-02
> **jimbob said:**
> This worked for me sometime ago:

sudo apt-get remove ubuntu-artwork-usplash
sudo apt-get install --reinstall usplash

You may have to regenerate initrd.img also.

I had installed kubuntu, and consequently lost my beloved ubuntu bootup splash screen.  This fixed it!!!  Thanks.

Shane

---

