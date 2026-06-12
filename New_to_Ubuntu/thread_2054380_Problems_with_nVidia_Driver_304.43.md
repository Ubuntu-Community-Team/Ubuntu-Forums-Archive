---
title: "Problems with nVidia Driver 304.43"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by SpongeBob SquarePants on 2012-09-07
I have an nVidia GT640 video card, meaning I have to enable the [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) and [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) repos to get a driver which works. If I don't, there are no options to install when I click on additional drivers. Anyway, it goes through its download and install routine, before coming up with the error message that there was some king of fault, and that I should look in var/log/jockey.log file. The log file says:

> 2012-09-07 10:28:23,982 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:28:23,983 DEBUG: KMH enabled: False
2012-09-07 10:28:25,443 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:28:25,443 DEBUG: KMH enabled: False
2012-09-07 10:28:25,577 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:28:25,578 DEBUG: KMH enabled: False
2012-09-07 10:28:35,378 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:28:35,378 DEBUG: KMH enabled: False
2012-09-07 10:28:42,995 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2012-09-07 10:28:42,996 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2012-09-07 10:29:16,159 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:29:16,159 DEBUG: KMH enabled: False
2012-09-07 10:29:16,172 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:29:16,172 DEBUG: KMH enabled: False
2012-09-07 10:31:42,007 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:31:42,007 DEBUG: KMH enabled: False
2012-09-07 10:31:42,019 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:31:42,020 DEBUG: KMH enabled: False
2012-09-07 10:31:42,170 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:31:42,171 DEBUG: KMH enabled: False
2012-09-07 10:31:42,183 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:31:42,184 DEBUG: KMH enabled: False
2012-09-07 10:31:42,321 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:31:42,321 DEBUG: KMH enabled: False
2012-09-07 10:31:42,333 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:31:42,333 DEBUG: KMH enabled: False
2012-09-07 10:38:59,782 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:38:59,782 DEBUG: KMH enabled: False
2012-09-07 10:38:59,795 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:38:59,795 DEBUG: KMH enabled: False
2012-09-07 10:38:59,929 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:38:59,929 DEBUG: KMH enabled: False
2012-09-07 10:38:59,942 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:38:59,942 DEBUG: KMH enabled: False
2012-09-07 10:39:00,075 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:39:00,075 DEBUG: KMH enabled: False
2012-09-07 10:39:00,088 DEBUG: NVidia(nvidia_current).enabled(): target_alt /usr/lib/nvidia-current/ld.so.conf current_alt /usr/lib/nvidia-current/ld.so.conf other target alt /usr/lib/nvidia-current/alt_ld.so.conf other current alt /usr/lib/nvidia-current/alt_ld.so.conf
2012-09-07 10:39:00,088 DEBUG: KMH enabled: False

I'm not sure, but the driver, although inactive in the additional drivers pane, still shows as "this driver was recently disabled but is still in use".

Any ideas on what to do?

---

### Post by NikTh on 2012-09-07
Hello , 

forget about "additional drivers" and jockey-gtk , and open a terminal(ctrl+alt+t keys Combo)  and apply bellow commands , one line at time. 
Copy-paste in terminal from here if you want (for more accuracy)

```
sudo apt-get update
sudo apt-get purge nvidia*
sudo apt-get install ubuntu-desktop 
sudo rm /etc/X11/xorg.conf
sudo apt-get dist-upgrade
sudo apt-get install nvidia-current
sudo nvidia-xconfig
```After above , reboot your system . 

Thanks

---

