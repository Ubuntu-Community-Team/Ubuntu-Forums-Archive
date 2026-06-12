---
title: "Fullscreen Youtube?"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by d4m1r on 2012-08-02
Hey guys, has anyone else been getting their entire PC to freeze while watching a video on Youtube in fullscreen? I have the latest Firefox and Flash. It is weird because it only affects the workspace I was watching it on so can move to another one, kill firefox and the related plugin process, and relaunch it....

Anyone else experiencing similar issues? Nvidia GPU and usually happens when watching in 720p or 1080p if it matters.

---

### Post by richpri on 2012-08-02
I am aware of a number of nvidia graphics driver freezes with various symptoms,

For example 
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1027724](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1027724)

They all seem to start occurring after an upgrade to 12.04.

---

### Post by d4m1r on 2012-08-02
Subscribed to the bug....Why do they think it is related to Nvidia drivers and not Firefox/Flash? I am still using the initial proprietary drives installed along with 12.04 and I wasn't getting this issue....

There have been several Firefox and flash updates however and now I am :(

---

### Post by evilsoup on 2012-08-02
Look up the add-on FlashVideoReplacer, it embeds mplayer into youtube pages. I've been getting better results from it than with flash & people who have done benchmarks have told me that it uses less processing power etc.

If your problem is flash, then it'll probably help.

---

### Post by md2020 on 2012-10-31
I had a similar issue with playing videos with VLC and Ubuntu 12.04 that I was able to resolve. You could see if this works for you:  [http://ubuntuforums.org/showpost.php?p=12328809&postcount=19]("http://ubuntuforums.org/showpost.php?p=12328809&postcount=19")

---

### Post by pqwoerituytrueiwoq on 2012-10-31
sounds like a issue i had on 10.04 (even the keyword leds froze up)
sudo rm /etc/adobe/mms.cfg

only way to regain control was to reboot (i could do this via ssh)

---

