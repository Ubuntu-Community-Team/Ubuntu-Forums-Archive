---
title: "[SOLVED] new grub options"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Repus on 2008-05-31
I do'nt usually watch the grub startup but today I did and found I have 4 new options - two new sets of 8.04 and two new 8.04-recovery options. 

I can only imagine this is a result of several crashes I had when I tried to use power management. I have since stopped because it was a 50-50 shot that the computer would actual recover from a slumber. 

So my question now is what do I do with these extra grub menu options? Not knowing about them didn't seem to hurt the computer so I'm a little confused.

---

### Post by overdrank on 2008-05-31
> **Repus said:**
> I do'nt usually watch the grub startup but today I did and found I have 4 new options - two new sets of 8.04 and two new 8.04-recovery options. 

I can only imagine this is a result of several crashes I had when I tried to use power management. I have since stopped because it was a 50-50 shot that the computer would actual recover from a slumber. 

So my question now is what do I do with these extra grub menu options? Not knowing about them didn't seem to hurt the computer so I'm a little confused.

HI and you have the additional opitions due to the kernel update. You can comment them out if you edit your grub menu. ```
gksudo gedit /boot/grub/menu.lst

``` But I would suggest leaving the recovery and one old kernel in case of errors.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Rocket2DMn on 2008-05-31
I agree with overdrank, I would just leave them.  The newest kernel will be the default option, but it is beneficial to have other kernels to boot into in case something fails with one of them.

---

### Post by Repus on 2008-06-01
Thank you both

---

### Post by meierfra. on 2008-06-01
I suggest  to change "howmany=all" in menu.lst to "howmany=2". Otherwise you will have three kernels on the Grub menu after the next kernel update, and I just don't see why one would  need more than two.

---

