---
title: "Dual boot, ubuntu won’t install additional programs from unmet dependencies"
date: 2014-09-30
forum: New to Ubuntu
---

### Post by mnield on 2014-09-30
Hello I have been looking around trying to solve this for awhile now and have tried most of what I have found in the search results. 
amd fx4350, 8gb coinsar vengeance ram, samsung 840evo, Sapphire 7870 
Dual booted a ssd primary partition windows 7 with a split partition Ubuntu 12.04
Had to rebuild many windows drivers after installation because of broken or installed packages.
So far in ubuntu I have done,
sudo apt-get -f install
sudo apt-get autoclean
sudo dpkg --configure -a
sudo apt-get -u dist-upgrade
sudo apt-get update
sudo apt-get upgrade

I upgraded 62 packages initially during -f install the first time. 
upgrade downloaded some data but could also not fetch.
Fetched 4,268 kB in 5s (835 kB/s)                                          
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>






here is what i get when I try to install vlc
The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 2.0.8-0ubuntu0.12.04.1) but 2.0.8-0ubuntu0.12.04.1 is to be installed
     Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 4:0.8.16ubuntu0.12.04.1 is to be installed
     Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.16ubuntu0.12.04.1 is to be installed
     Depends: libc6 (>= 2.15) but 2.15-0ubuntu10.7 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2.1 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.8 is to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.8 is to be installed
     Depends: libsdl-image1.2 (>= 1.2.10) but it is not going to be installed
     Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
     Depends: libtar0 but it is not going to be installed
     Depends: libva-x11-1 (> 1.0.15~) but it is not going to be installed
     Depends: libva1 (> 1.0.15~) but it is not going to be installed
     Depends: libxcb-keysyms1 (>= 0.3.8) but it is not going to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed

I have installed ubuntu before once on a computer of mine but not with a duel boot, I am learning so if I have left anything out please let me know.

---

### Post by Bucky Ball on 2014-09-30
Welcome. You had to reinstall windows drivers after installing Ubuntu? Shouldn't be and suggests you are installing Ubuntu inside Windows using a Wubi install. This in no longer supported by Canonical or these forums. It is a real dual-boot with Windows on one partition, Ubuntu on the other? Please confirm ... 

Wubi recommendations:
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

Incidentally, ALWAYS in this order:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

You must update before upgrading. ;)

---

### Post by mnield on 2014-10-01
I am not using them both in one partition, My primary partition has windows 7 and the partition I split has Ubuntu. 
I wiped my ssd, re installed windows, re installed windows drivers, installed Ubuntu on the other partition, duel boot works fine going to either OS during boot loader. 
I think I did them in order at the time but I went back to try again but nothing new came up, Ill try to keep my commands better organized, thanks.

---

