---
title: "Unable to update new software for ubuntu programme updates"
date: 2023-12-11
forum: New to Ubuntu
---

### Post by harfinuk on 2023-12-11
For the last couple of weeks the Programme Updater (*briefcase icon*) shows new update, but it shows in blue diamond OS updates, as well as an**A** button Software Updater text 22.04.10 - 22.04.17. Neither of the options produces no action and fails. Please help! 
Harfin UK

---

### Post by Holger_Gehrke on 2023-12-11
Might be a "phased upgrade". Those are updates to very basic components of the system that are somewhat risky and are therefore not given to everyone all at once. Instead they are given to a random sample of users first and only if nothing catastrophic happens to those they are given out to everyone. Use 'apt list --upgradeable' on the command line to get a list of upgradeable packages and then run 'apt-cache policy name-of-an-upgradeable-package' (replace the obvious placeholder with one of the packages the previous command listed ...). If the version table in the output of 'apt-cache' mentions 'phased' with a percentage after it, then that's the reason for you not getting the package yet.

Holger

---

### Post by harfinuk on 2023-12-29
R?ecent upgrade via option for security updates reccomending me to upgrade to Ubuntu Pro. States I should login to ubuntu.pro/  and  enter a code M04QLI

Is this for real? If so how do go about completing the reccomendation?
OAP, Alan Harfinuk

---

### Post by ActionParsnip on 2023-12-29
What is the output of
```

sudo apt update
sudo apt upgrade

```

---

### Post by harfinuk on 2023-12-29
Hi
how do I copy the data to insert in my reply?

---

### Post by ActionParsnip on 2023-12-29
> **harfinuk said:**
> Hi
how do I copy the data to insert in my reply?

It's text. Select the text in the console, copy it and then paste as an update rather than typing text. Remember to encompass it with the code tags

---

### Post by harfinuk on 2023-12-29
Sudo apt update
[sudo] password for harfin: 
Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy InRelease
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates InRelease [119 kB]
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-backports InRelease
etched 229 kB in 0s (520 kB/s)
ReaHit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy InRelease
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates InRelease [119 kB]
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Fetched 229 kB in 0s (520 kB/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up-to-date.ding package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up-to-date.

---

### Post by ActionParsnip on 2023-12-29
Looks fine. Has the icon gone away?

---

### Post by harfinuk on 2023-12-29
sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libffi7 libflashrom1 libftdi1-2 libllvm13 libpython2-stdlib python2
  python2-minimal python2.7 python2.7-minimal
Use 'sudo apt autoremove' to remove them.
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libvlc5 python2.7-minimal vlc-data libvlccore9 imagemagick libopenexr25
  libpostproc55 libmagickcore-6.q16-6-extra libavcodec58 libmagickwand-6.q16-6
  libpython2.7 libavutil56 imagemagick-6.q16 libswscale5 libmagickcore-6.q16-6
  libswresample3 imagemagick-6-common vlc-plugin-video-output libavformat58
  python2.7 libpython2.7-minimal libvlc-bin libpython2.7-stdlib
  vlc-plugin-base libavfilter7
Learn more about Ubuntu Pro at [https://ubuntu.com/pro](https://ubuntu.com/pro)
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

---

### Post by TheFu on 2023-12-29
I consider all marketing of Ubuntu-Pro to be FUD and ignore it.  It is playing on your fear.
If you stay on a supported release and use core packages only, these will be supported for 3 yrs (5 yrs for Ubuntu Server).


Python2 support ended in 2020, so there's nobody supporting it. You have some old packages installed if those are still there.  As the output shows, 
> Use '**sudo apt autoremove**' to remove them.

---

### Post by ActionParsnip on 2023-12-29
Sounds fine. You can clear up with
```

sudo apt --purge autoremove

```

---

### Post by harfinuk on 2023-12-29
In the software updater I am advised that "updated software" is stil available. "Ubuntu Pro Security. I am advised I need to "enable Ubunto Pro Security. My laptop it says is not covered by the Ubuntu Pro subscription. This is all out of my league!! So far I have selected the option of "Remind me later" Other updates occur from time to time, mostly security updates. 

harfinuk
Alan

---

### Post by pantazi on 2023-12-29
Don't worry over Ubuntu Pro, see here:

[https://learnubuntu.com/use-ubuntu-pro/](https://learnubuntu.com/use-ubuntu-pro/)

---

### Post by ian-weisser on 2023-12-29
> **harfinuk said:**
> This is all out of my league!!

No, it's not out of your league.
Two experts explained Ubuntu Pro in clear terms earlier in the thread. Re-read what they wrote.
You really can do it.

---

### Post by MAFoElffen on 2023-12-31
> 
"You can do it!"
(Rob Schneider quote from 5 different Adam Sandler movies...)

+1

---

