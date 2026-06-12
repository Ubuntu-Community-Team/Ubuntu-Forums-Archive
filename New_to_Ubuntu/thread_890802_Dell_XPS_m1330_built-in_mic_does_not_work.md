---
title: "Dell XPS m1330 built-in mic does not work"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by futuroimperfetto on 2008-08-15
Hello,

 I've just bought a Dell XPS m1330 with Gutsy Gibbon preinstalled. Everything seems to work perfectly, for what I have tested, but I cannot get the built-in mic to work. I've downloaded all the avaliable updates, but this did not change the situation. I checked this page

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work")

I downloaded the backport modules and followed the instructions, but when I go to the alsamixer setting, I cannot find digital mic 1, even though I activated the digital input source. I found this page too on launchpad

[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/147682]("https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.22/+bug/147682")

There is a comment describing how to download unreleased backport modules. I haven't tried it yet (not even sure if it still is available).

Being a Linux newbie, I'm somewhat hesitant at downloading savagely packages without knowing how to invert the process in case it makes things works.

Does anyone have suggestions about this? I would prefer not to download Ubuntu 8.04 immediately, because my connection is not very good right now. On the other hand, is it known if it is supported on Hardy?

Thanks for your help!

---

### Post by uberdonkey5 on 2008-08-27
I had gutsy first and also hardy. With both (on dell inspiron 1520) I had microphone problems. First, try this page and see if it is useful (I am guessing you have the software now):
[http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

---

### Post by futuroimperfetto on 2008-09-01
Thanks uberdonkey5!

I found this page announcing that the mic would be supported on Hardy

[https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1330]("https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1330")

I did the upgrade and it is now working normally, though the volume is very low and I haven't yet looked into how to fix it.

However, I have another laptop that does have the same problem with the mic and I can't upgrade it to Hardy, so I'll make some tests according to the page you sent and post the results when I can.

---

