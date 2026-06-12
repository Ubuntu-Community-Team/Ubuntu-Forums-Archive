---
title: "My Task bar is gone"
date: 2013-08-02
forum: New to Ubuntu
---

### Post by greatdane2 on 2013-08-02
Hi guys,

absolute noob here, installed ubuntu 12.04 yesterday, added some programs, all was good.

Today had to shut down my computer by pressing the hardware power button, restarted and instead of booting to the desktop I got some command line looking thing. Can't really remember what it said, sorry. I'm new to ubuntu and didn't know what I was supposed to do, but remembered seeing a friend type "startx" a long time ago on startup, so I tried that, gave username and pw and I booted to desktop. Only it wasn't the full desktop, it was the background image without any of the toolbars. I tried the windows shortcuts but obviously those don't work. I can't start any programs, I can create folders and documents and change the background but those are obviously useless. I tried resetting the computer but every time I boot I get to the same empty desktop.

There's gotta be an easy solution for this, right?

---

### Post by petrucho on 2013-08-02
Try using  "sudo service gdm start " instead of "startx" for full desktop, if it doesn't work, check if "sudo chkconfig --add gdm" gives you any error message

---

### Post by Dave_L on 2013-08-02
This may not help,  but it's worth a try.  Try rebooting with the command:

```
reboot
```

or you might need:

```
sudo reboot
```

If the first reboot doesn't fix the problem, try a  second reboot.

---

### Post by greatdane2 on 2013-08-02
I cannot type anything in command line or terminal because I cannot open them. I don't have any way of rebooting except for pushing the power button on my case. When putting it back on I go straight to the desktop, I'm even automatically logged in. I don't have any shortcut for terminal or any program on the desktop. I'm a sitting duck looking at my desktop background, able to create new folders and new documents on it but that's it.

---

### Post by Dave_L on 2013-08-02
Try Control+Alt+F2. That should give you a command shell interface.  If that works, Control+Alt+F7 should switch back to the graphic interface.

---

### Post by greatdane2 on 2013-08-02
> **Dave_L said:**
> Try Control+Alt+F2. That should give you a command shell interface.  If that works, Control+Alt+F7 should switch back to the graphic interface.
Awesome, didn't know that :oops:

> **Dave_L said:**
> This may not help, but it's worth a try. Try rebooting with the command:

```
reboot
```

or you might need:

```
sudo reboot
```

If the first reboot doesn't fix the problem, try a second reboot.
The one with the sudo made the system reboot, still same problem 

> **petrucho said:**
> Try using "sudo service gdm start " instead of "startx" for full desktop, if it doesn't work, check if "sudo chkconfig --add gdm" gives you any error message
didn't work, "gdm: unrecognized service".
 the 2nd one gave back "sudo: chkconfig: command not found"

edit: installed gdm, gave the command and it still gave me the exact same display without the task bars.

---

### Post by Werne on 2013-08-02
Just out of curiosity, did you by any chance play around with CompizConfig Settings Manager right before you had to forcibly power down your PC?

Anyway, Ubuntu uses LightDM by default, not GDM, therefore the command to start it should go:
```
sudo service lightdm start
```

---

### Post by greatdane2 on 2013-08-02
> **Werne said:**
> Just out of curiosity, did you by any chance play around with CompizConfig Settings Manager right before you had to forcibly power down your PC?

Anyway, Ubuntu uses LightDM by default, not GDM, therefore the command to start it should go:
```
sudo service lightdm start
```
start: job is already running: lightdm

no, wasn't using it, installed and started 0 A.D., left my computer alone for 30 minutes, it was frozen and I had to shut the computer down. Honestly don't know why this is happening, the only mistake I made was type startx on a reboot and now it seems like nobody knows how to solve it and I'll have to reinstall my os on day 2 to get it back to normal, seems like a bad omen.:(

---

### Post by grahammechanical on 2013-08-02
Ubuntu 12.04 and later versions do not use GDM (Gnome Display Manager) They use LightDM instead. That is why that command does not work. Is ubuntu the only OS? Do you get a Grub menu? If Ubuntu is the only OS you will not see a Grub menu but it is there but hidden. Hold down the shift key as you boot.

When the Grub menu appears select Recovery Mode and at the menu select Resume. That may get you to a desktop on open source video drivers. Knowing the error message would have been useful. If you get a desktop even without Unity running you can right click the desktop and select Change Desktop Background that will open System Settings and from there you can open Additional Drivers and select a different video driver and reboot.

As you have been told Ctrl+Alt+F opens a command line prompt and Ctrl+Alt+T will open a terminal. Two useful commands

```
sudo shutdown -r now
```
```
sudo shutdown -h now
```

-r = reboot. -h = halt now = do it now.

```
sudo restart lightdm
```
```
sudo unity --reset
```

Unity reset should work on 12.04 but not on 12.10 onwards.  The commands for 12.10, 13.04 are

```
dconf reset -f /org/compiz/
```
```
setsid unity
```

It may be simpler to just re-install.

Regards.

---

### Post by SweetAurora on 2013-08-02
What graphics card do you have?

---

### Post by greatdane2 on 2013-08-02
> **grahammechanical said:**
> Ubuntu 12.04 and later versions do not use GDM (Gnome Display Manager) They use LightDM instead. That is why that command does not work. Is ubuntu the only OS? Do you get a Grub menu? If Ubuntu is the only OS you will not see a Grub menu but it is there but hidden. Hold down the shift key as you boot.

don't know what grub is, held down the shift key during boot and it didn't change a thing.
> 
When the Grub menu appears select Recovery Mode and at the menu select Resume. That may get you to a desktop on open source video drivers. Knowing the error message would have been useful. If you get a desktop even without Unity running you can right click the desktop and select Change Desktop Background that will open System Settings and from there you can open Additional Drivers and select a different video driver and reboot.

Can do that, additional drivers gives an empty window saying "no proprietary drivers are in use on this system."
> 
As you have been told Ctrl+Alt+F opens a command line prompt and Ctrl+Alt+T will open a terminal. Two useful commands

ctrl alt F doesn't work. 
> 
```
sudo restart lightdm
```

Didn't do anything
> 
```
sudo unity --reset
```

**Booooom**

It's all back!

Thanks for the help guys, really appreciate it. Tbh I'm still pretty worried how 1 wrong command can cause a problem I would never in a million years solve myself and that wasn't easy to find for a bunch of more experienced people on this forum... guess I'd better keep this in mind and don't get lazy on the backups...

Using Haswell onboard graphics btw

edit: and before I get too excited... it was all back, so I rebooted to try and see if it was fixed. Got the usual no taskbar desktop:mad: obv got back after using the command again but it seems like I'll ahve to do this now on every startup.

---

### Post by greatdane2 on 2013-08-02
Is there any easy way to reinstall the os without losing the programs installed? Would probably save me a less than an hour for this time, but might be handy for future reference.

edit: whatever, prob not worth the headache, reinstalling everything.

---

### Post by Vladlenin5000 on 2013-08-03
> **greatdane2 said:**
> Is there any easy way to reinstall the os without losing the programs installed? Would probably save me a less than an hour for this time, but might be handy for future reference.

edit: whatever, prob not worth the headache, reinstalling everything.


I was about to recommend that anyway. Good luck :)

---

### Post by 5l4y3r on 2013-08-04
Great that you've managed to solve the problem. I was about to suggest finding a way to execute automatically the command that solved the problem everytime you log into the system.

---

### Post by barnesal87 on 2013-09-19
This sounds like the same exact problem I'm having currently. I'm  running Ubuntu version 13.04. I wanted to switch from using the Intel graphics to the AMD HD8800M graphics card in my laptop. I followed this guide exactly [http://ubuntuxtreme.com/news/amd-catalyst-13-2-beta-3-driver-up-to-300-performance/](http://ubuntuxtreme.com/news/amd-catalyst-13-2-beta-3-driver-up-to-300-performance/) using the "Manual way" (cause its more fun). 

But when i restarted, no task bars. I can log in just fine, but cannot start programs. I can create folders on the desktop that allow me to navigate through my hard drive. Basically all i can do is browse files. Any help is greatly appreciated!

---

