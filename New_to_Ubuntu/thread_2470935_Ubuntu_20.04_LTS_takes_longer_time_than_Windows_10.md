---
title: "Ubuntu 20.04 LTS takes longer time than Windows 10 in starting"
date: 2022-01-17
forum: New to Ubuntu
---

### Post by esso10 on 2022-01-17
Ubuntu 20.04 LTS takes longer time than Windows 10 in starting, it takes very long time comparing to Win 10

---

### Post by Autodave on 2022-01-17
That is because Windows doesn't shut down......it hibernates.  If you want to see how long it really takes Win to boot, hit the RESTART while in Win and start timing it.

---

### Post by T6&amp;sfpER35% on 2022-01-17
what i've noticed with win10 ,it seems like it starts up quick ,the desktop will appear ,but try clicking on anything right away and nothing happens.
it's like it's still busy starting up for a while in the background...
at least with ubuntu or whatever linux distro ,when the desktop appears ,you can immediately get to work.
just my observation ...

---

### Post by T6&amp;sfpER35% on 2022-01-17
>  hit the RESTART while in Win and start timing it
on win10 atm and was curious ,so closed all applications and hit restart...it took a hole 5.5 min before i could do anything again...yikes 
before when i had xubuntu on this same machine , a restart would take just under a minute.

anyway , [here](https://www.tecmint.com/find-and-fix-linux-boot-issues/) ,and  [here](https://askubuntu.com/questions/35497/how-to-fix-very-slow-ubuntu-booting) is something that might help with startup issues

---

### Post by ActionParsnip on 2022-01-17
Shutdown the system fully then boot Ubuntu. Once booted, run:
```

dmesg -t > /tmp/boot.txt; gedit /tmp/boot.txt

```
Look for large gaps in time on the left

---

### Post by Autodave on 2022-01-17
I have Win10 on an SSD and Xubuntu on another SSD.  There is a 1 TB spinner to store files from either operating system.  I boot the machine and then choose what drive I want to boot from.  Booting the Win drive gives me a desktop in about 45 seconds.  From there I have to enter my password and wait another 15 seconds for the actual desktop to appear.  Then another 15 seconds before I can actually do something.  So, over a minute.  Xubuntu is 13 seconds.

---

### Post by oldfred on 2022-01-18
I updated M.2 SATA SSD to NVMe. But it only is a bit faster with my 2016 build.
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$  systemd-analyze [/COLOR]
Startup finished in 3.668s (kernel) + 5.877s (userspace) = 9.546s  
graphical.target reached after 5.865s in userspace

[/FONT]
```

I do use Kubuntu which is a bit lighter than Ubuntu and then loads a bit faster.

Changes I make:
turned off NetworkManager-wait with systemctl
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo
sudo apt install libblockdev-crypto2 libblockdev-mdraid2
turned off printer when rebooting
removed snaps

Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
If UEFI firmware update not supported (yet):
sudo apt-get purge fwupd

And have made some changes.
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

---

### Post by esso10 on 2022-01-19
much better now, thank you all!

---

