---
title: "Slow Ubuntu - video drivers issue ?"
date: 2020-02-02
forum: New to Ubuntu
---

### Post by valtiel2 on 2020-02-02
Hello,

I would like to investigate the reason why Ubuntu performs so poorly on my computer : windows are very slow when moved or maximized/reduced, scrolling is laggy, power management terrible (even with tlp), and command top shows that compiz takes minimum 250% CPU all the time (even when when idle !). I cannot rescale the interface or adjust luminosity for some reason.
I own a Dell XPS 15 9570, with integrated Intel graphics and a 1050Ti, with Win10 (that runs very smoothly) in dual boot with Ubuntu 16.04. I'm using this installation for C++ programming and need cuda to compile librairies.

After trying to install cuda, my computer got stuck in a login loop (surely because the installation updated the nvidia drivers, which already cause trouble in the past). I managed to painfully make it to desktop by purging cuda and several times nvidia and reinstalling blindly old or recommended drivers in tty (and what worked is no driver currently, i think. cf. image). Installing nvidia drivers always seem to succeed, but I'm always greeted with a "Possible missing firmware *** for module i915" and loging loop or black screen after reboot, so I have to purge and hope to be able to reboot again. After all this, the computer seems even slower.

The installation is always getting worse and worse as I have trouble with cuda or nvidia drivers.
I've had problems before ([SIZE=1][SIZE=2]Black screen after installing xserver-xorg, no internet in recovery mode[/SIZE] : [/SIZE][https://ubuntuforums.org/showthread.php?t=2427425](https://ubuntuforums.org/showthread.php?t=2427425)).

What should I try to fix all this ? Why is compiz so slow ?
Is there a right way to install cuda ?

Thank you for your help/tips !

---

### Post by CelticWarrior on 2020-02-02
Here are some potential problems:

[LIST]
[*]According to your screenshot, you have a mix of an added graphics drivers PPA and a "manually installed driver" that likely came from running a Nvidia binary and/or installing CUDA using Nvidia's instructions.
[*]Possible Secure Boot enabled.
[*]An old release.
[/LIST]

So, starting from the last one, why 16.04? Sure, it's still supported but why not use a newer release?
Also please confirm you have Secure Boot disabled in UEFI.
Finally, and back at the beginning, **you've made a mess already**. Nvidia drivers - and CUDA support as well - can and should be installed from the Ubuntu repositories. When a newer version is needed we then have an argument to add the third-party PPA but, in your case - because you need CUDA as well, that's an argument to use a **current released** and not a 4 years old one!

---

### Post by valtiel2 on 2020-02-02
Thank you for that quick response !

Secure boot disabled.

I'm using 16.04 LTS because of the librairies I'm working with, those aren't working under Ubuntu 18 for example (and I guess I have to use an older cuda version as well). I know this is far from ideal.

Is there a way to clean this ?

---

### Post by CelticWarrior on 2020-02-02
There's always a way to clean thing up but the amount and complexity of work now required to get the system to a point where the correct drivers can be tried again is huge. I wouldn't even start. Reinstalling Ubuntu would be my choice but please wait for other suggestions.

---

### Post by CatKiller on 2020-02-02
> **valtiel2 said:**
> Why is compiz so slow ? 

Because you're trying to do the whole OpenGL context emulated in software. 

> Is there a right way to install cuda ?

There are lots of ways to install CUDA that will work fine. There are also lots of ways to mess it up.

Making propriety software work isn't something that the rest of the ecosystem can do much about, or have that much interest in, and making their propriety software work on end-user desktop linux installs isn't something that Nvidia are terribly interested in. The other thing that you're trying to do - make it work on an Optimus setup - makes it harder still: "Optimus isn't intended to function on Linux" was Nvidia's official policy until quite recently.

Your best bet is to get rid of all your Nvidia and CUDA stuff first, and then install the proprietary driver so that you can make your Optimus setup work. Just that part can be a pain, and has various options for how you run each application, or if you use one device for everything for the whole session. Once you've got that working, it's relatively straightforward to install CUDA without mucking up your drivers. I found it quite painless to install the appropriate metapackage from Nvidia's repository when I was playing with it.

---

### Post by valtiel2 on 2020-02-02
> **CatKiller said:**
> Because you're trying to do the whole OpenGL context emulated in software. 

I don't get that. I would just like to have a functional desktop !

> **CatKiller said:**
> Making propriety software work isn't something that the rest of the ecosystem can do much about, or have that much interest in, and making their propriety software work on end-user desktop linux installs isn't something that Nvidia are terribly interested in. The other thing that you're trying to do - make it work on an Optimus setup - makes it harder still: "Optimus isn't intended to function on Linux" was Nvidia's official policy until quite recently.

Your best bet is to get rid of all your Nvidia and CUDA stuff first, and then install the proprietary driver so that you can make your Optimus setup work. Just that part can be a pain, and has various options for how you run each application, or if you use one device for everything for the whole session. Once you've got that working, it's relatively straightforward to install CUDA without mucking up your drivers. I found it quite painless to install the appropriate metapackage from Nvidia's repository when I was playing with it.

I had no idea, thank you for the insight. 

Is purging CUDA and Nvidia enough ? And then download manually the latest compatible driver on Nvidia's website ? 
Thank you for your help

---

### Post by CatKiller on 2020-02-02
> **valtiel2 said:**
> I don't get that. I would just like to have a functional desktop ! 

Compiz was specifically created to show off cool stuff you can do with graphics hardware acceleration. If you don't *have* hardware acceleration - because you've broken your graphics - then all of that needs to be emulated in software, which is slow and hard work. 

>  Is purging CUDA and Nvidia enough ? And then download manually the latest compatible driver on Nvidia's website ? 


Definitely don't do the last part. The driver file on the Nvidia website is really intended for package maintainers of the various distros rather than end users. End users should be using their distro's packages; for Ubuntu that's the packages in the main repositories or the graphics driver PPA if you need something newer. Using other methods is exactly the kind of thing that can break your graphics setup. 

As to whether purging the stuff will be sufficient, that depends on how thoroughly everything's been broken. A fresh install, and going for 18.04 rather than 16.04, may well be the quickest, most thorough, way to get back to a functional computer. 18.04 uses Gnome by default rather than Compiz/Unity, which might be a difference that matters to you or not.

Get a functioning computer first, by whichever method, then think about CUDA.

---

