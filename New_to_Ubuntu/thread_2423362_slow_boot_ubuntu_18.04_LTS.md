---
title: "slow boot ubuntu 18.04 LTS"
date: 2019-07-22
forum: New to Ubuntu
---

### Post by amitjatin on 2019-07-22
Hi all

 i installed ubuntu 18.04 LTS and it is the first time i am using any linux OS
i am facing slow boot on on my laptop, i did google to find out the exact boot time and the services that is causing the delay, but dont know which services need to be removed and how....pls help

systemd-analyze
```
Startup finished in 5.255s (firmware) + 2.958s (loader) + 4.528s (kernel) + 1min 38.977s (userspace) = 1min 51.719s
graphical.target reached after 1min 12.210s in userspace

```
```
systemd-analyze blame
     1min 1.964s apt-daily.service
         59.927s fstrim.service
         48.567s plymouth-quit-wait.service
         14.868s dev-sda9.device
         11.378s systemd-journal-flush.service
         10.888s systemd-modules-load.service
         10.776s systemd-tmpfiles-setup-dev.service
         10.720s keyboard-setup.service
         10.402s swapfile.swap
          8.622s snapd.service
          7.704s tlp.service
          7.452s NetworkManager-wait-online.service
          5.927s apt-daily-upgrade.service
          5.245s NetworkManager.service
          5.045s networkd-dispatcher.service
          3.549s motd-news.service
          3.352s grub-common.service
          3.044s udisks2.service
          2.806s systemd-random-seed.service
          2.618s thermald.service
          2.157s ModemManager.service
          1.672s gdm.service
          1.416s systemd-journald.service
lines 1-23...skipping...
     1min 1.964s apt-daily.service
         59.927s fstrim.service
         48.567s plymouth-quit-wait.service
         14.868s dev-sda9.device
         11.378s systemd-journal-flush.service
         10.888s systemd-modules-load.service
         10.776s systemd-tmpfiles-setup-dev.service
         10.720s keyboard-setup.service
         10.402s swapfile.swap
          8.622s snapd.service
          7.704s tlp.service
          7.452s NetworkManager-wait-online.service
          5.927s apt-daily-upgrade.service
          5.245s NetworkManager.service
          5.045s networkd-dispatcher.service
          3.549s motd-news.service
          3.352s grub-common.service
          3.044s udisks2.service
          2.806s systemd-random-seed.service
          2.618s thermald.service
          2.157s ModemManager.service
          1.672s gdm.service
          1.416s systemd-journald.service
          1.199s fwupd.service
          1.166s accounts-daemon.service
          1.092s packagekit.service
           974ms plymouth-start.service
           963ms colord.service
           782ms [EMAIL="systemd-fsck@dev-disk-by\x2duuid-D29D\x2d0407.servic"]systemd-fsck@dev-disk-by\x2duuid-D29D\x2d0407.servic[/EMAIL]e
           750ms [EMAIL="user@121.servic"]user@121.servic[/EMAIL]e
           749ms [EMAIL="systemd-backlight@backlight:intel_backlight.servic"]systemd-backlight@backlight:intel_backlight.servic[/EMAIL]e
           716ms networking.service
           563ms dev-loop16.device
           558ms wpa_supplicant.service
           527ms dev-loop8.device
           523ms dev-loop9.device
           513ms alsa-restore.service
```

---

### Post by jimmy-frydkaer on 2019-07-22
what are your HW specs?

---

### Post by amitjatin on 2019-07-22
Lenovo B490 Laptop
Intel(R) Core(TM) i3-3110M CPU @ 2.40GHz, Freq 1197.246 MHz, L2 Cache 3072 KB
Ram DDR3 8 GB
Swap 1184 MB
HDD 1 TB 5400 RPM

---

### Post by amitjatin on 2019-07-22
i have gone through ubuntu forums for my problem and after a solution the revised output is as follows, is this boot time is ok for my system or it can be improved more ??

amit@Lenovo-B490:~$ systemd-analyze
Startup finished in 6.560s (firmware) + 2.679s (loader) + 4.361s (kernel) + 39.381s (userspace) = 52.983s
graphical.target reached after 39.144s in userspace
amit@Lenovo-B490:~$ systemd-analyze blame
         27.672s dev-sda9.device
         23.074s systemd-journal-flush.service
         22.564s systemd-modules-load.service
         21.551s systemd-tmpfiles-setup-dev.service
         20.104s swapfile.swap
          6.351s NetworkManager-wait-online.service
          6.078s plymouth-quit-wait.service
          4.068s snapd.service
          3.370s dev-loop12.device
          3.330s dev-loop16.device
          3.311s dev-loop17.device
          3.310s dev-loop11.device
          3.252s dev-loop5.device
          3.230s dev-loop10.device
          3.230s dev-loop15.device
          3.221s dev-loop14.device
          3.142s dev-loop8.device
          3.112s dev-loop13.device
          2.949s keyboard-setup.service
          2.877s dev-loop9.device
          2.694s dev-loop1.device
          2.655s dev-loop4.device
          2.627s dev-loop0.device
lines 1-23...skipping...
         27.672s dev-sda9.device
         23.074s systemd-journal-flush.service
         22.564s systemd-modules-load.service
         21.551s systemd-tmpfiles-setup-dev.service
         20.104s swapfile.swap
          6.351s NetworkManager-wait-online.service
          6.078s plymouth-quit-wait.service
          4.068s snapd.service
          3.370s dev-loop12.device
          3.330s dev-loop16.device
          3.311s dev-loop17.device
          3.310s dev-loop11.device
          3.252s dev-loop5.device
          3.230s dev-loop10.device
          3.230s dev-loop15.device
          3.221s dev-loop14.device
          3.142s dev-loop8.device
          3.112s dev-loop13.device
          2.949s keyboard-setup.service
          2.877s dev-loop9.device
          2.694s dev-loop1.device
          2.655s dev-loop4.device
          2.627s dev-loop0.device
          2.613s dev-loop2.device
          2.550s dev-loop7.device
          2.466s dev-loop6.device
          2.200s dev-loop3.device
          2.189s systemd-random-seed.service
          1.990s systemd-udevd.service
          1.775s udisks2.service
          1.513s NetworkManager.service
          1.486s networkd-dispatcher.service
          1.311s grub-common.service
          1.182s gpu-manager.service
          1.152s preload.service
           986ms ModemManager.service
           959ms accounts-daemon.service

---

### Post by him610 on 2019-07-23
> Startup finished in 6.560s (firmware) + 2.679s (loader) + 4.361s (kernel) + 39.381s (userspace) = 52.983s
graphical.target reached after 39.144s in userspace
This is fine for your system specs.

---

### Post by cruzer001 on 2019-07-23
```
4.068s snapd.service
3.370s dev-loop12.device
3.330s dev-loop16.device
3.311s dev-loop17.device
3.310s dev-loop11.device
3.252s dev-loop5.device
3.230s dev-loop10.device
3.230s dev-loop15.device
3.221s dev-loop14.device
3.142s dev-loop8.device
3.112s dev-loop13.device
2.877s dev-loop9.device
2.694s dev-loop1.device
2.655s dev-loop4.device
2.627s dev-loop0.device
2.613s dev-loop2.device
2.550s dev-loop7.device
2.466s dev-loop6.device
2.200s dev-loop3.device
```
Those snap packages are slowing you down.
```
snap list
```
You can replace snap packages with .deb using Synaptic Package Manager.
```
sudo apt install synaptic
```
[https://geek-university.com/linux/synaptic/](https://geek-university.com/linux/synaptic/)

[https://ubuntuforums.org/showthread.php?t=2419177](https://ubuntuforums.org/showthread.php?t=2419177)

---

### Post by oldfred on 2019-07-23
boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) & 
[https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead](https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead) 
   [https://askubuntu.com/questions/906581/what-is-dev-loopx](https://askubuntu.com/questions/906581/what-is-dev-loopx) 
   sudo apt autoremove --purge snapd 

      
 Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453)
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html) 
   turned off NetworkManager-wait
Changed systemctl daily timer 
housecleaned systemctl logs
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo
sudo apt install libblockdev-crypto2 libblockdev-mdraid2
turned off printer when rebooting
removed snaps

---

