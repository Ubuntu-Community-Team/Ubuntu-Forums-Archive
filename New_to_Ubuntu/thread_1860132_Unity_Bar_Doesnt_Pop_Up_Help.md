---
title: "Unity Bar Doesnt Pop Up Help"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by hunter99507 on 2011-10-14
When i bring my mouse to the left side of the screen the unity bar doesnt pop out. The only way to access the bar is to minimize all applications (so it shows the desktop) or press the "super" button.

I am running 11.10 version
I have acer aspire 6900G
nvidia 9600m GS graphics card
4GB of ram
centrino core 2 duo

---

### Post by Frogs Hair on 2011-10-14
Try to reset from the terminal or Alt + F2 . ```
unity --reset
```

---

### Post by collisionystm on 2011-10-14
There is a longer delay set it. Hold your mouse there for a few moments.

---

### Post by guillermo_arg on 2011-10-16
I have the same problem![B] Unity Bar Doesnt Pop Up
[/B]Is it a bug?

Ubuntu 11.10 64 
I3 530
Nvidia GTS 250
4gb ram

---

### Post by Fraoch on 2011-10-16
Same issue here.  unity --reset sort of works, bringing the bar back up, but the bar doesn't behave as normal:

- it won't pop out if I'm running another program, I have to minimize that program and drop back to the desktop

- once unity --reset is run it remains permanently on screen and won't autohide

Also if I logout/restart I have to issue unity --reset again or I never see the Unity bar.

It should be noted unity --reset hangs on me, it doesn't complete its script.  It seems to hang at a random line, it's different every time.

---

### Post by LaptopU on 2011-10-16
I'm another one adding my name to this problem.  I've found for me it doesn't work for about the first 20 minutes of logging in, so I will use the start key to bring it up on the keyboard.  Then after a while it goes back to how it should work normally.

I think this is definitely a bug.

---

### Post by CarlosFerreira on 2011-10-16
It seems to have this issue now and then for me as well.

---

### Post by Carborundum on 2011-10-16
It's a known bug: [#832150]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/832150")

---

### Post by guillermo_arg on 2011-10-16
> **Carborundum said:**
> It's a known bug: [#832150]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/832150")

Thanks for the advice.

---

### Post by LaptopU on 2011-10-20
Seems to have been fixed now.

---

### Post by d4m1r on 2011-10-20
Some of you might not actually be experiencing a bug...trying holding your mouse there for 2-3 seconds. Does it pop out now?

If the answer is still no, click somewhere randomly within your Firefox window and try again. I get this sometimes but I think it is related to what window I have active at the moment vs a bug. Haven't been able to figuire out a pattern though...if it doesn't pop out, I click anywhere within Firefox, retry, and it works;)

---

### Post by CarlosFerreira on 2011-10-22
> **d4m1r said:**
> Some of you might not actually be experiencing a bug...trying holding your mouse there for 2-3 seconds. Does it pop out now?

If the answer is still no, click somewhere randomly within your Firefox window and try again. I get this sometimes but I think it is related to what window I have active at the moment vs a bug. Haven't been able to figuire out a pattern though...if it doesn't pop out, I click anywhere within Firefox, retry, and it works;)

I think this is correct. Part of my problem was the changes to the Unity launcher from 11.04 to 11.10 - the behaviour is different.

---

### Post by cottfcfan on 2011-11-07
I know this thread has been marked as solved, but it is still an issue for me.
I find if I leave my computer, and have to unlock the screensaver on return, the bar doesn't appear when moving the cursor to the left, so I have to minimize my apps. After about 10 minutes of use, it seems to work again.
Any ideas?

---

### Post by d4m1r on 2011-11-07
> **cottfcfan said:**
> I know this thread has been marked as solved, but it is still an issue for me.
I find if I leave my computer, and have to unlock the screensaver on return, the bar doesn't appear when moving the cursor to the left, so I have to minimize my apps. After about 10 minutes of use, it seems to work again.
Any ideas?

See my comment 2 posts above yours.

---

### Post by cottfcfan on 2011-11-07
d4m1r
I tried your suggestion above but no joy.
The only thing that seems to start it working again is time.
About 10 minutes in my case.

---

### Post by cottfcfan on 2011-11-07
Actually ive just seen what the problem is.
I opened a terminal which is semi transparent & moved my cursor across.
The Unity bar is actually coming out underneath the main window instead of above it, which is why you can't see it.
After about 10 minutes it rights itself.
No idea how to fix it though.

Think i'll start a separate thread with this one.

---

