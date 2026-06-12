---
title: "Tried everything, just cannot install Ubuntu"
date: 2016-01-13
forum: New to Ubuntu
---

### Post by Gavin_Walker on 2016-01-13
Hello,

Newbie here.

I'm trying to install Ubuntu on my Wintel CX-W8 mini PC.
It's currently dual booting Windows 10 & Android 4.4 (I want to install Ubuntu as my main OS removing those)

Every time I go to recovery to install Ubuntu from my USB the system just reboots, like I've just restarted / turned on my PC, I get no screen to install, nothing, I just get taken back to my log in screen.

I've tried turning off fastboot, setting my USB stick as primary boot option, I even purchased a new USB stick as I'd heard this can cause problems. I have an EFI partition but I've noticed I do not have an EFI shell, when I press enter on this it states nothing found, I don't know if this would affect it?

Can anyone please help me, I've been trying for days to no avail, any help would be very much appreciated.

---

### Post by buzzingrobot on 2016-01-13
> **Gavin_Walker said:**
> 
Every time I go to recovery...

Not sure what you're referring to?  Does that mean Windows recovery mode?

Can you outline how you made the USB?

If the machine has a DVD drive, you can burn an Ubuntu install ISO to a DVD using Windows.  I believe a right click on the file name will display the option. I've seen success with a DVD when a USB was being recalcitrant.

The machine needs to be actually shut down, not left in the pseudo-hibernation mode Windows uses for fast booting. (It looks like you've taken care of that.) A BIOS can usually be interrupted as the system boots with a specific keysttoke that displays the drives the BIOS has detected.  If you choose one, it will attempt to boot from it. (This is not the keystoke you use to enter the BIOS.)

---

### Post by Gavin_Walker on 2016-01-14
Hi,

Thanks for your reply.
I think the problem I'm having is with my BIOS.
I set to boot from my USB first but my system reboots back in to Windows, not acknowloging the USB at all, so I do not even get in to the Ubuntu set up screen.

I've no idea what is going on!

I've tried a CD that doesn't work either.

---

### Post by Shaun_Dixon on 2016-01-14
When you say the CD is not working as well, is the PC just ignoring the CD and booting Windows?  

Like Buzzingrobot was saying you should have a keystroke which interrupts the booting process when the computer is first switched on (on my computer it is F8).  it then asks what do you want to boot from and you can choose USB/CD etc.  Is that the process you are following?  Or are you going into the BIOS and adjust the boot order in there?

---

### Post by Autodave on 2016-01-14
Are you making the USB and DVD an ISO file?  It must be in the ISO format for the computer to recognize that it is a bootable medium.

---

