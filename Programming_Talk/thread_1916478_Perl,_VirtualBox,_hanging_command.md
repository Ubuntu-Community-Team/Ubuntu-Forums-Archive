---
title: "Perl, VirtualBox, hanging command"
date: 2012-01-28
forum: Programming Talk
---

### Post by sprouty on 2012-01-28
Hi,

I have a short perl Script that controls some of the VMs I use in Virtual box. Every know and again when the perl script tell VirtualBox to power on or off the VM's, and sometimes the command will freeze at 50/60%.

I'm wondering if there is a way to execute the command from perl, and if it as to wait longer that 40 Seconds to kill that command off.

The command that I am currently using to start and power the vm off is: `/usr/lib/virtualbox/VBoxManage startvm $Virtual_Machine`;

Any Help would be excellent.

Many Thanks,
Paul.

---

