---
title: "Having problems with shutting down"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Crope on 2008-05-24
Hello. I'm having a small problem with shutting down Ubuntu 7.10.

When I go to shutdown, my computer hangs for about 30 seconds. Then the normal shutdown window pops up, asking me what I want to do. It gives me the following options:
 - Log Off
 - Lock Screen
 - Switch User
 - Restart
 - Shutdown

Notice it's missing the Suspend and Hibernate buttons. When I hit cancel after this, then try shutting down again, the shutdown window comes up instantaneously, this time with all of the correct buttons. 

I remember seeing this somewhere, and it's the result of the video card driver installation, and all you have to do is add a piece of code to some file which adds the two missing buttons. I can't seem to find it though. Keep in mind that I properly installed my video drivers, with direct rendering enabled.

Any ideas or walkthroughs are highly appreciated.

---

### Post by Crope on 2008-05-24
bump, kind sirs :)

---

### Post by Crope on 2008-05-24
:(

---

### Post by Crope on 2008-05-25
*third bump*

---

### Post by Joeb454 on 2008-05-25
Hmmm, odd, I've never seen this issue before :confused:

And also - please try not to bump your thread more than once every 24 hours (let alone 3 times ;)). I know it can be frustrating however

---

### Post by sayakb on 2008-05-25
Not very sure whether this is a walkthrough or not. Just goto System->Preferences->Keyboard shortcuts and there, assign a key combination for Suspend. Now, goto System->Preferences->Power management and Click the General tab. There, set the "When the power button is pressed" action to Hibernate. In that way, you might be able to utilize both the facilities, even though they don't come up in the actions window.

> **Joeb454 said:**
> Hmmm, odd, I've never seen this issue before :confused:
+1, Neither did I :D

---

### Post by Crope on 2008-05-25
>  Suspend/Hibernation work with 7.12

With Gutsy release, there was a big problem using the ATI proprietary drivers. The Suspend/Hibernate function stopped working. The problem was due to the new SLUB allocator incorporated in 2.6.22 / 2.6.23 Kernel.

The problem has been solved in the AMD Catalyst 7.12 driver release. UPDATE: The problem has NOT been solved in the AMD Catalyst 7.12 driver release.

Suspend/hibernate is not working for FireGL 5250. For FireGL 5200, suspend works with the 7.12 fglrx kernel module loaded (which did not work before this release) , but does not work if X is running.

For Thinkpad T60 with ATI X1400, to get the laptop to wake up from suspend, I had to change the following in /etc/default/acpi-support:

SAVE_VBE_STATE=false

POST_VIDEO=false

Even with the above settings (like POST_VIDEO=false, etc.) my ASUS Z96J with an X1600 does not suspend.

This bug has been a serious issue for several months now. There is a lot of frustration over this, because Ubuntu/Canonical has not been helpful. They've said things like suggesting not using fglrx (thanks a lot, that really helps).

Current status on this bug can be found here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121653/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121653/)
[edit] 

Apparently I'm stuck with it :[

---

### Post by Joeb454 on 2008-05-25
Suspend/Hibernate is an issue for most people. Luckily I don't use it, so I don't have to spend time dealing with it.

Though I do know a few people who have managed to get it to work for them :)

---

### Post by sayakb on 2008-05-25
How big is your swap and what is your RAM size? Your swap should be slightly bigger than your RAM so that you can suspend or hibernate. Just check it, in case..

---

