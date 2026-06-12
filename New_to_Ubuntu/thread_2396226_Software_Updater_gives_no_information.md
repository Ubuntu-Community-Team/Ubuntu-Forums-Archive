---
title: "Software Updater gives no information"
date: 2018-07-12
forum: New to Ubuntu
---

### Post by kate.t on 2018-07-12
Hello, all!

I use Ubuntu 16.04 on a Lenovo G50-70 laptop.

Just now I received notification from the Software Updater with the usual question: "Updated software is available for this computer. Do you want to install it now?"

HOWEVER, under the headings "Details of updates" and "Technical description" there is zero information. Those sections are blank. The only information available to me is below the "Technical description" heading, where I am informed that "102.3 MB will be downloaded".

What does this signify? Am I right to be leery of downloading unknown update(s)? Is there any way I can determine whether this update is legit or not? I tried googling to find out if anyone else has been in this situation, but so far I have found nothing.

Thanks in advance for any advice you can give!

Best regards,
Kate

---

### Post by #&amp;thj^% on 2018-07-12
Hi kate.t long time no see>>>Post back this so we can see.
```
apt list --upgradable
```

---

### Post by kate.t on 2018-07-12
Hello, 1fallen! Good to see you, hope you are well.

Here's the output:

```
apt list --upgradable
Listing... Done
apt/xenial-updates 1.2.27 amd64 [upgradable from: 1.2.26]
apt-transport-https/xenial-updates 1.2.27 amd64 [upgradable from: 1.2.26]
apt-utils/xenial-updates 1.2.27 amd64 [upgradable from: 1.2.26]
gnome-software/xenial-updates 3.20.5-0ubuntu0.16.04.11 amd64 [upgradable from: 3.20.5-0ubuntu0.16.04.10]
gnome-software-common/xenial-updates,xenial-updates 3.20.5-0ubuntu0.16.04.11 all [upgradable from: 3.20.5-0ubuntu0.16.04.10]
libapt-inst2.0/xenial-updates 1.2.27 amd64 [upgradable from: 1.2.26]
libapt-pkg5.0/xenial-updates 1.2.27 amd64 [upgradable from: 1.2.26]
libdrm-amdgpu1/xenial-updates 2.4.91-2~16.04.1 amd64 [upgradable from: 2.4.83-1~16.04.1]
libdrm-common/xenial-updates,xenial-updates 2.4.91-2~16.04.1 all [upgradable from: 2.4.83-1~16.04.1]
libdrm-intel1/xenial-updates 2.4.91-2~16.04.1 amd64 [upgradable from: 2.4.83-1~16.04.1]
libdrm-nouveau2/xenial-updates 2.4.91-2~16.04.1 amd64 [upgradable from: 2.4.83-1~16.04.1]
libdrm-radeon1/xenial-updates 2.4.91-2~16.04.1 amd64 [upgradable from: 2.4.83-1~16.04.1]
libdrm2/xenial-updates 2.4.91-2~16.04.1 amd64 [upgradable from: 2.4.83-1~16.04.1]
libegl1-mesa/xenial-updates 18.0.5-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.8-0ubuntu0~16.04.1]
libgbm1/xenial-updates 18.0.5-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.8-0ubuntu0~16.04.1]
libgl1-mesa-dri/xenial-updates 18.0.5-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.8-0ubuntu0~16.04.1]
libgl1-mesa-glx/xenial-updates 18.0.5-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.8-0ubuntu0~16.04.1]
libglapi-mesa/xenial-updates 18.0.5-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.8-0ubuntu0~16.04.1]
libosmesa6/xenial-updates 18.0.5-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.8-0ubuntu0~16.04.1]
libwayland-egl1-mesa/xenial-updates 18.0.5-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.8-0ubuntu0~16.04.1]
libxatracker2/xenial-updates 18.0.5-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.8-0ubuntu0~16.04.1]
linux-firmware/xenial-updates,xenial-updates 1.157.20 all [upgradable from: 1.157.19]
mesa-va-drivers/xenial-updates 18.0.5-0ubuntu0~16.04.1 amd64 [upgradable from: 17.2.8-0ubuntu0~16.04.1]
rfkill/xenial-updates 0.5-1ubuntu3.1 amd64 [upgradable from: 0.5-1ubuntu3]
ubuntu-software/xenial-updates 3.20.5-0ubuntu0.16.04.11 amd64 [upgradable from: 3.20.5-0ubuntu0.16.04.10]
unity-control-center/xenial-updates 15.04.0+16.04.20171130-0ubuntu1 amd64 [upgradable from: 15.04.0+16.04.20160705-0ubuntu1]
update-notifier/xenial-updates 3.168.9 amd64 [upgradable from: 3.168.8]
update-notifier-common/xenial-updates,xenial-updates 3.168.9 all [upgradable from: 3.168.8]


```

---

### Post by #&amp;thj^% on 2018-07-12
I am well thanks. :D
Everything looks good to go  for the updates and shows nothing fishy.
If you want to watch it in the terminal as it progresses you can use:
```
sudo apt update
```
May I ask why you were skeptical?

---

### Post by kate.t on 2018-07-12
Thanks for looking it over, 1fallen!

I thought it strange that there was no information given. That never happened before. Usually everything is listed. Do you know why it wouldn't be listed in the Software Updater interface?

---

### Post by #&amp;thj^% on 2018-07-12
That happens from time to time, I think that it just dosen't populate in time to show in that box. :)
But you now know how to check what should have been shown there.
Take Good care and drop in to say Howdy now and then. ;)

---

### Post by kate.t on 2018-07-12
:KS Thanks so much for teaching me how to check it! 
You take care, too, and I'll be back for sure...especially if and when I decide to go on to 18.04. Scary times ahead, LOL!
'Bye for now! ):P

Gratefully,
Kate

---

### Post by p-bethe on 2018-08-20
I, too, have been away for some time. I am glad I logged in. This is what I have:

Listing...
chromium-codecs-ffmpeg-extra/xenial-updates,xenial-security 68.0.3440.106-0ubuntu0.16.04.1 amd64 [upgradable from: 68.0.3440.75-0ubuntu0.16.04.1]
flashplugin-installer/xenial-updates,xenial-security 30.0.0.154ubuntu0.16.04.1 amd64 [upgradable from: 30.0.0.134ubuntu0.16.04.1]
libpam-systemd/xenial-updates 229-4ubuntu21.4 amd64 [upgradable from: 229-4ubuntu21.2]
libsystemd0/xenial-updates 229-4ubuntu21.4 amd64 [upgradable from: 229-4ubuntu21.2]
libudev1/xenial-updates 229-4ubuntu21.4 amd64 [upgradable from: 229-4ubuntu21.2]
squashfs-tools/xenial-updates 1:4.3-3ubuntu2.16.04.3 amd64 [upgradable from: 1:4.3-3ubuntu2.16.04.2]
systemd/xenial-updates 229-4ubuntu21.4 amd64 [upgradable from: 229-4ubuntu21.2]
systemd-sysv/xenial-updates 229-4ubuntu21.4 amd64 [upgradable from: 229-4ubuntu21.2]
udev/xenial-updates 229-4ubuntu21.4 amd64 [upgradable from: 229-4ubuntu21.2]
wpasupplicant/xenial-updates,xenial-security 2.4-0ubuntu6.3 amd64 [upgradable from: 2.4-0ubuntu6.2]

This only amounts to 5.8 Mb, but this is the first time that I have seen the blank description. I guess this is all OK. It has been a long time since I used apt-get.

Your last post raises another guestion: when is a good time to upgrade to 18.04? 

Paul

---

### Post by deadflowr on 2018-08-20
here's a bug on the blank updates issue:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1783023]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1783023")
and  previous discussion (on-going, still?): [https://ubuntuforums.org/showthread.php?t=2394240]("https://ubuntuforums.org/showthread.php?t=2394240")

> when is a good time to upgrade to 18.04? 

Ideally, in a year or two. (or try stretching it out till 16.04 reaches it's end of life)
I'm not sure what the point is of running an LTS if you're just going to upgrade to the next one as soon as it's released (or available to upgrade to).

---

