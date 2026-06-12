---
title: "New to Linux, trying to update git-all i get errors"
date: 2017-01-07
forum: New to Ubuntu
---

### Post by muzzh on 2017-01-07
```
VirtualBox:~$ sudo apt-get install git-all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git-all is already the newest version (1:2.7.4-0ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 132 not upgraded.
6 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up runit (2.1.2-3ubuntu1) ...
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
dpkg: error processing package runit (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of git-daemon-run:
 git-daemon-run depends on runit; however:
  Package runit is not configured yet.

dpkg: error processing package git-daemon-run (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-4.4.0-57-generic (4.4.0-57.78) ...
Running depmod.
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-4.4.0-57-generic
) points to /boot/initrd.img-4.4.0-57-generic
 (/boot/initrd.img-4.4.0-57-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-57-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-4.4.0-57-generic
) points to /boot/vmlinuz-4.4.0-57-generic
 (/boot/vmlinuz-4.4.0-57-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-57-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/vboxadd 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: failed to exec /etc/kernel/postinst.d/vboxadd: Exec format error
run-parts: /etc/kernel/postinst.d/vboxadd exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-57-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-57-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-57-generic:
 linux-image-extra-4.4.0-57-generic depends on linux-image-4.4.0-57-generic; however:
  Package linux-image-4.4.0-57-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-57-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-57-generic; however:
  Package linux-image-4.4.0-57-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-57-generic; however:
  Package linux-image-extra-4.4.0-57-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:No apport report written because MaxReports is reached already

 linux-generic depends on linux-image-generic (= 4.4.0.57.60); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 runit
 git-daemon-run
 linux-image-4.4.0-57-generic
 linux-image-extra-4.4.0-57-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

any suggestion ?
As I said, I'm completely new to Linux.
the only thing I have done to the VB Xubuntu is install PyCharm in usr/local/bin

the last 4 (all containing linux-xxxxx, happen when I have tried to do other updates/installs)

Thanks for your help!

---

### Post by ian-weisser on 2017-01-07
The runit and git-deamon-run errors are a known bug: [LP#1448164]("https://bugs.launchpad.net/ubuntu/+source/runit/+bug/1448164"). A workaround is in the bug report.

---

### Post by muzzh on 2017-01-17
thanks you !
I have fixed that part, but now I'm still wondering what the milion other errors are, which I get anytime i try to install or remove something
```
xavier@xavier-VirtualBox:/boot/grub$ sudo apt-get install git-all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git-all is already the newest version (1:2.7.4-0ubuntu1).
The following packages were automatically installed and are no longer required:
  fgetty libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libgail18 libglade2-0 libgnome-2-0 libgnome2-0
  libgnome2-bin libgnome2-common libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-common libidl-2-0 liborbit-2-0 liborbit2 python-cairo python-dbus python-gconf python-gi python-gnome2
  python-gobject python-gobject-2 python-gtk2 python-keybinder python-notify python-pyorbit python-vte
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 151 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-4.4.0-57-generic (4.4.0-57.78) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-4.4.0-57-generic
) points to /boot/initrd.img-4.4.0-57-generic
 (/boot/initrd.img-4.4.0-57-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-57-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-4.4.0-57-generic
) points to /boot/vmlinuz-4.4.0-57-generic
 (/boot/vmlinuz-4.4.0-57-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-57-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/vboxadd 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: failed to exec /etc/kernel/postinst.d/vboxadd: Exec format error
run-parts: /etc/kernel/postinst.d/vboxadd exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-57-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-57-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-57-generic:
 linux-image-extra-4.4.0-57-generic depends on linux-image-4.4.0-57-generic; however:
  Package linux-image-4.4.0-57-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-57-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-57-generic; however:
  Package linux-image-4.4.0-57-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-57-generic; however:
  Package linux-image-extra-4.4.0-57-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.57.60); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-4.4.0-57-generic
 linux-image-extra-4.4.0-57-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ian-weisser on 2017-01-17
Stop trying to install git-all. Read the system response - it's already installed.

The other errors seem completely unrelated to your previous issues, which is why I didn't discuss them...it wasn't part of your question.
What's happening is that the Kernel upgrade triggers a VirtualBox script...which fails, aborting the entire queue of package actions.
Since apt remembers previously marked actions and requeues them each time it is run, all apt actions will fail until you fix the virtualbox script.

The easiest way is to simply use dpkg to purge virtualbox (dpkg --purge virtualbox)
If that's not acceptable because you wish to keep Virtualbox, several solutions are discussed in this [AskUbuntu thread]("http://askubuntu.com/questions/850101/ubuntu-16-04-broken-kernel-packages-wont-let-me-install-or-remove-anything-with").

---

### Post by muzzh on 2017-01-17
Thanks for your response.

I used git-all again cause I actually knew it was there and then it could show those specific errors...
thanks for pointing out that vbox was the problem, if I could have read the system response I probably would have figured it out, but then I wouldnt have asked here now would I,
anyway thanks for pointing this out, I could locate it in the response and learn from it. Many thanks!

I could not remove the Vbox as Linux is running on it, but following instructions on the thread you pointed out worked once I deleted the problematic file :)
Onwards to see if VBox survives ah !

---

