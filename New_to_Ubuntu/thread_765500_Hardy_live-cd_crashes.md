---
title: "Hardy live-cd crashes"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by larsdk on 2008-04-24
Hi,

I downloaded the iso today (and checked it in the menu = no errors) but when I try to install it (or even just run it "without any changes to my computer") it hangs. It looks like a graphiccard issue, since the screen goes all ugly, and then it hangs (I have to turn of the power)

I haven't had this problem with any other ubuntu releases. Anyone else having this problem?

---

### Post by gary4gar on 2008-04-24
Try using Alternate Install CD

---

### Post by larsdk on 2008-04-24
Maybe I should give that a try. Just a bit afraid that Hardy won't work on my laptop, since the live-cd cannot boot properly.

---

### Post by Pbethe on 2008-04-24
> **larsdk said:**
> Hi,

I downloaded the iso today (and checked it in the menu = no errors) but when I try to install it (or even just run it "without any changes to my computer") it hangs. It looks like a graphiccard issue, since the screen goes all ugly, and then it hangs (I have to turn of the power)

I haven't had this problem with any other ubuntu releases. Anyone else having this problem?

This has happened to me with every release that I have tried.  Do you know about Raising Skinny Elephants (there is a thread about magic sysreq keys)?  If that works, you can reboot somewhat gracefully rather than power off.

Let us know if the alternate install works.

---

### Post by larsdk on 2008-04-24
since my guess was that it was a grpahic/crad issue, I tried using the safemode option in the livecd boot menu and that worked. Not sure if I want to install Hardy right away though, since I wont have time to mess around with stuff for quite some time, and really just need a working computer :)

---

### Post by Ozor Mox on 2008-04-24
Just to chip in and say I have had the same problem. The live CD will not boot unless I start it in safe graphics mode. However, I'm still planning to install Hardy, so I'll let you know how that goes. If everything works nicely after installation, you'll know you're probably safe!

---

### Post by Cybergod on 2008-04-29
> **Ozor Mox said:**
> Just to chip in and say I have had the same problem. The live CD will not boot unless I start it in safe graphics mode. However, I'm still planning to install Hardy, so I'll let you know how that goes. If everything works nicely after installation, you'll know you're probably safe!

I'm trying to install Hardy right now and I'm having this issue.  I do not see a choice for safe graphics mode like I did in previous releases.

---

### Post by lwvmobile on 2008-04-29
What kind of graphics chip do you have. I know some, namely Sis, that don't work well with Hardy.

---

### Post by Cybergod on 2008-04-29
> **lwvmobile said:**
> What kind of graphics chip do you have. I know some, namely Sis, that don't work well with Hardy.

nVidia GeForce 6200

---

### Post by larsdk on 2008-04-30
> What kind of graphics chip do you have. I know some, namely Sis, that don't work well with Hardy. 

mine is an ati 9600 as far as I recall :)

---

### Post by Ozor Mox on 2008-05-01
> **Cybergod said:**
> I'm trying to install Hardy right now and I'm having this issue.  I do not see a choice for safe graphics mode like I did in previous releases.

At the initial boot screen press F4 and select safe graphics mode, then start Ubuntu as normal.

I find it odd that I need to do this since all previous versions of Ubuntu have booted the live CD on the same computer fine.

---

### Post by Cybergod on 2008-05-01
> **Ozor Mox said:**
> At the initial boot screen press F4 and select safe graphics mode, then start Ubuntu as normal.

I find it odd that I need to do this since all previous versions of Ubuntu have booted the live CD on the same computer fine.

I tried all the function keys and did not see safe graphics mode.  I did get Hardy installed by using the alternate CD (text base install).  Everything is working fine now.

---

