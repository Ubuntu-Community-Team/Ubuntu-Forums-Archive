---
title: "HOWTO:  Thinklight Notification for Evolution"
date: 2008-12-20
forum: Outdated Tutorials &amp; Tips
---

### Post by uljanow on 2008-12-20
This article describes how to enable [Thinklight]("http://en.wikipedia.org/wiki/Thinklight") notification for [Evolution]("http://projects.gnome.org/evolution"). The package **thinklight-notification** is an **Evolution** plugin to notify the user with a blinking light whenever a new message has arrived.

**[SIZE="3"]Installation (Intrepid)[/SIZE]**
Create a new file (as root) in **/etc/apt/sources.list.d** named **iplist.list** with the following content depending on your current distribution:
```
deb http://ppa.launchpad.net/ssakar/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/ssakar/ppa/ubuntu karmic main
```
```
deb http://ppa.launchpad.net/ssakar/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/ssakar/ppa/ubuntu jaunty main
```
```
deb http://ppa.launchpad.net/ssakar/ubuntu intrepid main
deb-src http://ppa.launchpad.net/ssakar/ubuntu intrepid main
```
The key of the signed packages can be imported like this: 
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C6E3D905C8BCD56BB02E6E0B39456311108B243F
```
After an update of the Software sources **thinklight-notification** can be installed with any package manager. E.g.:
```
sudo aptitude update
sudo aptitude install thinklight-notification
```

**[SIZE="3"]Testing[/SIZE]**
Start **Evolution**, go to *Edit -> Plugins* and make sure it is enabled. The following command should indicate that the module is already loaded:
```
lsmod | grep thinkpad_acpi
```

**[SIZE="3"]Troubleshooting[/SIZE]**
On Ubuntu desktop installation the **thinkpad_acpi** module is loaded automatically. But if that's not the case it should be added to **/etc/modules**.

---

### Post by lunatico on 2009-02-26
Thanks for the tutorial!
It installs alright but update keeps complaining.

```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 39456311108B243F
```

A key signature problem?

Thanks!

---

### Post by uljanow on 2009-02-27
PPA finally allows signing of packages. The key must be imported. I've updated the instructions.

---

### Post by lunatico on 2009-02-27
> **uljanow said:**
> I've updated the instructions.
Thanks for that!

One other thing, have you noticed that the [mail-notification]("http://www.nongnu.org/mailnotify/") deamon is also picked up by this thinklight notification plugin? And I don't have mail-notification configured to notify about my evolution emails, just my gmail ones.
This is good in one way (two birds with one stone) but bad if you only want to 'thinklight notify' your evolution emails as there is no way of disabling for mail-notification (I think...).

---

### Post by binbash on 2009-02-27
It works great

---

### Post by andresmh on 2009-09-27
This looks great but it doesn't seem to be a PPA for Karmic. I tried using the Jaunty PPA and it succeeds in installing the package but it doesn't show up in the Evolution plugins.

---

### Post by uljanow on 2009-09-30
I will upload packages for karmic next week.

---

### Post by chancekang on 2009-11-29
Thanks for the post.

I was following this how-to on Karmic with t61p. In the last step, when I tried to install the package, it told me 

```
Couldn't find any package whose name or description matched "thinklight-notification"
```

I have followed the tutorial step-by-step with no error exception. Any suggestions? Thanks a lot.

Here is the output of running "lsmod | grep thinkpad_acpi"

```
thinkpad_acpi          67108  0 
led_class               4096  3 iwlcore,thinkpad_acpi,sdhci
nvram                   7528  1 thinkpad_acpi
```

And my file content in /etc/modules

```
  1 # /etc/modules: kernel modules to load at boot time.
  2 #
  3 # This file contains the names of kernel modules that should be loaded
  4 # at boot time, one per line. Lines beginning with "#" are ignored.
  5 
  6 lp
  7 thinkpad_acpi
```

Any suggestions will be appreciated. Thanks a lot.

---

### Post by uljanow on 2009-11-29
There are some [build issues]("http://launchpadlibrarian.net/36221356/buildlog_ubuntu-karmic-i386.thinklight-notification_0.04-0ubuntu2_FAILEDTOBUILD.txt.gz") with karmic which I haven't resolved yet. Currently there are no packages for karmic.

---

