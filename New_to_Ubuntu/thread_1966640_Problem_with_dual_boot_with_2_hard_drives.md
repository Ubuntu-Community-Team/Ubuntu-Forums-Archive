---
title: "Problem with dual boot with 2 hard drives"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by Covalent Bond on 2012-04-27
I had 11.04 installed on a 2nd hard drive with Windows 7 on first hard drive; worked well.  New install with 12.04 but when restarted get this error message:  "Error-no such device (bunch of numbers) <grub rescue>.  Do not know what to do next.  2nd question; when installing 12.04 I chose the option to erase 11.04 and install 12.04.  Should I have used the third option. something else, and if so, what.  Please make any answer simple as I am not all that technically proficient.

CB

---

### Post by oldfred on 2012-04-28
With two drives and two systems is is not so simple. You may have been booting from sdb, but the auto installs default to install to sda. 

Try booting from the other drive with BIOS or one time boot key (f12 on my system).

Manual install or Something else is the only way you get the combo box on which drive to install grub2's boot loader. But you have to tell it which partition to use as / (root) and what format, and /home (DO NOT format it) if you have it. It finds swap automatically then.

If that does not work post link to Boot info script.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

Grub also remembers where to reinstall it boot loader on major updates so you will want to fix that if it did install to sda, as it will reinstall there again.

---

