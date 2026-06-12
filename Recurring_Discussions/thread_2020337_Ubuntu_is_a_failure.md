---
title: "Ubuntu is a failure"
date: 2012-07-08
forum: Recurring Discussions
---

### Post by barisurum on 2012-07-08
With the current state of unity and a lack of proper display drivers the ubuntu project is doomed to be a failure. The nvidia 295.40 and later drivers are known to be unstable and ubuntu team should have downgraded the drivers and use the ones that simply work. I boot into a recovery mode and the filesystem is read-only. WTF? What is the purpose of recovery mode without write access? I try to revert and use nouveau as display driver but there's no easy way to do that. Overall ubuntu sucks big time.

---

### Post by Elfy on 2012-07-08
[https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/982134](https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/982134)

There's probably a mention of why it happened deep in the bowels of a mailing list post somewhere that very few people would find. 

I certainly never managed to find one.

---

### Post by Cheesehead on 2012-07-08
> **barisurum said:**
> The nvidia 295.40 and later drivers are known to be unstable and ubuntu team should have downgraded the drivers and use the ones that simply work.

See [Launchpad Bug #982485]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485http://"). Upstream bug. Reported April 15. Active involvement by triagers and developers within 24 hours. High-priority. Fix Released May 4. That doesn't seem like a failure at all.


> **barisurum said:**
> I boot into a recovery mode and the filesystem is read-only. Unrelated issue. You may have filesystem corruption that prevents the system from mounting rw. Or maybe you *told* grub to do it that way. There's an easy workaround so you can diagnose and fix your system: [http://ubuntuforums.org/showthread.php?t=1870817](http://ubuntuforums.org/showthread.php?t=1870817)


> **barisurum said:**
> I try to revert and use nouveau as display driver but there's no easy way to do that. Sure there is. See [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Installation_without_X_.2BAC8_from_the_console](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Installation_without_X_.2BAC8_from_the_console)

---

### Post by barisurum on 2012-07-08
> **Cheesehead said:**
> See [Launchpad Bug #982485]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485http://"). Upstream bug. Reported April 15. Active involvement by triagers and developers within 24 hours. High-priority. Fix Released May 4. That doesn't seem like a failure at all.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187)

The severity is critical and marked as Wont Fix. But actually 295.33 driver works quite well and could be used as a fallback. Your claim is baseless.


[QUOTE=Cheesehead]Unrelated issue. You may have filesystem corruption that prevents the system from mounting rw. Or maybe you *told* grub to do it that way. There's an easy workaround so you can diagnose and fix your system: [http://ubuntuforums.org/showthread.php?t=1870817](http://ubuntuforums.org/showthread.php?t=1870817)[/QUOTE]

I don't have filesystem corruption.

```
mount -o rw,remount /
```

fixes the problem. This is a bug. Your claim is baseless.


[QUOTE=Cheesehead]Sure there is. See [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Installation_without_X_.2BAC8_from_the_console](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Installation_without_X_.2BAC8_from_the_console)[/QUOTE]

Your link points to an article about **removing** nouveau. What I wanted to accomplish is reverting **back to** nouveau.

All of your claims are baseless. Ubuntu is a failure.

---

### Post by Sef on 2012-07-08
Moved to Recurring Discussions for the following reasons:

1) Since this thread is titled "Ubuntu is a Failure" and not 'Ubuntu is a Failure for me' (or something similar.) The title implies that the Ubuntu is doomed to fail for everyone, and not just the OP.

2) There is nothing new about Ubuntu will fail and be abandoned by it users. Threads like this have been posted over the years. 

3) The thread is turning into a how to help the OP thread and that is not the purpose of T&T. I had thought about locking the thread, but decided to move it here and keep it open.

---

### Post by Paddy Landau on 2012-07-08
> **barisurum said:**
> What is the purpose of recovery mode without write access?
This is a [reported bug]("https://bugs.launchpad.net/ubuntu/+source/friendly-recovery/+bug/996454"). Please visit the bug and add your vote (the green writing at the top left of the page).

Workaround: When booting into recovery mode, enter the two following commands:
```
mount --options remount,rw /
mount --all
```

---

### Post by Carborundum on 2012-07-08
> **barisurum said:**
> [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187)

The severity is critical and marked as Wont Fix.
The reason for the 'Won't Fix' status is explained in the comments; too many similar but unrelated issues cluttering up the report, effectively rendering it un-fixable. The original issue is re-reported as Bug [#999910]("https://bugs.launchpad.net/ubuntu/precise/+source/linux/+bug/999910"), and is currently 'Fix Released' with regards to Linux, and 'In Progress' with regards to Precise.

---

### Post by cbennett926 on 2012-07-08
> **Sef said:**
> Moved to Recurring Discussions for the following reasons:

1) Since this thread is titled "Ubuntu is a Failure" and not 'Ubuntu is a Failure for me' (or something similar.) The title implies that the Ubuntu is doomed to fail for everyone, and not just the OP.

2) There is nothing new about Ubuntu will fail and be abandoned by it users. Threads like this have been posted over the years. 

3) The thread is turning into a how to help the OP thread and that is not the purpose of T&T. I had thought about locking the thread, but decided to move it here and keep it open.

I'm pretty sure this is the best list of why to move a thread I have ever seen haha

---

### Post by 3rdalbum on 2012-07-09
> a lack of proper display drivers

Eh? Which lack? The one that leaves my desktop computer with pretty good 3D acceleration with Nvidia graphics, or the one that leaves my netbook with perfectly-good 3D acceleration with Intel graphics?

Every version of Nvidia's graphics drivers has some sort of problem that prevents one or more of their cards working properly. Basically, Nvidia's drivers suck - it's just that they suck for different people at different times. Fortunately, they haven't sucked for me since 2007.

Just because you're having a problem, doesn't mean that everyone has a problem. And Ubuntu shipping an earlier version of the Nvidia driver won't solve any problems, it will merely move the problems to a different set of users.

---

### Post by barisurum on 2012-07-15
I've started to use [AVLinux]("http://www.bandshed.net/AVLinux.html") based on debian 5.0.3 as my primary operating system.

AVLinux:
 
Stability -> PASS
Features -> PASS (not the latest of packages but they work)
Device Support -> PASS (nvidia 302.17 drivers work with 3.0 kernel)
Performance -> PASS

Conclusion: AVLinux is effective.

---

### Post by coffeecat on 2012-07-15
> **barisurum said:**
> 
Conclusion: AVLinux is effective.

Since the OP has found a distro that suits them, there would be no point further debating the pros and cons of Ubuntu with them. Thank you all for contributing.

Thread closed.

---

