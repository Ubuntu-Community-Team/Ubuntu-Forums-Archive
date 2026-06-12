---
title: "can't install ubuntu in dell insrpon"
date: 2015-06-01
forum: New to Ubuntu
---

### Post by suhail3 on 2015-06-01
I have a dell inspron 15z ultabook , with windows 8 preinstalled. it has a 500gb hard drive and a 32GB ssd.
when i am trying to install ubuntu alongside with windows it partition with 32gb ssd , actually window's bootloader is installed in /dev/sdb (32gb ssd).
when i tried to install by something else method , and installing ubuntu in sda , hard drive during the installation process it shows an error
**"Executing 'grub-install/dev/sda ' failed. " **Thus installation stops.
Can any help me please.

---

### Post by RobGoss on 2015-06-01
How are you trying to install your Ubuntu DVD or USB?

If you wanted to install Ubuntu normally when using your Ubuntu live disk it will do all the work for you. Just choose the option to install Ubuntu along side of Windows 8 and it should be just fine. If you choose something different them you will need to know how to setup your partitions and get things in order.

This is a great starting point: [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

---

### Post by DuckHook on 2015-06-02
I don't have any laptop as new as yours, so am just repeating what I've read many times in these forums, but it seems that the new ultrabooks such as yours use a sort of cheater's hybrid design where Windows uses the tiny ssd as a cache to pseudo-hibernate your session with each shutdown. This allows Windows to launch quickly on power-up because it is not actually booting. The downside is that such pseudo-hibernation recovery will bypass the hdd and any bootloader that happens to be on it. There is also some fancy raid-foo happening between the BIOS, the two disks and the OS, so it gets very touchy, brittle and complicated.

You can use these past threads as a sort of guide, but read through them carefully first. These procedures end up nuking Windows, which you may not wish to do. I don't know how to make both OSes coexist, and suspect that it is either not possible, or the solution is so obscure and convoluted (not to mention fragile) that you wouldn't want to chance it.

[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2038320](http://ubuntuforums.org/showthread.php?t=2038320)
[http://ubuntuforums.org/showthread.php?t=2215582](http://ubuntuforums.org/showthread.php?t=2215582)
[http://ubuntuforums.org/showthread.php?t=2130516](http://ubuntuforums.org/showthread.php?t=2130516)

---

### Post by suhail3 on 2015-06-03
Thanks a lot DuckHook , the link u provided are very helpful, it worked for me , now i can successfully dual boot.
:guitar::guitar:

---

### Post by DuckHook on 2015-06-03
Glad it worked out for you. Please mark thread "solved".

---

