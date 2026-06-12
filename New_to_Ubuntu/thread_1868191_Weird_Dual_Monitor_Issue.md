---
title: "Weird Dual Monitor Issue"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by decrow06 on 2011-10-23
Hello,

I recently upgraded to 11.10 64-bit. I am having a lot of trouble with dual-monitors. It seems like a lot of other people have similar issues. I managed to get them to work by deleting my xorg.conf. However, I have one other issue. When I press Ctrl+Alt+Backspace, only my external monitor works. My laptop monitor just stays black. 

I am on a Dell XPS 15 with a nvidia graphics card.

---

### Post by LowSky on 2011-10-26
sudo nvidia-settings

set up everything from there, then save to xorg.conf

---

### Post by dave0109 on 2011-10-26
You don't really say what the problem is though. :)

A lot of systems are struggling with the extra graphics work required by Compiz and Unity and fail to drive 2 monitors at the same time.  On my system, I had to drop back to the Classic desktop with no effects - but obviously that's not an option in 11.10.  Though, once I got it running in "no effects", the monitors.xml file was set up correctly, and I could run Classic with effects if I wanted to.

Now I'm running Xubuntu on my main laptop and it can drive the external monitor no probs.

---

### Post by Drowz0r on 2011-10-26
Hey man, it'd be good to know what kind of graphics card you're running. ATI, Nvidia, some other thing...

Maybe this will help you:

[http://ubuntuforums.org/showthread.php?t=1867948&highlight=Dual+monitors](http://ubuntuforums.org/showthread.php?t=1867948&highlight=Dual+monitors)

---

