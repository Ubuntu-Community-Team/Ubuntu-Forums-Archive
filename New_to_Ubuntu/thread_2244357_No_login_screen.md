---
title: "No login screen"
date: 2014-09-15
forum: New to Ubuntu
---

### Post by randy15 on 2014-09-15
Hello all...

I'm a linux noob, and I was using ubuntu to successfully set up a nice plex server.  it's been up for several months, and then i decided to see about remote desktoping into the ubuntu box.  after several failed attempts (and installing several desktop environments), i finally got it to work.  Then i decided to try and clean up the several desktop environments that i installed.

somehow, i lost my desktop.  so i rebooted, and all i get is a weird ubuntu splash animation (it says ubuntu 14.04 with 4 dots under it) and it never goes away.

I can hit escape, and see the boot text.  i can hit escape again and see the splash screen.

I know the machine is functional because i can terminal into it fine, and use some of the servers i installed (plex, couchpotato, sickbeard, minecraft, etc) but when it comes to sitting at the machine, i can't do anything graphical (i can use the control-alt-function key to get into terminals).

can anybody please help me?

thanks,

Randy

---

### Post by deadflowr on 2014-09-15
Start with something simple
In one of those tty1-6 consoles(terminals)
try
```
startx
```
What happens?
Does a gui screen/desktop start or does it produce a lot of errors or stuff?


Also, what desktop environments did you install, and how did you go about cleaning them?

---

### Post by maxinstuff2 on 2014-09-15
You could also disable the splashscreen so you can see the bootloader doing it's thing and where it get's stuck.

```
sudo nano /etc/default/grub
```

You need to edit this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" (you might have other things in this line too - please don't change them)

Just delete the phrase "quiet splash" to make the line read:
GRUB_CMDLINE_LINUX_DEFAULT="" (as above if you have other parameters in here, leave them in there - only delete "quiet splash")

Ctrl+X to exit (it will confirm if you want to save).

Then:
```
sudo update-grub
```

And reboot. The splashscreen will now be disabled and you will see the bootloader instead - including where it get's stuck.

---

### Post by randy15 on 2014-09-15
> **deadflowr said:**
> Start with something simple
In one of those tty1-6 consoles(terminals)
try
```
startx
```
What happens?
Does a gui screen/desktop start or does it produce a lot of errors or stuff?


Also, what desktop environments did you install, and how did you go about cleaning them?

That brought me to a weird gui screen! (see attachment)

as for what desktop environments i installed, i tried cinnamon, kde, xfce.. i can't remember all of them... and for cleaning them, i tried to follow instructions for each one using terminal, and that i don't remember either...

---

### Post by randy15 on 2014-09-15
> **maxinstuff2 said:**
> You could also disable the splashscreen so you can see the bootloader doing it's thing and where it get's stuck.

```
sudo nano /etc/default/grub
```

You need to edit this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" (you might have other things in this line too - please don't change them)

Just delete the phrase "quiet splash" to make the line read:
GRUB_CMDLINE_LINUX_DEFAULT="" (as above if you have other parameters in here, leave them in there - only delete "quiet splash")

Ctrl+X to exit (it will confirm if you want to save).

Then:
```
sudo update-grub
```

And reboot. The splashscreen will now be disabled and you will see the bootloader instead - including where it get's stuck.

Thanks, it looks the same as my /var/log/boot.log

```

 * Stopping Read required files in advance[122G[ OK ]
 * Starting Mount filesystems on boot[122G[ OK ]
 * Starting Populate /dev filesystem[122G[ OK ]
 * Starting Populate and link to /run filesystem[122G[ OK ]
 * Stopping Populate /dev filesystem[122G[ OK ]
 * Stopping Populate and link to /run filesystem[122G[ OK ]
 * Stopping Track if upstart is running in a container[122G[ OK ]
 * Starting Initialize or finalize resolvconf[122G[ OK ]
 * Starting set console keymap[122G[ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted[122G[ OK ]
 * Starting Signal sysvinit that virtual filesystems are mounted[122G[ OK ]
 * Starting Signal sysvinit that remote filesystems are mounted[122G[ OK ]
 * Stopping set console keymap[122G[ OK ]
 * Starting Bridge udev events into upstart[122G[ OK ]
 * Starting device node and kernel event manager[122G[ OK ]
 * Starting load modules from /etc/modules[122G[ OK ]
 * Starting cold plug devices[122G[ OK ]
 * Starting log initial device creation[122G[ OK ]
 * Stopping load modules from /etc/modules[122G[ OK ]
 * Starting configure network device security[122G[ OK ]
 * Starting configure network device security[122G[ OK ]
 * Starting configure network device[122G[ OK ]
 * Starting Mount network filesystems[122G[ OK ]
 * Stopping Mount network filesystems[122G[ OK ]
 * Starting Bridge socket events into upstart[122G[ OK ]
 * Starting configure network device[122G[ OK ]
 * Starting set console font[122G[ OK ]
 * Stopping set console font[122G[ OK ]
 * Starting userspace bootsplash[122G[ OK ]
 * Starting Send an event to indicate plymouth is up[122G[ OK ]
 * Stopping userspace bootsplash[122G[ OK ]
 * Stopping cold plug devices[122G[ OK ]
 * Stopping log initial device creation[122G[ OK ]
 * Starting Signal sysvinit that the rootfs is mounted[122G[ OK ]
 * Starting Clean /tmp directory[122G[ OK ]
 * Stopping Clean /tmp directory[122G[ OK ]
 * Stopping Read required files in advance (for other mountpoints)[122G[ OK ]
 * Stopping Read required files in advance (for other mountpoints)[122G[ OK ]
 * Stopping Read required files in advance (for other mountpoints)[122G[ OK ]
 * Stopping Read required files in advance (for other mountpoints)[122G[ OK ]
 * Stopping Read required files in advance (for other mountpoints)[122G[ OK ]
 * Stopping Read required files in advance (for other mountpoints)[122G[ OK ]
 * Starting Signal sysvinit that local filesystems are mounted[122G[ OK ]
 * Starting configure network device security[122G[ OK ]
 * Stopping Mount filesystems on boot[122G[ OK ]
 * Starting flush early job output to logs[122G[ OK ]
 * Stopping Failsafe Boot Delay[122G[ OK ]
 * Starting System V initialisation compatibility[122G[ OK ]
 * Stopping flush early job output to logs[122G[ OK ]
 * Starting configure virtual network devices[122G[ OK ]
 * Starting Bridge file events into upstart[122G[ OK ]
 * Starting system logging daemon[122G[ OK ]
 * Starting D-Bus system message bus[122G[ OK ]
 * Starting modem connection manager[122G[ OK ]
 * Starting configure network device security[122G[ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles       [160G 
[154G[ OK ]
 * Starting SystemD login management service[122G[ OK ]
 * Starting mDNS/DNS-SD daemon[122G[ OK ]
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated[122G[ OK ]
 * Setting up X socket directories...       [160G 
[154G[ OK ]
 * Starting bluetooth daemon[122G[ OK ]
 * Stopping System V initialisation compatibility[122G[ OK ]
 * Starting System V runlevel compatibility[122G[ OK ]
 * Starting GNOME Display Manager[122G[ OK ]
 * Starting anac(h)ronistic cron[122G[ OK ]
 * Starting save kernel messages[122G[ OK ]
 * Stopping Send an event to indicate plymouth is up[122G[ OK ]
 * Stopping Reload cups, upon starting avahi-daemon to make sure remote queues are populated[122G[ OK ]
 * Stopping Restore Sound Card State[122G[ OK ]
 * Starting cups-browsed - Bonjour remote printer browsing daemon[122G[ OK ]
 * Starting ACPI daemon[122G[ OK ]
 * Stopping crash report submission daemon[122G[ OK ]
 * Stopping GNOME Display Manager[122G[ OK ]
 * Starting CPU interrupts balancing daemon[122G[ OK ]
 * Starting automatic crash report generation[122G[ OK ]
 * Loading cpufreq kernel modules...       [160G 
[154G[ OK ]
 * Starting network connection manager[122G[ OK ]
 * CPU0...       [160G  * Stopping save kernel messages[122G[ OK ]
 * Stopping anac(h)ronistic cron[122G[ OK ]
 * CPU1...       [160G  * CPU2...       [160G  * CPU3...       [160G  * CPU4...       [160G  * CPU5...       [160G  * CPU6...       [160G  * CPU7...       [160G  * CPUFreq Utilities: Setting ondemand CPUFreq governor...       [160G 
[154G[ OK ]
 * Starting OpenSSH server[122G[ OK ]
/etc/default/sickbeard not found using default settings.
Starting SickBeard
 * speech-dispatcher disabled; edit /etc/default/speech-dispatcher
Starting VirtualBox kernel modules ...failed!
  (modprobe vboxdrv failed. Please use 'dmesg' to find out why)
 * Starting Remote Desktop Protocol server       [160G 
[154G[ OK ]
saned disabled; edit /etc/default/saned
 * Restoring resolver state...       [160G 
[154G[ OK ]
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message
 * 
 * Starting MySQL Server[122G[ OK ]
 * Starting SABnzbd+ binary newsgrabber       [160G 
[154G[ OK ]
 * Stopping System V runlevel compatibility[122G[ OK ]
 * Starting Mount network filesystems[122G[ OK ]
 * Starting Plex Media Server[122G[ OK ]
 * Stopping Mount network filesystems[122G[ OK ]
 * Starting CUPS printing spooler/server[122G[ OK ]

```

---

### Post by randy15 on 2014-09-16
So what does this mean? Why dont i have a login or desktop?

---

### Post by randy15 on 2014-09-16
So what does this mean? Why dont i have a login or desktop?

---

### Post by pissedoffdude on 2014-09-16
Looks like your display manager (GDM) is starting and stopping.  Try going back to the default after you log into the terminal:

```
sudo apt-get update
sudo apt-get install lightdm
sudo dpkg-reconfigure lightdm

```

Select lightdm and reboot (by typing in sudo reboot). It might be a little ugly if you ended up removing the default theme, but we can take care of that later if this works.

---

### Post by randy15 on 2014-09-17
> **pissedoffdude said:**
> Looks like your display manager (GDM) is starting and stopping.  Try going back to the default after you log into the terminal:

```
sudo apt-get update
sudo apt-get install lightdm
sudo dpkg-reconfigure lightdm

```

Select lightdm and reboot (by typing in sudo reboot). It might be a little ugly if you ended up removing the default theme, but we can take care of that later if this works.

it didn't work...

i got this from "sudo apt-get install lightdm"

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cryptsetup-bin : Depends: libcryptsetup4 (>= 2:1.6) but it is not going to be installed
 grub-efi-amd64 : Depends: grub-common
                  Depends: grub2-common (= 2.02~beta2-9ubuntu1)
                  Depends: grub-efi-amd64-bin (= 2.02~beta2-9ubuntu1)
 gvfs-daemons : Depends: udisks2
                Recommends: policykit-1-gnome
 lightdm : Depends: plymouth (>= 0.8.8-0ubuntu6.1) but it is not going to be installed
           Recommends: xserver-xorg but it is not going to be installed
 upstart : Depends: initscripts
           Depends: mountall
           Depends: ifupdown (>= 0.6.10ubuntu5)
 xchat-indicator : Depends: xchat but it is not going to be installed
 xul-ext-webaccounts : Depends: webaccounts-extension-common (= 0.5-0ubuntu2) but it is not going to be instaed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

---

### Post by randy15 on 2014-09-17
ooh i fixed it!

```

 sudo aptitude install lightdm
The following NEW packages will be installed:
  lightdm plymouth{ab} plymouth-theme-ubuntu-text{ab}
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 207 kB of archives. After unpacking 1,115 kB will be used.
The following packages have unmet dependencies:
 plymouth-theme-ubuntu-text : Conflicts: plymouth-theme-ubuntu-text:i386 but 0.8.8-0ubuntu17 is installed.
 plymouth-theme-ubuntu-text:i386 : Conflicts: plymouth-theme-ubuntu-text but 0.8.8-0ubuntu17 is to be installed.
 plymouth : Conflicts: plymouth:i386 but 0.8.8-0ubuntu17 is installed.
 plymouth:i386 : Conflicts: plymouth but 0.8.8-0ubuntu17 is to be installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     mountall:i386
2)     plymouth:i386
3)     plymouth-theme-ubuntu-text:i386

     Install the following packages:
4)     mountall [2.53 (trusty)]



Accept this solution? [Y/n/q/?] y
The following NEW packages will be installed:
  lightdm mountall{a} plymouth{a} plymouth-theme-ubuntu-text{a}
The following packages will be REMOVED:
  mountall:i386{a} plymouth:i386{a} plymouth-theme-ubuntu-text:i386{a}
0 packages upgraded, 4 newly installed, 3 to remove and 0 not upgraded.
Need to get 263 kB of archives. After unpacking 593 kB will be used.
Do you want to continue? [Y/n/?] Y
Get: 1 http://us.archive.ubuntu.com/ubuntu/ trusty/main mountall amd64 2.53 [55.8 kB]
Get: 2 http://us.archive.ubuntu.com/ubuntu/ trusty/main plymouth amd64 0.8.8-0ubuntu17 [98.5 kB]
Get: 3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main lightdm amd64 1.10.1-0ubuntu1 [100 kB]
Get: 4 http://us.archive.ubuntu.com/ubuntu/ trusty/main plymouth-theme-ubuntu-text amd64 0.8.8-0ubuntu17 [7,962 B]
Fetched 263 kB in 0s (668 kB/s)
Preconfiguring packages ...
(Reading database ... 243327 files and directories currently installed.)
Removing plymouth-theme-ubuntu-text (0.8.8-0ubuntu17) ...
update-initramfs: deferring update (trigger activated)
dpkg: mountall: dependency problems, but removing anyway as you requested:
 initscripts depends on mountall (>= 2.28).
 upstart depends on mountall.
 plymouth depends on mountall (>= 2.0).

Removing mountall (2.53) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic
Processing triggers for man-db (2.6.7.1-1) ...
Selecting previously unselected package mountall.
(Reading database ... 243304 files and directories currently installed.)
Preparing to unpack .../mountall_2.53_amd64.deb ...
Unpacking mountall (2.53) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for man-db (2.6.7.1-1) ...
(Reading database ... 243321 files and directories currently installed.)
Removing plymouth (0.8.8-0ubuntu17) ...
rmdir: failed to remove &#8216;/lib/plymouth/themes&#8217;: No such file or directory
rmdir: failed to remove &#8216;/lib/plymouth&#8217;: No such file or directory
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic
Selecting previously unselected package plymouth.
(Reading database ... 243299 files and directories currently installed.)
Preparing to unpack .../plymouth_0.8.8-0ubuntu17_amd64.deb ...
Unpacking plymouth (0.8.8-0ubuntu17) ...
Selecting previously unselected package lightdm.
Preparing to unpack .../lightdm_1.10.1-0ubuntu1_amd64.deb ...
Unpacking lightdm (1.10.1-0ubuntu1) ...
Selecting previously unselected package plymouth-theme-ubuntu-text.
Preparing to unpack .../plymouth-theme-ubuntu-text_0.8.8-0ubuntu17_amd64.deb ...
Unpacking plymouth-theme-ubuntu-text (0.8.8-0ubuntu17) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for man-db (2.6.7.1-1) ...
Setting up mountall (2.53) ...
Setting up plymouth (0.8.8-0ubuntu17) ...
update-initramfs: deferring update (trigger activated)
Setting up lightdm (1.10.1-0ubuntu1) ...
Adding group `lightdm' (GID 130) ...
Done.
Adding system user `lightdm' (UID 121) ...
Adding new user `lightdm' (UID 121) with group `lightdm' ...
Creating home directory `/var/lib/lightdm' ...
usermod: no changes
usermod: no changes
usermod: no changes
Setting up plymouth-theme-ubuntu-text (0.8.8-0ubuntu17) ...
update-alternatives: using /lib/plymouth/themes/ubuntu-text/ubuntu-text.plymouth to provide /lib/plymouth/themes/text.plymouth (text.plymouth) in auto mode
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic
Processing triggers for ureadahead (0.100.0-16) ...


```

so now i get a log in after i reboot, but now i'm stuck with broken desktops... cinnamon keeps saying it crashed, and there's no menu things in gnome3 and cfxe (or something like that) but i think that'll be a different post... 

thanks to all that helped!

---

