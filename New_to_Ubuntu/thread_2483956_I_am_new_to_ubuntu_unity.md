---
title: "I am new to ubuntu unity"
date: 2023-02-13
forum: New to Ubuntu
---

### Post by taterofwedges on 2023-02-13
If I were to have a problem how do I go to my terminal to copy and paste what's in my computer to help you?

---

### Post by DuckHook on 2023-02-13
Welcome to the forums, taterofwedges

[LIST=1]
[*]To launch a terminal, <Ctrl> + <Alt> + <t>
[*]You can copy any content in the terminal by dragging your mouse over the text to select it, then either right clicking to bring up the copy menu, or with <Shift> + <Ctrl> + <c>
[*]You can then paste into the forum's browser dialogues using the usual mouse menus or keyboard shortcuts.
[/LIST]

---

### Post by MAFoElffen on 2023-02-13
Of course, when posting raw output or commands, go to the "Adv Reply" and use the "#" Icon to wrap that output with CODE Tags...

---

### Post by DuckHook on 2023-02-13
A slightly more sophisticated/geeky way to capture terminal output is to pipe it to a file. You can then use GUI tools like the Text Editor to open it. Some people find this easier, although I find the multiple steps irritating.

Example:```
ls -laH /etc > ~/Documents/etc_listing
```&#8230;produces a file in my Documents directory called etc_listing with the following content:```
total 1364
drwxr-xr-x 147 root root   12288 Feb  9 13:10 .
drwxr-xr-x  22 root root    4096 Feb 11  2022 ..
drwxr-xr-x   3 root root    4096 Apr 15  2022 acpi
-rw-r--r--   1 root root    3028 Oct 12  2021 adduser.conf
drwxr-xr-x   3 root root    4096 Oct 12  2021 alsa
drwxr-xr-x   2 root root    4096 Dec 17 00:13 alternatives
-rw-r--r--   1 root root     335 Oct  7  2021 anacrontab
drwxr-xr-x   3 root root    4096 Feb 11  2022 apache2
-rw-r--r--   1 root root     433 Oct  7  2021 apg.conf
drwxr-xr-x   5 root root    4096 Oct 12  2021 apm
drwxr-xr-x   3 root root    4096 Jul  4  2022 apparmor
drwxr-xr-x   8 root root    4096 Jan 31 09:06 apparmor.d
-----snip------
drwxr-xr-x  12 root root    4096 Apr  4  2022 X11
-rw-r--r--   1 root root     681 Aug 29  2021 xattr.conf
drwxr-xr-x   6 root root    4096 Mar 28  2022 xdg
drwxr-xr-x   2 root root    4096 Mar 24  2022 xml
drwxr-xr-x   4 root root    4096 Jul  4  2022 zfs
```
I posted that by opening up the file with Ubuntu's native GUI editor, gedit, then just copying and pasting in the usual way.

And please post as MAFoElffen advises.

---

### Post by taterofwedges on 2023-02-14
Is this my appropriate terminal output to help you if I had trouble? Thanks for the help guys.

---

### Post by taterofwedges on 2023-02-14
```
total 1204
drwxr-xr-x 138 root root   12288 Feb 14 01:35 .
drwxr-xr-x  20 root root    4096 Jan 29 00:18 ..
drwxr-xr-x   3 root root    4096 Apr 19  2022 acpi
-rw-r--r--   1 root root    3028 Apr 19  2022 adduser.conf
drwxr-xr-x   3 root root    4096 Apr 19  2022 alsa
drwxr-xr-x   2 root root    4096 Jan 17 00:17 alternatives
-rw-r--r--   1 root root     335 Mar 23  2022 anacrontab
drwxr-xr-x   3 root root    4096 Aug  4  2022 apache2
-rw-r--r--   1 root root     433 Mar 23  2022 apg.conf
drwxr-xr-x   5 root root    4096 Apr 19  2022 apm
drwxr-xr-x   3 root root    4096 Aug  4  2022 apparmor
drwxr-xr-x   7 root root    4096 Feb 10 20:11 apparmor.d
drwxr-xr-x   5 root root    4096 Jan 17 02:30 apport
-rw-r--r--   1 root root     769 Feb 22  2022 appstream.conf
drwxr-xr-x   8 root root    4096 Jan 17 00:19 apt
drwxr-xr-x   3 root root    4096 Apr 19  2022 avahi
-rw-r--r--   1 root root    2319 Jan  6  2022 bash.bashrc
-rw-r--r--   1 root root      45 Nov 11  2021 bash_completion
drwxr-xr-x   2 root root    4096 Jan 17 02:30 bash_completion.d
-rw-r--r--   1 root root     367 Dec 16  2020 bindresvport.blacklist
drwxr-xr-x   2 root root    4096 Apr  7  2022 binfmt.d
drwxr-xr-x   2 root root    4096 Apr 19  2022 bluetooth
-rw-r-----   1 root root      33 Apr 19  2022 brlapi.key
drwxr-xr-x   7 root root    4096 Apr 19  2022 brltty
-rw-r--r--   1 root root   29219 Mar 18  2022 brltty.conf
drwxr-xr-x   3 root root    4096 Apr 19  2022 ca-certificates
-rw-r--r--   1 root root    5532 Jan 17 02:29 ca-certificates.conf
-rw-r--r--   1 root root    5529 Apr 19  2022 ca-certificates.conf.dpkg-old
-rw-r--r--   1 root root     119 Jan 10  2022 catdocrc
drwxr-s---   2 root dip     4096 Apr 19  2022 chatscripts
drwxr-xr-x   2 root root    4096 Jan 17 02:29 compizconfig
drwxr-xr-x   2 root root    4096 Jan 17 00:16 console-setup
drwxr-xr-x   2 root root    4096 Apr 19  2022 cracklib
drwxr-xr-x   2 root root    4096 Jan 17 00:18 cron.d
drwxr-xr-x   2 root root    4096 Jan 17 02:30 cron.daily
drwxr-xr-x   2 root root    4096 Apr 19  2022 cron.hourly
drwxr-xr-x   2 root root    4096 Apr 19  2022 cron.monthly
-rw-r--r--   1 root root    1136 Mar 23  2022 crontab
drwxr-xr-x   2 root root    4096 Apr 19  2022 cron.weekly
drwxr-xr-x   5 root lp      4096 Feb 14 01:26 cups
drwxr-xr-x   2 root root    4096 Apr 19  2022 cupshelpers
drwxr-xr-x   4 root root    4096 Apr 19  2022 dbus-1
drwxr-xr-x   4 root root    4096 Apr 19  2022 dconf
-rw-r--r--   1 root root    2969 Feb 20  2022 debconf.conf
-rw-r--r--   1 root root      13 Aug 22  2021 debian_version
drwxr-xr-x   3 root root    4096 Jan 17 02:30 default
-rw-r--r--   1 root root     604 Sep 15  2018 deluser.conf
drwxr-xr-x   2 root root    4096 Apr 19  2022 depmod.d
drwxr-xr-x   4 root root    4096 Jan 17 02:29 dhcp
drwxr-xr-x   2 root root    4096 Jan 17 00:18 dictionaries-common
drwxr-xr-x   3 root root    4096 Aug  4  2022 doc-base
drwxr-xr-x   4 root root    4096 Aug  4  2022 dpkg
-rw-r--r--   1 root root     685 Jan  8  2022 e2scrub.conf
drwxr-xr-x   3 root root    4096 Apr 19  2022 emacs
-rw-r--r--   1 root root     106 Apr 19  2022 environment
drwxr-xr-x   2 root root    4096 Apr 19  2022 environment.d
-rw-r--r--   1 root root    1816 Dec 26  2019 ethertypes
drwxr-xr-x   4 root root    4096 Apr 19  2022 fonts
-rw-r--r--   1 root root      20 Feb 24  2022 fprintd.conf
-rw-r--r--   1 root root     665 Jan 17 00:09 fstab
-rw-r--r--   1 root root     694 Mar 23  2022 fuse.conf
drwxr-xr-x   3 root root    4096 Jan 17 02:30 fwupd
-rw-r--r--   1 root root    2584 Feb  3  2022 gai.conf
drwxr-xr-x   3 root root    4096 Jan 17 02:29 gdb
drwxr-xr-x   2 root root    4096 Aug  4  2022 geoclue
drwxr-xr-x   4 root root    4096 Apr 19  2022 ghostscript
drwxr-xr-x   3 root root    4096 Apr 19  2022 glvnd
drwxr-xr-x   2 root root    4096 Aug  4  2022 gnome
drwxr-xr-x   2 root root    4096 Aug  4  2022 gnome-system-tools
drwxr-xr-x   2 root root    4096 Apr 19  2022 groff
-rw-r--r--   1 root root    1195 Jan 17 02:30 group
-rw-r--r--   1 root root    1174 Jan 17 00:16 group-
drwxr-xr-x   2 root root    4096 Jan 17 02:30 grub.d
-rw-r-----   1 root shadow  1005 Jan 17 02:30 gshadow
-rw-r-----   1 root shadow   987 Jan 17 00:16 gshadow-
drwxr-xr-x   3 root root    4096 Feb 21  2022 gss
drwxr-xr-x   2 root root    4096 Apr 19  2022 gtk-2.0
drwxr-xr-x   2 root root    4096 Aug  4  2022 gtk-3.0
drwxr-xr-x   2 root root    4096 Nov  5  2021 guest-session
-rw-r--r--   1 root root    4436 Dec 15  2020 hdparm.conf
-rw-r--r--   1 root root      92 Oct 15  2021 host.conf
-rw-r--r--   1 root root       4 Apr 19  2022 hostid
-rw-r--r--   1 root root      29 Jan 17 00:16 hostname
-rw-r--r--   1 root root     243 Jan 17 00:16 hosts
-rw-r--r--   1 root root     411 Apr 19  2022 hosts.allow
-rw-r--r--   1 root root     711 Apr 19  2022 hosts.deny
drwxr-xr-x   2 root root    4096 Apr 19  2022 hp
drwxr-xr-x   3 root root    4096 Apr 19  2022 ifplugd
drwxr-xr-x   2 root root    4096 Aug  4  2022 ImageMagick-6
drwxr-xr-x   2 root root    4096 Jan 17 00:18 init
drwxr-xr-x   2 root root    4096 Jan 17 02:30 init.d
drwxr-xr-x   5 root root    4096 Jan 17 02:30 initramfs-tools
-rw-r--r--   1 root root    1748 Jan  6  2022 inputrc
-rw-r--r--   1 root root      71 Feb  9  2017 inxi.conf
drwxr-xr-x   2 root root    4096 Apr 19  2022 ipp-usb
drwxr-xr-x   4 root root    4096 Apr 19  2022 iproute2
-rw-r--r--   1 root root      26 Jul 28  2022 issue
-rw-r--r--   1 root root      19 Jul 28  2022 issue.net
drwxr-xr-x   6 root root    4096 Apr 19  2022 kernel
-rw-r--r--   1 root root     110 Jan 17 00:17 kernel-img.conf
-rw-r--r--   1 root root    1308 Mar 24  2022 kerneloops.conf
drwxr-xr-x   2 root root    4096 Jan 17 02:29 ldap
-rw-r--r--   1 root root   73571 Feb 14 01:35 ld.so.cache
-rw-r--r--   1 root root      34 Dec 16  2020 ld.so.conf
drwxr-xr-x   2 root root    4096 Aug  4  2022 ld.so.conf.d
-rw-r--r--   1 root root     267 Oct 15  2021 legal
-rw-r--r--   1 root root      27 Mar 13  2022 libao.conf
-rw-r--r--   1 root root     191 Mar 17  2022 libaudit.conf
drwxr-xr-x   3 root root    4096 Apr 19  2022 libblockdev
drwxr-xr-x   2 root root    4096 Apr 19  2022 libnl-3
drwxr-xr-x   2 root root    4096 Aug  4  2022 libpaper.d
drwxr-xr-x   3 root root    4096 Jan 17 00:16 libreoffice
drwxr-xr-x   3 root root    4096 Jan 17 00:16 lightdm
drwxr-xr-x   4 root root    4096 Aug  4  2022 lighttpd
-rw-r--r--   1 root root    2996 Mar  3  2022 locale.alias
-rw-r--r--   1 root root    9456 Jan 17 00:16 locale.gen
lrwxrwxrwx   1 root root      36 Jan 17 02:29 localtime -> /usr/share/zoneinfo/America/New_York
drwxr-xr-x   4 root root    4096 Apr 19  2022 logcheck
-rw-r--r--   1 root root   10734 Nov 11  2021 login.defs
-rw-r--r--   1 root root     592 Jan 24  2022 logrotate.conf
drwxr-xr-x   2 root root    4096 Jan 17 02:30 logrotate.d
-rw-r--r--   1 root root     104 Jul 28  2022 lsb-release
-r--r--r--   1 root root      33 Jan 17 00:20 machine-id
-rw-r--r--   1 root root     111 Mar 24  2022 magic
-rw-r--r--   1 root root     111 Mar 24  2022 magic.mime
-rw-r--r--   1 root root   40846 Feb 10 20:12 mailcap
-rw-r--r--   1 root root     449 Dec 10  2021 mailcap.order
-rw-r--r--   1 root root    5217 Mar 17  2022 manpath.config
-rw-r--r--   1 root root   72029 Mar 21  2022 mime.types
-rw-r--r--   1 root root     744 Jan  8  2022 mke2fs.conf
drwxr-xr-x   3 root root    4096 Apr 19  2022 ModemManager
drwxr-xr-x   2 root root    4096 Jan 17 02:29 modprobe.d
-rw-r--r--   1 root root     195 Apr 19  2022 modules
drwxr-xr-x   2 root root    4096 Jan 17 02:28 modules-load.d
lrwxrwxrwx   1 root root      19 Jan 17 00:17 mtab -> ../proc/self/mounts
-rw-r--r--   1 root root   11204 Feb  9  2022 nanorc
-rw-r--r--   1 root root     767 Mar 24  2022 netconfig
drwxr-xr-x   2 root root    4096 Apr 19  2022 netplan
drwxr-xr-x   7 root root    4096 Aug  4  2022 network
drwxr-xr-x   8 root root    4096 Apr 19  2022 networkd-dispatcher
drwxr-xr-x   7 root root    4096 Aug  4  2022 NetworkManager
-rw-r--r--   1 root root      91 Oct 15  2021 networks
drwxr-xr-x   2 root root    4096 Apr 19  2022 newt
-rwxr-xr-x   1 root root     228 Mar 23  2022 nftables.conf
-rw-r--r--   1 root root     542 Jan 17 00:18 nsswitch.conf
drwxr-xr-x   2 root root    4096 Aug  4  2022 openal
drwxr-xr-x   2 root root    4096 Aug  4  2022 openni2
drwxr-xr-x   4 root root    4096 Jan 17 02:28 openvpn
drwxr-xr-x   2 root root    4096 Apr 19  2022 opt
lrwxrwxrwx   1 root root      21 Jan 17 00:10 os-release -> ../usr/lib/os-release
drwxr-xr-x   2 root root    4096 Apr 19  2022 PackageKit
-rw-r--r--   1 root root     552 Aug 11  2020 pam.conf
drwxr-xr-x   2 root root    4096 Feb 10 20:11 pam.d
-rw-r--r--   1 root root       7 Jan 17 00:17 papersize
-rw-r--r--   1 root root    2941 Jan 17 02:30 passwd
-rw-r--r--   1 root root    2920 Jan 17 02:30 passwd-
drwxr-xr-x   2 root root    4096 Apr 19  2022 pcmcia
drwxr-xr-x   4 root root    4096 Aug  4  2022 perl
drwxr-xr-x   4 root root    4096 Apr 19  2022 pki
drwxr-xr-x   3 root root    4096 Apr 19  2022 pm
-rw-r--r--   1 root root    7649 Apr 19  2022 pnm2ppa.conf
drwxr-xr-x   4 root root    4096 Apr 19  2022 polkit-1
drwxr-xr-x   9 root dip     4096 Aug  4  2022 ppp
lrwxrwxrwx   1 root root      18 Jan 17 00:10 printcap -> /run/cups/printcap
-rw-r--r--   1 root root     582 Oct 15  2021 profile
drwxr-xr-x   2 root root    4096 Feb 10 20:11 profile.d
-rw-r--r--   1 root root    2932 Apr  1  2013 protocols
drwxr-xr-x   4 root root    4096 Jan 17 02:30 pulse
-rw-------   1 root root       0 Apr 19  2022 .pwd.lock
drwxr-xr-x   2 root root    4096 Apr 19  2022 python3
drwxr-xr-x   2 root root    4096 Jan 17 02:28 python3.10
drwxr-xr-x   2 root root    4096 Jan 17 00:18 rc0.d
drwxr-xr-x   2 root root    4096 Jan 17 00:18 rc1.d
drwxr-xr-x   2 root root    4096 Jan 17 00:18 rc2.d
drwxr-xr-x   2 root root    4096 Jan 17 00:18 rc3.d
drwxr-xr-x   2 root root    4096 Jan 17 00:18 rc4.d
drwxr-xr-x   2 root root    4096 Jan 17 00:18 rc5.d
drwxr-xr-x   2 root root    4096 Jan 17 00:18 rc6.d
drwxr-xr-x   2 root root    4096 Jan 17 00:18 rcS.d
lrwxrwxrwx   1 root root      39 Jan 17 00:16 resolv.conf -> ../run/systemd/resolve/stub-resolv.conf
lrwxrwxrwx   1 root root      13 Jan 17 00:10 rmt -> /usr/sbin/rmt
-rw-r--r--   1 root root     887 Apr  1  2013 rpc
-rw-r--r--   1 root root    1382 Dec 23  2021 rsyslog.conf
drwxr-xr-x   2 root root    4096 Apr 19  2022 rsyslog.d
drwxr-xr-x   3 root root    4096 Apr 19  2022 sane.d
drwxr-xr-x   4 root root    4096 Feb 10 20:11 security
drwxr-xr-x   2 root root    4096 Apr 19  2022 selinux
-rw-r--r--   1 root root   10593 Mar 31  2022 sensors3.conf
drwxr-xr-x   2 root root    4096 Apr 19  2022 sensors.d
-rw-r--r--   1 root root   12813 Mar 27  2021 services
drwxr-xr-x   3 root root    4096 Apr 19  2022 sgml
-rw-r-----   1 root shadow  1465 Jan 17 02:30 shadow
-rw-r-----   1 root shadow  1465 Jan 17 02:30 shadow-
-rw-r--r--   1 root root     128 Apr 19  2022 shells
drwxr-xr-x   2 root root    4096 Aug  4  2022 skel
drwxr-xr-x   2 root root    4096 Jan 17 02:29 snmp
drwxr-xr-x   4 root root    4096 Jan 17 02:30 speech-dispatcher
drwxr-xr-x   3 root root    4096 Jan 17 02:29 ssh
drwxr-xr-x   4 root root    4096 Feb 10 20:12 ssl
-rw-r--r--   1 root root      27 Jan 17 00:16 subgid
-rw-r--r--   1 root root       0 Apr 19  2022 subgid-
-rw-r--r--   1 root root      27 Jan 17 00:16 subuid
-rw-r--r--   1 root root       0 Apr 19  2022 subuid-
-rw-r--r--   1 root root    4573 Feb 14  2022 sudo.conf
-r--r-----   1 root root    1671 Feb  8  2022 sudoers
drwxr-xr-x   2 root root    4096 Jan 19 07:43 sudoers.d
-rw-r--r--   1 root root    9390 Feb 14  2022 sudo_logsrvd.conf
-rw-r--r--   1 root root    2355 Feb 25  2022 sysctl.conf
drwxr-xr-x   2 root root    4096 Jan 17 02:28 sysctl.d
drwxr-xr-x   5 root root    4096 Jan 17 02:29 systemd
drwxr-xr-x   2 root root    4096 Apr 19  2022 terminfo
drwxr-xr-x   8 root root    4096 Aug  4  2022 texmf
drwxr-xr-x   2 root root    4096 Jan 17 02:29 thermald
drwxr-xr-x   2 root root    4096 Feb 10 20:12 thunderbird
-rw-r--r--   1 root root      17 Jan 17 02:29 timezone
drwxr-xr-x   2 root root    4096 Aug  4  2022 timidity
drwxr-xr-x   2 root root    4096 Apr  7  2022 tmpfiles.d
drwxr-xr-x   2 root root    4096 Jan 17 02:29 ubuntu-advantage
-rw-r--r--   1 root root    1260 Jun 16  2020 ucf.conf
drwxr-xr-x   4 root root    4096 Jan 17 02:29 udev
drwxr-xr-x   2 root root    4096 Apr 19  2022 udisks2
drwxr-xr-x   3 root root    4096 Apr 19  2022 ufw
drwxr-xr-x   3 root root    4096 Jan 17 02:30 update-manager
drwxr-xr-x   2 root root    4096 Jan 17 02:30 update-motd.d
drwxr-xr-x   2 root root    4096 Mar 30  2022 update-notifier
drwxr-xr-x   2 root root    4096 Apr 19  2022 UPower
-rw-r--r--   1 root root    1523 Mar 25  2022 usb_modeswitch.conf
drwxr-xr-x   2 root root    4096 Sep  6  2021 usb_modeswitch.d
-rw-r--r--   1 root root      51 Apr  9  2020 vdpau_wrapper.cfg
drwxr-xr-x   2 root root    4096 Jan 17 02:29 vim
lrwxrwxrwx   1 root root      23 Jan 17 00:10 vtrgb -> /etc/alternatives/vtrgb
drwxr-xr-x   5 root root    4096 Apr 19  2022 vulkan
-rw-r--r--   1 root root    4942 Jan 24  2022 wgetrc
drwxr-xr-x   2 root root    4096 Aug  4  2022 wpa_supplicant
drwxr-xr-x  12 root root    4096 Aug  4  2022 X11
-rw-r--r--   1 root root     681 Mar 23  2022 xattr.conf
drwxr-xr-x   6 root root    4096 Aug  4  2022 xdg
drwxr-xr-x   2 root root    4096 Apr 19  2022 xml
-rw-r--r--   1 root root     460 Dec  8  2021 zsh_command_not_found
```

---

### Post by Impavidus on 2023-02-14
If you're really lazy, you can also select the text in the terminal, move your mouse to wherever you want to paste it and click the mouse wheel / middle mouse button.

What is appropriate terminal output depends on your problem. If you have some problem, somebody on the forum can suggest a useful command. It's best to include the command that produced the output and sometimes also to show the current working directory.

You correctly copied the terminal output to your forum post. One of our moderators added the [code] tags to get a monospaced font, which makes the columns line up nicely. Try to include those [code] tags yourself next time.

---

### Post by kc1di on 2023-02-14
I usually install a small program named inxi ```
sudo apt install inxi
```
it is run in the terminal and gives a good output of your system.  This can be immensely helpful to those trying to diagnose the problem with any particular machine. 

[See here ]("https://itsfoss.com/inxi-system-info-linux/")for instructions on how to use it. 

Good luck and welcome to Ubuntu. Enjoy the journey! :)

A typical inxi output might look like this
```
$ inxi -Fxxzr
System:
  Kernel: 5.15.0-60-generic x86_64 bits: 64 compiler: gcc v: 11.3.0
    Desktop: GNOME 42.5 tk: GTK 3.24.33 wm: gnome-shell dm: GDM3
    Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: LENOVO product: 20BV000AUS v: ThinkPad T450
    serial: <superuser required> Chassis: type: 10 serial: <superuser required>
  Mobo: LENOVO model: 20BV000AUS v: SDK0E50510 WIN
    serial: <superuser required> UEFI-[Legacy]: LENOVO v: JBET71WW (1.35 )
    date: 09/14/2018
Battery:
  ID-1: BAT0 charge: 16.9 Wh (97.7%) condition: 17.3/23.2 Wh (74.4%)
    volts: 12.3 min: 11.1 model: SANYO 45N1773 serial: <filter>
    status: Not charging
  ID-2: BAT1 charge: 14.6 Wh (100.0%) condition: 14.6/23.2 Wh (63.1%)
    volts: 12.4 min: 11.1 model: SANYO 45N1775 serial: <filter>
    status: Not charging
  Device-1: hidpp_battery_0 model: Logitech Wireless Mouse M325
    serial: <filter> charge: 55% (should be ignored) status: Discharging
CPU:
  Info: dual core model: Intel Core i5-5300U bits: 64 type: MT MCP
    arch: Broadwell rev: 4 cache: L1: 128 KiB L2: 512 KiB L3: 3 MiB
  Speed (MHz): avg: 2295 high: 2296 min/max: 500/2900 cores: 1: 2296
    2: 2295 3: 2295 4: 2294 bogomips: 18357
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3
Graphics:
  Device-1: Intel HD Graphics 5500 vendor: Lenovo driver: i915 v: kernel
    ports: active: eDP-1 empty: DP-1, DP-2, HDMI-A-1, HDMI-A-2 bus-ID: 00:02.0
    chip-ID: 8086:1616
  Device-2: Acer Integrated Camera type: USB driver: uvcvideo bus-ID: 2-8:5
    chip-ID: 5986:0366
  Display: wayland server: X.org v: 1.21.1.3 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: gpu: i915 display-ID: 0
  Monitor-1: eDP-1 model: Chi Mei Innolux res: 1600x900 dpi: 132
    diag: 355mm (14")
  OpenGL: renderer: Mesa Intel HD Graphics 5500 (BDW GT2)
    v: 4.6 Mesa 22.2.5 direct render: Yes
Audio:
  Device-1: Intel Broadwell-U Audio vendor: Lenovo driver: snd_hda_intel
    v: kernel bus-ID: 00:03.0 chip-ID: 8086:160c
  Device-2: Intel Wildcat Point-LP High Definition Audio vendor: Lenovo
    driver: snd_hda_intel v: kernel bus-ID: 00:1b.0 chip-ID: 8086:9ca0
  Sound Server-1: ALSA v: k5.15.0-60-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Ethernet I218-LM vendor: Lenovo driver: e1000e v: kernel
    port: 3080 bus-ID: 00:19.0 chip-ID: 8086:15a2
  IF: enp0s25 state: down mac: <filter>
  Device-2: Intel Wireless 7265 driver: iwlwifi v: kernel pcie:
    speed: 2.5 GT/s lanes: 1 bus-ID: 03:00.0 chip-ID: 8086:095b
  IF: wlp3s0 state: up mac: <filter>
Drives:
  Local Storage: total: 238.47 GiB used: 17.06 GiB (7.2%)
  ID-1: /dev/sda vendor: LITE-ON model: LCH-256V2S size: 238.47 GiB
    speed: 6.0 Gb/s serial: <filter>
Partition:
  ID-1: / size: 36.55 GiB used: 11.31 GiB (30.9%) fs: ext4 dev: /dev/sda1
  ID-2: /home size: 193.15 GiB used: 5.75 GiB (3.0%) fs: ext4
    dev: /dev/sda6
Swap:
  ID-1: swap-1 type: partition size: 3.72 GiB used: 0 KiB (0.0%) priority: -2
    dev: /dev/sda5
Sensors:
  System Temperatures: cpu: 40.0 C pch: 40.5 C mobo: N/A
  Fan Speeds (RPM): fan-1: 0
Repos:
  Packages: 2432 apt: 2423 snap: 9
  Active apt repos in: /etc/apt/sources.list
    1: deb http://us.archive.ubuntu.com/ubuntu/ jammy main restricted
    2: deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates main restricted
    3: deb http://us.archive.ubuntu.com/ubuntu/ jammy universe
    4: deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates universe
    5: deb http://us.archive.ubuntu.com/ubuntu/ jammy multiverse
    6: deb http://us.archive.ubuntu.com/ubuntu/ jammy-updates multiverse
    7: deb http://us.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
    8: deb http://security.ubuntu.com/ubuntu jammy-security main restricted
    9: deb http://security.ubuntu.com/ubuntu jammy-security universe
    10: deb http://security.ubuntu.com/ubuntu jammy-security multiverse
  Active apt repos in: /etc/apt/sources.list.d/gerardpuig-ubuntu-ppa-jammy.list
    1: deb https://ppa.launchpadcontent.net/gerardpuig/ppa/ubuntu/ jammy main
  Active apt repos in: /etc/apt/sources.list.d/slimbook-ubuntu-slimbook-jammy.list
    1: deb https://ppa.launchpadcontent.net/slimbook/slimbook/ubuntu/ jammy main
  Active apt repos in: /etc/apt/sources.list.d/vivaldi.list
    1: deb [arch=amd64] https://repo.vivaldi.com/stable/deb/ stable main
Info:
  Processes: 244 Uptime: 57m Memory: 7.47 GiB used: 2.39 GiB (32.0%)
  Init: systemd v: 249 runlevel: 5 Compilers: gcc: 
```

---

### Post by taterofwedges on 2023-02-15
I am very familiar with inxi and prefer it if the moderators here are okay with that. Thanks everyone I am downloading inxi now.:cool:

---

