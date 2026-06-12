---
title: "No tty Ctrl + F1 thru F6 Black Screen/Desktop Distorted Ctrl + F7"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by HolyDonut on 2011-09-27
Ctrl + Alt + F1 (through F6) take me to a blank black screen.

When I hit Ctrl Alt F7 my desktop gets all distorted (see the screenshot).

Is it the NVIDIA proprietary driver just sucking? I'm on a laptop with an NVIDIA GeForce video card. ```
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
```

I'm using a fully updated Natty 11.04 Ubuntu. I'm in Ubuntu Classic (no Unity). I have Compiz installed.

I'm also using version 173 of the NVIDIA accelerated graphics driver (NOT the current version). I got the idea here: [http://ubuntuforums.org/showthread.php?p=10748878](http://ubuntuforums.org/showthread.php?p=10748878) because I was having an issue with my windows randomly turning white.

I may have messed with the xorg.conf settings, not directly but through the NVIDIA X Server Settings app in System > Administration. I did NOT click the "Save to X Configuration File" button though.

Someone suggested that my suspend/hibernate settings may be at fault here: [http://ubuntuforums.org/showthread.php?t=1849669&page=2](http://ubuntuforums.org/showthread.php?t=1849669&page=2). But suspend works perfectly and I haven't ever used hibernate yet.

---

### Post by SecretCode on 2011-09-27
No definite recommendations, but I would be tempted to try eliminating things. Does it make any difference if you boot in an Ubuntu (Safe Mode) session?

Most extreme: Do you have a partition that you could do a test installation of Natty on your hardware and see if the problem exists there? Then add the nvidia driver and test ... then add Compiz and test ...
I don't suggest you repartition your drive just for this. But when I install I make a point of having a spare OS partition mainly for testing the next version.

---

### Post by HolyDonut on 2011-09-27
Oh and I forgot to mention that I'm using Wubi. The drive is partitioned entirely for Windows Vista. 

By the way, not installing any nVidia drivers results in the shadow from the panels printing over and over on my screen like I'm looking at it through blinds. And the right 50 pixels of the screen wrap around to the left. So not installing the nVidia drivers really isn't an option.

---

### Post by SecretCode on 2011-09-27
Aha. 

It's a long time since I've used wubi. I can't think of a reason why wubi would interfere with access to the virtual terminals ... but it might.

---

### Post by HolyDonut on 2011-09-28
No luck in safe mode. I'm just going to have to be very careful not to attempt anything that might require the virtual terminals. 

Things I discovered through testing:

Recovery console works fine when I first boot up.
When the Xserver is unhappy with a change I made to xorg.conf and won't start I get tty1 through 6 with no problems. (I tried to attack my inability to have dual monitors and failed miserably)

So I think it is the nVidia driver, which I cannot uninstall because Ubuntu won't work without it. 

I'm going to stop worrying about it and hopefully someone will come up with an idea. 

Thanks for the suggestions SecretCode.

---

### Post by rvv on 2011-09-29
HolyDonut, do you have grub2 boot menu at startup ?
I've solved problem with empty black screen tty's by changing graphical mode for grub2 boot menu.
It must be the same you have in NVIDIA X Server Settings.

---

### Post by HolyDonut on 2011-09-30
Yes I do use the grub menu at startup. What did you change in grub? Did you edit the settings in a config file or is there a chance for me to alter grub at startup?

---

### Post by rvv on 2011-09-30
1. gksu gedit /etc/default/grub
2. Change the GRUB_GFXMODE value (don't forget to remove # at the beginning of line).
3. sudo update-grub
4. reboot

---

### Post by HolyDonut on 2011-09-30
Thanks for the suggestion rvv, but that didn't change anything for me. I saw no difference anywhere and ctrl alt F1 was still black and ctrl alt F7 still distorted my desktop.

I made sure to uncomment the line. The value I used was 1280x800 (which is my screen's resolution).

Although, I did notice a weird error when I update grub:

Generating grub.cfg ...
**cat: /boot/grub/video.lst: No such file or directory**
Found linux image: /boot/vmlinuz-2.6.38-11-generic
Found initrd image: /boot/initrd.img-2.6.38-11-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found Windows Vista (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
done

---

### Post by rvv on 2011-09-30
What screen's resolution do you have when grub boot menu started? Is it high or low?
The contents of ** /boot/grub/video.lst** on my system is:
```

vbe
vga
video_bochs
video_cirrus

```

---

### Post by HolyDonut on 2011-09-30
The grub boot menu looks like it starts out in high resolution. It's white on purple and it looks like its at 1280x800 resolution.

---

### Post by HolyDonut on 2011-09-30
I managed to figure out half of the problem, I have tty 1-6 now, but when I come back to the gui with ctrl alt F7 my desktop is still distorted. :confused: 

Thank you, rvv, for pointing me in the right direction! I followed "Alternative One" on this page: [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml).

Distorted Desktop: Double-clicking the panels makes them come back, but my desktop background is gone. Compiz still works perfectly. 

NEW(ish) PROBLEM: The "Unable to enumerate USB device on port __" error takes over the terminal on tty. 

I have been using this code to make the error go away.

```
cd /sys/bus/pci/drivers/ehci_hcd/
sudo sh -c 'echo -n "0000:00:02.1" > unbind'
```

I have to enter this every time I restart and adding this code to /etc/rc.local doesn't help. (The script runs and unbinds 0000:00:02.1, but the unable to enumerate message doesn't go away.) The unable to enumerate message only goes away if I unbind 0000:00:02.1 after the system boots up. 

By the way, I'm just blindly using this code, but it works and it hasn't caused any problems for me. What exactly am I doing when use it?

---

### Post by HolyDonut on 2011-10-01
Okay, I solved the unable to enumerate usb device on port __ problem. 

Now I still can't come back to the gui (ctrl alt F7) without distorting my desktop.

---

### Post by HolyDonut on 2011-10-01
I got it working.

I installed plymouth-manager and that fixed whatever was wrong.
 
[http://www.n00bsonubuntu.net/content/install-plymouth-manager-ubuntu-11-04-natty-narwhal/](http://www.n00bsonubuntu.net/content/install-plymouth-manager-ubuntu-11-04-natty-narwhal/)

I also updated my nVidia driver to the latest driver. The problem with the windows turning white doesn't seem to be as frequent now. And it goes away if the window is resized or the focus is changed to another window. 

Wow, Ubuntu requires a lot of tinkering to get it to work.

---

### Post by HolyDonut on 2011-10-02
[SIZE="3"]**[COLOR="Red"]BETTER FIX:[/COLOR]**[/SIZE]

Use nVidia 173 driver (not the current version)

I installed plymouth-manager and that fixed whatever was wrong. [http://www.n00bsonubuntu.net/content...natty-narwhal/](http://www.n00bsonubuntu.net/content...natty-narwhal/)

When CTRL + ALT + F7 distorts the desktop, open a terminal restart Nautilus. ```
nautilus -q
```

This repairs the distortion and everything is fixed!

---

### Post by merc669 on 2012-07-19
> **HolyDonut said:**
> I managed to figure out half of the problem, I have tty 1-6 now, but when I come back to the gui with ctrl alt F7 my desktop is still distorted. :confused: 



How did you fix the tty 1 thru 6. I still cannot figure that one out. I am on 12.04 after upgrading from 11.1. Still no tty 1 thru 6. I can get to 7 no problem. But tty 1thru 6 is just clack with no cursor, etc. Thanks!!

Bill...

---

