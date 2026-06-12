---
title: "lost network monitor at panel ."
date: 2011-09-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by raja.genupula on 2011-09-28
Hi
I dont know what happen , but this is not the first time that this is happening to me & i dont know how its recovered .

Frequently that network applet in my xubuntu top panel , i am losting it .I have losted recently today morning . total morning i spend in my system but i didnt get it . because with out that applet i cant able to connect to network with my USB modem.

Thanks in advance.
Regards 
raja

---

### Post by dino99 on 2011-09-28
dont know about xubuntu, but:

sudo dpkg-reconfigure -phigh -a
( can take a while, be patient)

---

### Post by raja.genupula on 2011-09-29
Thanks dino99.
I will try it when i get back to my room.

---

### Post by raja.genupula on 2011-09-29
hey dino99 , just now i have tried and no result.
for more suggestions i am giving the output here.

```
assassin@raju-xubuntu:~$ sudo dpkg-reconfigure -phigh -a
[sudo] password for assassin: 
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service acpid stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop acpid
acpid stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service acpid start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start acpid
acpid start/running, process 2146
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_NAME missing
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_PACKAGE missing
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service apport stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop apport
apport stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service apport start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start apport
apport start/running
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service atd stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop atd
atd stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service atd start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start atd
atd start/running, process 2531
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service avahi-daemon stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop avahi-daemon
avahi-daemon stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload dbus
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service avahi-daemon start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start avahi-daemon
avahi-daemon start/running, process 2610
Rebuilding /usr/share/applications/bamf.index...
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode.
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service binfmt-support stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop binfmt-support
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service binfmt-support start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start binfmt-support
binfmt-support stop/waiting
 * Stopping bluetooth                                                    [ OK ] 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload dbus
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload udev
 * Starting bluetooth                                                    [ OK ] 
update-initramfs: Generating /boot/initrd.img-3.0.0-11-generic
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....done.
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs: Generating /boot/initrd.img-3.0.0-11-generic
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service cron stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop cron
cron stop/waiting
dpkg-maintscript-helper: error: couldn't identify the package
assassin@raju-xubuntu:~$ 
```

thanks in advance

---

### Post by raja.genupula on 2011-10-08
Hello 
please any one help me on this issue .

---

### Post by raja.genupula on 2011-10-08
Thank god , finally my issue got solved.
I did as like this

Panel preferences--> Items --> add indicator applet.
that's worked for me.

I am marking this is as solved.

---

