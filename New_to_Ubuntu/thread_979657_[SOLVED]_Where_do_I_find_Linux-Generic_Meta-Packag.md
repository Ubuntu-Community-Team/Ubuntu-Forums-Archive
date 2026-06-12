---
title: "[SOLVED] Where do I find Linux-Generic Meta-Package"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by OMR on 2008-11-12
In my update Manager there is A security update available titled "Linux-Unbuntu-Modules-2.6.24-21-Generic", and when I checked the details it said "You likely do not want to install this package directly.  Instead, install the Linux-Generic Meta Package".  Where do I find this package?
Thanks in advance for any help you can give to point me in the right direction!

---

### Post by PartisanEntity on 2008-11-12
This and most other packages can be found under System > Administration > Synaptic Package Manager.

However I think you will be fine letting the updater install it for you.

---

### Post by OMR on 2008-11-12
> **OMR said:**
> In my update Manager there is A security update available titled "Linux-Unbuntu-Modules-2.6.24-21-Generic", and when I checked the details it said "You likely do not want to install this package directly.  Instead, install the Linux-Generic Meta Package".  Where do I find this package?
Thanks in advance for any help you can give to point me in the right direction!

Note to PartisanEntity: I followed your recommendation, after installation I discovered some unsupported dependencies, Firestarter would not start and I lost my internet, it took two hours to get back on line, then I used Synaptic Package Manager to install the recommended Meta Package and all problems were solved.  I would suggest that you just answer the question asked and not included what you think as this caused a-lot of work for me! 
I do want to thank you for your time,

---

### Post by landtodd on 2009-09-28
Great question you asked.  I'm exactly there trying to get some backported ath5k modules.  What did you finally download, and how did you pick specific modules from it?  :-D

---

### Post by rakete on 2009-10-01
this is confusing me, too...

Why is is marked as SOLVED? I did not find a solution in this thread...

I searched Synaptics but did not find the so called "Linux-Generic Meta Package"... 

Synaptics shows only linux-image generic and linux-ubuntu-modules ...everything installed in latest version. The package which is showing up in the update manager is marked with a star...

Can anyone tell me, how the package I should install is named exactly? I am not willing to risk any upgradeproblems in the future... A temporary internet loss is not acceptable, since I deleted my Vista 64bit, because of such a problem after an update. I would do this with ubuntu, too, burn all my ubuntu stickers and CD's left and tell everyone to buy a mac... :twisted:

Seriously: Why is a package recommended to update via update Manager and then it says in the Description "It is not recomemnded to install this package over the update manager, instead...." :confused::confused::confused: 

I do not have to understand this, right? But I would like to...

---

### Post by ptn107 on 2009-10-01
The appropriate packages [and associations] for the Linux kernel in Ubuntu are:
```

linux-generic (meta-package)
 - linux-image-generic (meta-package)
    - linux-image-<version>-generic (desktop kernel)
       - linux-ubuntu-modules-<version>-generic (kernel modules; Ubuntu 8.04.x only)
linux-headers-generic (meta-package)
 - linux-headers-<version> (common system headers)
 - linux-headers-<version>-generic (desktop headers)
linux-firmware (kernel driver firmware; >= Ubuntu 8.10 only)
```

*<version>* varies depending on which Ubuntu version you use:
```
8.04.x = 2.6.24-24
  8.10 = 2.6.27-14
  9.04 = 2.6.28-15
  9.10 = 2.6.31-12
```

---

### Post by rakete on 2009-10-01
so, as far as I understand you, if I do not find this packages in synaptics directly, I should go fine with a

 sudo apt-get install linux-generic

?

if I do so, he states that there is nothing to install, just an update for one package... I saw this package before in the update manager...:rolleyes:

---

### Post by rakete on 2009-10-02
so, I presume, the solution is to just ignore this update and hope not to install it by incident in the future, right?

Any chance to ignore this update for ever?

Thanks for nothing...

---

### Post by Paqman on 2009-10-02
linux-generic is a meta-package that should be installed on your system by default (unless you've removed it, which isn't a good idea)

It's purpose is to depend on the latest kernel, so that when a new kernel is released, linux-generic gets updated and that pulls down the new kernel for you. Nice and simple. If you don't have linux-generic on the system, you won't get kernel updates, which would be bad.

So yes, if you don't have this package already, install it now.

---

### Post by OMR on 2009-10-08
Sorry the post that started this was my first post. Re: [SOLVED] Where do I find Linux-Generic Meta-Package
this is confusing me, too...

Why is is marked as SOLVED? I did not find a solution in this thread...

I searched Synaptics but did not find the so called "Linux-Generic Meta Package"...

Synaptics shows only linux-image generic and linux-ubuntu-modules ...everything installed in latest version. The package which is showing up in the update manager is marked with a star...

Can anyone tell me, how the package I should install is named exactly? I am not willing to risk any upgradeproblems in the future... A temporary internet loss is not acceptable, since I deleted my Vista 64bit, because of such a problem after an update. I would do this with ubuntu, too, burn all my ubuntu stickers and CD's left and tell everyone to buy a mac...

Seriously: Why is a package recommended to update via update Manager and then it says in the Description "It is not recomemnded to install this package over the update manager, instead...."

I do not have to understand this, right? But I would like to...
This WILL solve the problem. Go to synaptic, to the left at the window that says ALL at the top scroll down to Meta Packages click it, then on the left scroll down to linux-image- generic that is what you need. But the easy way is to click the box Mark all upgrades near the top then click apply let it do its thing and you are done. This has worked for me without fail for almost a year, Iwas brand new to any forums when I made the first post in this thread, BTW I had to figure out this solution myself, I hope this solves everyones confusion, I hope this will help anyone else with this problem.  OMR

---

### Post by rakete on 2009-10-08
I did the update via synaptics... everything is fine, nothing is broken...
:D

sorry for being hysteric ;)

---

### Post by oldschoolgentoo on 2013-04-02
i appreciate the reply and the update on this issue.  Their are alot of  users who will do simple but stupid things on the Nix Boxes.  So  being clear and exact on the process when it comes to the Kernel helps greatly.  Thank you for the updated info.  I realize this is  an old Post but it comes up in new systems that havent been updated in years....

---

### Post by QIII on 2013-04-03
Thank you for sharing,

If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.

*Thread **closed.***

---

### Post by cariboo on 2013-04-03
Info from 2009, isn't up-to-date, I'd suggest instead of wasting time searching old threads, you probably could have created a new thread, and received an answer fairly quickly. Thread closed.

**Edit:** Ninja'd by QIII :-D

---

