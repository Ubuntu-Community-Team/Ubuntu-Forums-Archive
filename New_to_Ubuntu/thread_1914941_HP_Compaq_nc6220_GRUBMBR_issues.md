---
title: "HP Compaq nc6220 GRUB/MBR issues"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by Nick_Kats on 2012-01-25
[SIZE=2]Good Evening.
My father brought me an old laptop from his work, the HP Compaq nc6220. Due to security reasons, the old hard drive was removed by the company and I had to buy and install a new HD. I bought a Western Digital 250GB (WD2500BEVE) and installed it.
The laptop used to run with Windows XP Professional.
I managed to install Ubuntu 10.04, and everything went well for the first 2 or 3 boots.
But then, suddenly the laptop does not load Ubuntu and pops out a grub-rescue command prompt. I have tried to update the laptop's MBR and GRUB but nothing happens.
What is the solution? Can I make this laptop useable or no?

Thank you.[/SIZE]

---

### Post by oldfred on 2012-01-25
How did you update grub2's boot loader in the MBR?

Did you try this?
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration. May be better to run the git/beta version of boot script as it has some fixes.

Or this?
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

