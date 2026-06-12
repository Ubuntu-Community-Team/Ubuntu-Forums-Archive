---
title: "Black Screen No Login Ubuntu 20.4 and XWayland"
date: 2022-03-12
forum: New to Ubuntu
---

### Post by bhubunt on 2022-03-12
Hi All,
After removing XWayland from Ubuntu 20.04, I could no longer login, but only got a black screen. 

I switched to terminal, logged in that way and then followed all the steps on this link, but nothing worked: [https://support.system76.com/articles/login-loop-ubuntu/](https://support.system76.com/articles/login-loop-ubuntu/)

As you will have seen, that link is for Ubuntu 18. 

I do not have X11 as this is Ubuntu 20.04. But I also could not reinstall the login manager as it said it could not find ubuntu-desktop.

My questions to you:
1/ Could someone send me the link to a step-by-step guide for reinstalling the login screen for Ubuntu 20.04?
I'm afraid I am a newbie still, so everything needs to be spelled out with full commands at this stage. 

I do not have internet on this computer so pls no solutions/suggestions that require connecting to the internet.

2/Is there any way in which I could copy some screenshots and a doc off my laptop, through the terminal, without needing to go through the graphic login screen? 

Many thanks, as always, for your help.

---

### Post by grahammechanical on 2022-03-12
That link to system76 support has some good suggestions which did not help you because your problem was not caused by any of the things that the support page was designed to help with.

I have Ubuntu 20.04 and at the login screen and I can choose to login with Ubuntu on Wayland or Ubuntu (which would be Ubuntu on X-server). When Ubuntu 22.04 is released we will be able to login to Ubuntu on X-server or Ubuntu (which would be Ubuntu on Wayland). So, we can see that with Ubuntu 20.04 the X-server is the default login and with Ubuntu 22.04 Wayland becomes the default login.

I am guessing that by removing X-wayland you also removed ubuntu desktop. It is a matter of interconnected dependencies. In that system76 support page there is a heading called Reinstall the login manager. Those commands may be the answer to your problem. But you cannot install packages without downloading from the internet. If that machine can be connected to the internet you can try this:

1) At the Grub menu select Advanced Options for Ubuntu. Then select a Linux kernel with recovery mode.
2) At the recovery menu select Network to establish a network connection using information that Ubuntu already holds.
3) Select Root shell prompt and run those commands.

Regards

---

### Post by bhubunt on 2022-03-12
> **grahammechanical said:**
> If that machine can be connected to the internet you can try this:


Regards

Hi,
Thanks for the reply. No, I cannot connect the laptop to the internet, so that's not an option.

Is there no other way to restore the login page? Before I removed the packages that came with XWayland, I looked very carefully at the list of dependencies and it only included vpn, broadband and a few other things that did not look of consequence and that I don't use anyways. Ubuntu desktop was definitely not listed, otherwise I would not have entered the remove command. Would ubuntu desktop simply be removed without a warning? That seems strange to me. As I said, I carefully looked at the list of what would be removed. 

Perhaps some old files are preventing a proper reboot? 

Also, do you or anyone else know if I can get some pics and docs off the computer in its present state, even if I cannot properly log in?

Thanks for the feed-back.

---

### Post by tea for one on 2022-03-12
> **bhubunt said:**
> I cannot connect the laptop to the internet
It is impossible to know the exact state of your system therefore any suggestion (without downloading packages from the repositories) would be guesswork.
> **bhubunt said:**
> Also, do you or anyone else know if I can get some pics and docs off the computer in its present state, even if I cannot properly log in?
Yes, boot up a live session and copy the the required items to another USB device.
After you have saved what you need, continue the live session by re-installing.

Up and running within a short time.

---

### Post by bhubunt on 2022-03-13
> **tea for one said:**
> 

Yes, boot up a live session and copy the the required items to another USB device.
After you have saved what you need, continue the live session by re-installing.

Up and running within a short time.

Hi,

Thanks for the explanation.

Just to make sure that I fully understand the instructions: 

so, once I have started up the laptop and gotten the black screen, I basically stick the ubuntu usb stick with the installation software in the laptop? 

Or, do I first need to log in via the terminal and hit a specific F key to open system boot settings? (Which F key)

I'm afraid this is not clear to me. 

Also, am I right in assuming then that, once I see the USB stick with the installation software, instead of hitting install, I hit "try ubuntu." This then gives me the ubuntu screen with all the icons, including the files icon. I then click the files icon, see my files and can copy what I need to an USB stick. After I have done that, I can reinstall ubuntu.

Did I get that right?

Thanks for letting me know.

---

### Post by tea for one on 2022-03-13
In order to boot into a live session, the PC has to be [COLOR="#0000FF"]powered off[/COLOR]/[COLOR="#0000FF"]shut down[/COLOR].

Insert your Ubuntu USB installation USB stick.
Power on the PC and repeatedly tap the dedicated key to access the one-time boot menu.
(e.g. F10 for Intel, F9 for HP, F12 for Lenovo etc)
Select your USB stick and boot into a live session (preferably in UEFI mode indicated by UEFI:name-of-device)
Then Try Ubuntu
Use the file manager to save your personal data to another USB device.

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by bhubunt on 2022-03-13
> **tea for one said:**
> In order to boot into a live session, the PC has to be [COLOR=#0000FF]powered off[/COLOR]/[COLOR=#0000FF]shut down[/COLOR].

Insert your Ubuntu USB installation USB stick.
Power on the PC and repeatedly tap the dedicated key to access the one-time boot menu.
(e.g. F10 for Intel, F9 for HP, F12 for Lenovo etc)
Select your USB stick and boot into a live session (preferably in UEFI mode indicated by UEFI:name-of-device)
Then Try Ubuntu
Use the file manager to save your personal data to another USB device.

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Thanks very much. That's helpful.

After I reinstall, can I remove XWayland or will that cause the same problem, i e black screen, no login? 

On the login screen, lower-hand right side, one has the option to log in using Wayland or not, so I assumed that meant that Wayland was not a vital aspect of the OS. 

Can someone explain?

---

### Post by #&amp;thj^% on 2022-03-13
> **bhubunt said:**
> Thanks very much. That's helpful.

After I reinstall, can I remove XWayland or will that cause the same problem, i e black screen, no login? 

On the login screen, lower-hand right side, one has the option to log in using Wayland or not, so I assumed that meant that Wayland was not a vital aspect of the OS. 

Can someone explain?
Ubuntu by default uses Gnome Shell for its desktop environment. That is designed to run on Wayland, and can also run on Xorg.
Wayland is another display session meant to replace X11 in a near future. 
I wouldn't mess with removing it, that be quite technical.  
Wayland packages are installed as hard dependencies.
If you want to disable it, and would make more sense use:
```
sudoedit /etc/gdm3/custom.conf
```
look for "WaylandEnable=false" and remove the leading "#"
Then restart GDM with:
```
sudo systemctl restart gdm3
```
Wayland display server this option would not be available at all. (At Login)

---

