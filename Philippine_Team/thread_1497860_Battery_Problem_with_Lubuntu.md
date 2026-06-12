---
title: "Battery Problem with Lubuntu"
date: 2010-05-31
forum: Philippine Team
---

### Post by sencen on 2010-05-31
I need help!

I have recently installed lubuntu and it's really fast with my pretty low spec laptop. I have one problem though. My battery is a little weak. It cannot be unplugged from the socket for around 15 to 20 minutes because the battery drains fast.

My problem is everytime that I unplug the charger, the system would immediately go suspended. Not even a minute would pass before it goes suspended. Hmm. I have tried playing with the battery preferences but same thing happens. Is there anyway I can just disable that part where the laptop suspends?

Hmm. It didn't happen with Xubuntu before but the distro is pretty bloated for my laptop. Same thing with dreamlinux. Didn't have this problem with these distros before.

---

### Post by nerdtron on 2010-05-31
Kung 10.04 ang gamit mo, try mo ung 9.10 baka gumana sya ng maayos dun.
Pasensya na sa advise ko...di ko nasagot ung tanong mo.

---

### Post by sencen on 2010-05-31
> **nerdtron said:**
> Kung 10.04 ang gamit mo, try mo ung 9.10 baka gumana sya ng maayos dun.
Pasensya na sa advise ko...di ko nasagot ung tanong mo.

lubuntu 9.10? sige try ko...

---

### Post by sencen on 2010-05-31
I went hopeless. Haha. I installed back xubuntu and added lxde instead. I wanted to remove xubuntu but I decided not to &#263;ause the updates from ubuntu would get removed as well.

I wanted to install Ubuntu base and add lxde but I always get stuck with network configuration.

Anyway, I am happy for now. Hopefully, with few more googling I´d be able to figure few more stuff. :)

---

### Post by loell on 2010-05-31
for easy network configuration, try  **nm-applet** in lxde.

---

### Post by _duncan_ on 2010-05-31
> **sencen said:**
> ... I wanted to remove xubuntu but I decided not to &#263;ause the updates from ubuntu would get removed as well...


The .deb packages from the ubuntu repos are stored locally in the folder /var/cache/apt/archives unless you cleared out your cache. You can stow away these .deb packages somewhere where it won't be touched by a new installation.

If for some reason you decide to go back, you just have to copy back these .deb packages to the original folder (/var/cahce/apt/archives), update the package list, and go through the motion of updating the system.

You will notice that instead of downloading from the ubuntu repos, the package manager will "see" these existing .deb packages and use them instead. Same thing with additional apps installed through ubuntu's package managers.

This is also helpful if you are installing the same version to other computers. Saves a lot of downloading.

---

### Post by sencen on 2010-06-01
> **_duncan_ said:**
> The .deb packages from the ubuntu repos are stored locally in the folder /var/cache/apt/archives unless you cleared out your cache. You can stow away these .deb packages somewhere where it won't be touched by a new installation.

If for some reason you decide to go back, you just have to copy back these .deb packages to the original folder (/var/cahce/apt/archives), update the package list, and go through the motion of updating the system.

You will notice that instead of downloading from the ubuntu repos, the package manager will "see" these existing .deb packages and use them instead. Same thing with additional apps installed through ubuntu's package managers.

This is also helpful if you are installing the same version to other computers. Saves a lot of downloading.

nice! i dont know that! thanks for this. :P

---

### Post by sencen on 2010-06-01
> **loell said:**
> for easy network configuration, try  **nm-applet** in lxde.

yup! did that. :) my problem with that was i had to run it manually since it wont show up automatically on the system tray but was able to resolve it... well, accidentally that is. i just checked the box beside **network manager** from the **desktop session settings** and restarted. it automatically connects onto wireless connection now everytime i turn on my laptop. :)

---

