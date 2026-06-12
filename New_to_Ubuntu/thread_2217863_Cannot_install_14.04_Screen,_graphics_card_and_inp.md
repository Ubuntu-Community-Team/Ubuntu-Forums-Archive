---
title: "Cannot install 14.04: Screen, graphics card and input device settings not detected"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by doco2 on 2014-04-18
Hi!

I just tried to install Ubuntu 14.04 LTS on my laptop but it does not work.
The CD boots normally (I can see the Ubuntu Logo), but then I receive the following error message:

The system is running in low-graphics mode
Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.

After confirming with OK, I got the following choice:
What would you like to do?
 . Run in low-graphics mode for just one session
 . Reconfigure graphics
 . Troubleshoot the error
 . Exit to console login

I took the 1. Option. Then it tells me:
 Stand by one minute while display restarts... (-> OK)

But the display remains black, cannot do anything afterwards.

What can I do now?

I am using the following laptop:
Acer Aspire E1-572G with Intel Core i5 processor and an AMD Radeon HD 8670M graphics card.

Many thanks,
doco

---

### Post by kc1di on 2014-04-18
try booting using the nomodset parameter.

[this thread]("http://ubuntuforums.org/showthread.php?t=1613132") should be of help.

---

### Post by doco2 on 2014-04-21
Many thanks Dave! This was exactly what I needed.
I found out that I have somethings called UEFI therefore I got a different screen than in your link above. The below link handled exactly the problem that I have:
[http://ubuntuforums.org/showthread.php?t=2058178](http://ubuntuforums.org/showthread.php?t=2058178)

Now the live CD is running properly. Now, I tried to install Ubuntu with Dual Boot, but my new problem is that Ubuntu tells me that it does not recognize any other operating system, but I will open another thread for this...

Many thanks!

---

