---
title: "kinit: No resume image, doing normal boot."
date: 2008-11-26
forum: New to Ubuntu
---

### Post by SoonerLaw83 on 2008-11-26
I have checked on google for the answer to this and a lot of the responses have been to complicated for me to understand. That being said here is my problem. I picked up a Dell Poweredge 400SC  that someone had loaded XP on for cheap. I decided to load Ubuntu on it and it worked fine. I also added a linux compatible wireless card and it worked fine after that as well. I then copied all my music to the computer. The onboard graphics card was pretty crappy so after some researching on forums, several people suggested that NVIDIA video cards are compatible with Ubuntu. I ordered a NVIDIA GeForce FX 5500 / 256MB DDR / AGP 8x / DVI / VGA / TV-Out / Video Card and installed it. The driver CD that came with it did not run under Ubuntu, but Ubuntu recommended a certain driver (which I did not write down). I installed that driver and restarted the computer. When it restarted i got the kinit: No resume image, doing normal boot. message and it asked for my log in information in a DOS like environment. I removed the video card and tried to boot it up again, only now when it boots up it says the same thing, but after a few seconds my monitor reads "Out of range". I have tried it on a better monitor and it says something similar. 

I need someone to help me do one of 2 things:
1. Get it working again OR
2. Help me copy all of my music to an external hard drive so I can just start over again. I tried booting ubuntu from the CD only, but it does not allow me to copy my music files because I guess I set my privacy settings to a high level when I was running ubuntu off of the hard drive.

Any help is appreciated. Thanks

---

### Post by ibuclaw on 2008-11-26
kinit: No resume image is not an issue, and neither is doing normal boot :)

So what is the problem exactly?

Does Ubuntu boot properly? Does the XScreen (GUI) work with the NVIDIA card plugged in?

As for your monitor saying "Out of Range", this is because you have your Monitor settings set to a higher frequency/level than what your onboard graphics card can handle. This is because everything has been altered so it works for your NVIDIA card.

Best thing to do is to re-insert your NVIDIA card and boot again.

I see absolutely nothing wrong with your computer unless you give more information as to why you think your NVIDIA card isn't working properly.

For example, what else is being showed on screen?

Regards
Iain

---

### Post by SoonerLaw83 on 2008-11-26
Well before I installed the card, it entered into the ubuntu desktop automatically. Now it just stays in this DOS-like mode indefinitely. How do I get it back into the graphical desktop environment? If you need more info let me know

---

### Post by Skripka on 2008-11-26
Power down, put your card back where it was, login at the prompt then try:

```
sudo /etc/init.d/kdm start
```

---

### Post by jimreynold2nd on 2008-11-26
"kinit: No resume image, doing normal boot" is normal, it just means that you did not hibernate but did a regular shutdown.
You problem is with graphic card and/or driver.
Check those to make sure:
-GrUB boots the newest kernel that you have.
-You have installed the nvidia-glx package (the driver for your card). If not sure, do 'sudo apt-get install nvidia-glx' (from command line, make sure you have internet cable plugged in)
-You ran 'sudo nvidia-xconfig' after installing the package

---

### Post by SoonerLaw83 on 2008-11-26
Well I got it working, thanks to you all for your help. However, now the resolution of my monitor is extremely low and it will not let me increase it in my settings. Any ideas?

---

### Post by ibuclaw on 2008-11-26
Boot normally, and login to the terminal.

Then run:
```
sudo /etc/init.d/gdm start
```
If nothing happens, or error messages are being thrown, then reboot and select the "Recovery Mode" option in the GRUB bootloader.
```
sudo reboot
```

When Ubuntu boots and a Console Menu is shown, select the "**Fix X**" option, then continue with "**Normal Boot**"

Regards
Iain

---

### Post by SoonerLaw83 on 2008-11-26
Awesome, Thanks to you all.

---

