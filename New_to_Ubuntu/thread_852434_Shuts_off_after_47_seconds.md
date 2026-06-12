---
title: "Shuts off after 47 seconds?"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Falcon_14 on 2008-07-07
I am having a really strange problem with a fresh install of 8.04 on a Toshiba Satellite M35X-S309 laptop. It has been running Win XP SP2 for years with no problems. I had been wanting to try out Ubuntu on this laptop for a while, and tonight I finally got around to installing Ubuntu, which I did from the 8.04.1 disk.

It installs normally, and I boot it up the first time. everything seems normal, except for the text for my username and password is way too big - one dot in the password entry box takes up the entire width of the box.

Once I logged in everything seemed fine, so I looked away for a few seconds, and that is when I heard the hard drive spinning down. I looked back and the laptop was completely shut down. It was exactly as if I had held down the power button for a few seconds to force it to shut off.

I tried to restart it a few more times, and no matter what I did it would shut off without warning. I eventually started timing how long it would take it to shut off, and it seems to do so 47 seconds after the cursor appears for the first time. It also seems to be that I get an extra 10 seconds before it shuts off if I plug in the power adapter.

I have felt the airflow coming out of the exhaust, and it does not seem to be any warmer than it was under XP and neither does the laptop itself.

I installed a few other versions of Ubuntu and these are the results:

Xubuntu 8.04           - Same problem
Ubuntu  7.10           - Same problem
Ubuntu  7.10 alternate - Same problem
Ubuntu  7.04           - **Works Perfectly**

So what could have changed after 7.04 to make the computer shut off like this?

---

### Post by phidia on 2008-07-07
47 seconds isn't very long but then with AC you have 10 more seconds. Get to the System>Preferences>Power Management applet and check your settings there.
I had something similar happen on my laptop but it didn't power down-just killed the screen. Anyway hope that helps and if that doesn't work use (boot into) the livecd to look at your /var/log/dmesg (syslog, messages, and user.log).

---

### Post by pytheas22 on 2008-07-07
Your system log will probably provide a clue.  You can view it with the utility at System>Administration>System Log.  Please post it here and hopefully something will stand out related to the crashes.

---

### Post by Falcon_14 on 2008-07-07
Ok, I am dual-booting 7.04 and 8.04 now, so I was able to get dmesg, syslog, messages, and user.log from the 8.04 partition. I put all 4 into one zip archive. If there are any other logs that would help, just tell me which ones.

I was also able to have a look at the power management menu in 8.04 before it shut off, and nothing seemed to be amiss there. 

It is definitely shutting off though, and not turning off the screen because the power light on the laptop that turns green when on and amber when hibernating turns completely off when it happens.

---

### Post by AnarkistNZ on 2008-07-07
It appears the system is being restarted as opposed to crashing, although as to why I'm unsure.

> 
Jul  7 16:06:24 Toshiba-Ubuntu gconfd (drake-5251): Exiting
Jul  7 16:06:24 Toshiba-Ubuntu gdm[4755]: Restarting computer...
Jul  7 16:06:26 Toshiba-Ubuntu init: tty4 main process (4137) killed by TERM signal
Jul  7 16:06:26 Toshiba-Ubuntu init: tty5 main process (4138) killed by TERM signal
Jul  7 16:06:26 Toshiba-Ubuntu init: tty2 main process (4142) killed by TERM signal
Jul  7 16:06:26 Toshiba-Ubuntu init: tty3 main process (4143) killed by TERM signal
Jul  7 16:06:26 Toshiba-Ubuntu init: tty1 main process (4144) killed by TERM signal
Jul  7 16:06:26 Toshiba-Ubuntu init: tty6 main process (4145) killed by TERM signal
Jul  7 16:06:32 Toshiba-Ubuntu exiting on signal 15
Jul  7 16:07:22 Toshiba-Ubuntu syslogd 1.4.1#20ubuntu4: restart.


---

### Post by Falcon_14 on 2008-07-07
Well that is really strange, especially since it acts completely normal up until it shuts off, and when it does it is instantaneous. And it doesn't restart either, I have to press the power button to power it back up.

---

### Post by forger on 2008-07-07
So this was a fresh install of ubuntu on a separate hard drive or on a drive that is windows on?
The live cd of ubuntu 8.04.1 is working properly? What was wrong when you were running the older 8.04 (not 8.04.1) live cd?

Have you tried checking the disk? find out your device:
```
sudo fdisk -l
```
..and check it in a live cd, for example:
```
sudo e2fsck /dev/sda1
```


Or you could try with kubuntu 8.04, maybe with kde you'll be more lucky

---

### Post by AnarkistNZ on 2008-07-07
Upon looker closer it seems although 'exiting on signal 15" is quite a common problem, however I can't find any fixes for it (I didn't look that closely however)

[http://ubuntuforums.org/search.php?searchid=44235936](http://ubuntuforums.org/search.php?searchid=44235936)
&
[http://www.google.co.nz/search?q=exiting+on+signal+15](http://www.google.co.nz/search?q=exiting+on+signal+15)

---

### Post by Falcon_14 on 2008-07-07
> **forger said:**
> So this was a fresh install of ubuntu on a separate hard drive or on a drive that is windows on?
The live cd of ubuntu 8.04.1 is working properly? What was wrong when you were running the older 8.04 (not 8.04.1) live cd?

Have you tried checking the disk? find out your device:
```
sudo fdisk -l
```
..and check it in a live cd, for example:
```
sudo e2fsck /dev/sda1
```


Or you could try with kubuntu 8.04, maybe with kde you'll be more lucky

I never tried the 8.04 live cd, simply because the 8.04.1 cd would require less updates after install. But the 8.04.1 cd works flawlessly. And this was on a fresh format of hard disk that did have XP on it, but now I have 3 partitions, one for 7.04, one for 8.04.1, and the swap partition.

I shall try checking the disk now, though.

---

### Post by forger on 2008-07-07
I just noticed:
> Ubuntu 2.6.20-17.36-generic

That's an older kernel... Either try a terminal if you can from gnome or try press "Esc" key while grub is booting and choose the recovery mode/console.

Hoping your internet works in the console terminal:
1) login
2) try these commands:
```
sudo apt-get update
sudo apt-get upgrade
```

a) If your internet is working, it should download some updates, such as linux-generic, linux-image-2.6.24-19-generic, linux-image-generic etc.

b) If you don't see such packages, execute this (**EXACTLY** as it is written):
```
sudo echo "deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted" >> /etc/apt/sources.list
```
...then:
```
sudo apt-get update
sudo apt-get upgrade
```
...and this time it should work!

Reboot your pc to see what happens now:
```
sudo reboot
```

---

### Post by kansasnoob on 2008-07-07
My best guess, and it is a guess, is that it's due to overheating.

At this point in time I've had better luck with Linux Mint on laptops, but I'll bet Intrepid kicks butt!

---

### Post by Falcon_14 on 2008-07-07
I think somehow I posted the incorrect logs. Maybe these are the correct ones?

---

### Post by pytheas22 on 2008-07-07
The only thing that stands out to me from the logs is the line:
```

Marking TSC unstable due to: cpufreq changes.
```

I'm not sure what it means, but I'm just guessing that it has to do with your CPU doing something weird.  Are you overclocking?  Either way, you may want to see if adjusting the frequency in BIOS makes any difference.

---

### Post by forger on 2008-07-07
At what time did this weird restart happen? Around 17:30 yesterday(July 7th)? Are they random freezes?

Try booting with the pci=noacpi option in your grub boot:
[https://answers.edge.launchpad.net/ubuntu/+question/24737](https://answers.edge.launchpad.net/ubuntu/+question/24737)


These logs were interesting:

dmesg.log:> 
[    7.526145] Security Framework initialized
[    7.526201] SELinux:  Disabled at boot.
[    7.526267] AppArmor: AppArmor initialized
[    7.526320] Failure registering capabilities with primary security module.

messages:> 
Jul  7 17:28:42 Toshiba kernel: [  114.758783] [drm] Initialized drm 1.1.0 20060810
Jul  7 17:28:42 Toshiba kernel: [  114.766691] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul  7 17:28:42 Toshiba kernel: [  114.766865] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jul  7 17:28:42 Toshiba kernel: [  114.767001] [drm] Initialized i915 1.6.0 20060119 on minor 1

syslog:> 
Jul  7 17:28:42 Toshiba kernel: [  114.758783] [drm] Initialized drm 1.1.0 20060810
Jul  7 17:28:42 Toshiba kernel: [  114.766691] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Jul  7 17:28:42 Toshiba kernel: [  114.766727] PCI: Setting latency timer of device 0000:00:02.0 to 64
Jul  7 17:28:42 Toshiba kernel: [  114.766865] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jul  7 17:28:42 Toshiba kernel: [  114.766885] PCI: Setting latency timer of device 0000:00:02.1 to 64
Jul  7 17:28:42 Toshiba kernel: [  114.767001] [drm] Initialized i915 1.6.0 20060119 on minor 1
Jul  7 17:28:42 Toshiba NetworkManager: <debug> [1215466122.814523] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3582_drm_i915_card0'). 
Jul  7 17:28:42 Toshiba NetworkManager: <debug> [1215466122.831013] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3582_0_drm_i915_card1'). 

---

### Post by Falcon_14 on 2008-07-07
> **pytheas22 said:**
> The only thing that stands out to me from the logs is the line:
```

Marking TSC unstable due to: cpufreq changes.
```

I'm not sure what it means, but I'm just guessing that it has to do with your CPU doing something weird.  Are you overclocking?  Either way, you may want to see if adjusting the frequency in BIOS makes any difference.

I'm on a Toshiba M35X-S309 laptop, and about the most advanced thing you can do in this bios is change the boot order. 

But this laptop does have Intel Centrino technology, I dunno if that has something like the speedstep technology that is in the Core 2 duos and quads, where it automatically underclocks.

Right now I am seemingly running 8.04, it hasn't crashed yet, and it has been a few minutes. So I copied and pasted all of the log files from the System Log Files viewer to text documents, to be sure they were the correct ones. Here they are:

[Authlog]("http://dcbrook.googlepages.com/authlog")
[Daemon]("http://dcbrook.googlepages.com/daemon")
[Debug]("http://dcbrook.googlepages.com/Debug")
[Kernlog]("http://dcbrook.googlepages.com/Kernlog")
[Messages]("http://dcbrook.googlepages.com/Messages")
[Syslog]("http://dcbrook.googlepages.com/Syslog")
[Userlog]("http://dcbrook.googlepages.com/Userlog")
[Xorg0]("http://dcbrook.googlepages.com/Xorg0")

I think I will wait a while to reboot - I was able to get it to work without shutting down once before, but once I restarted to see if it was a fluke it started shutting down on its own again.

Edit: That sounds about right for the shutoffs, and I dunno if you can really call them random since I timed it and every time it shut off it would be right around 47 or 57 secs if plugged in after the cursor appeared.

---

### Post by Arthur Archnix on 2008-07-07
Boot into single user mode. Just let it run for a while. Does it shut down? If so we can rule out 'x' and just focus on the kernel. Stuff like noapic or nolapic. If it doesn't then 'X' is our next 'person of interest'.

Try updating from single user mode. Then reconfigure your xserver. If both those fail to help try going back into single user mode. Delete everything in /var/log. Create a new user. Reboot normally and log in with new user. Write down about the time it failed. Then zip up everything under /var/log and post it back here.

---

### Post by phidia on 2008-07-07
> **Falcon_14 said:**
> I think somehow I posted the incorrect logs. Maybe these are the correct ones?

I did not find anything in those logs unfortunately.
Does this shutdown still happen if you login in failsafe mode or into CLI (commandline)?

---

### Post by Arthur Archnix on 2008-07-07
There's some bad stuff in the xorg logs about a bad driver and extensions. If reconfiguring 'x' doesn't work getting the output of lspci and some details about his monitor would be a logical next step. Configure xorg.conf manually.

---

### Post by forger on 2008-07-07
again that signal 15
> Jul  7 19:41:39 Toshiba exiting on signal 15

Looks like a hardware problem...start a terminal window and do: ```
sudo lshw > ~/Desktop/lshw.txt
```

Then attach the file lshw.txt (on your Desktop) here.

You could also file a bug report about these random restarts, and attach this file lshw.txt there too! The link to file bugs is [http://www.launchpad.net/ubuntu/](http://www.launchpad.net/ubuntu/)

---

### Post by Falcon_14 on 2008-07-08
> **forger said:**
> again that signal 15


Looks like a hardware problem...start a terminal window and do: ```
sudo lshw > ~/Desktop/lshw.txt
```

Then attach the file lshw.txt (on your Desktop) here.

You could also file a bug report about these random restarts, and attach this file lshw.txt there too! The link to file bugs is [http://www.launchpad.net/ubuntu/](http://www.launchpad.net/ubuntu/)

Ok, I did that; the .txt file is attached. 

Also, I found something that I think is VERY interesting. While in 8.04's root shell prompt; I found out that if I unplug the laptop's power cable and reinsert it, that upon reinserting the power cable the laptop would shut off instantaneously just like I have described.

I also tried it when I booted normally into 8.04 to get the lshw.txt file, and the same thing happened, upon plugging in the power cable, the laptop would instantaneously power off.

I then tried starting 8.04 up with the power cable off, then plugging in the power cable once it was booted. Same thing- instantly powers off.

I tried unplugging the power cable and plugging it back in under 7.04 booted normally and 7.04's root shell prompt, and the computer acted normally - no sudden shut offs.

---

### Post by Arthur Archnix on 2008-07-08
Go here, [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Try the various options. Let us know which ones eliminate that behaviour and someone will let you know the best one to use.

Also, update your bios if possible.

---

### Post by forger on 2008-07-08
> **forger said:**
> At what time did this weird restart happen? Around 17:30 yesterday(July 7th)? Are they random freezes?

Try booting with the pci=noacpi option in your grub boot:
[https://answers.edge.launchpad.net/ubuntu/+question/24737](https://answers.edge.launchpad.net/ubuntu/+question/24737)


Already suggested that with noacpi

---

### Post by iSKUNK! on 2009-11-12
> **Arthur Archnix said:**
> Also, update your bios if possible.

This is probably what's going on. See [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/242400"), addressing the same issue on a Toshiba M35X-S149.

---

