---
title: "Keyboard presses missed"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by RobJN on 2008-07-04
Hi hopefully someone can help me with this problem:

I installed ubutu at the beginning of the week and at first no problems.  Today however, if I type too fast ubuntu misses some of my key presses. This includes both the space bar and backspace which makes things extremely annoying. I have had to boot into Windows to write this message as I was getting nowhere in ubuntu.

As I mentioned this has only started occurring after a few boot ups. not straight away. could it be one of the updates i added??

I have a laptop so really need to get it to work with this keyboard.

Thanks in advance

---

### Post by milosz.galazka on 2008-07-04
Something like [that]("https://bugs.launchpad.net/ubuntu/+bug/119259")?

---

### Post by RobJN on 2008-07-04
Thanks for looking but the problem was persistent not just the first key stroke.  Funnily enough I've just started Ubuntu up again and it seems fine this time.

Tho I have had to come back into windows as it was put into hibernate so ubuntu couldnt mount my windows and shared partition.  Steep learning curve.  I guess it is much easier if you do not try a dual boot, but I cant risk living without windows with my current work

---

### Post by milosz.galazka on 2008-07-04
I think that you should fill bug report at launchpad.

---

### Post by RobJN on 2008-07-04
Yes I probably will end up filling a bug report in.  Reason being after switching back to windows and shutting that down properly I booted ubuntu up again and the problem of it missing some of my key presses had come back.

The only difference between this boot and the previous (in which I had no problems) was the fact that ubuntu had managed to automount my NTFS partitions (as windows was no longer in hibernate).

The only idea i had was to unmount both drives, which i did and it solved the problem.  Really odd behaviour.  I then proceeded to mount each NTFS partition (windows and my shared), to see if the problem came back, but it didnt!

Maybe that was just coincidence.  I will see what happens tomorrow, and try to get to the bottom of things, before submitting a bug report.



EDIT:
Since posting this I have had no further problems these last few days so hopefully it was just freak coincidence and won't happen again.

---

