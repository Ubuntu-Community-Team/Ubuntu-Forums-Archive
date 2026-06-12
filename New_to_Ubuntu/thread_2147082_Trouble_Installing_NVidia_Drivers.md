---
title: "Trouble Installing NVidia Drivers"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by TortoiseDream on 2013-05-20
I recently bought a Lenovo U410 laptop which comes with an NVIDIA GeForce 610M graphics card, and no less than an hour ago I installed Ubuntu 13.04. I don't think I am currently using the graphics card, and I think I need to in order to play a few games (for example). I'm using gnome by the way instead of unity.

If I go to Software & Updates > Additional Drivers, it says no propriety drivers are in use, and there is nothing listed there at all. I'm able to download the driver file from the NVIDIA website directly, but (being a noob) I have no idea what to do with it.

Can someone help me? Thanks in advance!

---

### Post by The Cog on 2013-05-20
I would suggest you stick with drivers from the repositories. There are several versions to choose from and I'm not that familiar with differences between them. However, I suggest you choose one of these commands:
```

sudo apt-get install nvidia-304
sudo apt-get install nvidia-304-updates
sudo apt-get install nvidia-310
sudo apt-get install nvidia-310-updates
sudo apt-get install nvidia-313-updates

```
My nvidia pc is using 313-updates. Seems to work fine for me.

---

### Post by TortoiseDream on 2013-05-20
> **The Cog said:**
> I would suggest you stick with drivers from the repositories. There are several versions to choose from and I'm not that familiar with differences between them. However, I suggest you choose one of these commands:

Thank you for replying so quickly. I installed 313-updates. How can I be sure things are working as they are supposed to? For example, if I go to the NVIDIA X Server Settings menu, I get this message

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

Although I don't know what that means, am I right to suspect something isn't quite right?

Thanks again.

---

### Post by The Cog on 2013-05-20
Hmm. Have you rebooted since installing it?

You can see what driver is in use by using the command
```
lspci -v
```
and looking for the nvidia card info.

---

### Post by TortoiseDream on 2013-05-20
> **The Cog said:**
> Hmm. Have you rebooted since installing it?

You can see what driver is in use by using the command
```
lspci -v
```
and looking for the nvidia card info.

I found someone with a similar problem: [http://ubuntuforums.org/showthread.php?t=1966987](http://ubuntuforums.org/showthread.php?t=1966987)

But eventually I think my problem becomes too machine specific. I ran sudo nvidia-xconfig after backing up that file, and like the poster there I now have a 640x480 resolution.

The result of the code you had me run (after getting to the 640x480 resolution) was "Kernel driver in use: nvidia"

No idea what's going on here...

---

### Post by The Cog on 2013-05-20
Can you run nvidia-settings-manager and see what that says?

---

### Post by TortoiseDream on 2013-05-20
I get the same message: "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

---

### Post by The Cog on 2013-05-20
I don't understand that. I might be tempted to uninstall that driver again for now.
```
sudo apt-get purge nvidia-313-updates
``` 
Maybe try older drivers, such as nvidia-304. 
This command lists the packages available:
```
apt-cache search nvidia-[0-9]
```

Or see if anyone who understands more about nvidia can answer. I've not had the problems you're seeing.

---

### Post by TortoiseDream on 2013-05-20
Okay so I did a bit more research. Here is what one guy said here: [http://askubuntu.com/questions/207368/cannot-make-nvidia-driver-work-with-ubuntu-12-10](http://askubuntu.com/questions/207368/cannot-make-nvidia-driver-work-with-ubuntu-12-10)

"[COLOR=#333333][FONT=Ubuntu Beta]I had the same problem with my Lenovo G780... Could not understand why the nvidia-drivers weren't working.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]THEN... I discovered the notebook relies on **Optimus** technology. *Hybrid graphics* where the nvidia chip is "piggybacked" onto the intel graphics. Useful for saving a lot of power, the nvidia only comes into play when using graphics intensive programs.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]This is a great feature... when you are running Windows. Linux has yet to catch up but there are open source measures being taken.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]The project is called [Bumblebee.]("http://ubuntuportal.com/2012/01/bumblebee-3-0-tumblewed-nvidia-optimus-gpu-switching-for-linux-has-been-released-how-to-install-bumblebee-3-0-on-ubuntu.html") It works for me so far.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I wish I had known this before. I'm not sure if this applies to your scenario but from what I've read, the technology is used greatly by Sandy/Ivy bridge chipsets."[/FONT][/COLOR]

---

