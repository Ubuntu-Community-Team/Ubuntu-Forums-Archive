---
title: "Fatal Display problems with jaunty alfa-6."
date: 2009-03-21
forum: Packaging and Compiling Programs
---

### Post by TDFlanders on 2009-03-21
Hi, I experienced fatal display problems with alfa 6.

Due to the forum bug, I could not place this post under Jaunty Jackalope Testing & Discussion, please relocate.

[https://bugs.launchpad.net/ubuntuforums.org/+bug/315181](https://bugs.launchpad.net/ubuntuforums.org/+bug/315181)

I could upgrade to jaunty through #root update-manager -d. After that update-manager until no more change. Then software-properties-gtk updates restricted and backports, + virtualbox and dbgsym landscape and skype (everything open really). Then update-manager -c until no more change.

After reboot I experienced a fatal display issue, which is not just gdm. If it was I should have been able to just wait, and provide username and password. Also ctrl+alt+del or ctrl+alt+F12 or ctrl+alt+F or ctrl+alt+backapace or ctrl+alt+F5/F10 did do absolutely nothing. When pessing the numlock key the light did not light up.

I tried recovery mode xfix to no avail, dpkg-reconfigure same thing. fsck indicate file system errors. I had this efore, when manipulating with jaunty, suddenly the filesystem becomes corrupted, for no reason. I did not format, upgrade ext3 to ext4 or anything.

Anyway, went down to root terminal. dpkg-reconfigure -aup low Had a problem with cpufreqd, it stuck, could not find a file. I aborted and rebooted and did apt-get remove cpufreqd. Now I could complete dpkg-reconfigure -aup low. I als tried dpkg-reconfigure -p low gdm and same thing for xserver-org, to alter some opions. Nothing works. Still gdm tells me: failed to reload something. I have not taken a look in fstab nor mtab.

I think this issue could be the xorg problem with acer aspires (at least 5050 and 9410), were the VGA graphical accelerator alters something in the BIOS. owever, this time I could not fix the problem by reflashing the BIOS in Windows and reinstalling the VGA driver. So is this something else?

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/323694](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/323694)

Note that I mentioned openoffice.org in the descriptions, as faulty permissions seemed related at that time. (virus?)

Anyway,

won't be able to beta-test like that.

---

### Post by TDFlanders on 2009-03-29
Confirmed in beta, 8.10 works fine, ubuntu 9.04 beta is unbootable because of /dev/agapart does not exist. update-initramfs fails on 2.6.28-11.

---

### Post by TDFlanders on 2009-04-01
Seems to be solved now in beta.

---

### Post by TDFlanders on 2009-04-04
Correction:

problem still occurs after dpkg-reconfigure -au and accepting all the defaults.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354532](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/354532)

Also:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/323694](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/323694)

---

