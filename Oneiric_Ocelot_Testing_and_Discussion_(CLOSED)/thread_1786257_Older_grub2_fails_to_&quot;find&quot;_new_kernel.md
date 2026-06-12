---
title: "Older grub2 fails to &quot;find&quot; new kernel ???"
date: 2011-06-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-06-19
I may not have time to fully pursue what's going on with this for a day or two (due to moving my computer equipment to a new room) but thought I should mention it.

I was using Lubuntu Oneiric this AM and installed the following updates:

```
Start-Date: 2011-06-19  07:37:37
Commandline: /usr/sbin/synaptic
Install: linux-headers-3.0-1:i386 (3.0-1.2, automatic), linux-headers-3.0-1-generic:i386 (3.0-1.2, automatic), xdiagnose:i386 (0.6, automatic), linux-image-3.0-1-generic:i386 (3.0-1.2), libllvm2.9:i386 (2.9+dfsg-1, automatic)
Upgrade: xserver-xorg:i386 (7.6+4ubuntu3, 7.6+7ubuntu1), libgtk2.0-common:i386 (2.24.4-0ubuntu3, 2.24.5-0ubuntu1), libatk1.0-0:i386 (2.0.0-1ubuntu1, 2.0.1-0ubuntu1), python-lazr.restfulclient:i386 (0.11.2-2, 0.11.2-2ubuntu1), liblaunchpad-integration1:i386 (0.1.53, 0.1.54), libswscale1:i386 (0.7~beta2-2ubuntu1, 0.7~rc1-1ubuntu1), libstdc++6:i386 (4.6.0-11ubuntu2, 4.6.0-14ubuntu1), libxfixes3:i386 (5.0-2ubuntu1, 5.0-4), libnih-dbus1:i386 (1.0.3-4ubuntu1, 1.0.3-4ubuntu2), libzbar0:i386 (0.10+doc-4ubuntu3, 0.10+doc-6), libnm-glib-vpn1:i386 (0.8.9997-1ubuntu2, 0.8.9997+git.20110614t173923.b4a72d1-0ubuntu1), libegl1-mesa:i386 (7.10.2-0ubuntu2, 7.10.3-0ubuntu3), libgail18:i386 (2.24.4-0ubuntu3, 2.24.5-0ubuntu1), libavutil51:i386 (0.7~beta2-2ubuntu1, 0.7~rc1-1ubuntu1), update-manager:i386 (0.151.4, 0.151.5), libegl1-mesa-drivers:i386 (7.10.2-0ubuntu2, 7.10.3-0ubuntu3), libutouch-grail1:i386 (1.0.20-0ubuntu4, 2.0.0-0ubuntu1), gir1.2-gtk-2.0:i386 (2.24.4-0ubuntu3, 2.24.5-0ubuntu1), gir1.2-gtk-3.0:i386 (3.0.11-0ubuntu1, 3.1.6-0ubuntu3), linux-headers-generic:i386 (2.6.39.3.4, 3.0.0.1.2), libgtksourceview-3.0-0:i386 (3.0.3-1, 3.1.2-0ubuntu1), libsensors4:i386 (3.2.0-1ubuntu1, 3.2.0-1ubuntu3), xserver-xorg-video-all:i386 (7.6+4ubuntu3, 7.6+7ubuntu1), python-debian:i386 (0.1.18ubuntu2, 0.1.20ubuntu1), libcupscgi1:i386 (1.4.6-8, 1.4.6-9), xchat-common:i386 (2.8.8-3ubuntu5, 2.8.8-3ubuntu6), ubuntu-standard:i386 (1.227, 1.230), network-manager:i386 (0.8.9997-1ubuntu2, 0.8.9997+git.20110614t173923.b4a72d1-0ubuntu1), gir1.2-gdkpixbuf-2.0:i386 (2.23.3-0ubuntu3, 2.23.4-0ubuntu1), libx11-data:i386 (1.4.3-1ubuntu1, 1.4.3-2ubuntu1), ubufox:i386 (0.9.1-0ubuntu2, 1.0~a1-0ubuntu1), libsvga1:i386 (1.4.3-30ubuntu1, 1.4.3-31), update-manager-core:i386 (0.151.4, 0.151.5), xchat:i386 (2.8.8-3ubuntu5, 2.8.8-3ubuntu6), linux-image-generic:i386 (2.6.39.3.4, 3.0.0.1.2), libburn4:i386 (1.0.6.pl00-1, 1.0.6.pl00-2), libxxf86vm1:i386 (1.1.1-1ubuntu1, 1.1.1-2), libgstfarsight0.10-0:i386 (0.0.26-1ubuntu1, 0.0.29-1ubuntu1), xterm:i386 (268-1ubuntu1, 270-1ubuntu1), gedit:i386 (3.0.4-0ubuntu2, 3.0.5-0ubuntu1), libnm-util2:i386 (0.8.9997-1ubuntu2, 0.8.9997+git.20110614t173923.b4a72d1-0ubuntu1), gtk2-engines-pixbuf:i386 (2.24.4-0ubuntu3, 2.24.5-0ubuntu1), libaiksaurusgtk-1.2-0c2a:i386 (1.2.1+dev-0.12-6build3, 1.2.1+dev-0.12-6.1), grub2-common:i386 (1.99-4ubuntu2, 1.99-7ubuntu1), libglu1-mesa:i386 (7.10.2-0ubuntu2, 7.10.3-0ubuntu3), xserver-xorg-input-mouse:i386 (1.7.0-2, 1.7.0-4), cups-client:i386 (1.4.6-8, 1.4.6-9), libieee1284-3:i386 (0.2.11-7, 0.2.11-9), libcupsmime1:i386 (1.4.6-8, 1.4.6-9), logrotate:i386 (3.7.8-6ubuntu3, 3.7.8-6ubuntu4), xserver-common:i386 (1.10.1-1ubuntu3, 1.10.2-1ubuntu1), libaiksaurus-1.2-0c2a:i386 (1.2.1+dev-0.12-6build3, 1.2.1+dev-0.12-6.1), libpostproc52:i386 (0.7~beta2-2ubuntu1, 0.7~rc1-1ubuntu1), xserver-xorg-video-vesa:i386 (2.3.0-5, 2.3.0-7), apt-xapian-index:i386 (0.41ubuntu7, 0.43ubuntu1), libx11-xcb1:i386 (1.4.3-1ubuntu1, 1.4.3-2ubuntu1), module-init-tools:i386 (3.13-1ubuntu1, 3.16-1ubuntu1), gir1.2-atk-1.0:i386 (2.0.0-1ubuntu1, 2.0.1-0ubuntu1), gir1.2-gtksource-3.0:i386 (3.0.3-1, 3.1.2-0ubuntu1), libparted0debian1:i386 (2.3-5ubuntu6, 2.3-6ubuntu1), xdg-user-dirs:i386 (0.13-2ubuntu2, 0.14-0ubuntu1), libavformat53:i386 (0.7~beta2-2ubuntu1, 0.7~rc1-1ubuntu1), xserver-xorg-core:i386 (1.10.1-1ubuntu3, 1.10.2-1ubuntu1), parted:i386 (2.3-5ubuntu6, 2.3-6ubuntu1), grub-pc:i386 (1.99-4ubuntu2, 1.99-7ubuntu1), liblaunchpad-integration-common:i386 (0.1.53, 0.1.54), network-manager-gnome:i386 (0.8.9997+git.20110529t170033.9ec4c5d-0ubuntu1, 0.8.9997+git.20110616t193616.b2e6a33-0ubuntu1), cups-ppdc:i386 (1.4.6-8, 1.4.6-9), gedit-common:i386 (3.0.4-0ubuntu2, 3.0.5-0ubuntu1), firefox-globalmenu:i386 (5.0~b5+build1+nobinonly-0ubuntu1, 5.0+build1+nobinonly-0ubuntu1), libgtk-3-common:i386 (3.0.11-0ubuntu1, 3.1.6-0ubuntu3), libgcc1:i386 (4.6.0-11ubuntu2, 4.6.0-14ubuntu1), libcupsppdc1:i386 (1.4.6-8, 1.4.6-9), libvte-2.90-9:i386 (0.28.0-1ubuntu3, 0.28.1-1ubuntu1), firefox:i386 (5.0~b5+build1+nobinonly-0ubuntu1, 5.0+build1+nobinonly-0ubuntu1), locales:i386 (2.13+git20100825-4, 2.13+git20110617-1), cups-common:i386 (1.4.6-8, 1.4.6-9), libpango1.0-0:i386 (1.28.4-0ubuntu1, 1.28.4-0ubuntu2), xserver-xorg-input-all:i386 (7.6+4ubuntu3, 7.6+7ubuntu1), libcups2:i386 (1.4.6-8, 1.4.6-9), libsigc++-2.0-0c2a:i386 (2.2.4.2-1ubuntu1, 2.2.9-1), libaiksaurus-1.2-data:i386 (1.2.1+dev-0.12-6build3, 1.2.1+dev-0.12-6.1), libgtk-3-0:i386 (3.0.11-0ubuntu1, 3.1.6-0ubuntu3), libgtk2.0-bin:i386 (2.24.4-0ubuntu3, 2.24.5-0ubuntu1), libxft2:i386 (2.2.0-2ubuntu2, 2.2.0-3ubuntu1), launchpad-integration:i386 (0.1.53, 0.1.54), python-vte:i386 (0.28.0-1ubuntu3, 0.28.1-1ubuntu1), unattended-upgrades:i386 (0.72.1ubuntu1, 0.72.3), libnm-glib4:i386 (0.8.9997-1ubuntu2, 0.8.9997+git.20110614t173923.b4a72d1-0ubuntu1), libvte9:i386 (0.28.0-1ubuntu3, 0.28.1-1ubuntu1), lm-sensors:i386 (3.2.0-1ubuntu1, 3.2.0-1ubuntu3), dpkg:i386 (1.16.0~ubuntu8, 1.16.0.3ubuntu2), flashplugin-installer:i386 (10.3.181.22ubuntu1, 10.3.181.26ubuntu1), gir1.2-pango-1.0:i386 (1.28.4-0ubuntu1, 1.28.4-0ubuntu2), libgail-3-0:i386 (3.0.11-0ubuntu1, 3.1.6-0ubuntu3), ubuntu-minimal:i386 (1.227, 1.230), cups:i386 (1.4.6-8, 1.4.6-9), libgtksourceview-3.0-common:i386 (3.0.3-1, 3.1.2-0ubuntu1), gcc-4.6-base:i386 (4.6.0-11ubuntu2, 4.6.0-14ubuntu1), ntp:i386 (4.2.6.p2+dfsg-1ubuntu7, 4.2.6.p2+dfsg-1ubuntu8), libcupsdriver1:i386 (1.4.6-8, 1.4.6-9), libglib2.0-data:i386 (2.29.6-0ubuntu4, 2.29.8-0ubuntu1), gnome-user-guide:i386 (3.0.0+git20110406ubuntu9, 3.0.0+git20110406ubuntu10), libatk1.0-data:i386 (2.0.0-1ubuntu1, 2.0.1-0ubuntu1), libasyncns0:i386 (0.8-0ubuntu2, 0.8-2), grub-pc-bin:i386 (1.99-4ubuntu2, 1.99-7ubuntu1), xul-ext-ubufox:i386 (0.9.1-0ubuntu2, 1.0~a1-0ubuntu1), libgdome2-cpp-smart0c2a:i386 (0.2.6-5ubuntu3, 0.2.6-6), gnome-icon-theme:i386 (3.0.0-2ubuntu2, 3.0.0-2ubuntu3), libgdk-pixbuf2.0-0:i386 (2.23.3-0ubuntu3, 2.23.4-0ubuntu1), libgl1-mesa-dri:i386 (7.10.2-0ubuntu2, 7.10.3-0ubuntu3), dpkg-repack:i386 (1.33ubuntu2, 1.34ubuntu1), libexo-1-0:i386 (0.6.1-1, 0.6.2-1), libnl1:i386 (1.1-6, 1.1-6ubuntu1), libglib2.0-0:i386 (2.29.6-0ubuntu4, 2.29.8-0ubuntu1), libcupsimage2:i386 (1.4.6-8, 1.4.6-9), libavcodec53:i386 (0.7~beta2-2ubuntu1, 0.7~rc1-1ubuntu1), x11-common:i386 (7.6+4ubuntu3, 7.6+7ubuntu1), libgl1-mesa-glx:i386 (7.10.2-0ubuntu2, 7.10.3-0ubuntu3), libx11-6:i386 (1.4.3-1ubuntu1, 1.4.3-2ubuntu1), gir1.2-vte-2.90:i386 (0.28.0-1ubuntu3, 0.28.1-1ubuntu1), xorg:i386 (7.6+4ubuntu3, 7.6+7ubuntu1), ntpdate:i386 (4.2.6.p2+dfsg-1ubuntu7, 4.2.6.p2+dfsg-1ubuntu8), rsyslog:i386 (4.6.4-2ubuntu4, 5.8.1-1ubuntu1), libgtkmathview0c2a:i386 (0.8.0-6ubuntu3, 0.8.0-7), cpp-4.6:i386 (4.6.0-11ubuntu2, 4.6.0-14ubuntu1), libgtk-3-bin:i386 (3.0.11-0ubuntu1, 3.1.6-0ubuntu3), grub-common:i386 (1.99-4ubuntu2, 1.99-7ubuntu1), libxi6:i386 (1.4.1-1ubuntu3, 1.4.3-3ubuntu1), libxt6:i386 (1.1.1-1ubuntu1, 1.1.1-2), libvte-common:i386 (0.28.0-1ubuntu3, 0.28.1-1ubuntu1), linux-generic:i386 (2.6.39.3.4, 3.0.0.1.2), libexo-common:i386 (0.6.1-1, 0.6.2-1), liblaunchpad-integration-3.0-1:i386 (0.1.53, 0.1.54), libgtk2.0-0:i386 (2.24.4-0ubuntu3, 2.24.5-0ubuntu1), libnih1:i386 (1.0.3-4ubuntu1, 1.0.3-4ubuntu2), python-httplib2:i386 (0.6.0-5, 0.7.0-1), less:i386 (443-1, 444-1), python-gobject:i386 (2.28.4-1, 2.28.6-1), python-gobject-cairo:i386 (2.28.4-1, 2.28.6-1)
End-Date: 2011-06-19  07:46:48
```

It's on my sda15 but when I booted into the OS that controls boot (with grub version 1.98+20100804-5ubuntu3) it doesn't show up:

> lance@lance-desktop:~$ sudo update-grub
[sudo] password for lance: 
Generating grub.cfg ...
Found background image: desktop-grub.png
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-9-generic
Found initrd image: /boot/initrd.img-2.6.38-9-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found linux image: /boot/vmlinuz-2.6.38-7-generic
Found initrd image: /boot/initrd.img-2.6.38-7-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found Ubuntu 11.04 (11.04) on /dev/sda1
Found Ubuntu oneiric (development branch) (11.10) on /dev/sda10
Found Debian GNU/Linux (6.0.1) on /dev/sda11
Found Peppermint Two (2) on /dev/sda12
Found Ubuntu oneiric (development branch) (11.10) on /dev/sda13
Found Ubuntu 11.04 (11.04) on /dev/sda16
Found Ubuntu 11.04 (11.04) on /dev/sda17
Found Ubuntu 10.10 (10.10) on /dev/sda2
Found Ubuntu 10.04.2 LTS (10.04) on /dev/sda3
Found Ubuntu 11.04 (11.04) on /dev/sdb1
done

I'll explore a bit until the folks show up to help me move stuff :D

---

### Post by kansasnoob on 2011-06-19
Well, I used a chroot to transfer booting to that Lubuntu's grub2 and it boots fine, so it seems that older versions of grub2 may not recognize or boot the newest kernel :confused:

No doubt this will take some studying to figure out ;)

Let the fun begin.

---

### Post by kansasnoob on 2011-06-19
This is an odd mess. The OS I was using to boot was Natty but I'd downgraded to Maverick grub as explained here:

[http://ubuntuforums.org/showpost.php?p=10778491&postcount=55](http://ubuntuforums.org/showpost.php?p=10778491&postcount=55)

Other Natty's seem OK with this change as do other Mavericks, And it appears to be a forward and/or backward thing. What I mean by that is Oneirics grub doesn't want to recognize the Natty with Maverick's grub installed.

Odd, eh?

Good time to have this disc:

[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

---

### Post by dino99 on 2011-06-20
i've never understood, and never will, this mess done by multiple different bootloader versions installed together on a single machine; seems that those devs only knows how to create complicated design. What is needed: a bootloader dealing with all the installed systems, but not dependent to a system, so it needs a boot partition and act as a system itself. GAG is a good example and not the only one.

---

### Post by kansasnoob on 2011-06-20
Well, this makes no real sense to me.

After having booted into the new kernel once the grub that wouldn't find it now does:

> Generating grub.cfg ...
Found background image: desktop-grub.png
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-9-generic
Found initrd image: /boot/initrd.img-2.6.38-9-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found linux image: /boot/vmlinuz-2.6.38-7-generic
Found initrd image: /boot/initrd.img-2.6.38-7-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found Ubuntu 11.04 (11.04) on /dev/sda1
Found Ubuntu oneiric (development branch) (11.10) on /dev/sda10
Found Debian GNU/Linux (6.0.1) on /dev/sda11
Found Peppermint Two (2) on /dev/sda12
Found Ubuntu oneiric (development branch) (11.10) on /dev/sda13
Found Ubuntu oneiric (development branch) (11.10) on /dev/sda14
**[COLOR="Red"]Found Ubuntu oneiric (development branch) (11.10) on /dev/sda15[/COLOR]**
Found Ubuntu 11.04 (11.04) on /dev/sda16
Found Ubuntu 11.04 (11.04) on /dev/sda17
Found Ubuntu 10.10 (10.10) on /dev/sda2
Found Ubuntu 10.04.2 LTS (10.04) on /dev/sda3
Found Ubuntu 11.04 (11.04) on /dev/sdb1
done


Maybe something with init not updating properly until after the first boot :confused:

---

