---
title: "udevd[89] runtime directory /run/dev not writeable"
date: 2011-07-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2011-07-02
Hello,

Yesterday I installed Ubuntu alternate CD July 01 build.  Everything seemed fine until after reboot.  Here's what the black screen shows in sequence:

1.  Input not supported

2. [COLOR="blue"]udevd[89] runtime directory /run/udev not writeable. Fallback to 'dev.udev'
[/COLOR]
3. Input not supported

I installed the June 13 build before on my PC with GeForce 7300GT Nvidia video card and everything works.

Any suggestions?  Thanks for your help.

:(

---

### Post by dino99 on 2011-07-02
its the harmless verbosity, everyone see it

---

### Post by iClouseau88 on 2011-07-02
Thanks dino99 for your reply.  The problem is I waited and waited a very long time and I still don't see my login screen!

---

### Post by donniezazen on 2011-07-02
I have similar problem. It never boots to GDM. Check out the pictures.

---

### Post by RJ12 on 2011-07-02
Hmmm... I saw this problem eariler on the forums. I get that message, but it flies by very quickly that it's hard to notice it.

---

### Post by donniezazen on 2011-07-02
> **RJ12 said:**
> Hmmm... I saw this problem eariler on the forums. I get that message, but it flies by very quickly that it's hard to notice it.

I get this in USB Live CD installation so i am not able to install a new build.

On my old installation the error goes off pretty quickly.

---

### Post by garvinrick4 on 2011-07-02
> udevd[89] runtime directory /run/udev not writeable. Fallback to 'dev.udev'I have same as of July 2nd 4:30 PM pacific time after upgrades using mirror.pnl.gov  Usa
Can ctrl/alt/F1 and use terminal but will not give me a GUI. Chrooted from another install
fsck is clean, dpkg --configure -a is clean, Have gdm, xorg, ubuntu desktop and all latest.

```

[UPGRADE] apport 1.21.1-0ubuntu2 -> 1.21.2-0ubuntu1
[UPGRADE] apport-gtk 1.21.1-0ubuntu2 -> 1.21.2-0ubuntu1
[UPGRADE] apt 0.8.15ubuntu1 -> 0.8.15.1ubuntu1
[UPGRADE] apt-transport-https 0.8.15ubuntu1 -> 0.8.15.1ubuntu1
[UPGRADE] apt-utils 0.8.15ubuntu1 -> 0.8.15.1ubuntu1
[UPGRADE] avahi-autoipd 0.6.30-3ubuntu3 -> 0.6.30-4ubuntu1
[UPGRADE] avahi-daemon 0.6.30-3ubuntu3 -> 0.6.30-4ubuntu1
[UPGRADE] avahi-utils 0.6.30-3ubuntu3 -> 0.6.30-4ubuntu1
[UPGRADE] ca-certificates 20110421ubuntu1 -> 20110502
[UPGRADE] casper 1.269 -> 1.271
[UPGRADE] checkbox 0.12.2 -> 0.12.3
[UPGRADE] checkbox-gtk 0.12.2 -> 0.12.3
[UPGRADE] command-not-found 0.2.41ubuntu3 -> 0.2.41ubuntu4
[UPGRADE] command-not-found-data 0.2.41ubuntu3 -> 0.2.41ubuntu4
[UPGRADE] debhelper 8.1.6ubuntu2 -> 8.9.0ubuntu1
[UPGRADE] fontconfig 2.8.0-2.2ubuntu1 -> 2.8.0-3ubuntu1
[UPGRADE] fontconfig-config 2.8.0-2.2ubuntu1 -> 2.8.0-3ubuntu1
[UPGRADE] gconf-defaults-service 2.32.4-1ubuntu1 -> 2.32.4-1ubuntu2
[UPGRADE] gconf2 2.32.4-1ubuntu1 -> 2.32.4-1ubuntu2
[UPGRADE] gconf2-common 2.32.4-1ubuntu1 -> 2.32.4-1ubuntu2
[UPGRADE] gdm 2.32.1-0ubuntu5 -> 3.0.4-0ubuntu3
[UPGRADE] gir1.2-gconf-2.0 2.32.4-1ubuntu1 -> 2.32.4-1ubuntu2
[UPGRADE] gir1.2-gnomebluetooth-1.0 3.0.1-0ubuntu1 -> 3.0.1-0ubuntu3
[UPGRADE] gir1.2-gtk-2.0 2.24.5-0ubuntu2 -> 2.24.5-0ubuntu3
[UPGRADE] gir1.2-lightdm-0 0.4.0-0ubuntu7 -> 0.4.1-0ubuntu1
[UPGRADE] gnome-bluetooth 3.0.1-0ubuntu1 -> 3.0.1-0ubuntu3
[UPGRADE] gnome-control-center-data 1:3.0.2-1ubuntu6 -> 1:3.0.2-1ubuntu7
[UPGRADE] gnome-disk-utility 3.0.0-1ubuntu1 -> 3.0.0-1ubuntu2
[UPGRADE] gnome-keyring 3.0.3-2 -> 3.0.3-2ubuntu1
[UPGRADE] gnome-power-manager 3.0.2-0ubuntu1 -> 3.0.2-0ubuntu2
[UPGRADE] gnome-session-canberra 0.28-0ubuntu5 -> 0.28-0ubuntu7
[UPGRADE] gnome-user-share 3.0.0-2ubuntu1 -> 3.0.0-2ubuntu2
[UPGRADE] gtk2-engines-pixbuf 2.24.5-0ubuntu2 -> 2.24.5-0ubuntu3
[UPGRADE] gtk3-engines-unico 0.1.0+r69-0ubuntu1 -> 0.1.0+r74-0ubuntu1
[UPGRADE] keyutils 1.4-4ubuntu2 -> 1.4-5
[UPGRADE] language-pack-en 1:11.10+20110627 -> 1:11.10+20110630.1
[UPGRADE] language-pack-es 1:11.10+20110627 -> 1:11.10+20110630.1
[UPGRADE] language-pack-gnome-en 1:11.10+20110627 -> 1:11.10+20110630
[UPGRADE] language-pack-gnome-es 1:11.10+20110627 -> 1:11.10+20110630
[UPGRADE] language-pack-gnome-pt 1:11.10+20110627 -> 1:11.10+20110630
[UPGRADE] language-pack-gnome-xh 1:11.10+20110627 -> 1:11.10+20110630
[UPGRADE] language-pack-pt 1:11.10+20110627 -> 1:11.10+20110630.1
[UPGRADE] language-pack-xh 1:11.10+20110627 -> 1:11.10+20110630
[UPGRADE] libavahi-client3 0.6.30-3ubuntu3 -> 0.6.30-4ubuntu1
[UPGRADE] libavahi-common-data 0.6.30-3ubuntu3 -> 0.6.30-4ubuntu1
[UPGRADE] libavahi-common3 0.6.30-3ubuntu3 -> 0.6.30-4ubuntu1
[UPGRADE] libavahi-core7 0.6.30-3ubuntu3 -> 0.6.30-4ubuntu1
[UPGRADE] libavahi-glib1 0.6.30-3ubuntu3 -> 0.6.30-4ubuntu1
[UPGRADE] libavahi-gobject0 0.6.30-3ubuntu3 -> 0.6.30-4ubuntu1
[UPGRADE] libavahi-ui-gtk3-0 0.6.30-3ubuntu3 -> 0.6.30-4ubuntu1
[UPGRADE] libavahi-ui0 0.6.30-3ubuntu3 -> 0.6.30-4ubuntu1
[UPGRADE] libc-bin 2.13-6ubuntu2 -> 2.13-8ubuntu1
[UPGRADE] libc-dev-bin 2.13-6ubuntu2 -> 2.13-8ubuntu1
[UPGRADE] libc6 2.13-6ubuntu2 -> 2.13-8ubuntu1
[UPGRADE] libc6-dev 2.13-6ubuntu2 -> 2.13-8ubuntu1
[UPGRADE] libc6-i386 2.13-6ubuntu2 -> 2.13-8ubuntu1
[UPGRADE] libcanberra-gtk-module 0.28-0ubuntu5 -> 0.28-0ubuntu7
[UPGRADE] libcanberra-gtk0 0.28-0ubuntu5 -> 0.28-0ubuntu7
[UPGRADE] libcanberra-gtk3-0 0.28-0ubuntu5 -> 0.28-0ubuntu7
[UPGRADE] libcanberra-gtk3-module 0.28-0ubuntu5 -> 0.28-0ubuntu7
[UPGRADE] libcanberra-pulse 0.28-0ubuntu5 -> 0.28-0ubuntu7
[UPGRADE] libcanberra0 0.28-0ubuntu5 -> 0.28-0ubuntu7
[UPGRADE] libcurl3-gnutls 7.21.6-1ubuntu2 -> 7.21.6-3ubuntu1
[UPGRADE] libdb4.8 4.8.30-8ubuntu1 -> 4.8.30-9
[UPGRADE] libdb5.1 5.1.25-10ubuntu1 -> 5.1.25-11
[UPGRADE] libegl1-mesa 7.10.3-0ubuntu4 -> 7.11~1-0ubuntu2
[UPGRADE] libegl1-mesa-drivers 7.10.3-0ubuntu4 -> 7.11~1-0ubuntu2
[UPGRADE] libfontconfig1 2.8.0-2.2ubuntu1 -> 2.8.0-3ubuntu1
[UPGRADE] libgail-common 2.24.5-0ubuntu2 -> 2.24.5-0ubuntu3
[UPGRADE] libgail18 2.24.5-0ubuntu2 -> 2.24.5-0ubuntu3
[UPGRADE] libgck0 3.0.3-2 -> 3.0.3-2ubuntu1
[UPGRADE] libgconf2-4 2.32.4-1ubuntu1 -> 2.32.4-1ubuntu2
[UPGRADE] libgcr-3-0 3.0.3-2 -> 3.0.3-2ubuntu1
[UPGRADE] libgcr0 3.0.3-2 -> 3.0.3-2ubuntu1
[UPGRADE] libgdu-gtk0 3.0.0-1ubuntu1 -> 3.0.0-1ubuntu2
[UPGRADE] libgdu0 3.0.0-1ubuntu1 -> 3.0.0-1ubuntu2
[UPGRADE] libgl1-mesa-dri 7.10.3-0ubuntu4 -> 7.11~1-0ubuntu2
[UPGRADE] libgl1-mesa-glx 7.10.3-0ubuntu4 -> 7.11~1-0ubuntu2
[UPGRADE] libglu1-mesa 7.10.3-0ubuntu4 -> 7.11~1-0ubuntu2
[UPGRADE] libgnome-bluetooth8 3.0.1-0ubuntu1 -> 3.0.1-0ubuntu3
[UPGRADE] libgnome-control-center1 1:3.0.2-1ubuntu6 -> 1:3.0.2-1ubuntu7
[UPGRADE] libgtk2.0-0 2.24.5-0ubuntu2 -> 2.24.5-0ubuntu3
[UPGRADE] libgtk2.0-bin 2.24.5-0ubuntu2 -> 2.24.5-0ubuntu3
[UPGRADE] libgtk2.0-common 2.24.5-0ubuntu2 -> 2.24.5-0ubuntu3
[UPGRADE] libkeyutils1 1.4-4ubuntu2 -> 1.4-5
[UPGRADE] liblightdm-gobject-0-0 0.4.0-0ubuntu7 -> 0.4.1-0ubuntu1
[UPGRADE] libmtp-common 1.1.0-1ubuntu1 -> 1.1.0-2ubuntu1
[UPGRADE] liboverlay-scrollbar-0.2-0 0.2.1-0ubuntu2 -> 0.2.3-0ubuntu1
[UPGRADE] liboverlay-scrollbar3-0.2-0 0.2.1-0ubuntu2 -> 0.2.3-0ubuntu1
[UPGRADE] libpam-gnome-keyring 3.0.3-2 -> 3.0.3-2ubuntu1
[UPGRADE] libpulse-browse0 1:0.9.23-0ubuntu1 -> 1:0.9.23-0ubuntu2
[UPGRADE] libpulse-mainloop-glib0 1:0.9.23-0ubuntu1 -> 1:0.9.23-0ubuntu2
[UPGRADE] libpulse0 1:0.9.23-0ubuntu1 -> 1:0.9.23-0ubuntu2
[UPGRADE] libunity-core-4.0-4 4.0.1-0ubuntu2 -> 4.0.1-0ubuntu3
[UPGRADE] libxcursor1 1:1.1.11-3 -> 1:1.1.12-1
[UPGRADE] libxrandr2 2:1.3.1-2 -> 2:1.3.2-2
[UPGRADE] light-themes 0.1.8.15 -> 0.1.8.16
[UPGRADE] lightdm 0.4.0-0ubuntu7 -> 0.4.1-0ubuntu1
[UPGRADE] lightdm-greeter-example-python-gtk 0.4.0-0ubuntu7 -> 0.4.1-0ubuntu1
[UPGRADE] lightdm-greeter-example-vala-gtk 0.4.0-0ubuntu7 -> 0.4.1-0ubuntu1
[UPGRADE] lintian 2.5.0ubuntu1 -> 2.5.1ubuntu1
[UPGRADE] multiarch-support 2.13-6ubuntu2 -> 2.13-8ubuntu1
[UPGRADE] nautilus-sendto 3.0.0-1ubuntu1 -> 3.0.0-1ubuntu2
[UPGRADE] netcat-openbsd 1.89-3ubuntu6 -> 1.89-4ubuntu1
[UPGRADE] onboard 0.94.0-0ubuntu2b2 -> 0.95.1-0ubuntu1
[UPGRADE] overlay-scrollbar 0.2.1-0ubuntu2 -> 0.2.3-0ubuntu1
[UPGRADE] policykit-desktop-privileges 0.5 -> 0.6
[UPGRADE] popularity-contest 1.52ubuntu1 -> 1.53ubuntu1
[UPGRADE] pulseaudio 1:0.9.23-0ubuntu1 -> 1:0.9.23-0ubuntu2
[UPGRADE] pulseaudio-esound-compat 1:0.9.23-0ubuntu1 -> 1:0.9.23-0ubuntu2
[UPGRADE] pulseaudio-module-bluetooth 1:0.9.23-0ubuntu1 -> 1:0.9.23-0ubuntu2
[UPGRADE] pulseaudio-module-gconf 1:0.9.23-0ubuntu1 -> 1:0.9.23-0ubuntu2
[UPGRADE] pulseaudio-module-raop 1:0.9.23-0ubuntu1 -> 1:0.9.23-0ubuntu2
[UPGRADE] pulseaudio-module-x11 1:0.9.23-0ubuntu1 -> 1:0.9.23-0ubuntu2
[UPGRADE] pulseaudio-module-zeroconf 1:0.9.23-0ubuntu1 -> 1:0.9.23-0ubuntu2
[UPGRADE] pulseaudio-utils 1:0.9.23-0ubuntu1 -> 1:0.9.23-0ubuntu2
[UPGRADE] python-apport 1.21.1-0ubuntu2 -> 1.21.2-0ubuntu1
[UPGRADE] python-cups 1.9.56-0ubuntu1 -> 1.9.56-0ubuntu3
[UPGRADE] python-cupshelpers 1.3.3+20110602-0ubuntu2 -> 1.3.3+20110602-0ubuntu3
[UPGRADE] python-problem-report 1.21.1-0ubuntu2 -> 1.21.2-0ubuntu1
[UPGRADE] system-config-printer-common 1.3.3+20110602-0ubuntu2 -> 1.3.3+20110602-0ubuntu3
[UPGRADE] system-config-printer-gnome 1.3.3+20110602-0ubuntu2 -> 1.3.3+20110602-0ubuntu3
[UPGRADE] system-config-printer-udev 1.3.3+20110602-0ubuntu2 -> 1.3.3+20110602-0ubuntu3
[UPGRADE] ubiquity-casper 1.269 -> 1.271
[UPGRADE] ubuntu-desktop 1.231 -> 1.232
[UPGRADE] ubuntu-minimal 1.231 -> 1.232
[UPGRADE] ubuntu-standard 1.231 -> 1.232
[UPGRADE] unity 4.0.1-0ubuntu2 -> 4.0.1-0ubuntu3
[UPGRADE] unity-common 4.0.1-0ubuntu2 -> 4.0.1-0ubuntu3
[UPGRADE] unity-services 4.0.1-0ubuntu2 -> 4.0.1-0ubuntu3
[UPGRADE] update-notifier 0.112ubuntu1 -> 0.112ubuntu2
[UPGRADE] update-notifier-common 0.112ubuntu1 -> 0.112ubuntu2
[UPGRADE] vino 3.1.2-0ubuntu1 -> 3.1.2-0ubuntu2
[UPGRADE] x11-utils 7.6+2 -> 7.6+3
[UPGRADE] xdg-user-dirs-gtk 0.8-1ubuntu1 -> 0.8-1ubuntu2
[UPGRADE] xfonts-utils 1:7.6~1 -> 1:7.6+1
[UPGRADE] xserver-xorg-video-ati 1:6.14.0-0ubuntu5 -> 1:6.14.2-1ubuntu2
[UPGRADE] xserver-xorg-video-radeon 1:6.14.0-0ubuntu5 -> 1:6.14.2-1ubuntu2
[UPGRADE] zeitgeist-datahub 0.7.0-0ubuntu1 -> 0.7.0-0ubuntu3
===============================================================================

Log complete.
```

---

### Post by garvinrick4 on 2011-07-02
Apport log at boot: Looking for assistance.

```
ERROR: apport (pid 1137) Sat Jul  2 17:35:06 2011: called for pid 1028, signal 11
ERROR: apport (pid 1137) Sat Jul  2 17:35:06 2011: executable: /usr/lib/gdm/gdm-simple-slave (command line "/usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1")
ERROR: apport (pid 1137) Sat Jul  2 17:35:06 2011: apport: report /var/crash/_usr_lib_gdm_gdm-simple-slave.0.crash already exists and unseen, doing nothing to avoid disk usage DoS
ERROR: apport (pid 1185) Sat Jul  2 17:35:51 2011: called for pid 1154, signal 11
ERROR: apport (pid 1185) Sat Jul  2 17:35:51 2011: executable: /usr/lib/gdm/gdm-simple-slave (command line "/usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display2")
ERROR: apport (pid 1185) Sat Jul  2 17:35:51 2011: apport: report /var/crash/_usr_lib_gdm_gdm-simple-slave.0.crash already exists and unseen, doing nothing to avoid disk usage DoS
ERROR: apport (pid 1195) Sat Jul  2 17:35:52 2011: called for pid 1190, signal 11
ERROR: apport (pid 1195) Sat Jul  2 17:35:52 2011: executable: /usr/lib/gdm/gdm-simple-slave (command line "/usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display3")
ERROR: apport (pid 1195) Sat Jul  2 17:35:52 2011: apport: report /var/crash/_usr_lib_gdm_gdm-simple-slave.0.crash already exists and unseen, doing nothing to avoid disk usage DoS
ERROR: apport (pid 1587) Sat Jul  2 17:36:50 2011: called for pid 1198, signal 6
ERROR: apport (pid 1587) Sat Jul  2 17:36:50 2011: executable: /usr/bin/Xorg (command line "/usr/bin/Xorg :3 -br -verbose -auth /var/run/gdm/auth-for-gdm-eq4JP6/database -nolisten tcp")
ERROR: apport (pid 1587) Sat Jul  2 17:36:50 2011: apport: report /var/crash/_usr_bin_Xorg.0.crash already exists and unseen, doing nothing to avoid disk usage DoS
``````

```

---

### Post by iClouseau88 on 2011-07-02
Hi,

Since SHA256 is OK for the July 01 image and because the physical disk integrity is OK too, I tried reinstalling again but putting Grub bootloader in the root partition this time whereas before the installer automatically looks for other OS's and suggests putting bootloader in MBR as default.  After reboot, I got:

1. Same error message as before but this time it's udev[90] and the letter "u" is blinking.

2.  After 2-3 minutes, I see Ubuntu 11.10 and plymouth, ie. round dots changing color.

3. Another screen message: "Disk drive for / is not ready yet or is not present.  Continue to wait, or press S to skip mounting, or M for manual recovery".

4. I pressed M, got "root filesystem check failed, a maintenance shell will now be started".

I rebooted, then got nothing but "Input not supported"

When I first reloaded the CD today, I saw and tried the rescue mode option but did not know how to work it.

---

### Post by dino99 on 2011-07-03
for those using gdm, which is not the default choice now, uninstall it and log with lightdm (Oneiric default)

---

### Post by caryb on 2011-07-03
> **dino99 said:**
> for those using gdm, which is not the default choice now, uninstall it and log with lightdm (Oneiric default)

I am getting the same with KDM ???

Cary

---

### Post by garvinrick4 on 2011-07-03
I actually did not have a theme installed, had lightdm installed of course was using gdm
when had to switch to lightdm needed to install a theme. Always something so simple:
rick@rick-HP:~$ aptitude show lightdm-greeter
No current or candidate version found for lightdm-greeter
Package: lightdm-greeter
State: not a real package
Provided by: lightdm-greeter-example-gtk, lightdm-greeter-example-python-gtk,
             lightdm-greeter-example-qt, lightdm-greeter-example-vala-gtk

As per Warning in lightdm.log below:
```

[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 0.4.1, UID=0 PID=1917
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.01s] DEBUG: Loading display seat-0
[+0.01s] DEBUG: Logging to /var/log/lightdm/:0.log
[+0.01s] DEBUG: Starting on /dev/tty1
[+0.01s] DEBUG: Writing X server authorization to /var/run/lightdm/authority/0
[+0.01s] DEBUG: Launching X Server
[+0.01s] DEBUG: Launching process 1921: /usr/bin/X :0 -auth /var/run/lightdm/authority/0 -nolisten tcp vt1
[+0.01s] DEBUG: Waiting for ready signal from X server :0
[+0.23s] DEBUG: Got signal 10 from process 1921
[+0.23s] DEBUG: Got signal from X server :0
[+0.23s] DEBUG: Connecting to XServer :0
[+0.24s] DEBUG: Looking for example-gtk-gnome theme in /usr/share/lightdm/themes/example-gtk-gnome/index.theme
[+0.24s] WARNING: Failed to find theme example-gtk-gnome: No such file or directory
[+57.13s] DEBUG: Got signal 15 from process 1
[+57.13s] DEBUG: Caught Terminated signal, shutting down
[+57.13s] DEBUG: Stopping display manager
[+57.13s] DEBUG: Stopping display
[+57.13s] DEBUG: Sending signal 15 to process 1921
[+57.16s] DEBUG: Process 1921 exited with return value 0
[+57.16s] DEBUG: Display stopped
[+57.16s] DEBUG: Display manager stopped
[+57.16s] DEBUG: All processes complete, exiting

```

---

### Post by iClouseau88 on 2011-07-03
Hi everyone,

I simply re-installed June 13 build and placed Grub bootloader in the root partition. Now my Ubuntu is up to date.  A few occasional updates between now and October release should be OK; no need for frequent disc burning and installation of daily-built iso's.

:)

---

### Post by cariboo on 2011-07-03
> **iClouseau88 said:**
> Hi everyone,

I simply re-installed June 13 build and placed Grub bootloader in the root partition. Now my Ubuntu is up to date.  A few occasional updates between now and October release should be OK; no need for frequent disc burning and installation of daily-built iso's.

:)

October is a long ways away, there is still plenty of time to break your install doing at minimum daily updates. I did a fresh instatll back in May, what I had after daily updates, ended up being nothing like the fresh install I did last week.

With the amount of changes Oneiric is going through, the desktop is pretty well a moving target that is bound to change without notice for some time to come.

---

### Post by williejones on 2011-07-03
> **cariboo907 said:**
> October is a long ways away, there is still plenty of time to break your install doing at minimum daily updates. I did a fresh instatll back in May, what I had after daily updates, ended up being nothing like the fresh install I did last week.

With the amount of changes Oneiric is going through, the desktop is pretty well a moving target that is bound to change without notice for some time to come.

I have 2 usb installs, one Natty--changed sources to Oneiric, the other is the alpha install.  Both look and act different.

---

### Post by donniezazen on 2011-07-03
This bugs seems to affect all ISOs i have downloaded so far. Is their any workaround. I just can't install a fresh system. I use amd64 version.

---

### Post by klim8 on 2011-07-04
> **williejones said:**
> I have 2 usb installs, one Natty--changed sources to Oneiric, the other is the alpha install.  Both look and act different.

How are they different?

---

### Post by teachop on 2011-07-04
> **soham_1207 said:**
> This bugs seems to affect all ISOs i have downloaded so far. Is their any workaround. I just can't install a fresh system. I use amd64 version.
Ditto.  Oneiric Xubuntu testing from the daily... doesn't boot.  Hope the problem is resolved before the Alpha this week.

---

### Post by garvinrick4 on 2011-07-04
> Ditto.  Oneiric Xubuntu testing from the daily... doesn't boot.  Hope the problem is resolved before the Alpha this week
What does /var/log/lightdm/lighdm.log say?
Look at dino99 posts, if you were not using lightdm I had to install a lightdm theme and 
use lightdm instead of gdm. Now boots fine, Title line has nothing to do with problem as I
understand it.

---

### Post by donniezazen on 2011-07-04
> **garvinrick4 said:**
> What does /var/log/lightdm/lighdm.log say?
Look at dino99 posts, if you were not using lightdm I had to install a lightdm theme and 
use lightdm instead of gdm. Now boots fine, Title line has nothing to do with problem as I
understand it.

How can i check lightdm.log and use lightdm on live ISO? I do not see any command prompt. Ctrl+Alt+F1 is where i am i can't type or do anything. Ctrl+Alt+F7 takes me to blank screen.

---

### Post by garvinrick4 on 2011-07-05
> How can i check lightdm.log and use lightdm on live ISO? I do not see  any command prompt. Ctrl+Alt+F1 is where i am i can't type or do  anything. Ctrl+Alt+F7 takes me to blank screen.
I would think maybe a USB install with persistence and when you choose Try Ubuntu to boot
there would be a log of why it would not boot. Could mount in /mnt from a working system to
read logs.
Or will it install a file system to a test partition and can use chroot or mount in /mnt to look
at logs. 
But if you just have some CD's burned that will not install or boot I got nothing to help that
you are right. If you cannot get to a tty then I imagine it is a lot more than gdm or lightdm.

---

### Post by donniezazen on 2011-07-05
> **garvinrick4 said:**
> I would think maybe a USB install with persistence and when you choose Try Ubuntu to boot
there would be a log of why it would not boot. Could mount in /mnt from a working system to
read logs.
Or will it install a file system to a test partition and can use chroot or mount in /mnt to look
at logs. 
But if you just have some CD's burned that will not install or boot I got nothing to help that
you are right. If you cannot get to a tty then I imagine it is a lot more than gdm or lightdm.

I made a persistent Live USB of Jul 5th ISO. Ran it and how exactly do i get the logs? I don't know how to mount it as a filesystem. Mounting it as it is gets me same thing what is in usb drive.

---

### Post by garvinrick4 on 2011-07-05
Boot into USB drive, if it does not boot. Reboot into HDD and then:
You can mount USB in /mnt
```
sudo mount /dev/sdb1 /mnt 
```
sdb1 being your output of "sudo fdisk -l" (lower case L)
Open your file system and open /mnt and another file system is in there, is USB file system.
Will have logs of the attempted boot.
```
sudo umount /mnt
```
Above when done with file system in /mnt

---

### Post by donniezazen on 2011-07-05
> **garvinrick4 said:**
> Boot into USB drive, if it does not boot. Reboot into HDD and then:
You can mount USB in /mnt
```
sudo mount /dev/sdb1 /mnt 
```
sdb1 being your output of "sudo fdisk -l" (lower case L)
Open your file system and open /mnt and another file system is in there, is USB file system.
Will have logs of the attempted boot.
```
sudo umount /mnt
```
Above when done with file system in /mnt

> donnie@donnie-laptop:~$ sudo mount /dev/sdb1 /mnt
donnie@donnie-laptop:~$ cd /mnt
donnie@donnie-laptop:/mnt$ ls
autorun.inf  boot  casper  casper-rw  dists  efi  install  ldlinux.sys  md5sum.txt  pics  pool  preseed  README.diskdefines  syslinux  wubi.exe


That's what i said before. Mounting as it is will get me same thing that is in usb drive not a live file system where i can get into /var/logs.

---

### Post by garvinrick4 on 2011-07-05
> autorun.inf  boot  casper  casper-rw  dists  efi  install  ldlinux.sys   md5sum.txt  pics  pool  preseed  README.diskdefines  syslinux  wubi.exe 			 		
You are right there anything with Casper does not make a readable filesystem I gave you
the instructions to mount a install not a Live USB install.
> I would think maybe a USB install with persistence and when you choose Try Ubuntu to boot there would be a log of why it would not boot. Could mount in /mnt from a working system to read logs.
I am sorry I should have left out the word "persistence" that really does mean a "casper install with persistance".

---

### Post by donniezazen on 2011-07-07
No luck with Alpha 2.

---

### Post by k1n3t on 2011-07-07
I upgraded from Ubuntu 11.04 to 11.10 and it gives me this error: Udev[57]: error: runtime directory `/run/udev´ not writable, for now falling back to `/dev/.udev´.
 no usplash on screen and also I get the applets did not seem to want to know if I can help

---

### Post by seeker5528 on 2011-07-07
> **k1n3t said:**
> I upgraded from Ubuntu 11.04 to 11.10 and it gives me this error: Udev[57]: error: runtime directory `/run/udev´ not writable, for now falling back to `/dev/.udev´.
 no usplash on screen and also I get the applets did not seem to want to know if I can help

The udev thing is is just informational, telling you one directory is not available so it's going to use another. The one that's not available is one the devs want to transition to using, but we are not there yet, the one it's falling back to is the one that has been used for several years.

That's not necessarily saying there is not some udev related problem, but if there is it is not being indicated by that message.

Don't know about usplash, with plymouth I have one machine where it generally works another where it works a little more intermittently. 

Don't know what you are saying with "also I get the applets did not seem to want to know if I can help", is that in relation to something else that's coming up later?

Later, Seeker

---

### Post by teachop on 2011-07-07
> **soham_1207 said:**
> No luck with Alpha 2.
Same.  Alpha 2 Xubuntu doesn't boot from USB.

---

### Post by donniezazen on 2011-07-07
How did it pass ISO testing when it isn't booting at all? Has someone filed a bug? If not I will do it later today.

---

### Post by garvinrick4 on 2011-07-08
Here is the link for known issues if helps anyone:
[https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha2#Known_issues](https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha2#Known_issues)

[B]Known issues
[/B]

 As is to be expected, at this **very early**  stage of the release process, there are some significant known bugs  that users may run into with the Oneiric Alpha 2 Release.  The ones we  know about at this point (and some of the workarounds), are documented  here so you don't need to spend time reporting these bugs again:  
 
**Boot, installation and post-install**

 
[LIST]
[*]Many  CD images are oversized and do not fit on a standard 700 MB CD. Please  burn the images onto a DVD, or use usb-creator to put them onto an USB  stick.  This will be fixed by the first Beta release.
[*]usb-creator is currently unable to create EFI-bootable USB sticks. ([702283]("https://bugs.launchpad.net/bugs/702283"))
[*]In some cases, booting the live system takes a long time until the desktop starts. ([791139]("https://bugs.launchpad.net/bugs/791139"))
[*]A  gnome-settings-daemon crash report will pop up in the live system  unless you selected "Try Ubuntu without installing" in the boot menu.  This crash is harmless and does not break the live system or  installation.
[*]Shutdown  in the live session sometimes does not work and seems to just hang on  the desktop. Just restart the computer with the power button in that  case, there is no possibility of data loss. ([805906]("https://bugs.launchpad.net/bugs/805906")) If shutdown does work properly, the "please press Enter to shutdown" message is hard to read. ([806082]("https://bugs.launchpad.net/bugs/806082"))
[*]Configuring autologin in the OEM setup screen does not work. ([806247]("https://bugs.launchpad.net/bugs/806247"))
[*]OEM  mode installation will fail if there is no network available. As a  workaround, please ensure you have an internet connection for  installation in this mode. ([806349]("https://bugs.launchpad.net/bugs/806349"))
[*]When  overwriting an existing installation in the Ubiquity desktop installer,  it creates a new swap partition instead of re-using the already  existing one. ([782507]("https://bugs.launchpad.net/bugs/782507"))
[*]Ubiquity  desktop installer proceeds to use free space without warning, if  sufficient free space exists, and "install alongside" is selected, then  clicking on the forward button just begins the installation without  warning. ([766265]("https://bugs.launchpad.net/bugs/766265"))
[*]During boot there is a warning message about "/run/udev not writable". This is harmless and can be ignored. ([784216]("https://bugs.launchpad.net/bugs/784216"))
[*]ARM  Desktop installations sometimes crash during the OEM configuration step  or upgrades, due to a race condition in flash-kernel. ([779410]("https://bugs.launchpad.net/bugs/779410"))
[/LIST]

---

### Post by donniezazen on 2011-07-08
> **garvinrick4 said:**
> Here is the link for known issues if helps anyone:
[https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha2#Known_issues](https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha2#Known_issues)

[B]Known issues
[/B]

 As is to be expected, at this **very early**  stage of the release process, there are some significant known bugs  that users may run into with the Oneiric Alpha 2 Release.  The ones we  know about at this point (and some of the workarounds), are documented  here so you don't need to spend time reporting these bugs again:  
 
**Boot, installation and post-install**

 
[LIST]
[*]Many  CD images are oversized and do not fit on a standard 700 MB CD. Please  burn the images onto a DVD, or use usb-creator to put them onto an USB  stick.  This will be fixed by the first Beta release.
[*]usb-creator is currently unable to create EFI-bootable USB sticks. ([702283]("https://bugs.launchpad.net/bugs/702283"))
[*]In some cases, booting the live system takes a long time until the desktop starts. ([791139]("https://bugs.launchpad.net/bugs/791139"))
[*]A  gnome-settings-daemon crash report will pop up in the live system  unless you selected "Try Ubuntu without installing" in the boot menu.  This crash is harmless and does not break the live system or  installation.
[*]Shutdown  in the live session sometimes does not work and seems to just hang on  the desktop. Just restart the computer with the power button in that  case, there is no possibility of data loss. ([805906]("https://bugs.launchpad.net/bugs/805906")) If shutdown does work properly, the "please press Enter to shutdown" message is hard to read. ([806082]("https://bugs.launchpad.net/bugs/806082"))
[*]Configuring autologin in the OEM setup screen does not work. ([806247]("https://bugs.launchpad.net/bugs/806247"))
[*]OEM  mode installation will fail if there is no network available. As a  workaround, please ensure you have an internet connection for  installation in this mode. ([806349]("https://bugs.launchpad.net/bugs/806349"))
[*]When  overwriting an existing installation in the Ubiquity desktop installer,  it creates a new swap partition instead of re-using the already  existing one. ([782507]("https://bugs.launchpad.net/bugs/782507"))
[*]Ubiquity  desktop installer proceeds to use free space without warning, if  sufficient free space exists, and "install alongside" is selected, then  clicking on the forward button just begins the installation without  warning. ([766265]("https://bugs.launchpad.net/bugs/766265"))
[*]During boot there is a warning message about "/run/udev not writable". This is harmless and can be ignored. ([784216]("https://bugs.launchpad.net/bugs/784216"))
[*]ARM  Desktop installations sometimes crash during the OEM configuration step  or upgrades, due to a race condition in flash-kernel. ([779410]("https://bugs.launchpad.net/bugs/779410"))
[/LIST]

I don't know if this bug is related to /run/udev. This is a very harmful bug which i have seen starting Alpha 1. None of the images for past month booted. But if you say so, i will wait and not report it.

---

### Post by garvinrick4 on 2011-07-08
> I don't know if this bug is related to /run/udev. This is a very harmful  bug which i have seen starting Alpha 1. None of the images for past  month booted. But if you say so, i will wait and not report it.
The image I burned today booted and installed Unity but am having a bit of trouble with Gnome 3 as of last 2 or 3 days, running all kernel drivers.

---

