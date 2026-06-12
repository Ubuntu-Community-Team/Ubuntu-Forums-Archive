---
title: "Error when installing Virtualbox Guest Additions"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by Jake Sweeney on 2013-02-12
Hello Everyone :)

I'm running Ubuntu 12.10 via virtualbox and upon installing virtualbox guest additions, the installation process fails at finding a suitable kernel. I've tried autoremoving guest additions ad installing it again via the command line and not the mountable ISO file.
This is the error message that is displayed:
```
sudo apt-get install virtualbox-guest-additions -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgsoap2 libqt4-opengl virtualbox virtualbox-dkms
  virtualbox-guest-additions-iso virtualbox-qt
Suggested packages:
  vde2
The following NEW packages will be installed
  libgsoap2 libqt4-opengl virtualbox virtualbox-dkms
  virtualbox-guest-additions virtualbox-guest-additions-iso virtualbox-qt
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/60.2 MB of archives.
After this operation, 123 MB of additional disk space will be used.
Selecting previously unselected package libqt4-opengl:amd64.
(Reading database ... 158250 files and directories currently installed.)
Unpacking libqt4-opengl:amd64 (from .../libqt4-opengl_4%3a4.8.3+dfsg-0ubuntu3_amd64.deb) ...
Selecting previously unselected package libgsoap2.
Unpacking libgsoap2 (from .../libgsoap2_2.8.7-1_amd64.deb) ...
Selecting previously unselected package virtualbox.
Unpacking virtualbox (from .../virtualbox_4.1.18-dfsg-1ubuntu1.1_amd64.deb) ...
Selecting previously unselected package virtualbox-dkms.
Unpacking virtualbox-dkms (from .../virtualbox-dkms_4.1.18-dfsg-1ubuntu1.1_all.deb) ...
Selecting previously unselected package virtualbox-qt.
Unpacking virtualbox-qt (from .../virtualbox-qt_4.1.18-dfsg-1ubuntu1.1_amd64.deb) ...
Selecting previously unselected package virtualbox-guest-additions-iso.
Unpacking virtualbox-guest-additions-iso (from .../virtualbox-guest-additions-iso_4.1.18-1_all.deb) ...
Selecting previously unselected package virtualbox-guest-additions.
Unpacking virtualbox-guest-additions (from .../virtualbox-guest-additions_4.1.18-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Setting up libqt4-opengl:amd64 (4:4.8.3+dfsg-0ubuntu3) ...
Setting up libgsoap2 (2.8.7-1) ...
Setting up virtualbox (4.1.18-dfsg-1ubuntu1.1) ...
 * Stopping VirtualBox kernel modules                                                              [ OK ] 
 * Starting VirtualBox kernel modules                                                                      * No suitable module for running kernel found
                                                                                                   [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.
Setting up virtualbox-dkms (4.1.18-dfsg-1ubuntu1.1) ...
Loading new virtualbox-4.1.18 DKMS files...
First Installation: checking all kernels...
Building only for 3.5.0-23-generic
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
 * Stopping VirtualBox kernel modules                                                              [ OK ] 
 * Starting VirtualBox kernel modules                                                                      * No suitable module for running kernel found
                                                                                                   [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.
Setting up virtualbox-qt (4.1.18-dfsg-1ubuntu1.1) ...
Setting up virtualbox-guest-additions-iso (4.1.18-1) ...
Setting up virtualbox-guest-additions (4.1.18-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

It's probably something really stupid, but it has me stumped. :confused:

---

### Post by lykwydchykyn on 2013-02-12
I *think* that the virtualbox-guest-additions package is not something you install on guests, but something you install on the host so that it can make the guest additions available to guests.  This would be why it depends on Virtualbox itself (doesn't make any sense to install virtualbox on a vbox guest).

Check out the instructions here: [http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html)

(scroll down until you get to "Installing the Linux Guest Additions").

---

### Post by Jake Sweeney on 2013-02-12
I can't seem to be able to install guest additions on my Windows 7 host computer. I've followed the installation guide and it is still coming up with the same message as before :/

---

### Post by DuckHook on 2013-02-12
Guest additions are proprietary drivers that are indeed installed in the guest session to permit higher non-standard resolutions, dynamic resizing, mouse integration, etc. These replace the default video, mouse and other drivers of the guest OS and do not modify anything on the host. They are typically downloaded onto the host because VirtualBox creates a special folder from which they can be easily loaded and then keeps track of updates for you, but Guest Additions can be burned onto a cd-rom and installed into the guest quite independently of the host.

@OP

Try:```
sudo apt-get update
sudo apt-get install linux-headers-generic
```

Also, what is your host OS?

---

### Post by Jake Sweeney on 2013-02-12
Thanks for the suggestion of updating the generic kernel headers. It seems to have done the job. I'll mark this thread as solved :)

---

