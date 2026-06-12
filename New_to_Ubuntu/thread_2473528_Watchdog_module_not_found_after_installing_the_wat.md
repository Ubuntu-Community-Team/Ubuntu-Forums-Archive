---
title: "Watchdog module not found after installing the watchdog package in Ubuntu"
date: 2022-04-06
forum: New to Ubuntu
---

### Post by jasmine22 on 2022-04-06
Hello,
I am new to ubuntu.
Currently I would like to use watchdog package for python script to run in Ubuntu 16.04.1.
So I install watchdog package using the following comment:
[COLOR=#232629][FONT=ui-monospace]sudo apt-get install watchdog
[/FONT][/COLOR]Then, I received this message:
Reading package lists... Done
Building dependency tree
Reading state information... Done
watchdog [COLOR=var(--highlight-keyword)][FONT=inherit]is[/FONT][/COLOR] already the newest version ([COLOR=var(--highlight-namespace)][FONT=inherit]5.14[/FONT][/COLOR]-3ubuntu0[COLOR=var(--highlight-namespace)][FONT=inherit].16[/FONT][/COLOR][COLOR=var(--highlight-namespace)][FONT=inherit].04[/FONT][/COLOR][COLOR=var(--highlight-namespace)][FONT=inherit].1[/FONT][/COLOR]).
[COLOR=var(--highlight-namespace)][FONT=inherit]0[/FONT][/COLOR] upgraded, [COLOR=var(--highlight-namespace)][FONT=inherit]0[/FONT][/COLOR] newly installed, [COLOR=var(--highlight-namespace)][FONT=inherit]0[/FONT][/COLOR] to remove [COLOR=var(--highlight-keyword)][FONT=inherit]and[/FONT][/COLOR] [COLOR=var(--highlight-namespace)][FONT=inherit]485[/FONT][/COLOR] [COLOR=var(--highlight-keyword)][FONT=inherit]not[/FONT][/COLOR] upgraded.
Then I reboot the ubuntu.
When I check is the package installed successfully by using the following comment: 
[COLOR=#232629][FONT=ui-monospace]apt list --installed[/FONT][/COLOR]
However, I don't find watchdog package is installed. 

Before installing the watchdog, I also upgrade the packages by using the following comment:
[COLOR=#232629][FONT=ui-monospace]sudo apt-get update[/FONT][/COLOR]
However, I got this messages:

[INDENT]Fetched 6,704 kB in 58s (114 kB/s)[/INDENT]
[INDENT]Reading package lists... Done[/INDENT]
[INDENT]E: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/main/dep11/icons-64x64.tar](http://security.ubuntu.com/ubuntu/dists/xenial-security/main/dep11/icons-64x64.tar)  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-security_main_dep11_icons-64x64.tar.gz - open (13: Permission denied)[/INDENT]
[INDENT]E: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/xenial-updates/main/dep11/icons-64x64.tar](http://sg.archive.ubuntu.com/ubuntu/dists/xenial-updates/main/dep11/icons-64x64.tar)  Could not open file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_dep11_icons-64x64.tar.gz - open (13: Permission denied)[/INDENT]
[INDENT]E: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/xenial-backports/main/dep11/icons-64x64.tar](http://sg.archive.ubuntu.com/ubuntu/dists/xenial-backports/main/dep11/icons-64x64.tar)  Could not open file /var/lib/apt/lists/partial/sg.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_dep11_icons-64x64.tar.gz - open (13: Permission denied)[/INDENT]
[INDENT]E: Some index files failed to download. They have been ignored, or old ones used instead.[/INDENT]


May I know how can I install watchdog package in ubuntu ?
Thank you

---

### Post by QIII on 2022-04-06
Hello!

16.04 has passed its end of standard support.  It is currently only supported if you are paying for extended support.  If you are not, then it would be best to install a currently supported release.  Using a release that is out of support is dangerous because you are no longer getting security updates.

---

### Post by jasmine22 on 2022-04-07
May I know how can I install a currently supported release?

---

### Post by him610 on 2022-04-07
With LTS 20.04.4:
```

sudo apt install watchdog

```
> Description: system health checker and software/hardware watchdog handler
 The watchdog program writes to /dev/watchdog every ten seconds. If
 the device is opened but not written to within a minute, the machine
 will reboot. This feature is available when the kernel is built with
 "software watchdog" support (standard in Debian kernels) or if the
 machine is equipped with a hardware watchdog (in which case this
 package can also be used to "pet" it, resetting its timer).
 .
 The kernel software watchdog's ability to reboot will depend on the
 state of the machine and interrupts.
 .
 The watchdog tool itself runs several health checks and acts
 appropriately if the system is not in good shape.


---

