---
title: "Acer Monitor"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by Calerid on 2011-10-29
Hello,

I have an Acer AL715 that I am using. Ubuntu cannot detect the monitor type. It displays though it has some artifacting. I was wondering if anyone new how to install the driver I would need for this monitor. It does not display in the Proprietary drivers.

11.10 with Unity does not seem to be affected. so I will mark this as solved.

---

### Post by antoinethewiz on 2011-10-29
Ubuntu includes most of the drivers your computer needs (and they're all open source). The fact that you're screen is at least displaying something seems to indicate that it's using some kind of driver (even if generic). If not, you'll find them under the Restricted Drivers Manager. System > Administration > Hardware Drivers. Click "enable driver" to install it. (For Xubuntu, this is under Settings > Additional Drivers). Next, if you're positive that you don't have the appropriate driver, then go to the manufacturer's website and download the Ubuntu driver there. If it's not there, then you'll have to wait for the next release of Ubuntu.

Also, the monitor may be a bit defunct if it's showing consistent artifacts.

---

### Post by papibe on 2011-10-29
Just to be a little more precise, proprietary drivers are for graphic cards, not for monitors.

What graphic card do you have? The easiest way is to post the result of this command:
```
lspci | grep -i vga
```
It may be some relevant information on your X log. Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Copy the content here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post the link.

Regards.

---

### Post by Calerid on 2011-10-29
Nvidia 5200FX, I have the monitor somewhat configured in the Nvidia X.org server setup. Though I don't have the ability to change the refresh rate as I should be able to choose 75 and it only allows for 51.1? 

[http://paste.ubuntu.com/722845/](http://paste.ubuntu.com/722845/)

> **papibe said:**
> Just to be a little more precise, proprietary drivers are for graphic cards, not for monitors.

What graphic card do you have? The easiest way is to post the result of this command:
```
lspci | grep -i vga
```It may be some relevant information on your X log. Could you post the content of this file?
```
/var/log/Xorg.0.log
```Copy the content here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/), and then post the link.

Regards.

---

### Post by Bucky Ball on 2011-10-29
Not monitor problem, graphics driver issue, as is being delved into ...

---

### Post by Calerid on 2011-10-29
> **Bucky Ball said:**
> Not monitor problem, graphics driver issue, as is being delved into ...

Yeah, I could see a bit of that. I would still like to have the Computer itself and not just the card recognize the monitor. I have tried changing the driver for the 5200 before and nothing seems to work as well the default Ubuntu driver fails with it. The card worked fine in windows so I do believe it is a driver related issue.

---

### Post by antoinethewiz on 2011-10-30
If absolutely nothing works as recommended by the guru's here... then try inserting your graphics card on another computer running the same system. This will help you determine if you have a defunct PCI slot (on the motherboard) or a bad chipset driver. If the graphics card isn't working on any system, then the graphics card may be bad. Again, only do this after doing everything the guru's tell you to (it's a last resort kind of thing).

Let's just wait and see what papibe has to say.

---

### Post by Calerid on 2011-10-30
> **antoinethewiz said:**
> If absolutely nothing works as recommended by the guru's here... then try inserting your graphics card on another computer running the same system. This will help you determine if you have a defunct PCI slot (on the motherboard) or a bad chipset driver. If the graphics card isn't working on any system, then the graphics card may be bad. Again, only do this after doing everything the guru's tell you to (it's a last resort kind of thing).

Let's just wait and see what papibe has to say.

As I said it has worked recently on another OS within this same machine. Same AGP slot and all. I believe it must be a driver issue within Ubuntu and the device itself.

---

### Post by papibe on 2011-10-30
This is you log:
```
[    41.572] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
```
I don't have any straight forward suggestion, but this is the things I would try, if I were in your situation. After each idea, restart your machine and see if you have better results. Please take note of the shortcuts described in this [thread]("http://ubuntuforums.org/showthread.php?t=1743535&highlight=black"), so in case you boot into a black screen, you can get into text mode.

[LIST=1]
[*]First I would check the BIOS to check for any parameter that increase the memory assigned to the graphic card. If you find it, increase it to 256MB or even 512MB.
[*]You are using the 173 Nvidia version. When you installed, did you have any other option? It looks like nvidia-current supports your card. Try testing if that driver version gives you better results.
[*]At this point if any of the nvidia drivers give you better rendering. I would unistall them, and try the default driver (nouveau).
[/LIST]
I hope one of these ideas help you. Tell us how it goes.
Regards.

---

### Post by Calerid on 2011-10-30
I have already done all these things. The memory allocation is only 256 max. I have tried the experimental 3d, it did not work any better really. The default Ubuntu driver is about the same as 173 release.
> **papibe said:**
> This is you log:
```
[    41.572] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
```I don't have any straight forward suggestion, but this is the things I would try, if I were in your situation. After each idea, restart your machine and see if you have better results. Please take note of the shortcuts described in this [thread]("http://ubuntuforums.org/showthread.php?t=1743535&highlight=black"), so in case you boot into a black screen, you can get into text mode.

[LIST=1]
[*]First I would check the BIOS to check for any parameter that increase the memory assigned to the graphic card. If you find it, increase it to 256MB or even 512MB.
[*]You are using the 173 Nvidia version. When you installed, did you have any other option? It looks like nvidia-current supports your card. Try testing if that driver version gives you better results.
[*]At this point if any of the nvidia drivers give you better rendering. I would unistall them, and try the default driver (nouveau).
[/LIST]
I hope one of these ideas help you. Tell us how it goes.
Regards.

---

