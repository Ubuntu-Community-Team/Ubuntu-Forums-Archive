---
title: "load freeze in loading hardware drivers"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by pjina3 on 2008-04-27
When I boot with livecd of Ubuntu 8.4 Hardy Heron on my laptop Compaq presario R3000, the loading freeze in "loading hardware drivers".

The 2 last lines are :

- b43legacy-phy0: Broadcom 4301 WLAN found
- Clocksource tsc unstable (delta = 4687308187 ns)

and nothing else...

See the attached file.
[screen's picture]("http://launchpadlibrarian.net/13575193/DSCF0001.JPG")

Ubuntu 7.10 work perfectly on my laptop.
And now I have installed Hardy with alternate-cd, it's done without errors
but when I boot, It occur the same problem

I try to add "acpi=off noapic nolapic" in boot options but it's not solve this problem

---

### Post by pjina3 on 2008-04-27
up
nobody can help me? :(

---

### Post by maniacmusician on 2008-04-27
This bug was reported in launchpad, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190414](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190414)

5th comment down provided this fix:
> I'm seeing a similar problem on a NEC Versa P550, but it actually turns out to be the TSC clock source that's causing the trouble in my case.

Right after that "Clocksource tsc unstable" message in your dmesg output, you'll notice the kernel detects the problem and switches to another clock source:
"Time: hpet clocksource has been installed."

You can tell it to use the HPET clocksource from the start by adding "clocksource=hpet" to your kernel command line. The kernel command line is specified in /boot/grub/menu.lst at the line starting with "# kopt=...".

See if that fixes your problem. :)


So you can try that. Make sure you back up your menu.lst file first. Then, following the instructions in that comment, put in the clocksource option in the correct line, save, and it should fix it.

---

### Post by pjina3 on 2008-04-28
First of all, Thanks for help me :)
I try to add "clocksource=hpet" in boot option but it not solve the problem.
But I don't try to change /boot/grub/menu.lst because I can't boot to the system (I don't know another way to change it)
May be, I must wait for the new kernel (2.6.25)?

---

### Post by maniacmusician on 2008-04-28
> **pjina3 said:**
> First of all, Thanks for help me :)
I try to add "clocksource=hpet" in boot option but it not solve the problem.
But I don't try to change /boot/grub/menu.lst because I can't boot to the system (I don't know another way to change it)
May be, I must wait for the new kernel (2.6.25)?
perhaps you put it in the wrong line? Not really sure, I've never encountered this issue, but I hope you fix it.

If you have a LiveCD lying around, you could always boot that up, mount your hard drive, make the necessary changes as root, and do it that way.

---

### Post by pjina3 on 2008-04-29
I add the option in the line where begin by kernel and with out "quiet splash" option(in grub menu)
I will try it with the LiveCD

---

### Post by pjina3 on 2008-04-30
I try to add option "noapic nolapic" too but it not solve the problem (both liveCD and grub menu).
But this bug was reported here, [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192720](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192720)
I'm waiting for Ubuntu Kernel Team's solution :)

---

### Post by pjina3 on 2008-05-08
I have solved the problem by edit /etc/modprobe.d/blacklist; blacklist bcm43xx and b43 legacy, as follows:

# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43legacy

I can't boot the system to edit it but I use a knoppix's liveCD to boot and then remount the hda1 (in mode rw) then edit /media/hda1/etc/modprobe.d/blacklist

the solution can solve the problem but I can't use the b43legacy driver, it isn't problem for me because I use a D-Link usb wifi which use rt73 driver

---

### Post by tatrefthekiller on 2008-06-27
Thanks ! Works for me !

---

