---
title: "Updated 11.04 Won't Boot"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by CompBio on 2012-04-28
I recently applied updates on my Ubuntu 11.04 machine.  Due to problems in the past I've gotten used to running boot-repair after every update to ensure my machine will reboot, but this time it didn't work.

Now when I try to reboot I get a "grub>" prompt.  I have no idea how to get back to Gnome.  I'm unable to work on that machine at this point.

If it helps, the boot-repair paste link was paste.ubuntu.com/952580

I've also tried booting from the Ubuntu 11.04 install CD and the 11.10 install CD, but I get a very, very, very dim screen so I can't see anything.  The screen is just fine with the grub menu.  This is on an Acer laptop.

Help!!

UPDATE: After searching the internet I finally found some information on how to boot from the Grub2 menu.  I think I'm able to reboot using the following commands:
> 
linux (hd0,msdos1)/vmlinuz
initrd (hd0,msdos1)/initrd.img
boot


It does appear to start but I can no longer adjust the screen brightness so it is 100% DARK.  I cannot see anything!  So even if the boot is working, I cannot see to edit any of the Grub menu options.  In effect, I am still dead in the water.

---

### Post by CompBio on 2012-04-28
Epiphany -- I plugged in a spare monitor into the VGA port and then I was able to see once the system booted.  I'm in the process of trying to fix a system that really seems to be messed up.  Right now my only boot option from the Grub menu is recovery mode, so I'll have to see what needs fixing.

Sigh...  at least we don't have to PAY for this stuff...

---

