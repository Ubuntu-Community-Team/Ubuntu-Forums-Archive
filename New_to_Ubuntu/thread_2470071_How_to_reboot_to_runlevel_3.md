---
title: "How to reboot to runlevel 3?"
date: 2021-12-19
forum: New to Ubuntu
---

### Post by pczekalski on 2021-12-19
I'm helplessly trying to reboot my Ubuntu 20.04 LTS to runlevel 3 to install/check nVidia drivers for the eGPU.
Following guide on nVidia pages, it is necessary step.
The problem is when I add "3" to the GRUB_CMDLINE_LINUX_DEFAULT, update grub and reboot, machine hangs after checking cleanines of the filesystem - that is the only message showing up. Yet, I can issue shutdown by pressing physical power button. But there is no shell, no boot messages, nothing.
Any help is appreciated. I made it to reboot back to the normal runlevel removing "3" from the GRUB_CMDLINE_LINUX_DEFAULT during boot and it works like a charm again. Still I can't reboot to runlevel 3.

Boot mode: UEFI, Secure Boot disabled in BIOS.

```

GRUB_DEFAULT="Advanced options for Ubuntu>Ubuntu, with Linux 5.8.0-49-generic"
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT="5"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT=" quiet splash noresume "
GRUB_CMDLINE_LINUX=""

```

modification to boot to runlevel 3:
```

GRUB_DEFAULT="Advanced options for Ubuntu>Ubuntu, with Linux 5.8.0-49-generic"
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT="5"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT=" quiet splash noresume 3 "
GRUB_CMDLINE_LINUX=""

```

So my question is: what should I do, to sucessfully reboot to the runlevel 3 with shell working?

---

### Post by Bashing-om on 2021-12-19
pczekalski - Hey hey

[s]One makes the edit to the grub boot line from the boot menu re-direction as the system boots up.[/s]
see: [http://www.linuxandubuntu.com/home/how-to-boot-into-linux-command-line](http://www.linuxandubuntu.com/home/how-to-boot-into-linux-command-line) 

superseded indeed by systemD
See instead the following posts.
 
[INDENT]my bit to try and help
[/INDENT]

---

### Post by TheFu on 2021-12-19
Run levels don't exist anymore since systemd.  There is a multi-user target instead and other targets for other needs.  I'd use '**locate**' to find the systemd targets on a system.

If you like, systemd does have runlevel0-6 targets ... at least on one of my machines. These are part of the core snap package on some systems. If snap have been removed, it is a little cleaner:
```

$ ls -l   /usr/lib/systemd/system/runlevel*
lrwxrwxrwx 1 root root   15 Sep  7 14:37 /usr/lib/systemd/system/runlevel0.target -> poweroff.target
lrwxrwxrwx 1 root root   13 Sep  7 14:37 /usr/lib/systemd/system/runlevel1.target -> rescue.target
lrwxrwxrwx 1 root root   17 Sep  7 14:37 /usr/lib/systemd/system/runlevel2.target -> multi-user.target
lrwxrwxrwx 1 root root   17 Sep  7 14:37 /usr/lib/systemd/system/runlevel3.target -> multi-user.target
lrwxrwxrwx 1 root root   17 Sep  7 14:37 /usr/lib/systemd/system/runlevel4.target -> multi-user.target
lrwxrwxrwx 1 root root   16 Sep  7 14:37 /usr/lib/systemd/system/runlevel5.target -> graphical.target
lrwxrwxrwx 1 root root   13 Sep  7 14:37 /usr/lib/systemd/system/runlevel6.target -> reboot.target

```
Notice how the old runlevels are just symbolic links to "approved" systemd targets?
I don't think the **telinit** program will still work, however.  Probably should use **systemctl list-units** to get the actual name for the target you'd like, then use **systemctl start {target}** to get there.  An example is:
```
$ sudo systemctl start poweroff.target
```

Hope that helps.  What each target does is documented in the manpages for systemctl.

---

### Post by ActionParsnip on 2021-12-20
[https://www.tecmint.com/change-runlevels-targets-in-systemd/](https://www.tecmint.com/change-runlevels-targets-in-systemd/)
Explains it well

---

### Post by pczekalski on 2021-12-20
Thanks - clean and clear, but I just wonder, when was the systemd method introduced?
Nvidia guys provide the following instruction as suitable for Ubuntu 18.04 and 20.04 LTS:
[https://developer.nvidia.com/blog/accelerating-machine-learning-on-a-linux-laptop-with-an-external-gpu/](https://developer.nvidia.com/blog/accelerating-machine-learning-on-a-linux-laptop-with-an-external-gpu/)
with the other (old) way to edit GRUB.

Was it a change that was introduced between 18.04 LTS and 20.04 LTS?

Best regards,

P.

---

### Post by yetimon_64 on 2021-12-20
> Was it a change that was introduced between 18.04 LTS and 20.04 LTS?
Systemd has been in the Ubuntu repos since April 2013 and included in the default install since April 2015. It became the default and only option for Ubuntu installs since "Yaketty" (16.10) [[COLOR=#0000ff]--Source-- [/COLOR]]("https://en.wikipedia.org/wiki/Systemd"){scroll down to section 3 "Adoption", Ubuntu is the second last entry on the table of Linux distros.}

---

### Post by TheFu on 2021-12-20
Sometime after 16.04 systemd was forced onto us.  16.04 installs got it without proactive action or request for confirmation.

---

### Post by maketopsite on 2021-12-20
```
# init 3
``` ?

---

