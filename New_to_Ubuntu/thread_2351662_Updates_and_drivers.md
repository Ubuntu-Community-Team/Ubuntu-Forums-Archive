---
title: "Updates and drivers"
date: 2017-02-05
forum: New to Ubuntu
---

### Post by bitsnpcs on 2017-02-05
Hello,
I have installed Ubuntu 16.04.1 , it is the only OS on the computer, the computer is Zoostorm Origin, core i7-6700 Skylake, integrated graphics Intel HD530, ram 16Gb, motherboard H110M-R.
On install everything was good.
I then clicked Ubuntu Software>Updates, it says 22 updates, I clicked Install on the first item of this list named  "OS Updates", after this I see the graphics driver changed to Gallium with a maximum resolution of 1024, and noticed Firefox also updated, I am unsure what else the updates contained.
What happened then was shortly afterwards a black screen and the desktop crashed with errors about the motherboard H110M-R, after rebooting, I got a pop up message about calendar has crashed, when resizing the dash icons to 32, it resizes them back to default a few minutes later, then the computer crashed and shutdown and I could no longer get to the Ubuntu desktop.

I wiped and reinstalled Ubuntu 16.04.1, and have not done any updates, everything has been working without any problems.

I need some help please to learn what out of the 22 updates caused the problem and how to prevent this from being listed in the updates in future, so I am able to do updates without the computer becoming unstable ?

---

### Post by TheFu on 2017-02-05
Look at the log files.
Also, not using a GUI for update so you can send all the output to a log file (of your choosing) would be handy too.
[https://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](https://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc) would be worth a read, perhaps?

---

### Post by bitsnpcs on 2017-02-05
Thank you for your help, interesting and useful tutorial I will work through this, learn it.
I have worked through and enabled/set up ufw, following a tutorial on the Ubuntu website.

---

### Post by howefield on 2017-02-06
> **bitsnpcs said:**
> I am unsure what else the updates contained.

If you are not afraid of using the terminal, try a 

```
sudo apt update
```

then you can list the package updates with..

```
apt list --upgradable
```

Feel free to post the list back here.

---

### Post by TheFu on 2017-02-06
> **bitsnpcs said:**
> Thank you for your help, interesting and useful tutorial I will work through this, learn it.

That was created in 2010-ish, so a few things are a little different, but not much.
* If you use **apt** (instead of apt-get or aptitude), then old kernel removal seems to be handled automatically. apt can be used in most situations like apt-get or aptitude for the common stuff.  ```
sudo apt update && sudo apt upgrade
```
* Some people use **bleachbit** to clear some user-level cruft ; I've never used it. [http://www.howtogeek.com/116971/7-tips-to-get-the-most-out-of-bleachbit-a-ccleaner-for-linux/](http://www.howtogeek.com/116971/7-tips-to-get-the-most-out-of-bleachbit-a-ccleaner-for-linux/)
* to send text output to both the screen AND to a log file, use the '**tee**' program. Something like ```
sudo apt upgrade | tee /tmp/log.apt
```

---

### Post by bitsnpcs on 2017-02-06
Hello,
whilst on the computer last night the update number decreased from 22 to 16, I didn't click to install anything.
Today it won't boot up but goes to a black screen.
I will wipe and install again, do the updates and add in the list of updates to the thread in a short while.

---

### Post by howefield on 2017-02-06
> **bitsnpcs said:**
> Whilst on the computer last night the update number decreased from 22 to 16, I didn't click to install anything.

Unattended-upgrades may have taken care of some of them. Have a look at the log file..

```
/var/log/unattended-upgrades/unattended-upgrades.log
```

---

### Post by bitsnpcs on 2017-02-06
I have reinstalled Ubuntu now, as I was unable to boot up.

Here are the results

```
bitsnpcs@bitsnpcs:~$ sudo apt update
[sudo] password for bitsnpcs: 
Hit:1 http://gb.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Hit:3 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Hit:4 http://security.ubuntu.com/ubuntu xenial-security InRelease              
Reading package lists... Done                     
Building dependency tree       
Reading state information... Done
327 packages can be upgraded. Run 'apt list --upgradable' to see them.
bitsnpcs@bitsnpcs:~$ apt list --upgradable
Listing... Done
accountsservice/xenial-updates 0.6.40-2ubuntu11.3 amd64 [upgradable from: 0.6.40-2ubuntu11.1]
apparmor/xenial-updates 2.10.95-0ubuntu2.5 amd64 [upgradable from: 2.10.95-0ubuntu2]
apport/xenial-updates,xenial-updates 2.20.1-0ubuntu2.5 all [upgradable from: 2.20.1-0ubuntu2.1]
apport-gtk/xenial-updates,xenial-updates 2.20.1-0ubuntu2.5 all [upgradable from: 2.20.1-0ubuntu2.1]
appstream/xenial-updates 0.9.4-1ubuntu2 amd64 [upgradable from: 0.9.4-1ubuntu1]
apt/xenial-updates 1.2.19 amd64 [upgradable from: 1.2.12~ubuntu16.04.1]
apt-transport-https/xenial-updates 1.2.19 amd64 [upgradable from: 1.2.12~ubuntu16.04.1]
apt-utils/xenial-updates 1.2.19 amd64 [upgradable from: 1.2.12~ubuntu16.04.1]
bamfdaemon/xenial-updates 0.5.3~bzr0+16.04.20160824-0ubuntu1 amd64 [upgradable from: 0.5.3~bzr0+16.04.20160701-0ubuntu1]
base-files/xenial-updates 9.4ubuntu4.3 amd64 [upgradable from: 9.4ubuntu4.2]
bind9-host/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
binutils/xenial-updates,xenial-security 2.26.1-1ubuntu1~16.04.3 amd64 [upgradable from: 2.26.1-1ubuntu1~16.04.1]
bsdutils/xenial-updates 1:2.27.1-6ubuntu3.2 amd64 [upgradable from: 1:2.27.1-6ubuntu3.1]
compiz/xenial-updates,xenial-updates 1:0.9.12.2+16.04.20160823-0ubuntu1 all [upgradable from: 1:0.9.12.2+16.04.20160714-0ubuntu1]
compiz-core/xenial-updates 1:0.9.12.2+16.04.20160823-0ubuntu1 amd64 [upgradable from: 1:0.9.12.2+16.04.20160714-0ubuntu1]
compiz-gnome/xenial-updates 1:0.9.12.2+16.04.20160823-0ubuntu1 amd64 [upgradable from: 1:0.9.12.2+16.04.20160714-0ubuntu1]
compiz-plugins-default/xenial-updates 1:0.9.12.2+16.04.20160823-0ubuntu1 amd64 [upgradable from: 1:0.9.12.2+16.04.20160714-0ubuntu1]
cpp-5/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
cups-browsed/xenial-updates 1.8.3-2ubuntu3.1 amd64 [upgradable from: 1.8.3-2ubuntu3]
cups-filters/xenial-updates 1.8.3-2ubuntu3.1 amd64 [upgradable from: 1.8.3-2ubuntu3]
cups-filters-core-drivers/xenial-updates 1.8.3-2ubuntu3.1 amd64 [upgradable from: 1.8.3-2ubuntu3]
curl/xenial-updates,xenial-security 7.47.0-1ubuntu2.2 amd64 [upgradable from: 7.47.0-1ubuntu2]
dbus/xenial-updates 1.10.6-1ubuntu3.3 amd64 [upgradable from: 1.10.6-1ubuntu3]
dbus-x11/xenial-updates 1.10.6-1ubuntu3.3 amd64 [upgradable from: 1.10.6-1ubuntu3]
deja-dup/xenial-updates 34.2-0ubuntu1.1 amd64 [upgradable from: 34.2-0ubuntu1]
distro-info-data/xenial-updates,xenial-updates 0.28ubuntu0.2 all [upgradable from: 0.28ubuntu0.1]
dnsutils/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
eog/xenial-updates,xenial-security 3.18.2-1ubuntu2.1 amd64 [upgradable from: 3.18.2-1ubuntu1]
file-roller/xenial-updates,xenial-security 3.16.5-0ubuntu1.2 amd64 [upgradable from: 3.16.5-0ubuntu1.1]
firefox/xenial-updates,xenial-security 51.0.1+build2-0ubuntu0.16.04.2 amd64 [upgradable from: 47.0+build3-0ubuntu0.16.04.1]
fontconfig/xenial-updates,xenial-security 2.11.94-0ubuntu1.1 amd64 [upgradable from: 2.11.94-0ubuntu1]
fontconfig-config/xenial-updates,xenial-updates,xenial-security,xenial-security 2.11.94-0ubuntu1.1 all [upgradable from: 2.11.94-0ubuntu1]
fuse/xenial-updates 2.9.4-1ubuntu3.1 amd64 [upgradable from: 2.9.4-1ubuntu3]
fwupd/xenial-updates 0.7.0-0ubuntu4.3 amd64 [upgradable from: 0.7.0-0ubuntu4.2]
g++-5/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
gcc-5/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
gcc-5-base/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
ghostscript/xenial-updates,xenial-security 9.18~dfsg~0-0ubuntu2.3 amd64 [upgradable from: 9.18~dfsg~0-0ubuntu2]
ghostscript-x/xenial-updates,xenial-security 9.18~dfsg~0-0ubuntu2.3 amd64 [upgradable from: 9.18~dfsg~0-0ubuntu2]
gir1.2-dbusmenu-glib-0.4/xenial-updates 16.04.1+16.04.20160927-0ubuntu1 amd64 [upgradable from: 12.10.3+16.04.20160223.1-0ubuntu1]
gir1.2-gdkpixbuf-2.0/xenial-updates,xenial-security 2.32.2-1ubuntu1.2 amd64 [upgradable from: 2.32.2-1ubuntu1]
gir1.2-gst-plugins-base-1.0/xenial-updates 1.8.3-1ubuntu0.1 amd64 [upgradable from: 1.8.2-1ubuntu0.1]
gir1.2-gstreamer-1.0/xenial-updates 1.8.3-1~ubuntu0.1 amd64 [upgradable from: 1.8.2-1~ubuntu1]
gir1.2-javascriptcoregtk-4.0/xenial-updates,xenial-security 2.14.3-0ubuntu0.16.04.1 amd64 [upgradable from: 2.10.9-1ubuntu1]
gir1.2-webkit2-4.0/xenial-updates,xenial-security 2.14.3-0ubuntu0.16.04.1 amd64 [upgradable from: 2.10.9-1ubuntu1]
gnome-calculator/xenial-updates 1:3.18.3-0ubuntu1.16.04.1 amd64 [upgradable from: 1:3.18.3-0ubuntu1]
gnome-calendar/xenial-updates 3.20.4-0ubuntu0.1 amd64 [upgradable from: 3.20.2-0ubuntu0.1]
gnome-font-viewer/xenial-updates 3.16.2-1ubuntu1 amd64 [upgradable from: 3.16.2-1build1]
gnome-session-bin/xenial-updates 3.18.1.2-1ubuntu1.16.04.2 amd64 [upgradable from: 3.18.1.2-1ubuntu1.16.04.1]
gnome-session-common/xenial-updates,xenial-updates 3.18.1.2-1ubuntu1.16.04.2 all [upgradable from: 3.18.1.2-1ubuntu1.16.04.1]
gnome-settings-daemon-schemas/xenial-updates,xenial-updates 3.18.2-0ubuntu3.1 all [upgradable from: 3.18.2-0ubuntu3]
gnome-software/xenial-updates 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 amd64 [upgradable from: 3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1]
gnome-software-common/xenial-updates,xenial-updates 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 all [upgradable from: 3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1]
gnome-sudoku/xenial-updates 1:3.18.4-0ubuntu2 amd64 [upgradable from: 1:3.18.2-1]
gnome-system-monitor/xenial-updates 3.18.2-1ubuntu1 amd64 [upgradable from: 3.18.2-1]
gnupg/xenial-updates,xenial-security 1.4.20-1ubuntu3.1 amd64 [upgradable from: 1.4.20-1ubuntu3]
gpgv/xenial-updates,xenial-security 1.4.20-1ubuntu3.1 amd64 [upgradable from: 1.4.20-1ubuntu3]
grub-common/xenial-updates 2.02~beta2-36ubuntu3.7 amd64 [upgradable from: 2.02~beta2-36ubuntu3.1]
grub-pc/xenial-updates 2.02~beta2-36ubuntu3.7 amd64 [upgradable from: 2.02~beta2-36ubuntu3.1]
grub-pc-bin/xenial-updates 2.02~beta2-36ubuntu3.7 amd64 [upgradable from: 2.02~beta2-36ubuntu3.1]
grub2-common/xenial-updates 2.02~beta2-36ubuntu3.7 amd64 [upgradable from: 2.02~beta2-36ubuntu3.1]
gstreamer1.0-alsa/xenial-updates 1.8.3-1ubuntu0.1 amd64 [upgradable from: 1.8.2-1ubuntu0.1]
gstreamer1.0-plugins-base/xenial-updates 1.8.3-1ubuntu0.1 amd64 [upgradable from: 1.8.2-1ubuntu0.1]
gstreamer1.0-plugins-base-apps/xenial-updates 1.8.3-1ubuntu0.1 amd64 [upgradable from: 1.8.2-1ubuntu0.1]
gstreamer1.0-plugins-good/xenial-updates 1.8.3-1ubuntu0.3 amd64 [upgradable from: 1.8.2-1ubuntu0.1]
gstreamer1.0-pulseaudio/xenial-updates 1.8.3-1ubuntu0.3 amd64 [upgradable from: 1.8.2-1ubuntu0.1]
gstreamer1.0-tools/xenial-updates 1.8.3-1~ubuntu0.1 amd64 [upgradable from: 1.8.2-1~ubuntu1]
gstreamer1.0-x/xenial-updates 1.8.3-1ubuntu0.1 amd64 [upgradable from: 1.8.2-1ubuntu0.1]
gtk2-engines-murrine/xenial-updates 0.98.2-0ubuntu2.2 amd64 [upgradable from: 0.98.2-0ubuntu2.1]
humanity-icon-theme/xenial-updates,xenial-updates 0.6.10.1 all [upgradable from: 0.6.10]
ifupdown/xenial-updates 0.8.10ubuntu1.2 amd64 [upgradable from: 0.8.10ubuntu1]
im-config/xenial-updates,xenial-updates 0.29-1ubuntu12.3 all [upgradable from: 0.29-1ubuntu12]
imagemagick/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.3 amd64 [upgradable from: 8:6.8.9.9-7ubuntu5.1]
imagemagick-6.q16/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.3 amd64 [upgradable from: 8:6.8.9.9-7ubuntu5.1]
imagemagick-common/xenial-updates,xenial-updates,xenial-security,xenial-security 8:6.8.9.9-7ubuntu5.3 all [upgradable from: 8:6.8.9.9-7ubuntu5.1]
init/xenial-updates 1.29ubuntu3 amd64 [upgradable from: 1.29ubuntu2]
init-system-helpers/xenial-updates,xenial-updates 1.29ubuntu3 all [upgradable from: 1.29ubuntu2]
initramfs-tools/xenial-updates,xenial-updates 0.122ubuntu8.8 all [upgradable from: 0.122ubuntu8.1]
initramfs-tools-bin/xenial-updates 0.122ubuntu8.8 amd64 [upgradable from: 0.122ubuntu8.1]
initramfs-tools-core/xenial-updates,xenial-updates 0.122ubuntu8.8 all [upgradable from: 0.122ubuntu8.1]
isc-dhcp-client/xenial-updates 4.3.3-5ubuntu12.6 amd64 [upgradable from: 4.3.3-5ubuntu12.1]
isc-dhcp-common/xenial-updates 4.3.3-5ubuntu12.6 amd64 [upgradable from: 4.3.3-5ubuntu12.1]
kbd/xenial-updates 1.15.5-1ubuntu5 amd64 [upgradable from: 1.15.5-1ubuntu4]
klibc-utils/xenial-updates 2.0.4-8ubuntu1.16.04.2 amd64 [upgradable from: 2.0.4-8ubuntu1.16.04.1]
krb5-locales/xenial-updates,xenial-updates 1.13.2+dfsg-5ubuntu2 all [upgradable from: 1.13.2+dfsg-5]
language-selector-common/xenial-updates,xenial-updates 0.165.4 all [upgradable from: 0.165.3]
language-selector-gnome/xenial-updates,xenial-updates 0.165.4 all [upgradable from: 0.165.3]
less/xenial-updates 481-2.1ubuntu0.1 amd64 [upgradable from: 481-2.1]
libaccountsservice0/xenial-updates 0.6.40-2ubuntu11.3 amd64 [upgradable from: 0.6.40-2ubuntu11.1]
libapparmor-perl/xenial-updates 2.10.95-0ubuntu2.5 amd64 [upgradable from: 2.10.95-0ubuntu2]
libapparmor1/xenial-updates 2.10.95-0ubuntu2.5 amd64 [upgradable from: 2.10.95-0ubuntu2]
libappstream-glib8/xenial-updates 0.5.13-1ubuntu4 amd64 [upgradable from: 0.5.13-1ubuntu2]
libappstream3/xenial-updates 0.9.4-1ubuntu2 amd64 [upgradable from: 0.9.4-1ubuntu1]
libapt-inst2.0/xenial-updates 1.2.19 amd64 [upgradable from: 1.2.12~ubuntu16.04.1]
libapt-pkg5.0/xenial-updates 1.2.19 amd64 [upgradable from: 1.2.12~ubuntu16.04.1]
libasan2/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libatomic1/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libbamf3-2/xenial-updates 0.5.3~bzr0+16.04.20160824-0ubuntu1 amd64 [upgradable from: 0.5.3~bzr0+16.04.20160701-0ubuntu1]
libbind9-140/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
libblkid1/xenial-updates 2.27.1-6ubuntu3.2 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
libc-bin/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu3]
libc-dev-bin/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu3]
libc6/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu3]
libc6-dbg/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu3]
libc6-dev/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu3]
libcc1-0/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libcilkrts5/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libcompizconfig0/xenial-updates 1:0.9.12.2+16.04.20160823-0ubuntu1 amd64 [upgradable from: 1:0.9.12.2+16.04.20160714-0ubuntu1]
libcupsfilters1/xenial-updates 1.8.3-2ubuntu3.1 amd64 [upgradable from: 1.8.3-2ubuntu3]
libcurl3/xenial-updates,xenial-security 7.47.0-1ubuntu2.2 amd64 [upgradable from: 7.47.0-1ubuntu2]
libcurl3-gnutls/xenial-updates,xenial-security 7.47.0-1ubuntu2.2 amd64 [upgradable from: 7.47.0-1ubuntu2]
libdbus-1-3/xenial-updates 1.10.6-1ubuntu3.3 amd64 [upgradable from: 1.10.6-1ubuntu3]
libdbusmenu-glib4/xenial-updates 16.04.1+16.04.20160927-0ubuntu1 amd64 [upgradable from: 12.10.3+16.04.20160223.1-0ubuntu1]
libdbusmenu-gtk3-4/xenial-updates 16.04.1+16.04.20160927-0ubuntu1 amd64 [upgradable from: 12.10.3+16.04.20160223.1-0ubuntu1]
libdbusmenu-gtk4/xenial-updates 16.04.1+16.04.20160927-0ubuntu1 amd64 [upgradable from: 12.10.3+16.04.20160223.1-0ubuntu1]
libdecoration0/xenial-updates 1:0.9.12.2+16.04.20160823-0ubuntu1 amd64 [upgradable from: 1:0.9.12.2+16.04.20160714-0ubuntu1]
libdfu1/xenial-updates 0.7.0-0ubuntu4.3 amd64 [upgradable from: 0.7.0-0ubuntu4.2]
libdns-export162/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
libdns162/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
libdrm-amdgpu1/xenial-updates 2.4.67-1ubuntu0.16.04.2 amd64 [upgradable from: 2.4.67-1ubuntu0.16.04.1]
libdrm-intel1/xenial-updates 2.4.67-1ubuntu0.16.04.2 amd64 [upgradable from: 2.4.67-1ubuntu0.16.04.1]
libdrm-nouveau2/xenial-updates 2.4.67-1ubuntu0.16.04.2 amd64 [upgradable from: 2.4.67-1ubuntu0.16.04.1]
libdrm-radeon1/xenial-updates 2.4.67-1ubuntu0.16.04.2 amd64 [upgradable from: 2.4.67-1ubuntu0.16.04.1]
libdrm2/xenial-updates 2.4.67-1ubuntu0.16.04.2 amd64 [upgradable from: 2.4.67-1ubuntu0.16.04.1]
libegl1-mesa/xenial-updates 11.2.0-1ubuntu2.2 amd64 [upgradable from: 11.2.0-1ubuntu2]
libfcitx-config4/xenial-updates 1:4.2.9.1-1ubuntu1.16.04.2 amd64 [upgradable from: 1:4.2.9.1-1ubuntu1]
libfcitx-gclient0/xenial-updates 1:4.2.9.1-1ubuntu1.16.04.2 amd64 [upgradable from: 1:4.2.9.1-1ubuntu1]
libfcitx-utils0/xenial-updates 1:4.2.9.1-1ubuntu1.16.04.2 amd64 [upgradable from: 1:4.2.9.1-1ubuntu1]
libfdisk1/xenial-updates 2.27.1-6ubuntu3.2 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
libfontconfig1/xenial-updates,xenial-security 2.11.94-0ubuntu1.1 amd64 [upgradable from: 2.11.94-0ubuntu1]
libfontembed1/xenial-updates 1.8.3-2ubuntu3.1 amd64 [upgradable from: 1.8.3-2ubuntu3]
libframe6/xenial-updates 2.5.0daily13.06.05+16.04.20160809-0ubuntu1 amd64 [upgradable from: 2.5.0daily13.06.05-0ubuntu1]
libfuse2/xenial-updates 2.9.4-1ubuntu3.1 amd64 [upgradable from: 2.9.4-1ubuntu3]
libfwupd1/xenial-updates 0.7.0-0ubuntu4.3 amd64 [upgradable from: 0.7.0-0ubuntu4.2]
libgbm1/xenial-updates 11.2.0-1ubuntu2.2 amd64 [upgradable from: 11.2.0-1ubuntu2]
libgcc-5-dev/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libgcrypt20/xenial-updates,xenial-security 1.6.5-2ubuntu0.2 amd64 [upgradable from: 1.6.5-2]
libgd3/xenial-updates,xenial-security 2.1.1-4ubuntu0.16.04.5 amd64 [upgradable from: 2.1.1-4ubuntu0.16.04.2]
libgdk-pixbuf2.0-0/xenial-updates,xenial-security 2.32.2-1ubuntu1.2 amd64 [upgradable from: 2.32.2-1ubuntu1]
libgdk-pixbuf2.0-common/xenial-updates,xenial-updates,xenial-security,xenial-security 2.32.2-1ubuntu1.2 all [upgradable from: 2.32.2-1ubuntu1]
libgl1-mesa-dri/xenial-updates 11.2.0-1ubuntu2.2 amd64 [upgradable from: 11.2.0-1ubuntu2]
libgl1-mesa-glx/xenial-updates 11.2.0-1ubuntu2.2 amd64 [upgradable from: 11.2.0-1ubuntu2]
libglapi-mesa/xenial-updates 11.2.0-1ubuntu2.2 amd64 [upgradable from: 11.2.0-1ubuntu2]
libglib2.0-0/xenial-updates 2.48.2-0ubuntu1 amd64 [upgradable from: 2.48.1-1~ubuntu16.04.1]
libglib2.0-bin/xenial-updates 2.48.2-0ubuntu1 amd64 [upgradable from: 2.48.1-1~ubuntu16.04.1]
libglib2.0-data/xenial-updates,xenial-updates 2.48.2-0ubuntu1 all [upgradable from: 2.48.1-1~ubuntu16.04.1]
libgnutls-openssl27/xenial-updates,xenial-security 3.4.10-4ubuntu1.2 amd64 [upgradable from: 3.4.10-4ubuntu1.1]
libgnutls30/xenial-updates,xenial-security 3.4.10-4ubuntu1.2 amd64 [upgradable from: 3.4.10-4ubuntu1.1]
libgomp1/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libgs9/xenial-updates,xenial-security 9.18~dfsg~0-0ubuntu2.3 amd64 [upgradable from: 9.18~dfsg~0-0ubuntu2]
libgs9-common/xenial-updates,xenial-updates,xenial-security,xenial-security 9.18~dfsg~0-0ubuntu2.3 all [upgradable from: 9.18~dfsg~0-0ubuntu2]
libgssapi-krb5-2/xenial-updates 1.13.2+dfsg-5ubuntu2 amd64 [upgradable from: 1.13.2+dfsg-5]
libgstreamer-plugins-base1.0-0/xenial-updates 1.8.3-1ubuntu0.1 amd64 [upgradable from: 1.8.2-1ubuntu0.1]
libgstreamer-plugins-good1.0-0/xenial-updates 1.8.3-1ubuntu0.3 amd64 [upgradable from: 1.8.2-1ubuntu0.1]
libgstreamer1.0-0/xenial-updates 1.8.3-1~ubuntu0.1 amd64 [upgradable from: 1.8.2-1~ubuntu1]
libgweather-3-6/xenial-updates 3.18.2-0ubuntu0.1 amd64 [upgradable from: 3.18.1-1ubuntu1]
libgweather-common/xenial-updates,xenial-updates 3.18.2-0ubuntu0.1 all [upgradable from: 3.18.1-1ubuntu1]
libharfbuzz-icu0/xenial-updates,xenial-security 1.0.1-1ubuntu0.1 amd64 [upgradable from: 1.0.1-1build2]
libharfbuzz0b/xenial-updates,xenial-security 1.0.1-1ubuntu0.1 amd64 [upgradable from: 1.0.1-1build2]
libhogweed4/xenial-security 3.2-1ubuntu0.16.04.1 amd64 [upgradable from: 3.2-1]
libidn11/xenial-updates,xenial-security 1.32-3ubuntu1.1 amd64 [upgradable from: 1.32-3ubuntu1]
libido3-0.1-0/xenial-updates 13.10.0+16.04.20161028-0ubuntu1 amd64 [upgradable from: 13.10.0+15.10.20151002-0ubuntu1]
libisc-export160/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
libisc160/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
libisccc140/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
libisccfg140/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
libitm1/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libjavascriptcoregtk-4.0-18/xenial-updates,xenial-security 2.14.3-0ubuntu0.16.04.1 amd64 [upgradable from: 2.10.9-1ubuntu1]
libk5crypto3/xenial-updates 1.13.2+dfsg-5ubuntu2 amd64 [upgradable from: 1.13.2+dfsg-5]
libklibc/xenial-updates 2.0.4-8ubuntu1.16.04.2 amd64 [upgradable from: 2.0.4-8ubuntu1.16.04.1]
libkrb5-3/xenial-updates 1.13.2+dfsg-5ubuntu2 amd64 [upgradable from: 1.13.2+dfsg-5]
libkrb5support0/xenial-updates 1.13.2+dfsg-5ubuntu2 amd64 [upgradable from: 1.13.2+dfsg-5]
liblightdm-gobject-1-0/xenial-updates 1.18.3-0ubuntu1 amd64 [upgradable from: 1.18.2-0ubuntu1]
libllvm3.8/xenial-updates 1:3.8-2ubuntu4 amd64 [upgradable from: 1:3.8-2ubuntu3]
liblsan0/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
liblwres141/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
libmagickcore-6.q16-2/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.3 amd64 [upgradable from: 8:6.8.9.9-7ubuntu5.1]
libmagickcore-6.q16-2-extra/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.3 amd64 [upgradable from: 8:6.8.9.9-7ubuntu5.1]
libmagickwand-6.q16-2/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.3 amd64 [upgradable from: 8:6.8.9.9-7ubuntu5.1]
libmetacity-private3a/xenial-updates 1:3.18.7-0ubuntu0.2 amd64 [upgradable from: 1:3.18.5-0ubuntu0.1]
libmount1/xenial-updates 2.27.1-6ubuntu3.2 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
libmpx0/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libnautilus-extension1a/xenial-updates 1:3.18.4.is.3.14.3-0ubuntu5 amd64 [upgradable from: 1:3.18.4.is.3.14.3-0ubuntu4]
libnettle6/xenial-security 3.2-1ubuntu0.16.04.1 amd64 [upgradable from: 3.2-1]
libnm-glib-vpn1/xenial-updates 1.2.2-0ubuntu0.16.04.3 amd64 [upgradable from: 1.2.0-0ubuntu0.16.04.3]
libnm-glib4/xenial-updates 1.2.2-0ubuntu0.16.04.3 amd64 [upgradable from: 1.2.0-0ubuntu0.16.04.3]
libnm-gtk-common/xenial-updates,xenial-updates 1.2.0-0ubuntu0.16.04.4 all [upgradable from: 1.2.0-0ubuntu0.16.04.3]
libnm-gtk0/xenial-updates 1.2.0-0ubuntu0.16.04.4 amd64 [upgradable from: 1.2.0-0ubuntu0.16.04.3]
libnm-util2/xenial-updates 1.2.2-0ubuntu0.16.04.3 amd64 [upgradable from: 1.2.0-0ubuntu0.16.04.3]
libnm0/xenial-updates 1.2.2-0ubuntu0.16.04.3 amd64 [upgradable from: 1.2.0-0ubuntu0.16.04.3]
libnma-common/xenial-updates,xenial-updates 1.2.0-0ubuntu0.16.04.4 all [upgradable from: 1.2.0-0ubuntu0.16.04.3]
libnma0/xenial-updates 1.2.0-0ubuntu0.16.04.4 amd64 [upgradable from: 1.2.0-0ubuntu0.16.04.3]
libnss3/xenial-updates,xenial-security 2:3.26.2-0ubuntu0.16.04.2 amd64 [upgradable from: 2:3.23-0ubuntu0.16.04.1]
libnss3-nssdb/xenial-updates,xenial-updates,xenial-security,xenial-security 2:3.26.2-0ubuntu0.16.04.2 all [upgradable from: 2:3.23-0ubuntu0.16.04.1]
liboxideqt-qmlplugin/xenial-updates,xenial-security 1.19.4-0ubuntu0.16.04.1 amd64 [upgradable from: 1.15.8-0ubuntu0.16.04.1]
liboxideqtcore0/xenial-updates,xenial-security 1.19.4-0ubuntu0.16.04.1 amd64 [upgradable from: 1.15.8-0ubuntu0.16.04.1]
liboxideqtquick0/xenial-updates,xenial-security 1.19.4-0ubuntu0.16.04.1 amd64 [upgradable from: 1.15.8-0ubuntu0.16.04.1]
libp11-kit0/xenial-updates 0.23.2-5~ubuntu16.04.1 amd64 [upgradable from: 0.23.2-3]
libpam-systemd/xenial-updates 229-4ubuntu16 amd64 [upgradable from: 229-4ubuntu7]
libpcsclite1/xenial-updates,xenial-security 1.8.14-1ubuntu1.16.04.1 amd64 [upgradable from: 1.8.14-1ubuntu1]
libpoppler-glib8/xenial-updates 0.41.0-0ubuntu1.1 amd64 [upgradable from: 0.41.0-0ubuntu1]
libpoppler58/xenial-updates 0.41.0-0ubuntu1.1 amd64 [upgradable from: 0.41.0-0ubuntu1]
libprocps4/xenial-updates 2:3.3.10-4ubuntu2.3 amd64 [upgradable from: 2:3.3.10-4ubuntu2]
libpulse-mainloop-glib0/xenial-updates 1:8.0-0ubuntu3.2 amd64 [upgradable from: 1:8.0-0ubuntu3]
libpulse0/xenial-updates 1:8.0-0ubuntu3.2 amd64 [upgradable from: 1:8.0-0ubuntu3]
libpulsedsp/xenial-updates 1:8.0-0ubuntu3.2 amd64 [upgradable from: 1:8.0-0ubuntu3]
libpython2.7/xenial-updates,xenial-security 2.7.12-1ubuntu0~16.04.1 amd64 [upgradable from: 2.7.12-1~16.04]
libpython2.7-minimal/xenial-updates,xenial-security 2.7.12-1ubuntu0~16.04.1 amd64 [upgradable from: 2.7.12-1~16.04]
libpython2.7-stdlib/xenial-updates,xenial-security 2.7.12-1ubuntu0~16.04.1 amd64 [upgradable from: 2.7.12-1~16.04]
libpython3.5/xenial-updates,xenial-security 3.5.2-2ubuntu0~16.04.1 amd64 [upgradable from: 3.5.2-2~16.01]
libpython3.5-minimal/xenial-updates,xenial-security 3.5.2-2ubuntu0~16.04.1 amd64 [upgradable from: 3.5.2-2~16.01]
libpython3.5-stdlib/xenial-updates,xenial-security 3.5.2-2ubuntu0~16.04.1 amd64 [upgradable from: 3.5.2-2~16.01]
libqt5core5a/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5dbus5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5gui5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5network5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5opengl5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5printsupport5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5sql5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5sql5-sqlite/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5test5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5widgets5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5xml5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libquadmath0/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libsmartcols1/xenial-updates 2.27.1-6ubuntu3.2 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
libsmbclient/xenial-updates,xenial-security 2:4.3.11+dfsg-0ubuntu0.16.04.3 amd64 [upgradable from: 2:4.3.9+dfsg-0ubuntu0.16.04.2]
libssl1.0.0/xenial-updates,xenial-security 1.0.2g-1ubuntu4.6 amd64 [upgradable from: 1.0.2g-1ubuntu4.1]
libstdc++-5-dev/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libstdc++6/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libsystemd0/xenial-updates 229-4ubuntu16 amd64 [upgradable from: 229-4ubuntu7]
libtracker-sparql-1.0-0/xenial-updates,xenial-security 1.6.2-0ubuntu1.1 amd64 [upgradable from: 1.6.2-0ubuntu1]
libtsan0/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libubsan0/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libudev1/xenial-updates 229-4ubuntu16 amd64 [upgradable from: 229-4ubuntu7]
libunity-core-6.0-9/xenial-updates 7.4.0+16.04.20160906-0ubuntu1 amd64 [upgradable from: 7.4.0+16.04.20160715-0ubuntu1]
libuuid1/xenial-updates 2.27.1-6ubuntu3.2 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
libvncclient1/xenial-updates,xenial-security 0.9.10+dfsg-3ubuntu0.16.04.1 amd64 [upgradable from: 0.9.10+dfsg-3build1]
libwayland-egl1-mesa/xenial-updates 11.2.0-1ubuntu2.2 amd64 [upgradable from: 11.2.0-1ubuntu2]
libwbclient0/xenial-updates,xenial-security 2:4.3.11+dfsg-0ubuntu0.16.04.3 amd64 [upgradable from: 2:4.3.9+dfsg-0ubuntu0.16.04.2]
libwebkit2gtk-4.0-37/xenial-updates,xenial-security 2.14.3-0ubuntu0.16.04.1 amd64 [upgradable from: 2.10.9-1ubuntu1]
libwebkit2gtk-4.0-37-gtk2/xenial-updates,xenial-security 2.14.3-0ubuntu0.16.04.1 amd64 [upgradable from: 2.10.9-1ubuntu1]
libwhoopsie0/xenial-updates 0.2.52.2 amd64 [upgradable from: 0.2.52.1]
libxatracker2/xenial-updates 11.2.0-1ubuntu2.2 amd64 [upgradable from: 11.2.0-1ubuntu2]
libxpm4/xenial-updates,xenial-security 1:3.5.11-1ubuntu0.16.04.1 amd64 [upgradable from: 1:3.5.11-1]
light-themes/xenial-updates,xenial-updates 14.04+16.04.20161024-0ubuntu1 all [upgradable from: 14.04+16.04.20160621-0ubuntu1]
lightdm/xenial-updates 1.18.3-0ubuntu1 amd64 [upgradable from: 1.18.2-0ubuntu1]
linux-firmware/xenial-updates,xenial-updates 1.157.6 all [upgradable from: 1.157.2]
linux-generic/xenial-updates,xenial-security 4.4.0.62.65 amd64 [upgradable from: 4.4.0.31.33]
linux-headers-generic/xenial-updates,xenial-security 4.4.0.62.65 amd64 [upgradable from: 4.4.0.31.33]
linux-image-generic/xenial-updates,xenial-security 4.4.0.62.65 amd64 [upgradable from: 4.4.0.31.33]
linux-libc-dev/xenial-updates,xenial-security 4.4.0-62.83 amd64 [upgradable from: 4.4.0-31.50]
locales/xenial-updates,xenial-updates 2.23-0ubuntu5 all [upgradable from: 2.23-0ubuntu3]
metacity-common/xenial-updates,xenial-updates 1:3.18.7-0ubuntu0.2 all [upgradable from: 1:3.18.5-0ubuntu0.1]
mount/xenial-updates 2.27.1-6ubuntu3.2 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
mtools/xenial-updates 4.0.18-2ubuntu0.16.04 amd64 [upgradable from: 4.0.18-2]
multiarch-support/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu3]
nano/xenial-updates 2.5.3-2ubuntu1 amd64 [upgradable from: 2.5.3-2]
nautilus/xenial-updates 1:3.18.4.is.3.14.3-0ubuntu5 amd64 [upgradable from: 1:3.18.4.is.3.14.3-0ubuntu4]
nautilus-data/xenial-updates,xenial-updates 1:3.18.4.is.3.14.3-0ubuntu5 all [upgradable from: 1:3.18.4.is.3.14.3-0ubuntu4]
network-manager/xenial-updates 1.2.2-0ubuntu0.16.04.3 amd64 [upgradable from: 1.2.0-0ubuntu0.16.04.3]
network-manager-gnome/xenial-updates 1.2.0-0ubuntu0.16.04.4 amd64 [upgradable from: 1.2.0-0ubuntu0.16.04.3]
ntfs-3g/xenial-updates,xenial-security 1:2015.3.14AR.1-1ubuntu0.1 amd64 [upgradable from: 1:2015.3.14AR.1-1build1]
openssh-client/xenial-updates,xenial-security 1:7.2p2-4ubuntu2.1 amd64 [upgradable from: 1:7.2p2-4ubuntu1]
openssl/xenial-updates,xenial-security 1.0.2g-1ubuntu4.6 amd64 [upgradable from: 1.0.2g-1ubuntu4.1]
overlay-scrollbar/xenial-updates,xenial-updates 0.2.17.1+16.04.20151117-0ubuntu1.16.04.1 all [upgradable from: 0.2.17.1+16.04.20151117-0ubuntu1]
overlay-scrollbar-gtk2/xenial-updates 0.2.17.1+16.04.20151117-0ubuntu1.16.04.1 amd64 [upgradable from: 0.2.17.1+16.04.20151117-0ubuntu1]
oxideqt-codecs/xenial-updates,xenial-security 1.19.4-0ubuntu0.16.04.1 amd64 [upgradable from: 1.15.8-0ubuntu0.16.04.1]
p11-kit/xenial-updates 0.23.2-5~ubuntu16.04.1 amd64 [upgradable from: 0.23.2-3]
p11-kit-modules/xenial-updates 0.23.2-5~ubuntu16.04.1 amd64 [upgradable from: 0.23.2-3]
poppler-utils/xenial-updates 0.41.0-0ubuntu1.1 amd64 [upgradable from: 0.41.0-0ubuntu1]
procps/xenial-updates 2:3.3.10-4ubuntu2.3 amd64 [upgradable from: 2:3.3.10-4ubuntu2]
pulseaudio/xenial-updates 1:8.0-0ubuntu3.2 amd64 [upgradable from: 1:8.0-0ubuntu3]
pulseaudio-module-bluetooth/xenial-updates 1:8.0-0ubuntu3.2 amd64 [upgradable from: 1:8.0-0ubuntu3]
pulseaudio-module-x11/xenial-updates 1:8.0-0ubuntu3.2 amd64 [upgradable from: 1:8.0-0ubuntu3]
pulseaudio-utils/xenial-updates 1:8.0-0ubuntu3.2 amd64 [upgradable from: 1:8.0-0ubuntu3]
python2.7/xenial-updates,xenial-security 2.7.12-1ubuntu0~16.04.1 amd64 [upgradable from: 2.7.12-1~16.04]
python2.7-minimal/xenial-updates,xenial-security 2.7.12-1ubuntu0~16.04.1 amd64 [upgradable from: 2.7.12-1~16.04]
python3-apport/xenial-updates,xenial-updates 2.20.1-0ubuntu2.5 all [upgradable from: 2.20.1-0ubuntu2.1]
python3-cryptography/xenial-updates,xenial-security 1.2.3-1ubuntu0.1 amd64 [upgradable from: 1.2.3-1]
python3-distupgrade/xenial-updates,xenial-updates 1:16.04.21 all [upgradable from: 1:16.04.14]
python3-problem-report/xenial-updates,xenial-updates 2.20.1-0ubuntu2.5 all [upgradable from: 2.20.1-0ubuntu2.1]
python3-software-properties/xenial-updates,xenial-updates 0.96.20.5 all [upgradable from: 0.96.20.2]
python3-update-manager/xenial-updates,xenial-updates 1:16.04.5 all [upgradable from: 1:16.04.3]
python3.5/xenial-updates,xenial-security 3.5.2-2ubuntu0~16.04.1 amd64 [upgradable from: 3.5.2-2~16.01]
python3.5-minimal/xenial-updates,xenial-security 3.5.2-2ubuntu0~16.04.1 amd64 [upgradable from: 3.5.2-2~16.01]
qml-module-ubuntu-web/xenial-updates 0.23+16.04.20161028-0ubuntu2 amd64 [upgradable from: 0.23+16.04.20160413-0ubuntu1]
samba-libs/xenial-updates,xenial-security 2:4.3.11+dfsg-0ubuntu0.16.04.3 amd64 [upgradable from: 2:4.3.9+dfsg-0ubuntu0.16.04.2]
snapd/xenial-updates 2.21 amd64 [upgradable from: 2.0.10]
software-properties-common/xenial-updates,xenial-updates 0.96.20.5 all [upgradable from: 0.96.20.2]
software-properties-gtk/xenial-updates,xenial-updates 0.96.20.5 all [upgradable from: 0.96.20.2]
sudo/xenial-updates 1.8.16-0ubuntu1.2 amd64 [upgradable from: 1.8.16-0ubuntu1.1]
suru-icon-theme/xenial-updates,xenial-updates 14.04+16.04.20161024-0ubuntu1 all [upgradable from: 14.04+16.04.20160621-0ubuntu1]
systemd/xenial-updates 229-4ubuntu16 amd64 [upgradable from: 229-4ubuntu7]
systemd-sysv/xenial-updates 229-4ubuntu16 amd64 [upgradable from: 229-4ubuntu7]
tar/xenial-updates,xenial-security 1.28-2.1ubuntu0.1 amd64 [upgradable from: 1.28-2.1]
tzdata/xenial-updates,xenial-updates,xenial-security,xenial-security 2016j-0ubuntu0.16.04 all [upgradable from: 2016f-0ubuntu0.16.04]
ubuntu-artwork/xenial-updates,xenial-updates 1:14.04+16.04.20161024-0ubuntu1 all [upgradable from: 1:14.04+16.04.20160621-0ubuntu1]
ubuntu-core-launcher/xenial-updates 2.21 amd64 [upgradable from: 1.0.27.1]
ubuntu-drivers-common/xenial-updates 1:0.4.17.2 amd64 [upgradable from: 1:0.4.17.1]
ubuntu-mobile-icons/xenial-updates,xenial-updates 14.04+16.04.20161024-0ubuntu1 all [upgradable from: 14.04+16.04.20160621-0ubuntu1]
ubuntu-mono/xenial-updates,xenial-updates 14.04+16.04.20161024-0ubuntu1 all [upgradable from: 14.04+16.04.20160621-0ubuntu1]
ubuntu-release-upgrader-core/xenial-updates,xenial-updates 1:16.04.21 all [upgradable from: 1:16.04.14]
ubuntu-release-upgrader-gtk/xenial-updates,xenial-updates 1:16.04.21 all [upgradable from: 1:16.04.14]
ubuntu-session/xenial-updates,xenial-updates 3.18.1.2-1ubuntu1.16.04.2 all [upgradable from: 3.18.1.2-1ubuntu1.16.04.1]
ubuntu-software/xenial-updates 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 amd64 [upgradable from: 3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1]
udev/xenial-updates 229-4ubuntu16 amd64 [upgradable from: 229-4ubuntu7]
unattended-upgrades/xenial-updates,xenial-updates 0.90ubuntu0.3 all [upgradable from: 0.90]
unity/xenial-updates 7.4.0+16.04.20160906-0ubuntu1 amd64 [upgradable from: 7.4.0+16.04.20160715-0ubuntu1]
unity-schemas/xenial-updates,xenial-updates 7.4.0+16.04.20160906-0ubuntu1 all [upgradable from: 7.4.0+16.04.20160715-0ubuntu1]
unity-services/xenial-updates 7.4.0+16.04.20160906-0ubuntu1 amd64 [upgradable from: 7.4.0+16.04.20160715-0ubuntu1]
update-manager/xenial-updates,xenial-updates 1:16.04.5 all [upgradable from: 1:16.04.3]
update-manager-core/xenial-updates,xenial-updates 1:16.04.5 all [upgradable from: 1:16.04.3]
update-notifier/xenial-updates 3.168.3 amd64 [upgradable from: 3.168.1]
update-notifier-common/xenial-updates,xenial-updates 3.168.3 all [upgradable from: 3.168.1]
util-linux/xenial-updates 2.27.1-6ubuntu3.2 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
uuid-runtime/xenial-updates 2.27.1-6ubuntu3.2 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
vim-common/xenial-updates,xenial-security 2:7.4.1689-3ubuntu1.2 amd64 [upgradable from: 2:7.4.1689-3ubuntu1.1]
vim-tiny/xenial-updates,xenial-security 2:7.4.1689-3ubuntu1.2 amd64 [upgradable from: 2:7.4.1689-3ubuntu1.1]
vino/xenial-updates 3.8.1-0ubuntu9.1 amd64 [upgradable from: 3.8.1-0ubuntu9]
webapp-container/xenial-updates 0.23+16.04.20161028-0ubuntu2 amd64 [upgradable from: 0.23+16.04.20160413-0ubuntu1]
webbrowser-app/xenial-updates 0.23+16.04.20161028-0ubuntu2 amd64 [upgradable from: 0.23+16.04.20160413-0ubuntu1]
whoopsie/xenial-updates 0.2.52.2 amd64 [upgradable from: 0.2.52.1]
xdg-utils/xenial-updates,xenial-updates 1.1.1-1ubuntu1.16.04.1 all [upgradable from: 1.1.1-1ubuntu1]
xdiagnose/xenial-updates,xenial-updates 3.8.4.1 all [upgradable from: 3.8.4]
xserver-common/xenial-updates,xenial-updates 2:1.18.4-0ubuntu0.2 all [upgradable from: 2:1.18.3-1ubuntu2.2]
xserver-xorg-core/xenial-updates 2:1.18.4-0ubuntu0.2 amd64 [upgradable from: 2:1.18.3-1ubuntu2.2]
xserver-xorg-video-intel/xenial-updates 2:2.99.917+git20160325-1ubuntu1.2 amd64 [upgradable from: 2:2.99.917+git20160325-1ubuntu1]
bitsnpcs@bitsnpcs:~$ 

```

> **howefield said:**
> Unattended-upgrades may have taken care of some of them. Have a look at the log file..

```
/var/log/unattended-upgrades/unattended-upgrades.log
```

As soon as the unattended upgrades occur I will do this and add the results.

```
/var/log/unattended-upgrades/unattended-upgrades.log
bash: /var/log/unattended-upgrades/unattended-upgrades.log: No such file or directory
```

---

### Post by TheFu on 2017-02-06
I don't allow unattended updates - ever.

Want to know when things are changed and control when that happens so if/when something doesn't work as expected, I can check my last upgrade logs.  About once every 2-3 years, an upgrade breaks something. For me, it has been something relatively small, almost always.

BTW, having a backup means never having to setup your system again due to a failed update.  They aren't hard to setup for a desktop and don't take much storage (by today's idea of "lots of storage").  Really just need 3 things:
1) /etc
2) $HOME
3) list of the installed add-on packages (which can be used at restore time to quickly reinstall them)

---

### Post by bitsnpcs on 2017-02-06
I will need to learn how to make a back up to restore settings, I can see it will be an efficient way. 
I have had a look at backup, I already do this I back up to usb, cd/dvd and external hdd, files or things I am doing projects with. I don't do recovery of the OS backups as I am unsure how to do this yet.
I haven't installed any additional software, or added any files yet.

Solved

---

### Post by mastablasta on 2017-02-07
> **bitsnpcs said:**
> I will need to learn how to make a back up to restore settings, I can see it will be an efficient way. 
I have had a look at backup, I already do this I back up to usb, cd/dvd and external hdd, files or things I am doing projects with. I don't do recovery of the OS backups as I am unsure how to do this yet.
I haven't installed any additional software, or added any files yet.

or you cna image the whole disk drive :)

clonezilla screen by screen - save disk image and restore disk image:

[http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image)

~

[http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/02_Restore_disk_image](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/02_Restore_disk_image)

as for your issues - have you tried with 16.10? do you have same issues? furthermore, does the computer have dual GPU chips?

the update that broke it was likely the kernel update. block it and post a bug report on Ubutnu launchpad, so they can fix it.

---

### Post by bitsnpcs on 2017-02-07
Thank You, I am checking out Clonezilla;)

I have not tried Ubuntu 16.10, I am using 16.04.1 LTS, because it is the LTS. I have tried Linux Lite 3.2, it would not boot up on this computer, the staff and community helped me to edit the grub with nomodeset to get to a desktop, this had to be done each time to boot up. I use Linux Lite on 2 of my other computers.
With Ubuntu 16.04.1 it boots after install and on rebooting, without any editing of the grub, the problem only occurs once an auto update occurs. So Ubuntu seemed a better option for this computer, I need to discover the issue and learn how to stop the update causing the issue. 

I am unsure if the computer has dual GPU chips, it is Intel 530HD integrated graphics, on Asus H110M-R motherboard, it can do vga or hdmi monitors, I am currently using VGA HD monitor, in a few weeks I get my first HDMI enabled monitor.
I had a look on Google and found a tutorial on Ubuntu website for the graphics id, and to list other info, the results are -

```
bitsnpcs@bitsnpcs:~$ sudo lshw -C display
[sudo] password for bitsnpcs: 
  *-display               
       description: VGA compatible controller
       product: Sky Lake Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915_bpo latency=0
       resources: irq:123 memory:f6000000-f6ffffff memory:e0000000-efffffff ioport:f000(size=64)
bitsnpcs@bitsnpcs:~$ lspci
00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 06)
00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31)
00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA controller [AHCI mode] (rev 31)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #5 (rev f1)
00:1c.7 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #8 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #9 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
bitsnpcs@bitsnpcs:~$ 
```

I do not know how to block the Kernel or other updates. 
I only know how to block updates of PPA using the system settings>software and updates>other software ,untick the PPA and save changes.Or to remove PPA in this gui.

In the Ubuntu Software it said 23 updates, this changed to 21, a few hours later this changed back to 23, which is the current count.
The difference to previous Ubuntu install is I have not turned off this computer, since yesterday and then restarted it, I have just moved the mouse/entered password, to wake it up from the default locked screen.

I am unsure if the updates are related to each other/which ones work together.
It would be good to -
1/ learn how to download the updates 1 at a time.
2/ this will enable me to identify the exact update that causes the issue
3/ I then need to learn how to prevent that update happening in future

I am thinking it is a graphics or driver issue, because the black screen is a graphics issue, and the errors were for the motherboard, which is where the integrated graphics are, as I don't have a PCIe graphics card installed.
In the system settings>details icon, it has the install updates icon enabled for updating the processor and graphics drivers, so I know one of those auto updates is these drivers as this was not enabled before them. I think it is likely turning the computer off waiting and turning it back on, will cause the black screen as it will change those drivers without any action from myself as this is what it done previously.
I then wouldn't be able to access the software and updates gui to select the working drivers again, and would need to reinstall Ubuntu.

The log file has not been created after the auto updates the results on checking after them are -

```
bitsnpcs@bitsnpcs:~$ /var/log/unattended-upgrades/unattended-upgrades.log
bash: /var/log/unattended-upgrades/unattended-upgrades.log: No such file or directory
bitsnpcs@bitsnpcs:~$ 
```

Here is an up to date results, as you can see the previous one said 327 updates available, and this one is 228, so overnight and today, so far, 99 packages have been auto installed.

```
sudo apt update
[sudo] password for bitsnpcs: 
Hit:1 http://gb.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Get:3 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Fetched 306 kB in 0s (595 kB/s)                             
Reading package lists... Done
Building dependency tree       
Reading state information... Done
228 packages can be upgraded. Run 'apt list --upgradable' to see them.
bitsnpcs@bitsnpcs:~$ apt list --upgradable
Listing... Done
accountsservice/xenial-updates 0.6.40-2ubuntu11.3 amd64 [upgradable from: 0.6.40-2ubuntu11.1]
apparmor/xenial-updates 2.10.95-0ubuntu2.5 amd64 [upgradable from: 2.10.95-0ubuntu2]
apport/xenial-updates,xenial-updates 2.20.1-0ubuntu2.5 all [upgradable from: 2.20.1-0ubuntu2.4]
apport-gtk/xenial-updates,xenial-updates 2.20.1-0ubuntu2.5 all [upgradable from: 2.20.1-0ubuntu2.4]
appstream/xenial-updates 0.9.4-1ubuntu2 amd64 [upgradable from: 0.9.4-1ubuntu1]
apt/xenial-updates 1.2.19 amd64 [upgradable from: 1.2.15ubuntu0.2]
apt-transport-https/xenial-updates 1.2.19 amd64 [upgradable from: 1.2.15ubuntu0.2]
apt-utils/xenial-updates 1.2.19 amd64 [upgradable from: 1.2.15ubuntu0.2]
bamfdaemon/xenial-updates 0.5.3~bzr0+16.04.20160824-0ubuntu1 amd64 [upgradable from: 0.5.3~bzr0+16.04.20160701-0ubuntu1]
base-files/xenial-updates 9.4ubuntu4.3 amd64 [upgradable from: 9.4ubuntu4.2]
bsdutils/xenial-updates 1:2.27.1-6ubuntu3.2 amd64 [upgradable from: 1:2.27.1-6ubuntu3.1]
compiz/xenial-updates,xenial-updates 1:0.9.12.2+16.04.20160823-0ubuntu1 all [upgradable from: 1:0.9.12.2+16.04.20160714-0ubuntu1]
compiz-core/xenial-updates 1:0.9.12.2+16.04.20160823-0ubuntu1 amd64 [upgradable from: 1:0.9.12.2+16.04.20160714-0ubuntu1]
compiz-gnome/xenial-updates 1:0.9.12.2+16.04.20160823-0ubuntu1 amd64 [upgradable from: 1:0.9.12.2+16.04.20160714-0ubuntu1]
compiz-plugins-default/xenial-updates 1:0.9.12.2+16.04.20160823-0ubuntu1 amd64 [upgradable from: 1:0.9.12.2+16.04.20160714-0ubuntu1]
cups-browsed/xenial-updates 1.8.3-2ubuntu3.1 amd64 [upgradable from: 1.8.3-2ubuntu3]
cups-filters/xenial-updates 1.8.3-2ubuntu3.1 amd64 [upgradable from: 1.8.3-2ubuntu3]
cups-filters-core-drivers/xenial-updates 1.8.3-2ubuntu3.1 amd64 [upgradable from: 1.8.3-2ubuntu3]
dbus/xenial-updates 1.10.6-1ubuntu3.3 amd64 [upgradable from: 1.10.6-1ubuntu3.1]
dbus-x11/xenial-updates 1.10.6-1ubuntu3.3 amd64 [upgradable from: 1.10.6-1ubuntu3.1]
deja-dup/xenial-updates 34.2-0ubuntu1.1 amd64 [upgradable from: 34.2-0ubuntu1]
distro-info-data/xenial-updates,xenial-updates 0.28ubuntu0.2 all [upgradable from: 0.28ubuntu0.1]
fuse/xenial-updates 2.9.4-1ubuntu3.1 amd64 [upgradable from: 2.9.4-1ubuntu3]
fwupd/xenial-updates 0.7.0-0ubuntu4.3 amd64 [upgradable from: 0.7.0-0ubuntu4.2]
gir1.2-dbusmenu-glib-0.4/xenial-updates 16.04.1+16.04.20160927-0ubuntu1 amd64 [upgradable from: 12.10.3+16.04.20160223.1-0ubuntu1]
gir1.2-gst-plugins-base-1.0/xenial-updates 1.8.3-1ubuntu0.1 amd64 [upgradable from: 1.8.2-1ubuntu0.2]
gir1.2-gstreamer-1.0/xenial-updates 1.8.3-1~ubuntu0.1 amd64 [upgradable from: 1.8.2-1~ubuntu1]
gnome-calculator/xenial-updates 1:3.18.3-0ubuntu1.16.04.1 amd64 [upgradable from: 1:3.18.3-0ubuntu1]
gnome-calendar/xenial-updates 3.20.4-0ubuntu0.1 amd64 [upgradable from: 3.20.2-0ubuntu0.1]
gnome-font-viewer/xenial-updates 3.16.2-1ubuntu1 amd64 [upgradable from: 3.16.2-1build1]
gnome-session-bin/xenial-updates 3.18.1.2-1ubuntu1.16.04.2 amd64 [upgradable from: 3.18.1.2-1ubuntu1.16.04.1]
gnome-session-common/xenial-updates,xenial-updates 3.18.1.2-1ubuntu1.16.04.2 all [upgradable from: 3.18.1.2-1ubuntu1.16.04.1]
gnome-settings-daemon-schemas/xenial-updates,xenial-updates 3.18.2-0ubuntu3.1 all [upgradable from: 3.18.2-0ubuntu3]
gnome-software/xenial-updates 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 amd64 [upgradable from: 3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1]
gnome-software-common/xenial-updates,xenial-updates 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 all [upgradable from: 3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1]
gnome-sudoku/xenial-updates 1:3.18.4-0ubuntu2 amd64 [upgradable from: 1:3.18.2-1]
gnome-system-monitor/xenial-updates 3.18.2-1ubuntu1 amd64 [upgradable from: 3.18.2-1]
grub-common/xenial-updates 2.02~beta2-36ubuntu3.7 amd64 [upgradable from: 2.02~beta2-36ubuntu3.1]
grub-pc/xenial-updates 2.02~beta2-36ubuntu3.7 amd64 [upgradable from: 2.02~beta2-36ubuntu3.1]
grub-pc-bin/xenial-updates 2.02~beta2-36ubuntu3.7 amd64 [upgradable from: 2.02~beta2-36ubuntu3.1]
grub2-common/xenial-updates 2.02~beta2-36ubuntu3.7 amd64 [upgradable from: 2.02~beta2-36ubuntu3.1]
gstreamer1.0-alsa/xenial-updates 1.8.3-1ubuntu0.1 amd64 [upgradable from: 1.8.2-1ubuntu0.2]
gstreamer1.0-plugins-base/xenial-updates 1.8.3-1ubuntu0.1 amd64 [upgradable from: 1.8.2-1ubuntu0.2]
gstreamer1.0-plugins-base-apps/xenial-updates 1.8.3-1ubuntu0.1 amd64 [upgradable from: 1.8.2-1ubuntu0.2]
gstreamer1.0-plugins-good/xenial-updates 1.8.3-1ubuntu0.3 amd64 [upgradable from: 1.8.2-1ubuntu0.3]
gstreamer1.0-pulseaudio/xenial-updates 1.8.3-1ubuntu0.3 amd64 [upgradable from: 1.8.2-1ubuntu0.3]
gstreamer1.0-tools/xenial-updates 1.8.3-1~ubuntu0.1 amd64 [upgradable from: 1.8.2-1~ubuntu1]
gstreamer1.0-x/xenial-updates 1.8.3-1ubuntu0.1 amd64 [upgradable from: 1.8.2-1ubuntu0.2]
gtk2-engines-murrine/xenial-updates 0.98.2-0ubuntu2.2 amd64 [upgradable from: 0.98.2-0ubuntu2.1]
humanity-icon-theme/xenial-updates,xenial-updates 0.6.10.1 all [upgradable from: 0.6.10]
ifupdown/xenial-updates 0.8.10ubuntu1.2 amd64 [upgradable from: 0.8.10ubuntu1]
im-config/xenial-updates,xenial-updates 0.29-1ubuntu12.3 all [upgradable from: 0.29-1ubuntu12]
init/xenial-updates 1.29ubuntu3 amd64 [upgradable from: 1.29ubuntu2]
init-system-helpers/xenial-updates,xenial-updates 1.29ubuntu3 all [upgradable from: 1.29ubuntu2]
initramfs-tools/xenial-updates,xenial-updates 0.122ubuntu8.8 all [upgradable from: 0.122ubuntu8.1]
initramfs-tools-bin/xenial-updates 0.122ubuntu8.8 amd64 [upgradable from: 0.122ubuntu8.1]
initramfs-tools-core/xenial-updates,xenial-updates 0.122ubuntu8.8 all [upgradable from: 0.122ubuntu8.1]
isc-dhcp-client/xenial-updates 4.3.3-5ubuntu12.6 amd64 [upgradable from: 4.3.3-5ubuntu12.1]
isc-dhcp-common/xenial-updates 4.3.3-5ubuntu12.6 amd64 [upgradable from: 4.3.3-5ubuntu12.1]
kbd/xenial-updates 1.15.5-1ubuntu5 amd64 [upgradable from: 1.15.5-1ubuntu4]
klibc-utils/xenial-updates 2.0.4-8ubuntu1.16.04.2 amd64 [upgradable from: 2.0.4-8ubuntu1.16.04.1]
krb5-locales/xenial-updates,xenial-updates 1.13.2+dfsg-5ubuntu2 all [upgradable from: 1.13.2+dfsg-5]
language-selector-common/xenial-updates,xenial-updates 0.165.4 all [upgradable from: 0.165.3]
language-selector-gnome/xenial-updates,xenial-updates 0.165.4 all [upgradable from: 0.165.3]
less/xenial-updates 481-2.1ubuntu0.1 amd64 [upgradable from: 481-2.1]
libaccountsservice0/xenial-updates 0.6.40-2ubuntu11.3 amd64 [upgradable from: 0.6.40-2ubuntu11.1]
libapparmor-perl/xenial-updates 2.10.95-0ubuntu2.5 amd64 [upgradable from: 2.10.95-0ubuntu2]
libapparmor1/xenial-updates 2.10.95-0ubuntu2.5 amd64 [upgradable from: 2.10.95-0ubuntu2]
libappstream-glib8/xenial-updates 0.5.13-1ubuntu4 amd64 [upgradable from: 0.5.13-1ubuntu2]
libappstream3/xenial-updates 0.9.4-1ubuntu2 amd64 [upgradable from: 0.9.4-1ubuntu1]
libapt-inst2.0/xenial-updates 1.2.19 amd64 [upgradable from: 1.2.15ubuntu0.2]
libapt-pkg5.0/xenial-updates 1.2.19 amd64 [upgradable from: 1.2.15ubuntu0.2]
libbamf3-2/xenial-updates 0.5.3~bzr0+16.04.20160824-0ubuntu1 amd64 [upgradable from: 0.5.3~bzr0+16.04.20160701-0ubuntu1]
libblkid1/xenial-updates 2.27.1-6ubuntu3.2 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
libc-bin/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu3]
libc-dev-bin/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu3]
libc6/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu3]
libc6-dbg/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu3]
libc6-dev/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu3]
libcompizconfig0/xenial-updates 1:0.9.12.2+16.04.20160823-0ubuntu1 amd64 [upgradable from: 1:0.9.12.2+16.04.20160714-0ubuntu1]
libcupsfilters1/xenial-updates 1.8.3-2ubuntu3.1 amd64 [upgradable from: 1.8.3-2ubuntu3]
libdbus-1-3/xenial-updates 1.10.6-1ubuntu3.3 amd64 [upgradable from: 1.10.6-1ubuntu3.1]
libdbusmenu-glib4/xenial-updates 16.04.1+16.04.20160927-0ubuntu1 amd64 [upgradable from: 12.10.3+16.04.20160223.1-0ubuntu1]
libdbusmenu-gtk3-4/xenial-updates 16.04.1+16.04.20160927-0ubuntu1 amd64 [upgradable from: 12.10.3+16.04.20160223.1-0ubuntu1]
libdbusmenu-gtk4/xenial-updates 16.04.1+16.04.20160927-0ubuntu1 amd64 [upgradable from: 12.10.3+16.04.20160223.1-0ubuntu1]
libdecoration0/xenial-updates 1:0.9.12.2+16.04.20160823-0ubuntu1 amd64 [upgradable from: 1:0.9.12.2+16.04.20160714-0ubuntu1]
libdfu1/xenial-updates 0.7.0-0ubuntu4.3 amd64 [upgradable from: 0.7.0-0ubuntu4.2]
libdrm-amdgpu1/xenial-updates 2.4.67-1ubuntu0.16.04.2 amd64 [upgradable from: 2.4.67-1ubuntu0.16.04.1]
libdrm-intel1/xenial-updates 2.4.67-1ubuntu0.16.04.2 amd64 [upgradable from: 2.4.67-1ubuntu0.16.04.1]
libdrm-nouveau2/xenial-updates 2.4.67-1ubuntu0.16.04.2 amd64 [upgradable from: 2.4.67-1ubuntu0.16.04.1]
libdrm-radeon1/xenial-updates 2.4.67-1ubuntu0.16.04.2 amd64 [upgradable from: 2.4.67-1ubuntu0.16.04.1]
libdrm2/xenial-updates 2.4.67-1ubuntu0.16.04.2 amd64 [upgradable from: 2.4.67-1ubuntu0.16.04.1]
libegl1-mesa/xenial-updates 11.2.0-1ubuntu2.2 amd64 [upgradable from: 11.2.0-1ubuntu2]
libfcitx-config4/xenial-updates 1:4.2.9.1-1ubuntu1.16.04.2 amd64 [upgradable from: 1:4.2.9.1-1ubuntu1]
libfcitx-gclient0/xenial-updates 1:4.2.9.1-1ubuntu1.16.04.2 amd64 [upgradable from: 1:4.2.9.1-1ubuntu1]
libfcitx-utils0/xenial-updates 1:4.2.9.1-1ubuntu1.16.04.2 amd64 [upgradable from: 1:4.2.9.1-1ubuntu1]
libfdisk1/xenial-updates 2.27.1-6ubuntu3.2 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
libfontembed1/xenial-updates 1.8.3-2ubuntu3.1 amd64 [upgradable from: 1.8.3-2ubuntu3]
libframe6/xenial-updates 2.5.0daily13.06.05+16.04.20160809-0ubuntu1 amd64 [upgradable from: 2.5.0daily13.06.05-0ubuntu1]
libfuse2/xenial-updates 2.9.4-1ubuntu3.1 amd64 [upgradable from: 2.9.4-1ubuntu3]
libfwupd1/xenial-updates 0.7.0-0ubuntu4.3 amd64 [upgradable from: 0.7.0-0ubuntu4.2]
libgbm1/xenial-updates 11.2.0-1ubuntu2.2 amd64 [upgradable from: 11.2.0-1ubuntu2]
libgl1-mesa-dri/xenial-updates 11.2.0-1ubuntu2.2 amd64 [upgradable from: 11.2.0-1ubuntu2]
libgl1-mesa-glx/xenial-updates 11.2.0-1ubuntu2.2 amd64 [upgradable from: 11.2.0-1ubuntu2]
libglapi-mesa/xenial-updates 11.2.0-1ubuntu2.2 amd64 [upgradable from: 11.2.0-1ubuntu2]
libglib2.0-0/xenial-updates 2.48.2-0ubuntu1 amd64 [upgradable from: 2.48.1-1~ubuntu16.04.1]
libglib2.0-bin/xenial-updates 2.48.2-0ubuntu1 amd64 [upgradable from: 2.48.1-1~ubuntu16.04.1]
libglib2.0-data/xenial-updates,xenial-updates 2.48.2-0ubuntu1 all [upgradable from: 2.48.1-1~ubuntu16.04.1]
libgssapi-krb5-2/xenial-updates 1.13.2+dfsg-5ubuntu2 amd64 [upgradable from: 1.13.2+dfsg-5]
libgstreamer-plugins-base1.0-0/xenial-updates 1.8.3-1ubuntu0.1 amd64 [upgradable from: 1.8.2-1ubuntu0.2]
libgstreamer-plugins-good1.0-0/xenial-updates 1.8.3-1ubuntu0.3 amd64 [upgradable from: 1.8.2-1ubuntu0.3]
libgstreamer1.0-0/xenial-updates 1.8.3-1~ubuntu0.1 amd64 [upgradable from: 1.8.2-1~ubuntu1]
libgweather-3-6/xenial-updates 3.18.2-0ubuntu0.1 amd64 [upgradable from: 3.18.1-1ubuntu1]
libgweather-common/xenial-updates,xenial-updates 3.18.2-0ubuntu0.1 all [upgradable from: 3.18.1-1ubuntu1]
libido3-0.1-0/xenial-updates 13.10.0+16.04.20161028-0ubuntu1 amd64 [upgradable from: 13.10.0+15.10.20151002-0ubuntu1]
libk5crypto3/xenial-updates 1.13.2+dfsg-5ubuntu2 amd64 [upgradable from: 1.13.2+dfsg-5]
libklibc/xenial-updates 2.0.4-8ubuntu1.16.04.2 amd64 [upgradable from: 2.0.4-8ubuntu1.16.04.1]
libkrb5-3/xenial-updates 1.13.2+dfsg-5ubuntu2 amd64 [upgradable from: 1.13.2+dfsg-5]
libkrb5support0/xenial-updates 1.13.2+dfsg-5ubuntu2 amd64 [upgradable from: 1.13.2+dfsg-5]
liblightdm-gobject-1-0/xenial-updates 1.18.3-0ubuntu1 amd64 [upgradable from: 1.18.2-0ubuntu1]
libllvm3.8/xenial-updates 1:3.8-2ubuntu4 amd64 [upgradable from: 1:3.8-2ubuntu3]
libmetacity-private3a/xenial-updates 1:3.18.7-0ubuntu0.2 amd64 [upgradable from: 1:3.18.5-0ubuntu0.1]
libmount1/xenial-updates 2.27.1-6ubuntu3.2 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
libnautilus-extension1a/xenial-updates 1:3.18.4.is.3.14.3-0ubuntu5 amd64 [upgradable from: 1:3.18.4.is.3.14.3-0ubuntu4]
libnm-glib-vpn1/xenial-updates 1.2.2-0ubuntu0.16.04.3 amd64 [upgradable from: 1.2.0-0ubuntu0.16.04.3]
libnm-glib4/xenial-updates 1.2.2-0ubuntu0.16.04.3 amd64 [upgradable from: 1.2.0-0ubuntu0.16.04.3]
libnm-gtk-common/xenial-updates,xenial-updates 1.2.0-0ubuntu0.16.04.4 all [upgradable from: 1.2.0-0ubuntu0.16.04.3]
libnm-gtk0/xenial-updates 1.2.0-0ubuntu0.16.04.4 amd64 [upgradable from: 1.2.0-0ubuntu0.16.04.3]
libnm-util2/xenial-updates 1.2.2-0ubuntu0.16.04.3 amd64 [upgradable from: 1.2.0-0ubuntu0.16.04.3]
libnm0/xenial-updates 1.2.2-0ubuntu0.16.04.3 amd64 [upgradable from: 1.2.0-0ubuntu0.16.04.3]
libnma-common/xenial-updates,xenial-updates 1.2.0-0ubuntu0.16.04.4 all [upgradable from: 1.2.0-0ubuntu0.16.04.3]
libnma0/xenial-updates 1.2.0-0ubuntu0.16.04.4 amd64 [upgradable from: 1.2.0-0ubuntu0.16.04.3]
liboxideqt-qmlplugin/xenial-updates,xenial-security 1.19.4-0ubuntu0.16.04.1 amd64 [upgradable from: 1.15.8-0ubuntu0.16.04.1]
liboxideqtcore0/xenial-updates,xenial-security 1.19.4-0ubuntu0.16.04.1 amd64 [upgradable from: 1.15.8-0ubuntu0.16.04.1]
liboxideqtquick0/xenial-updates,xenial-security 1.19.4-0ubuntu0.16.04.1 amd64 [upgradable from: 1.15.8-0ubuntu0.16.04.1]
libp11-kit0/xenial-updates 0.23.2-5~ubuntu16.04.1 amd64 [upgradable from: 0.23.2-3]
libpam-systemd/xenial-updates 229-4ubuntu16 amd64 [upgradable from: 229-4ubuntu10]
libpoppler-glib8/xenial-updates 0.41.0-0ubuntu1.1 amd64 [upgradable from: 0.41.0-0ubuntu1]
libpoppler58/xenial-updates 0.41.0-0ubuntu1.1 amd64 [upgradable from: 0.41.0-0ubuntu1]
libprocps4/xenial-updates 2:3.3.10-4ubuntu2.3 amd64 [upgradable from: 2:3.3.10-4ubuntu2]
libpulse-mainloop-glib0/xenial-updates 1:8.0-0ubuntu3.2 amd64 [upgradable from: 1:8.0-0ubuntu3]
libpulse0/xenial-updates 1:8.0-0ubuntu3.2 amd64 [upgradable from: 1:8.0-0ubuntu3]
libpulsedsp/xenial-updates 1:8.0-0ubuntu3.2 amd64 [upgradable from: 1:8.0-0ubuntu3]
libqt5core5a/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5dbus5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5gui5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5network5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5opengl5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5printsupport5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5sql5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5sql5-sqlite/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5test5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5widgets5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libqt5xml5/xenial-updates 5.5.1+dfsg-16ubuntu7.2 amd64 [upgradable from: 5.5.1+dfsg-16ubuntu7.1]
libsmartcols1/xenial-updates 2.27.1-6ubuntu3.2 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
libsystemd0/xenial-updates 229-4ubuntu16 amd64 [upgradable from: 229-4ubuntu10]
libudev1/xenial-updates 229-4ubuntu16 amd64 [upgradable from: 229-4ubuntu10]
libunity-core-6.0-9/xenial-updates 7.4.0+16.04.20160906-0ubuntu1 amd64 [upgradable from: 7.4.0+16.04.20160715-0ubuntu1]
libuuid1/xenial-updates 2.27.1-6ubuntu3.2 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
libwayland-egl1-mesa/xenial-updates 11.2.0-1ubuntu2.2 amd64 [upgradable from: 11.2.0-1ubuntu2]
libwhoopsie0/xenial-updates 0.2.52.2 amd64 [upgradable from: 0.2.52.1]
libxatracker2/xenial-updates 11.2.0-1ubuntu2.2 amd64 [upgradable from: 11.2.0-1ubuntu2]
light-themes/xenial-updates,xenial-updates 14.04+16.04.20161024-0ubuntu1 all [upgradable from: 14.04+16.04.20160621-0ubuntu1]
lightdm/xenial-updates 1.18.3-0ubuntu1 amd64 [upgradable from: 1.18.2-0ubuntu1]
linux-firmware/xenial-updates,xenial-updates 1.157.6 all [upgradable from: 1.157.4]
locales/xenial-updates,xenial-updates 2.23-0ubuntu5 all [upgradable from: 2.23-0ubuntu3]
metacity-common/xenial-updates,xenial-updates 1:3.18.7-0ubuntu0.2 all [upgradable from: 1:3.18.5-0ubuntu0.1]
mount/xenial-updates 2.27.1-6ubuntu3.2 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
mtools/xenial-updates 4.0.18-2ubuntu0.16.04 amd64 [upgradable from: 4.0.18-2]
multiarch-support/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu3]
nano/xenial-updates 2.5.3-2ubuntu1 amd64 [upgradable from: 2.5.3-2]
nautilus/xenial-updates 1:3.18.4.is.3.14.3-0ubuntu5 amd64 [upgradable from: 1:3.18.4.is.3.14.3-0ubuntu4]
nautilus-data/xenial-updates,xenial-updates 1:3.18.4.is.3.14.3-0ubuntu5 all [upgradable from: 1:3.18.4.is.3.14.3-0ubuntu4]
network-manager/xenial-updates 1.2.2-0ubuntu0.16.04.3 amd64 [upgradable from: 1.2.0-0ubuntu0.16.04.3]
network-manager-gnome/xenial-updates 1.2.0-0ubuntu0.16.04.4 amd64 [upgradable from: 1.2.0-0ubuntu0.16.04.3]
overlay-scrollbar/xenial-updates,xenial-updates 0.2.17.1+16.04.20151117-0ubuntu1.16.04.1 all [upgradable from: 0.2.17.1+16.04.20151117-0ubuntu1]
overlay-scrollbar-gtk2/xenial-updates 0.2.17.1+16.04.20151117-0ubuntu1.16.04.1 amd64 [upgradable from: 0.2.17.1+16.04.20151117-0ubuntu1]
oxideqt-codecs/xenial-updates,xenial-security 1.19.4-0ubuntu0.16.04.1 amd64 [upgradable from: 1.15.8-0ubuntu0.16.04.1]
p11-kit/xenial-updates 0.23.2-5~ubuntu16.04.1 amd64 [upgradable from: 0.23.2-3]
p11-kit-modules/xenial-updates 0.23.2-5~ubuntu16.04.1 amd64 [upgradable from: 0.23.2-3]
poppler-utils/xenial-updates 0.41.0-0ubuntu1.1 amd64 [upgradable from: 0.41.0-0ubuntu1]
procps/xenial-updates 2:3.3.10-4ubuntu2.3 amd64 [upgradable from: 2:3.3.10-4ubuntu2]
pulseaudio/xenial-updates 1:8.0-0ubuntu3.2 amd64 [upgradable from: 1:8.0-0ubuntu3]
pulseaudio-module-bluetooth/xenial-updates 1:8.0-0ubuntu3.2 amd64 [upgradable from: 1:8.0-0ubuntu3]
pulseaudio-module-x11/xenial-updates 1:8.0-0ubuntu3.2 amd64 [upgradable from: 1:8.0-0ubuntu3]
pulseaudio-utils/xenial-updates 1:8.0-0ubuntu3.2 amd64 [upgradable from: 1:8.0-0ubuntu3]
python3-apport/xenial-updates,xenial-updates 2.20.1-0ubuntu2.5 all [upgradable from: 2.20.1-0ubuntu2.4]
python3-distupgrade/xenial-updates,xenial-updates 1:16.04.21 all [upgradable from: 1:16.04.14]
python3-problem-report/xenial-updates,xenial-updates 2.20.1-0ubuntu2.5 all [upgradable from: 2.20.1-0ubuntu2.4]
python3-software-properties/xenial-updates,xenial-updates 0.96.20.5 all [upgradable from: 0.96.20.2]
python3-update-manager/xenial-updates,xenial-updates 1:16.04.5 all [upgradable from: 1:16.04.3]
qml-module-ubuntu-web/xenial-updates 0.23+16.04.20161028-0ubuntu2 amd64 [upgradable from: 0.23+16.04.20160413-0ubuntu1]
snapd/xenial-updates 2.21 amd64 [upgradable from: 2.0.10]
software-properties-common/xenial-updates,xenial-updates 0.96.20.5 all [upgradable from: 0.96.20.2]
software-properties-gtk/xenial-updates,xenial-updates 0.96.20.5 all [upgradable from: 0.96.20.2]
sudo/xenial-updates 1.8.16-0ubuntu1.2 amd64 [upgradable from: 1.8.16-0ubuntu1.1]
suru-icon-theme/xenial-updates,xenial-updates 14.04+16.04.20161024-0ubuntu1 all [upgradable from: 14.04+16.04.20160621-0ubuntu1]
systemd/xenial-updates 229-4ubuntu16 amd64 [upgradable from: 229-4ubuntu10]
systemd-sysv/xenial-updates 229-4ubuntu16 amd64 [upgradable from: 229-4ubuntu10]
ubuntu-artwork/xenial-updates,xenial-updates 1:14.04+16.04.20161024-0ubuntu1 all [upgradable from: 1:14.04+16.04.20160621-0ubuntu1]
ubuntu-core-launcher/xenial-updates 2.21 amd64 [upgradable from: 1.0.27.1]
ubuntu-drivers-common/xenial-updates 1:0.4.17.2 amd64 [upgradable from: 1:0.4.17.1]
ubuntu-mobile-icons/xenial-updates,xenial-updates 14.04+16.04.20161024-0ubuntu1 all [upgradable from: 14.04+16.04.20160621-0ubuntu1]
ubuntu-mono/xenial-updates,xenial-updates 14.04+16.04.20161024-0ubuntu1 all [upgradable from: 14.04+16.04.20160621-0ubuntu1]
ubuntu-release-upgrader-core/xenial-updates,xenial-updates 1:16.04.21 all [upgradable from: 1:16.04.14]
ubuntu-release-upgrader-gtk/xenial-updates,xenial-updates 1:16.04.21 all [upgradable from: 1:16.04.14]
ubuntu-session/xenial-updates,xenial-updates 3.18.1.2-1ubuntu1.16.04.2 all [upgradable from: 3.18.1.2-1ubuntu1.16.04.1]
ubuntu-software/xenial-updates 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 amd64 [upgradable from: 3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1]
udev/xenial-updates 229-4ubuntu16 amd64 [upgradable from: 229-4ubuntu10]
unattended-upgrades/xenial-updates,xenial-updates 0.90ubuntu0.3 all [upgradable from: 0.90]
unity/xenial-updates 7.4.0+16.04.20160906-0ubuntu1 amd64 [upgradable from: 7.4.0+16.04.20160715-0ubuntu1]
unity-schemas/xenial-updates,xenial-updates 7.4.0+16.04.20160906-0ubuntu1 all [upgradable from: 7.4.0+16.04.20160715-0ubuntu1]
unity-services/xenial-updates 7.4.0+16.04.20160906-0ubuntu1 amd64 [upgradable from: 7.4.0+16.04.20160715-0ubuntu1]
update-manager/xenial-updates,xenial-updates 1:16.04.5 all [upgradable from: 1:16.04.3]
update-manager-core/xenial-updates,xenial-updates 1:16.04.5 all [upgradable from: 1:16.04.3]
update-notifier/xenial-updates 3.168.3 amd64 [upgradable from: 3.168.1]
update-notifier-common/xenial-updates,xenial-updates 3.168.3 all [upgradable from: 3.168.1]
util-linux/xenial-updates 2.27.1-6ubuntu3.2 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
uuid-runtime/xenial-updates 2.27.1-6ubuntu3.2 amd64 [upgradable from: 2.27.1-6ubuntu3.1]
vino/xenial-updates 3.8.1-0ubuntu9.1 amd64 [upgradable from: 3.8.1-0ubuntu9]
webapp-container/xenial-updates 0.23+16.04.20161028-0ubuntu2 amd64 [upgradable from: 0.23+16.04.20160413-0ubuntu1]
webbrowser-app/xenial-updates 0.23+16.04.20161028-0ubuntu2 amd64 [upgradable from: 0.23+16.04.20160413-0ubuntu1]
whoopsie/xenial-updates 0.2.52.2 amd64 [upgradable from: 0.2.52.1]
xdg-utils/xenial-updates,xenial-updates 1.1.1-1ubuntu1.16.04.1 all [upgradable from: 1.1.1-1ubuntu1]
xdiagnose/xenial-updates,xenial-updates 3.8.4.1 all [upgradable from: 3.8.4]
xserver-common/xenial-updates,xenial-updates 2:1.18.4-0ubuntu0.2 all [upgradable from: 2:1.18.3-1ubuntu2.2]
xserver-xorg-core/xenial-updates 2:1.18.4-0ubuntu0.2 amd64 [upgradable from: 2:1.18.3-1ubuntu2.2]
xserver-xorg-video-intel/xenial-updates 2:2.99.917+git20160325-1ubuntu1.2 amd64 [upgradable from: 2:2.99.917+git20160325-1ubuntu1]
bitsnpcs@bitsnpcs:~$ 
```

---

### Post by bitsnpcs on 2017-02-08
> **mastablasta said:**
> 

as for your issues - have you tried with 16.10? do you have same issues? furthermore, does the computer have dual GPU chips?

the update that broke it was likely the kernel update. block it and post a bug report on Ubuntu launchpad, so they can fix it.

It asked me to reboot to complete the install of auto updates on 16.04.1 which gave me the black screen monitor to standby again.
I reinstalled 16.04.1 again, this time I just added all of the updates at once, thinking it may have a fix, or give me the options in system settings>software and updates>additional drivers  , I would have options to choose them before rebooting, it didn't give me any options at all for graphics, only to continue using the Intel cpu driver or do not use the device option, it nagged for a reboot, got a black screen again on reboot.

It seems that 1 of the 99 overnight auto installs,  is the problem one, when I return later, I will go through both results lists, compare manually and this will reduce the number of packages that could be the cause down to 99, I will post the list tonight when I have done this.

I downloaded 16.10, and tried to install this, it begins to boot the live dvd to the first  purple screen with the 2 icons at the bottom, then it goes to a black screen and the  monitor powers off. Seems like whatever causes the error on the auto install updates  in 16.04 is already on the downloaded file of 16.10

I have now reinstalled 16.04.1 again now.

Update -
I have compared the 555 packages using the first and second results, below are the 99 packages that were auto installed overnight , one of which is causing the problem ?

```
bind9-host/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
binutils/xenial-updates,xenial-security 2.26.1-1ubuntu1~16.04.3 amd64 [upgradable from: 2.26.1-1ubuntu1~16.04.1]
cpp-5/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
curl/xenial-updates,xenial-security 7.47.0-1ubuntu2.2 amd64 [upgradable from: 7.47.0-1ubuntu2]
dnsutils/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
eog/xenial-updates,xenial-security 3.18.2-1ubuntu2.1 amd64 [upgradable from: 3.18.2-1ubuntu1]
file-roller/xenial-updates,xenial-security 3.16.5-0ubuntu1.2 amd64 [upgradable from: 3.16.5-0ubuntu1.1]
firefox/xenial-updates,xenial-security 51.0.1+build2-0ubuntu0.16.04.2 amd64 [upgradable from: 47.0+build3-0ubuntu0.16.04.1]
fontconfig/xenial-updates,xenial-security 2.11.94-0ubuntu1.1 amd64 [upgradable from: 2.11.94-0ubuntu1]
fontconfig-config/xenial-updates,xenial-updates,xenial-security,xenial-security 2.11.94-0ubuntu1.1 all [upgradable from: 2.11.94-0ubuntu1]
g++-5/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
gcc-5/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
gcc-5-base/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
ghostscript/xenial-updates,xenial-security 9.18~dfsg~0-0ubuntu2.3 amd64 [upgradable from: 9.18~dfsg~0-0ubuntu2]
ghostscript-x/xenial-updates,xenial-security 9.18~dfsg~0-0ubuntu2.3 amd64 [upgradable from: 9.18~dfsg~0-0ubuntu2]
gir1.2-gdkpixbuf-2.0/xenial-updates,xenial-security 2.32.2-1ubuntu1.2 amd64 [upgradable from: 2.32.2-1ubuntu1]
gir1.2-javascriptcoregtk-4.0/xenial-updates,xenial-security 2.14.3-0ubuntu0.16.04.1 amd64 [upgradable from: 2.10.9-1ubuntu1]
gir1.2-webkit2-4.0/xenial-updates,xenial-security 2.14.3-0ubuntu0.16.04.1 amd64 [upgradable from: 2.10.9-1ubuntu1]
gnupg/xenial-updates,xenial-security 1.4.20-1ubuntu3.1 amd64 [upgradable from: 1.4.20-1ubuntu3]
gpgv/xenial-updates,xenial-security 1.4.20-1ubuntu3.1 amd64 [upgradable from: 1.4.20-1ubuntu3]
imagemagick/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.3 amd64 [upgradable from: 8:6.8.9.9-7ubuntu5.1]
imagemagick-6.q16/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.3 amd64 [upgradable from: 8:6.8.9.9-7ubuntu5.1]
imagemagick-common/xenial-updates,xenial-updates,xenial-security,xenial-security 8:6.8.9.9-7ubuntu5.3 all [upgradable from: 8:6.8.9.9-7ubuntu5.1]
libasan2/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libatomic1/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libbind9-140/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
libcc1-0/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libcilkrts5/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libcurl3/xenial-updates,xenial-security 7.47.0-1ubuntu2.2 amd64 [upgradable from: 7.47.0-1ubuntu2]
libcurl3-gnutls/xenial-updates,xenial-security 7.47.0-1ubuntu2.2 amd64 [upgradable from: 7.47.0-1ubuntu2]
libdns-export162/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
libdns162/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
libfontconfig1/xenial-updates,xenial-security 2.11.94-0ubuntu1.1 amd64 [upgradable from: 2.11.94-0ubuntu1]
libgcc-5-dev/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libgcrypt20/xenial-updates,xenial-security 1.6.5-2ubuntu0.2 amd64 [upgradable from: 1.6.5-2]
libgd3/xenial-updates,xenial-security 2.1.1-4ubuntu0.16.04.5 amd64 [upgradable from: 2.1.1-4ubuntu0.16.04.2]
libgdk-pixbuf2.0-0/xenial-updates,xenial-security 2.32.2-1ubuntu1.2 amd64 [upgradable from: 2.32.2-1ubuntu1]
libgdk-pixbuf2.0-common/xenial-updates,xenial-updates,xenial-security,xenial-security 2.32.2-1ubuntu1.2 all [upgradable from: 2.32.2-1ubuntu1]
libgnutls-openssl27/xenial-updates,xenial-security 3.4.10-4ubuntu1.2 amd64 [upgradable from: 3.4.10-4ubuntu1.1]
libgnutls30/xenial-updates,xenial-security 3.4.10-4ubuntu1.2 amd64 [upgradable from: 3.4.10-4ubuntu1.1]
libgomp1/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libgs9/xenial-updates,xenial-security 9.18~dfsg~0-0ubuntu2.3 amd64 [upgradable from: 9.18~dfsg~0-0ubuntu2]
libgs9-common/xenial-updates,xenial-updates,xenial-security,xenial-security 9.18~dfsg~0-0ubuntu2.3 all [upgradable from: 9.18~dfsg~0-0ubuntu2]
libharfbuzz-icu0/xenial-updates,xenial-security 1.0.1-1ubuntu0.1 amd64 [upgradable from: 1.0.1-1build2]
libharfbuzz0b/xenial-updates,xenial-security 1.0.1-1ubuntu0.1 amd64 [upgradable from: 1.0.1-1build2]
libhogweed4/xenial-security 3.2-1ubuntu0.16.04.1 amd64 [upgradable from: 3.2-1]
libidn11/xenial-updates,xenial-security 1.32-3ubuntu1.1 amd64 [upgradable from: 1.32-3ubuntu1]
libisc-export160/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
libisc160/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
libisccc140/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
libisccfg140/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
libitm1/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libjavascriptcoregtk-4.0-18/xenial-updates,xenial-security 2.14.3-0ubuntu0.16.04.1 amd64 [upgradable from: 2.10.9-1ubuntu1]
liblsan0/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
liblwres141/xenial-updates,xenial-security 1:9.10.3.dfsg.P4-8ubuntu1.4 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1]
libmagickcore-6.q16-2/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.3 amd64 [upgradable from: 8:6.8.9.9-7ubuntu5.1]
libmagickcore-6.q16-2-extra/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.3 amd64 [upgradable from: 8:6.8.9.9-7ubuntu5.1]
libmagickwand-6.q16-2/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.3 amd64 [upgradable from: 8:6.8.9.9-7ubuntu5.1]
libmpx0/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libnettle6/xenial-security 3.2-1ubuntu0.16.04.1 amd64 [upgradable from: 3.2-1]
libnss3/xenial-updates,xenial-security 2:3.26.2-0ubuntu0.16.04.2 amd64 [upgradable from: 2:3.23-0ubuntu0.16.04.1]
libnss3-nssdb/xenial-updates,xenial-updates,xenial-security,xenial-security 2:3.26.2-0ubuntu0.16.04.2 all [upgradable from: 2:3.23-0ubuntu0.16.04.1]
libpcsclite1/xenial-updates,xenial-security 1.8.14-1ubuntu1.16.04.1 amd64 [upgradable from: 1.8.14-1ubuntu1]
libpython2.7/xenial-updates,xenial-security 2.7.12-1ubuntu0~16.04.1 amd64 [upgradable from: 2.7.12-1~16.04]
libpython2.7-minimal/xenial-updates,xenial-security 2.7.12-1ubuntu0~16.04.1 amd64 [upgradable from: 2.7.12-1~16.04]
libpython2.7-stdlib/xenial-updates,xenial-security 2.7.12-1ubuntu0~16.04.1 amd64 [upgradable from: 2.7.12-1~16.04]
libpython3.5/xenial-updates,xenial-security 3.5.2-2ubuntu0~16.04.1 amd64 [upgradable from: 3.5.2-2~16.01]
libpython3.5-minimal/xenial-updates,xenial-security 3.5.2-2ubuntu0~16.04.1 amd64 [upgradable from: 3.5.2-2~16.01]
libpython3.5-stdlib/xenial-updates,xenial-security 3.5.2-2ubuntu0~16.04.1 amd64 [upgradable from: 3.5.2-2~16.01]
libquadmath0/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libsmbclient/xenial-updates,xenial-security 2:4.3.11+dfsg-0ubuntu0.16.04.3 amd64 [upgradable from: 2:4.3.9+dfsg-0ubuntu0.16.04.2]
libssl1.0.0/xenial-updates,xenial-security 1.0.2g-1ubuntu4.6 amd64 [upgradable from: 1.0.2g-1ubuntu4.1]
libstdc++-5-dev/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libstdc++6/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libtracker-sparql-1.0-0/xenial-updates,xenial-security 1.6.2-0ubuntu1.1 amd64 [upgradable from: 1.6.2-0ubuntu1]
libtsan0/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libubsan0/xenial-updates,xenial-security 5.4.0-6ubuntu1~16.04.4 amd64 [upgradable from: 5.4.0-6ubuntu1~16.04.1]
libvncclient1/xenial-updates,xenial-security 0.9.10+dfsg-3ubuntu0.16.04.1 amd64 [upgradable from: 0.9.10+dfsg-3build1]
libwbclient0/xenial-updates,xenial-security 2:4.3.11+dfsg-0ubuntu0.16.04.3 amd64 [upgradable from: 2:4.3.9+dfsg-0ubuntu0.16.04.2]
libwebkit2gtk-4.0-37/xenial-updates,xenial-security 2.14.3-0ubuntu0.16.04.1 amd64 [upgradable from: 2.10.9-1ubuntu1]
libwebkit2gtk-4.0-37-gtk2/xenial-updates,xenial-security 2.14.3-0ubuntu0.16.04.1 amd64 [upgradable from: 2.10.9-1ubuntu1]
libxpm4/xenial-updates,xenial-security 1:3.5.11-1ubuntu0.16.04.1 amd64 [upgradable from: 1:3.5.11-1]
linux-generic/xenial-updates,xenial-security 4.4.0.62.65 amd64 [upgradable from: 4.4.0.31.33]
linux-headers-generic/xenial-updates,xenial-security 4.4.0.62.65 amd64 [upgradable from: 4.4.0.31.33]
linux-image-generic/xenial-updates,xenial-security 4.4.0.62.65 amd64 [upgradable from: 4.4.0.31.33]
linux-libc-dev/xenial-updates,xenial-security 4.4.0-62.83 amd64 [upgradable from: 4.4.0-31.50]
ntfs-3g/xenial-updates,xenial-security 1:2015.3.14AR.1-1ubuntu0.1 amd64 [upgradable from: 1:2015.3.14AR.1-1build1]
openssh-client/xenial-updates,xenial-security 1:7.2p2-4ubuntu2.1 amd64 [upgradable from: 1:7.2p2-4ubuntu1]
openssl/xenial-updates,xenial-security 1.0.2g-1ubuntu4.6 amd64 [upgradable from: 1.0.2g-1ubuntu4.1]
python2.7/xenial-updates,xenial-security 2.7.12-1ubuntu0~16.04.1 amd64 [upgradable from: 2.7.12-1~16.04]
python2.7-minimal/xenial-updates,xenial-security 2.7.12-1ubuntu0~16.04.1 amd64 [upgradable from: 2.7.12-1~16.04]
python3-cryptography/xenial-updates,xenial-security 1.2.3-1ubuntu0.1 amd64 [upgradable from: 1.2.3-1]
python3.5/xenial-updates,xenial-security 3.5.2-2ubuntu0~16.04.1 amd64 [upgradable from: 3.5.2-2~16.01]
python3.5-minimal/xenial-updates,xenial-security 3.5.2-2ubuntu0~16.04.1 amd64 [upgradable from: 3.5.2-2~16.01]
samba-libs/xenial-updates,xenial-security 2:4.3.11+dfsg-0ubuntu0.16.04.3 amd64 [upgradable from: 2:4.3.9+dfsg-0ubuntu0.16.04.2]
tar/xenial-updates,xenial-security 1.28-2.1ubuntu0.1 amd64 [upgradable from: 1.28-2.1]
tzdata/xenial-updates,xenial-updates,xenial-security,xenial-security 2016j-0ubuntu0.16.04 all [upgradable from: 2016f-0ubuntu0.16.04]
vim-common/xenial-updates,xenial-security 2:7.4.1689-3ubuntu1.2 amd64 [upgradable from: 2:7.4.1689-3ubuntu1.1]
vim-tiny/xenial-updates,xenial-security 2:7.4.1689-3ubuntu1.2 amd64 [upgradable from: 2:7.4.1689-3ubuntu1.1]
```

---

### Post by mastablasta on 2017-02-09
> 
 I do not know how to block the Kernel or other updates. 


option 1: before applying the updates deselect the kernel update.
option 2: install synaptic package manager, lock the kernel package 8forgot exactly how it is done but as i remember you right click it and select lock.
option 3: download and install 16.04 - it will hold the kernel at the first one (which seems to work).

you do not need to reinstall each time. if kernel is the issue, hold shift on boot until GRUB appears (or set grub timeout to say 7 sec and it will always appear). then select the older kernel and use that to boot it. see if that helps.


> **bitsnpcs said:**
> It asked me to reboot to complete the install of auto updates on 16.04.1 which gave me the black screen monitor to standby again.
I reinstalled 16.04.1 again, this time I just added all of the updates at once, thinking it may have a fix, or give me the options in system settings>software and updates>additional drivers  , I would have options to choose them before rebooting, it didn't give me any options at all for graphics, only to continue using the Intel cpu driver or do not use the device option, it nagged for a reboot, got a black screen again on reboot.

looks like only one GPU then. this will hopefully be easier to troubleshoot.
General blank screen trooubleshooting: [URL="https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen"][SIZE=2]https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen
[/SIZE][/URL]similar issue and specific for your chip: [URL="http://askubuntu.com/questions/698168/cant-get-intel-hd-graphics-530-skylake-i7-6700-to-work"][SIZE=2]http://askubuntu.com/questions/698168/cant-get-intel-hd-graphics-530-skylake-i7-6700-to-work
[/SIZE][/URL]
There is a intel graphics installer. plus according to one user you can also boot using [I]i915.modeset=0 
[/I]
how to add command to grub: [URL="http://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter"]https://help.ubuntu.com/community/BootOptions
[/URL]
this is not an ideal solution but it is a temporary one. or you can use it to boot and then install drivers using intel instaler. another **boot option** that might work is *nomodeset*

another solution for similar issue (scroll down a bit and ready the comments):

[URL="http://askubuntu.com/questions/845842/intel-skylake-blank-screen-on-ubuntu-16-10"]http://askubuntu.com/questions/845842/intel-skylake-blank-screen-on-ubuntu-16-10
[/URL]

> Are you using the display port ? I am also having troubles with skylake, kernel 4.8 and i915 drivers with Ubuntu 16.10 ==> Intel didn't release the latest graphics stack for 16.10 yet.
You could try to:
1) Switch back to Ubuntu 16.04 LTS (and kernel 4.4.x)
2) Use kernel 4.6.7: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6.7/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6.7/)
3) Use the latest drm-intel-nightly kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-nightly/) (but there is no amd64 successful build available anymore, last was 2016-10-19)


---

### Post by bitsnpcs on 2017-02-09
Thank you mastablasta.

I had installed Linux Lite 3.2 , it is an Ubuntu 16.04 base, I had help online to edit using nomodeset, but had to re enter on each reboot and didn't find out how to save it permanently, only using ctrl x.
I then tried Ubuntu 16.04 official which booted without needing nomodeset edit to the grub, but had to reinstall on each boot .

Someone posted a tutorial for me of how to edit leafpad (using "quiet splash nomodeset") via terminal and save, then update the grub from terminal command, I reinstalled Linux Lite 3.2 and have done this and it now boots, reboots, shutdown and restarts, all without any difficulty, it also accept updates including kernel and several drivers.

I have no options in additional software to select any graphic drivers, only option is for intel cpu driver or do not use the device, it is set on intel driver. Resolution is 640x480 pixels. 

I get the same error on updates as on one of the links you gave me, that i915 firmware is missing.

On the link #2 of your post, it discusses using the Intel graphics installer for Linux 1.4.0, will this be correct for Ubuntu 16.04 ?
It is a .deb file downloaded I am unsure if I need to unpack it in the downloads folder or which specific folder yet.
After running this and hopefully it finds a driver /installing a driver, should I remove nomodeset from the grub and update the grub before rebooting ?

Overall the improvement forward is the booting issue is solved, the graphics issue remains.
Once the graphics are done I will be adding Ubuntu 16.04 in virtual box, to follow a 7 hours Ubuntu video tutorial on youtube, including the setting up of VB.

---

### Post by mastablasta on 2017-02-10
> **bitsnpcs said:**
> 
On the link #2 of your post, it discusses using the Intel graphics installer for Linux 1.4.0, will this be correct for Ubuntu 16.04 ?

yes it seems to be for 16.04.

> 
It is a .deb file downloaded I am unsure if I need to unpack it in the downloads folder or which specific folder yet.

.deb is kind of like .exe file in windows, you are supposed to run it. or open it with software center.

> 
After running this and hopefully it finds a driver /installing a driver, should I remove nomodeset from the grub and update the grub before rebooting ?

Yes, that's how i understood the help pages. nomodeset pushes the graphics chip into a more basic software mode. it is often used until one can install the propper drivers. software mode means the CPU is doing the rendering rather than GPU so some things might be slower (YouTube and other videos, games...), but for other things this is not that important.

you are on a good path and i hope you can solve it or find a solution. the reis some reading ahead to sovle all issues but on the positive side you will learn a lot about computer this way. if oyu do not have the time for it now, then come back in April when 17.04 comes out. that one should support the chip well. 

> 
Once the graphics are done I will be adding Ubuntu 16.04 in virtual box, to follow a 7 hours Ubuntu video tutorial on youtube, including the setting up of VB.

7 hours? wow... let me offer a shorter step by step version: [SIZE=2][http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
[/SIZE]
it's with pics, with some sane default settings. it is for 12.04 but this basic stuff hasn't really changed since then.

---

### Post by bitsnpcs on 2017-02-10
Hello mastablasta,
thank you for your help, and the shorter version;)
I have updated the kernel to 4.9.0, installed 1.0.4 stack, it said already installed, so I chose remove option, restarted, then chose install option, removed nomodeset using leafpad via terminal, and updated the grub in terminal.
It has worked :p
Maximum resolution is now 1024, booting is lovely, video plays perfectly including YouTube.

It says there is a 1.5.0 released February 2017 that replaces 1.4.0, supplying bug fixes, would it be worth upgrading,  and if so do I need to remove 1.4.0 first or the 1.5.0 will do this as part of its install ?

I have also made restore points before kernel upgrade and afterwards, and after installing the stack, I have also now done a restore live iso using systemback, and burnt to usb using dd command in terminal.

Update - I now have completed setup of Ubuntu 16.04 running in virtual box with the LL host, and I have done updates regularly, and several installs, everything is running well. Thank You.

---

