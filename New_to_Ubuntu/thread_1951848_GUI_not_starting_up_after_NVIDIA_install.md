---
title: "GUI not starting up after NVIDIA install"
date: 2012-04-03
forum: New to Ubuntu
---

### Post by sknth on 2012-04-03
Hi everyone, I'm new here and have just installed Ubuntu 11.10, and installed a few applications. I wanted to install the NVIDIA driver which I downloaded from nvidia.com.

Had to stop lightdm for running the install.
Went to tty1 and ran it. It reported one error, "failed to load the pre-install script", Is that serious? Anyway, I continued with the installation, and once it completed, I rebooted my pc.

Now when Ubuntu boots up, after grub and the Ubuntu loading screen, the GUI doesn't load at all. It freezes in the process of starting the numerous services.

Even if I navigate to tty1 and try to start lightdm, no use. I've tried uninstalling nvidia, and rebooting the pc. Again, no luck. How do I solve this?

---

### Post by zombifier25 on 2012-04-03
It's not enough just to remove NVidia driver. You must restore the Noveau driver.
The steps to do so is here: [https://wiki.ubuntu.com/X/Troubleshooting/NvidiaDriverSwitching](https://wiki.ubuntu.com/X/Troubleshooting/NvidiaDriverSwitching)

---

### Post by sknth on 2012-04-03
Thanks. I'll try this and let you know what happens. :)

---

### Post by ksprasad on 2012-04-03
Hi,
 
Which Nvidia card you are having? Does is support Optimus? If so, you cannot directly install driver from nvidia site. You can install Bumblebee. Else go with default Nouveau driver.
 
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
 
Regards,
ksprasad

---

### Post by kc1di on 2012-04-03
after you have done what zombifier25 suggests go to ```
system setting > additional drivers
``` and install the Nvidia driver from there.
It should offer you a couple of choice depending on your actual Nvidia card.

Good Luck

---

### Post by sknth on 2012-04-03
> **zombifier25 said:**
> It's not enough just to remove NVidia driver. You must restore the Noveau driver.
The steps to do so is here: [https://wiki.ubuntu.com/X/Troubleshooting/NvidiaDriverSwitching](https://wiki.ubuntu.com/X/Troubleshooting/NvidiaDriverSwitching)
I followed the complete removal of nvidia and noveau and reinstallation of only noveau.. However, now, after selecting Ubuntu in grub and the Ubuntu loading screen, the screen stays blank, and I am not able to do anything except Ctrl + Alt + Del to reboot the pc.

---

### Post by sknth on 2012-04-03
> **kc1di said:**
> after you have done what zombifier25 suggests go to ```
system setting > additional drivers
``` and install the Nvidia driver from there.
It should offer you a couple of choice depending on your actual Nvidia card.

Good Luck
I did that the moment I installed Ubuntu. But I thought I required the specific driver from the nvidia site as well.

---

### Post by ksprasad on 2012-04-03
> **sknth said:**
> I followed the complete removal of nvidia and noveau and reinstallation of only noveau.. However, now, after selecting Ubuntu in grub and the Ubuntu loading screen, the screen stays blank, and I am not able to do anything except Ctrl + Alt + Del to reboot the pc.
 
 
Go to recovery mode. See if Xorg.conf exists.
 
/etc/X11/xorg.conf
 
If its there, remove it or move it to some other place. Then reboot.
 
Regards,
ksprasad

---

### Post by jerome1232 on 2012-04-03
> **sknth said:**
> I did that the moment I installed Ubuntu. But I thought I required the specific driver from the nvidia site as well.

No, the one you install through the additional drivers is one from nvidia, albiet it may be a bit older than the current one on nvidia's website.

It's best to stick with the one in additional drivers unless you really, really need the newest driver (you need a bug fix etc..)

Is this a laptop? If so does it have optimus? Currently optimus is not supported by nvidia's drivers, and you will have to stick with noveau (which doesn't do 3d very well)

--snip-- 

Turns out you have optimus.

---

### Post by sknth on 2012-04-03
> **ksprasad said:**
> Go to recovery mode. See if Xorg.conf exists.
 
/etc/X11/xorg.conf
 
If its there, remove it or move it to some other place. Then reboot.
 
Regards,
ksprasad
I am in root mode after choosing recovery.

I am in /etc/X11 and xorg.conf is present. However, I get the following error:
"mv: cannot move 'xorg.conf' to '/home/xorg.conf': Read-only file system"

Changing permissions using chmod 777 doesn't work either. Same result.

---

### Post by jerome1232 on 2012-04-03
the filesystem is mounted readonly remount it

```
sudo mount / -o remount,rw
```

---

### Post by sknth on 2012-04-03
> **jerome1232 said:**
> No, the one you install through the additional drivers is one from nvidia, albiet it may be a bit older than the current one on nvidia's website.

It's best to stick with the one in additional drivers unless you really, really need the newest driver (you need a bug fix etc..)

Is this a laptop? If so does it have optimus? Currently optimus is not supported by nvidia's drivers, and you will have to stick with noveau (which doesn't do 3d very well)

If this is a desktop or you are postiive you do not have a hybrid (optimus) card, I would try, from a terminal, reinstalling nvidia-current, and just to be sure running nvidia-xconfig, then rebooting.

Hit ctrl+alt+f1 and...
```
sudo apt-get install nvidia-current
sudo nvidia-xconfig
sudo reboot
```
Ok, now I know it. 

This is a Dell XPS L502X laptop with an Nvidia GeForce GT540M graphics card. I am not sure if I have optimus. Right now I'm trying what ksprasad has suggested. However, it is not working as per my previous reply.

---

### Post by jerome1232 on 2012-04-03
Based on my quick googleing, that laptop does indeed have optimus, so you'll need to try the bumblee thing someone mentioned (perhaps after you get noveau working again)

---

### Post by sknth on 2012-04-03
> **jerome1232 said:**
> the filesystem is mounted readonly remount it

```
sudo mount / -o remount,rw
```
It's working now! I just rebooted the system and voila! Noveau is back.

However, now once I log in, I don't see Unity anymore. The taskbar is missing too. All I have is an empty desktop, with "File    Edit     View    Go     Bookmarks    Help" at the top left of the screen.

---

### Post by ksprasad on 2012-04-03
Hi,
 
Press Alt+F2. Then type unity --replace. Hit enter.
 
Regards,
ksprasad

---

### Post by jerome1232 on 2012-04-03
Have a looksie here, I can't garuntee this guide will work 100% but it looked good to me

[http://hanynowsky.wordpress.com/2011/11/12/dell-xps-15-l502x-linux-ubuntu-11-10/](http://hanynowsky.wordpress.com/2011/11/12/dell-xps-15-l502x-linux-ubuntu-11-10/)

---

### Post by sknth on 2012-04-03
> **ksprasad said:**
> Hi,
 
Press Alt+F2. Then type unity --replace. Hit enter.
 
Regards,
ksprasad
Alt + F2 doesn't work. I can use the Desktop Wall (Ctrl + Alt + Arrow) . Ctrl + Alt + T opens the terminal. That's all the functionality I currently have. 

I don't see the battery, power, messaging icons on the taskbar at the top right.

---

### Post by sknth on 2012-04-03
> **jerome1232 said:**
> Have a looksie here, I can't garuntee this guide will work 100% but it looked good to me

[http://hanynowsky.wordpress.com/2011/11/12/dell-xps-15-l502x-linux-ubuntu-11-10/](http://hanynowsky.wordpress.com/2011/11/12/dell-xps-15-l502x-linux-ubuntu-11-10/)
Nice blog :). I'll do that once this issue is fixed and I have standard GUI working!

---

### Post by jerome1232 on 2012-04-03
run that in a terminal then, alternativly press ctrl+alt+f1, login and run it, then restart lightdm

```
unity --reset
sudo lightdm restart
```

Make sure your session is set to unity 3d or unity 2d when you login.

---

### Post by sknth on 2012-04-03
> **jerome1232 said:**
> run that in a terminal then, alternativly press ctrl+alt+f1, login and run it, then restart lightdm

```
unity --reset
sudo lightdm restart
```

Make sure your session is set to unity 3d or unity 2d when you login.
[IMG]https://mail.google.com/mail/?ui=2&ik=55fcffa5a8&view=att&th=136785232afc7b56&attid=0.1&disp=inline&realattid=1398233341884366848-1&safe=1&zw[/IMG]

---

### Post by sknth on 2012-04-03
> **jerome1232 said:**
> run that in a terminal then, alternativly press ctrl+alt+f1, login and run it, then restart lightdm

```
unity --reset
sudo lightdm restart
```

Make sure your session is set to unity 3d or unity 2d when you login.
that's my screen. Sorry it's a little blurred.. took it with the phone.

---

### Post by sknth on 2012-04-03
Ok! It worked now :). My Unity desktop is back, and it's working fine. I'm rebooting my pc to see if things are permanent!

I will install bumblebee now as that's the one supported.

How do I return to the desktops of 10.10 and older, i.e. no Unity?

---

### Post by zombifier25 on 2012-04-03
If you want a "classic" interface, install gnome-session-fallback
```
sudo apt-get install gnome-session-fallback
```then logout, and choose Classic Session at boot.
If you want to customize the panel, Alt - Right Click or Super - Right Click instead of just Right Click in older versions.

---

### Post by jerome1232 on 2012-04-03
> **sknth said:**
> Ok! It worked now :). My Unity desktop is back, and it's working fine. I'm rebooting my pc to see if things are permanent!

I will install bumblebee now as that's the one supported.

How do I return to the desktops of 10.10 and older, i.e. no Unity?

I humbly propose that you give unity a week, it grows on you, if it doesn't (or you absolutly hate it and you know it) That's ok, I'll try and not hold it against you.

---

### Post by Mariane on 2012-04-03
Is there also a kde-session-fallback?

---

### Post by ksprasad on 2012-04-03
> **Mariane said:**
> Is there also a kde-session-fallback?
 
I think the only option is kubuntu-desktop
 
```

sudo apt-get install kubuntu-desktop

```
 
 
Regards,
ksprasad

---

### Post by nardis_Miles1 on 2012-04-03
I just had a huge problem with nouveau-- machine would freeze on the first Ubutntu screen (the one with the five white/red dots). The screen would blink every 10 seconds. I finally was able to see it was a nouveau problem (no native ...  ), and even more finally, I figured out how to get the grub menu, and from there, I was able to make progress (remove nouveau, install the evil, but functional, proprietary driver). My big question is this: I had updated from maverick that was also using (happily) the evil, proprietary driver. To my knowledge, I never used nouveau before. Suddenly, it was my default graphics driver. WHY?! Is nouveau the default nvidia driver no matter what?

---

### Post by ksprasad on 2012-04-04
> **nardis_Miles1 said:**
> I just had a huge problem with nouveau-- machine would freeze on the first Ubutntu screen (the one with the five white/red dots). The screen would blink every 10 seconds. I finally was able to see it was a nouveau problem (no native ... ), and even more finally, I figured out how to get the grub menu, and from there, I was able to make progress (remove nouveau, install the evil, but functional, proprietary driver). My big question is this: I had updated from maverick that was also using (happily) the evil, proprietary driver. To my knowledge, I never used nouveau before. Suddenly, it was my default graphics driver. WHY?! Is nouveau the default nvidia driver no matter what?
 
Since this is a solved thread, I suggest you start a new thread :p
 
Regards,
ksprasad

---

