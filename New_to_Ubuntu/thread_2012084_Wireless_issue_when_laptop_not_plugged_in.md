---
title: "Wireless issue when laptop not plugged in"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by yasitha on 2012-06-28
Hi all,

This relates to an issue I was having in the thread below:
[http://ubuntuforums.org/showthread.php?t=1994792](http://ubuntuforums.org/showthread.php?t=1994792)

The root cause seems to be not having my laptop (LenovoX220, Ubuntu 12.04) plugged in during boot up. 

If the laptop is plugged in I don't need to do anything with modprobe, wireless just works.

If the laptop is not plugged in during boot, the wireless still connects, however I can't ping anything on the network or get internet access. I have to do the following:
sudo modprobe -r
sudo modprobe iwlwifi 11n_disable=0

at which point the wireless works **even though the laptop remains unplugged**.


I've printed the output from dmesg with the laptop unplugged:
[http://pastebin.com/3YySCNeL](http://pastebin.com/3YySCNeL)
and plugged in:
[http://pastebin.com/nAte0EZw](http://pastebin.com/nAte0EZw)

When unplugged, at [   17.535791]  there is a line related to power, but I can't see what causes the wireless specifically to stop working. Everything else seems to be fine.

Any ideas?

Cheers,
Yas

---

