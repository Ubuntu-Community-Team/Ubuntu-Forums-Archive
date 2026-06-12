---
title: "ati graphics card installation"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by eamo on 2008-05-25
hi 

just looking help or advice with a graphics problem.

i have been using ubuntu for a few weeks now and i have a dual boot setup with two hard disk drives.

i started with ubuntu 7.10 and i have installed the latest release "hardy heron".

i am currently reading a book about linux and learning more about it.

i recently installed an ati sapphire hd 3850 graphics card (AGP).
i had some problems with the installation in windows, it disabled my agp bus.  When i installed the latest drivers and updated the bios the card eventually worked for me.  i have agp fast write enabled in the bios but the ati catlyst software still says this feature is disabled, not to sure why!

when i booted up ubuntu i had no problems to start with, but when i enabled the ati driver the card would not function with x.

i have tried using the linux driver installer supplied buy ati, the installation works but when i restart the system i still encounter the same problem.

i have looked at some threads and some people have similar problems.

i would be grateful if somebody with more technical knowledge could give me adivce and a possible fix for this problem.

i can provide all hardware and system information etc... as requested

any help would be gratefully appreciated

thanks ;-)

---

### Post by iaculallad on 2008-05-25
For the Linux driver part, your first stop could be on the [Envy site]("http://www.albertomilone.com/nvidia_scripts1.html"). It that couldn't help, post your /etc/X11/xorg.conf (**cat /etc/X11/xorg.conf**) file.

---

