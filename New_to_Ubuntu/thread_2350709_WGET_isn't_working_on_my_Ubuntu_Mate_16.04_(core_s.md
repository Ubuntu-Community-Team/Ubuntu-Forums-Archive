---
title: "WGET isn't working on my Ubuntu Mate 16.04 (core segmentattion)"
date: 2017-01-26
forum: New to Ubuntu
---

### Post by tree-yellow60 on 2017-01-26
As a good newbie I Don't know what's happening but I can't execute wget command anymore so  I try randomly:

sudo apt-get install --fix-broken --fix-missing
sudo apt-get -f install
sudo apt-get install -f
sudo gdb wget
dmesg | grep "wget"
sudo apt install wget
sudo apt remove wget
sudo apt install --reinstall wget
sudo apt remove cairo-dock
sudo apt install --reinstall wget
sudo apt autoremove
sudo apt update ; sudo apt upgrade
sudo apt-get update
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove


sudo apt-get check && sudo apt update && sudo apt upgrade && sudo apt -f install && sudo apt install -f && sudo apt update && sudo apt upgrade && sudo apt remove wget && sudo apt install -f && sudo apt install --reinstall wget && sudo apt fix --broken install && sudo dpkg --configure -a



```
$ ls -l /lib/
total 420
drwxr-xr-x  2 root root   4096 Jan 11 03:42 apparmor
drwxr-xr-x  2 root root   4096 Jul 19  2016 brltty
lrwxrwxrwx  1 root root     21 Jan 11 02:03 cpp -> /etc/alternatives/cpp
drwxr-xr-x  3 root root   4096 Jul 19  2016 crda
drwxr-xr-x  4 root root   4096 Jan 12 01:58 cryptsetup
drwxr-xr-x 75 root root  32768 Jan 26 01:41 firmware
drwxr-xr-x  2 root root   4096 Jul 19  2016 hdparm
drwxr-xr-x  2 root root   4096 Jan 21 01:36 i386-linux-gnu
drwxr-xr-x  2 root root   4096 Jan 11 03:41 ifupdown
drwxr-xr-x  2 root root   4096 Jan 11 21:28 init
-rwxr-xr-x  1 root root  70952 Set 22 14:34 klibc-k3La8MUnuzHQ0_kG8hokcGAC0PA.so
lrwxrwxrwx  1 root root     25 Nov 16 19:51 ld-linux.so.2 -> i386-linux-gnu/ld-2.23.so
-rw-r--r--  1 root root 211112 Fev 18  2014 libdmraid.so.1.0.0.rc16
drwxr-xr-x  2 root root   4096 Jul 19  2016 linux-sound-base
drwxr-xr-x  3 root root   4096 Jul 19  2016 lsb
drwxr-xr-x  2 root root   4096 Jan 26 01:41 modprobe.d
drwxr-xr-x  4 root root   4096 Jan 26 01:41 modules
drwxr-xr-x  3 root root   4096 Jul 19  2016 recovery-mode
drwxr-xr-x  2 root root   4096 Jul 19  2016 resolvconf
drwxr-xr-x  2 root root   4096 Jan 26 17:26 security
drwxr-xr-x  8 root root   4096 Jan 21 01:36 systemd
drwxr-xr-x  2 root root   4096 Jan 11 21:28 sysvinit
drwxr-xr-x 15 root root   4096 Fev 19  2016 terminfo
drwxr-xr-x  4 root root   4096 Jan 26 20:25 udev
drwxr-xr-x  2 root root   4096 Jul 19  2016 ufw
drwxr-xr-x  4 root root  20480 Jan 25 09:07 x86_64-linux-gnu
drwxr-xr-x  2 root root   4096 Jul 19  2016 xtables
```

That's all I got till now and wget still not working. Any help please?

---

### Post by Impavidus on 2017-01-27
Can you post the exact command you used to run wget? And can you also post the entire error message you get when it fails?

---

