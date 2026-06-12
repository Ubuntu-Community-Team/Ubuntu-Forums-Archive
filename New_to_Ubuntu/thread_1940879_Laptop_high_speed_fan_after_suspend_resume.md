---
title: "Laptop high speed fan after suspend resume"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by Reylo on 2012-03-14
Hello.
I am a new user, 0 experience with linux, so please be patient with me.

I recently installed Ubuntu 11.10 (replaced windows 7) on my HP 620 laptop, and everytime i resume from suspend the fan speed goes extremely high and it goes that way for about 15-20 minutes. I didn't have this problem on windows 7 and it eats a lot of battery...

Specs:

2 gb ram
Celeron Dual Core CPU T3100 1.90 GHz
Mobile Intel GM45

Thanks in advance and sorry for my poor spelling.

(sorry if i posted in the wrong category)

---

### Post by Mark Phelps on 2012-03-15
This is a known bug in the current Linux kernels -- causes the system to overheat and the battery to run down because it does not throttle back the processor.

You could look into installing Jupiter -- but I wouldn't hold out much hope:

[http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")

---

### Post by Reylo on 2012-03-15
Yeah, it doesn't work...thanks anyway...

Still waiting for any alternate solutions if anyone has one.

---

### Post by Mark Phelps on 2012-03-16
> **Reylo said:**
> Yeah, it doesn't work...thanks anyway...

Still waiting for any alternate solutions if anyone has one.

You could try burning a bootable USB of Ubuntu 12.04, booting from that, and seeing if that helps -- but from what I've read, the kernel "fix" in that only helps if you have a Sandy Bridge processor.

---

### Post by Reylo on 2012-03-17
> **Mark Phelps said:**
> You could try burning a bootable USB of Ubuntu 12.04, booting from that, and seeing if that helps -- but from what I've read, the kernel "fix" in that only helps if you have a Sandy Bridge processor.

Updates: I made a bootable usb with the 12.04 and entered the demo mode. It didn't do the same because of one thing...the laptop was plugged in...so, even if it's 11.10 or 12.04 when on battery the cooler goes crazy, but when it's just plugged in, the cooler acts normal.

Any more ideas? Please? :)

---

### Post by Reylo on 2012-10-31
Hello again

With the new Ubuntu 12.10, the problem remains. I found a possible solution to this but i need some guidance:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77370/comments/84](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77370/comments/84)

or

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77370/comments/88](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/77370/comments/88)

Can anyone tell me how to do this? Maybe a step-by-step?

Thank you !

---

### Post by Reylo on 2012-11-05
Help?

---

