---
title: "Newby with slow boot"
date: 2018-12-25
forum: New to Ubuntu
---

### Post by noel55 on 2018-12-25
Hi. I have just tried Lubuntu after a while using Mint. It takes Lubuntu 1 min 30 secs to load the desktop. Mint was a bit quicker at 1 min 5 secs. I have amd fx quad core desktop and 16 gig of ram. Does a video card dictate boot time. Thanks

---

### Post by noel55 on 2018-12-25
noel@noel-pc:~$ systemd-analyze blame
         11.396s NetworkManager-wait-online.service
         10.698s networkd-dispatcher.service
         10.675s udisks2.service
          9.896s ModemManager.service
          8.268s dev-sda2.device
          7.952s accounts-daemon.service
          7.524s NetworkManager.service
          7.072s avahi-daemon.service
          6.964s rsyslog.service
          6.954s ofono.service
          6.901s gpu-manager.service
          6.898s apport.service
          6.895s grub-common.service
          6.547s wpa_supplicant.service
          6.423s thermald.service
          6.420s systemd-logind.service
          6.154s snapd.service
          3.771s lvm2-monitor.service
          3.734s systemd-journal-flush.service
          2.629s keyboard-setup.service
          2.462s colord.service
          2.311s systemd-modules-load.service
          1.905s apparmor.service
          1.869s systemd-tmpfiles-setup-dev.service
          1.651s systemd-sysctl.service
lines 1-25

---

### Post by Autodave on 2018-12-25
It can, but I really don't see anything that would indicate that.  What video card do you have?  Did you install a driver for it?  If so, what one and where did you get it from?

Merry Christmas!

---

