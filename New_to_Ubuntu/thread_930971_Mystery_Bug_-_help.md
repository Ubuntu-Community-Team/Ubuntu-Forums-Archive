---
title: "Mystery Bug - help"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by alexham on 2008-09-26
Hi, 

I have a very strange problem with <Suspend>.  Generally, it works OK, except when I use Gimp and then it goes into a loop and the password menu keep re-appearing and the computer will not go into suspend state.  

This is the last line of the system log.

Sep 26 23:57:54 alex-desktop kernel: [   35.815685] eth0: no IPv6 routers present

Is there a way out of this?

Many thanks,

Alex

---

### Post by nowshining on 2008-09-27
have u tried inserting ur pw??

---

### Post by alexham on 2008-09-27
> **nowshining said:**
> have u tried inserting ur pw??

Do you mean password? There is no option to insert password when activation <Suspend>.

---

### Post by alexham on 2008-09-29
What is happening here? No one knows? Suspend works provided I don't use Xsane or Gimp, otherwise I have to shut down and start again. Hibernate and Restart do not work at all.

Without these key facilities I have no option by to "retreat" to Windows.

Alex

---

### Post by seshomaru samma on 2008-09-30
What computer are you using?

---

### Post by hyper_ch on 2008-09-30
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

### Post by alexham on 2008-09-30
> **seshomaru samma said:**
> What computer are you using?
I am using AMD Athlon 64X2 Dual Core Processor 4000+ 2.11Ghz with NVidia GeForce 6100 nForce 430 graphics card and NVidia HDA sound card.

Thanks,

Alex

---

### Post by seshomaru samma on 2008-10-01
suspension depends mostly on the motherboard
what kind of motherboard are you using, did you build the computer yourself.

what i would do is find out more info about your computer and google suspension problems with the same model/motherboard

---

### Post by alexham on 2008-10-01
> **seshomaru samma said:**
> suspension depends mostly on the motherboard
what kind of motherboard are you using, did you build the computer yourself.

what i would do is find out more info about your computer and google suspension problems with the same model/motherboard

The motherboard is Asus M2N-MX.  I did not build the computer. I bought it from a local computer supplier, to my choice of components.  I was running Windows and Mepis 6.0 at that time and I was advised that this motherboard runs well with Mepis.   But Mepis does not have Suspend or Hibernate so I changed to Ubuntu.  I appreciate that the motherboard has a lot to do with this, but I don't understand why is it that Suspend works OK if I don't use Gimp or Xsane.  Every time I use Gimp or Xsane I have to shut down and reboot otherwise Suspend does not work.

Thanks for your response,

Alex

---

### Post by seshomaru samma on 2008-10-01
Will[ this]("http://ubuntuforums.org/showthread.php?t=809108") thread be of any help?
a similar problem was solved by re-enabling APIC in the BIOS and starting the kernel with the option "noapic"

---

### Post by alexham on 2008-10-01
> **seshomaru samma said:**
> Will[ this]("http://ubuntuforums.org/showthread.php?t=809108") thread be of any help?
a similar problem was solved by re-enabling APIC in the BIOS and starting the kernel with the option "noapic"

I followed the steps described in that thread. I was able to make a backup copy of menu.lst, but when I added "noapic" I could not save the change.

How do I save the change?

Thanks again,

Alex

---

### Post by alexham on 2008-10-01
> **seshomaru samma said:**
> Will[ this]("http://ubuntuforums.org/showthread.php?t=809108") thread be of any help?
a similar problem was solved by re-enabling APIC in the BIOS and starting the kernel with the option "noapic"

I have added "noapic" as suggested, but it has made no difference. Hibernate does not work at all and Suspend works only if I stay away from Xsane and Gimp.

Good try.

Thanks,

Alex

---

### Post by alexham on 2008-10-01
> **seshomaru samma said:**
> Will[ this]("http://ubuntuforums.org/showthread.php?t=809108") thread be of any help?
a similar problem was solved by re-enabling APIC in the BIOS and starting the kernel with the option "noapic"
Unfortunately, that did not work on my system.  Suspend still works provided I stay clear of Xsane and Gimp.  Hibernate and Restart do not work at all.

Thanks for trying anyway.

Alex

---

