---
title: "Sloooow boot and running on macbook"
date: 2018-07-12
forum: New to Ubuntu
---

### Post by happy-daze on 2018-07-12
Hi there,

I'm having a maor problem with a new install of ubuntu 18.04 LTS on an old macbook. (Intel core 2 duo 2.1ghz with 3.8GiBram, Intel 965GM graphics, 117.6GB disk space, nothing else installed. OS X gone.)

```
~$ systemd-analyze
Startup finished in 36.171s (kernel) + 2min 55.703s (userspace) = 3min 31.875s
graphical.target reached after 2min 55.666s in userspace

```

```
$ systemd-analyze blame
    1min 44.741s plymouth-read-write.service
    1min 30.929s plymouth-start.service
         46.086s plymouth-quit-wait.service
         17.027s systemd-backlight@backlight:intel_backlight.service
         13.585s dev-sda2.device
         10.581s systemd-journal-flush.service
          8.115s snapd.service
          8.083s keyboard-setup.service
          7.790s NetworkManager-wait-online.service
          7.457s udisks2.service
          6.595s systemd-sysctl.service
          6.195s ModemManager.service
          6.112s systemd-udevd.service
          6.031s accounts-daemon.service
          5.753s networkd-dispatcher.service
          5.316s NetworkManager.service
          4.256s wpa_supplicant.service
          3.840s dev-loop3.device
          3.825s dev-loop1.device
          3.784s dev-loop2.device
          3.750s dev-loop4.device
          3.723s dev-loop0.device
          3.722s dev-loop5.device
```

Something is badly wrong but I'm completely new to linux (its taken me yesterday and today to get it installed at all (third distro I tried too). I only knew to do those reports based on stuff I found in this forum.

Help please before I have to abandon it.

Please please, if you want more information spell out how I go about getting it for you!

---

### Post by apeitheo2 on 2018-07-13
There's a bug with the latest kernel that's causing long boot times for some people. I'm not sure if it's the issue you're having, but you could try this:
```
sudo apt install haveged
sudo systemctl enable haveged
```
If that doesn't reduce the boot time, it's easy to remove it.

If you're interested, here's more information about the problem I'm talking about: [https://ubuntuforums.org/showthread.php?t=2395459&p=13781140#post13781140](https://ubuntuforums.org/showthread.php?t=2395459&p=13781140#post13781140)

Hope it helps.

---

