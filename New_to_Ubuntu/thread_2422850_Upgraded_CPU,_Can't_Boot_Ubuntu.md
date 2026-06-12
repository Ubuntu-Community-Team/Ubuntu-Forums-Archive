---
title: "Upgraded CPU, Can't Boot Ubuntu"
date: 2019-07-13
forum: New to Ubuntu
---

### Post by megaboz2 on 2019-07-13
Hi, all,

With the 3000 series Ryzen chips out, I picked up a heavily discounted 2600X to replace my original 2400G on my Lin/Win box.  I got the new CPU installed, but seem to be unable to boot into Ubuntu from the internal SSD (or even from a thumbdrive).  I get the GRUB menu, select Ubuntu, and then... nothing.  Just a blank screen.  The drive activity light occasionally flickers, but I can't even get to the login screen.

I was, however, able to boot into Win10.  The first attempt was flaky -- I logged in and got to the desktop, but the display glitched out and then I got a VIDEO_TDR_FAILURE BSOD.  After rebooting, the system seems to be stable and I can use Win10, at least.  Given this, the CPU seems to working fine, but not being able to use Ubuntu is obviously tragic.

I'm definitely on the n00b end of the scale Linux-wise, so any advice would be terribly helpful.  Here's my specs:

Ryzen 5 2600X
Sapphire Nitro+ Radeon RX580 8GB
G.Skill 16GB 2933Mhz RAM
Ubuntu 19.04


Thanks,
MB

---

### Post by CatKiller on 2019-07-13
Were you using that graphics card prior to your cpu switch? Your description sounds exactly like it's sitting at the login screen waiting for you to log in, but the display manager isn't using that gpu, or potentially that monitor, for some reason.

---

### Post by Autodave on 2019-07-13
You may have to go into the BIOS and tell it not to use the internal graphics card.

---

### Post by megaboz2 on 2019-07-13
@CatKiller, Yes, I was using the 580 for the display prior to upgrading to the 2600X.  I'm using a AOC G2460V monitor with Freesync, FWIW.  Considering the 2600X lacks an iGPU, I don't know what else it could be looking for. 

@Autodave, Related to the above, the 2600X doesn't have an iGPU, unlike the 2400G.  If I disable to 580 in BIOS, nothing is going to reach the display (unless I'm mistaken), right?


--MB

---

### Post by CatKiller on 2019-07-13
There are some things that might be helpful for diagnostics. Getting a display between the Grub menu and the login window (it's normally a splash screen) would be good to see. Being able to switch to a TTY (Ctrl-Alt-F2) will be easier than doing everything from a live environment.

There are two main threads that I can think of that would cause your issue, one software, one hardware.

The BIOS sets up the display initially, then Plymouth takes over to do the splash screen (and boot up messages) and then the display manager draws the login widow and launches your X or Wayland session when you log in. It *could* be that your display manager is using the wrong display or resolution or similar. Heck, you might still be able to log in blind in that scenario and have everything work, depending on where the issue is.

The other thread is the hardware one. Either your card isn't getting enough power if your new cpu draws more than the old one, or you forgot to reconnect the power when you did the hardware swap, or it's not quite been seated properly, or something along those lines. You're getting an image, but getting it to initialise at full power is another task again.

---

### Post by kurt18947 on 2019-07-13
No expert on these problems, or even knowledgeable but that has never deterred me before:tongue:. If megaboz2 can get to GRUB, might booting temporarily with nomodeset be helpful? Or could the open source Nvidia driver be unhappy?

---

### Post by TheFu on 2019-07-13
Have you tried using a different tty?   <cntl><alt>-F1 will switch to the first tty.  In Ubuntu, F7 is the graphical TTY.

If you just swapped the CPU and didn't pre-setup the GPU correctly, the pre-existing install could be freakin' out.

---

### Post by megaboz2 on 2019-07-13
> **kurt18947 said:**
>  If megaboz2 can get to GRUB, might booting temporarily with nomodeset be helpful? Or could the open source Nvidia driver be unhappy?

Heh, well, I'm an AMD guy, but adding [FONT=courier new]nomodeset[/FONT] to the boot loader did the trick. I'm at least able to get into the desktop now, so yay!  Thanks, Kurt, you get a gold star for the day :D!  However, I guess using this workaround means I'm stuck using the basic VESA drivers instead, because there's no 3D acceleration, and it doesn't look like the open source AMD drivers got loaded at all.  Lutris is saying it can't find my Vulkan drivers to run Warcraft or Guild Wars -- grrrr.

@CatKiller and TheFu: I don't seem to be able to call up a TTY using either method.  Also, I tried just typing in my password after waiting several minutes at a blank screen, and was still unable to get to the desktop.  I'm almost certain this isn't a hardware problem, given that in Windows I was able to play Witcher 3 and Lone Echo (a processor-intensive VR game)  without any signs of overheating.  Whatever's at fault must be either in the BIOS settings or my system settings.  Are there specific BIOS settings I should be looking for to solve a situation like this?


--MB

---

### Post by megaboz2 on 2019-07-15
So, as it turns out, my little problem was due to an out-of-date kernel.  I had updated to 5.0.0-20 a while back and thought it was current enough for the 2600X.  Turns out, nope, it wasn't.  I updated to the latest stable release that built successfully for amd64 (v5.1.16) using this article as a guide:
[https://www.fosslinux.com/7167/how-to-upgrade-linux-kernel-in-ubuntu-and-linux-mint.htm](https://www.fosslinux.com/7167/how-to-upgrade-linux-kernel-in-ubuntu-and-linux-mint.htm)

On reboot, it worked!  Note to self: keep kernel updated when upgrading hardware...


--MB

---

