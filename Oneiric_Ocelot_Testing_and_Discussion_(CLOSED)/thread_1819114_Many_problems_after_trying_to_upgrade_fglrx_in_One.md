---
title: "Many problems after trying to upgrade fglrx in Oneiric"
date: 2011-08-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2011-08-05
Please refer to this thread, posts 41-52, where my problems started, then got worse:

[http://ubuntuforums.org/showthread.php?t=1773851&page=5](http://ubuntuforums.org/showthread.php?t=1773851&page=5)

I am starting this new thread because it has become off-topic to that thread.

From the beginning - I tried to follow the instructions in that thread to upgrade to Catalyst 11.7 because I could not run Unity (3D) in my Oneiric testing installation. In my case, the instructions failed.

Then, I discovered that I could no longer boot to Oneiric. I would get a black screen with a fairly large X as the mouse pointer. At that time, I could Ctrl-Alt-F1 and get a text console. So I rebooted to my main Natty installation to ask for advice on fixing my ATI driver in Oneiric. I was given some advice and attempted to go back to the Oneiric command line to try it.

This time, I got to the X mouse pointer, but it no longer responded to moving the mouse. Also, Ctrl-Alt-F1 no longer had any effect. It seemed that both the mouse and the keyboard were dead.

So I tried to go back to Natty for more advice. Natty booted to a somewhat similar situation. It took me to the GUI logon screen, but it would not respond to typing and the mouse cursor would not move the pointer.

More details in the other thread....

I finally reinstalled Oneiric, hoping that would resolve some of the problems, but it didn't and now I have at least one more problem. Neither Natty nor Oneiric mounts my external USB drive, which is where I have some of the code I need to finish installing Oneiric (a special wireless card driver that I need to install to get internet access).

What a mess!

1) It is now difficult to log on to either Natty or Oneiric. If I wait long enough (about 70 seconds), both the keyboard and the mouse start working again and I can log on.

2) Neither Natty nor Oneiric detect and mount my external USB drive. Both of them automounted it until this fiasco.

I never touched Natty. I just tried to upgrade the fglrx driver in Oneiric. But, somehow, both installations became messed up. I need serious help.

Thanks,
Tim

---

### Post by ratcheer on 2011-08-05
On problem #2, Ubuntu is not detecting anything on /dev/sdb. I cannot even mount the external drive, manually.

I tried unplugging it from the USB port and replugging it. Nothing happened.

Tim

---

### Post by ratcheer on 2011-08-05
A clue to both problems: I powered down the PC, unplugged the external drive, and rebooted to Natty. This time, I could log in to the desktop as soon as the login dialog came up.

So, something about the USB device is hanging the system for about 70 seconds at startup. As soon as the system stops dealing with it, things start running normally (except no USB drive).

Tim

---

### Post by ratcheer on 2011-08-05
Ok, I seem to have solved both problems by powering down the PC, disconnecting the USB drive from its power source, reconnecting the power to the USB drive, and rebooting the PC. The PC can be logged into immediately and the USB drive is detected and works properly.

Why installing fglrx 11.7 in Oeniric initiated all this mess is a mystery. Or maybe just a stupid coincidence.

Tim

---

