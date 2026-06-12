---
title: "wifi hardware switch???"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-15
I am at my HP Pavilion zd8000 laptop running XP and using a Gsky USB wireless adapter with an excellent signal of 54.0 Mbps.

If I boot into 11.10 I can see the Gsky LED flashing but no joy.

The error message is Hardware switch not enabled.

I did not install drivers when using the USB 11.10, however it was LAN connected to the router.

Suggestions please.

---

### Post by theknightlinux on 2012-04-15
Can you connect to the internet using the LAN you mentioned and run an update?

---

### Post by samuraiCat on 2012-04-21
Hi! I was fighting with this problem all day last Sunday on my Lenovo z570. I tried literally every solution, but nothing permanently fixed it until I tried the following:

1. Unplug from your ethernet cable, if you're connected directly to your router.
2. Plug the power adapter into your computer and boot up (if you aren't already). You don't need to log into a session.
3. With your computer entirely booted up, close the lid. You can allow it to suspend.
4. Take out the battery with the computer still plugged in.
5. Unplug the power supply, then quickly open the lid and press (and hold!) the power button. Don't release it for at least 30 seconds. 
6. Release the power button after 30 or more seconds.
7. Replace the battery.
8. Open the lid and plug back into the power adapter.
9. Press the power button on your laptop, and as soon as you get the option to go into BIOS (usually by pressing F2), do so.
10. In BIOS, select the "restore all defaults" option. Save and exit.

The laptop will finish booting, and your wireless should be available.

---

### Post by cortman on 2012-04-21
> **samuraiCat said:**
> Hi! I was fighting with this problem all day last Sunday on my Lenovo z570. I tried literally every solution, but nothing permanently fixed it until I tried the following:

1. Unplug from your ethernet cable, if you're connected directly to your router.
2. Plug the power adapter into your computer and boot up (if you aren't already). You don't need to log into a session.
3. With your computer entirely booted up, close the lid. You can allow it to suspend.
4. Take out the battery with the computer still plugged in.
5. Unplug the power supply, then quickly open the lid and press (and hold!) the power button. Don't release it for at least 30 seconds. 
6. Release the power button after 30 or more seconds.
7. Replace the battery.
8. Open the lid and plug back into the power adapter.
9. Press the power button on your laptop, and as soon as you get the option to go into BIOS (usually by pressing F2), do so.
10. In BIOS, select the "restore all defaults" option. Save and exit.

The laptop will finish booting, and your wireless should be available.

OP, before you try this, please open a terminal and run

```
sudo rfkill unblock all
```

and see if that gets it working. It  could just be a soft block. If it's much more, we may need to get wildmanne39 in on it.

---

### Post by samuraiCat on 2012-04-21
> **cortman said:**
> OP, before you try this, please open a terminal and run

```
sudo rfkill unblock all
```

and see if that gets it working. It  could just be a soft block. If it's much more, we may need to get wildmanne39 in on it.

Cortman, do you think I should delete my response? It was the only thing that worked for me. I suggested this because it's a hardware switch problem.

---

### Post by CharlesA on 2012-04-21
> **samuraiCat said:**
> Cortman, do you think I should delete my response? It was the only thing that worked for me. I suggested this because it's a hardware switch problem.
It's fine imo. That's just how HP resets their laptops, looks like Lenovo does too.

---

### Post by cortman on 2012-04-21
> **samuraiCat said:**
> Cortman, do you think I should delete my response? It was the only thing that worked for me. I suggested this because it's a hardware switch problem.

It seems a little odd, but if it worked for you it may work for OP. False wifi hardblocks can be difficult\impossible to overcome.
It's fine there, and thanks for the input!

---

### Post by samuraiCat on 2012-04-21
> **cortman said:**
> It seems a little odd, but if it worked for you it may work for OP. False wifi hardblocks can be difficult\impossible to overcome.
It's fine there, and thanks for the input!

Yeah, it took me all day to find that solution. Apparently it happens to all sorts of laptops.

I actually had to do it a second time after I ran all the updates after my upgrade to 12.04 Beta 2. I think it's an Ubuntu bug.

---

### Post by Boyntonstu on 2012-04-21
> **theknightlinux said:**
> Can you connect to the internet using the LAN you mentioned and run an update?

Solution found:

Installed the Hardy drivers.

[http://ubuntuforums.org/showthread.php?t=1960962&highlight=boyntonstu](http://ubuntuforums.org/showthread.php?t=1960962&highlight=boyntonstu)

---

### Post by Zill on 2012-04-22
> **Boyntonstu said:**
> Solution found:

Installed the Hardy drivers.

[http://ubuntuforums.org/showthread.php?t=1960962&highlight=boyntonstu](http://ubuntuforums.org/showthread.php?t=1960962&highlight=boyntonstu)
Just for clarification, AIUI, you did not actually "install the Hardy drivers".  "Hardy" refers to the [Ubuntu 8.04]("https://wiki.ubuntu.com/Releases") release of April 2008, code named "Hardy Heron".

As has already been explained in other posts, Linux OS's are continually updated to include many hardware drivers as standard.  Your research simply indicated that the driver for your device was first included in Ubuntu 8.04 (Hardy Heron).  Most, if not all, drivers then remain in future Linux kernels and so will be available automatically in later releases, such as the 11.10 (Oneiric Ocelot) you are currently using.

HTH.

---

