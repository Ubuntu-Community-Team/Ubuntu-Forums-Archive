---
title: "Upgrade from 12.04 to 12.10 doesn't work?"
date: 2013-08-19
forum: New to Ubuntu
---

### Post by rom3lol on 2013-08-19
I'm running dual OS with Windows 7. I upgraded from 12.04 to 12.10, but when I restarted, and booted to Ubuntu it does not show a log-in screen. It either stays in a purple or black screen. When I'm in the Grub2 boot screen I press 'e' and change 'quiet splash' to 'nomodeset', but the only thing I'm able to do is CTRL+SHIFT+F1 or any  other function key. I can log-in into my account this way, but I never get the GUI log-in screen.

I also used a live cd to mount my partition and change all the entries in /boot/grub/grub.cfg from 'quiet splash' to 'nomodeset', but it didn't work either so I restored the original file.

My Laptop is a Toshiba Satellite R845-S85
Thanks in advanced.

---

### Post by oldfred on 2013-08-19
Do you just have the Intel Video? The Intel driver is only the open source one and is supposed to work.

But some have had to add other settings. Try these instead of nomodeset.

 i915.i915_enable_rc6=1

Others:

 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

---

### Post by rom3lol on 2013-08-20
How do I know if I have the Intel video? My laptop has an Intel core. 
I'm confused; I don't know if I'm supposed to enter **i915.i915_enable_rc6=1** in /boot/grub/grub.cfg and replace  every entry of 'quiet splash' with it, or add it next to it?
And or entering it here /etc/default/grub and adding it next to 'quiet splash' or replace it with i915.i915_enable_rc6=1. 

At boot I press 'e' and replace 'quite splash' with i915.i915_enable_rc6=1, but still no change. 

I used Lubuntu 13.04 as live cd to mount and try and update the grub file with the info you gave me with the info stated above, but no avail.

---

### Post by deadflowr on 2013-08-20
> [COLOR=#000000]How do I know if I have the Intel video?[/COLOR]

You type this in the ctrl + alt + F1 screen
```
lspci | grep VGA
```
and it'll say the card
A more robust output
```
sudo lshw -C display
```
will give more information including driver and capabilities.

---

### Post by oldfred on 2013-08-20
Also best to test boot parameters with entry in grub menu (the e and edit). 
Then when you find the combination of parameters that work you can make them permanent in /etc/default/grub.

---

### Post by crazymonkey05 on 2013-08-20
if you can get to the screen that you log in at the code to start the GUI is ```
startx
``` type that in after you log in and a gui will load

---

