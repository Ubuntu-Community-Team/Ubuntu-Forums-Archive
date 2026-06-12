---
title: "[Solved] After kernel update wifi is not recognized anymore (Lubuntu 16.04.2)"
date: 2017-05-02
forum: New to Ubuntu
---

### Post by mago90 on 2017-05-02
Hello, as per title today I got an updated for my system, I think it was a kernel update even though on the 'system updated' it was called just ubuntu (can't remember the full name sorry), but it asked for my password so I think it was something about kernel. I updated and restarted, but to my surprised the wifi is not working anymore, when i click on the bar i only see "enable networking" (which is toggled) but no more the option about wifi.

Coincidence, after the update my laptop fell, and I thought it might ahve damaged the wifi card, however I tried with windows 10 (I have dual-boot) and it works perfectly so my conclusion is that with the new update it broke my wifi.

Now, can someone tell me how can I check whether is correct? Also how do I revert the update and get the wifi back to work?

Thank you!

---

### Post by Impavidus on 2017-05-02
Reverting an update isn't easy, but in case of kernel upgrades (which are the most likely to give problems), the old kernel isn't uninstalled automatically. If you get to the grub menu, you can use the advanced options and boot an older kernel. It may be fixed with the next upgrade.

Interestingly, I found someone with a very similar problem: [https://ubuntuforums.org/showthread.php?t=2360215](https://ubuntuforums.org/showthread.php?t=2360215)

---

### Post by mago90 on 2017-05-02
Thank you! I will try (I think from grub I have access to older kernel). I will let you know. In case the problem is in the kernel, one should just wait until a fix comes out?

---

### Post by mago90 on 2017-05-02
You were right! I was able to revert to 4.4.0-75-generic (via grub) and it works fine! I will open a bug file on launchpad and see what happens. Thank you!

---

