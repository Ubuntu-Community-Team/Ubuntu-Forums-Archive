---
title: "Ubuntu Installation: Reboots Everytime I Choose the Install Option"
date: 2014-05-03
forum: New to Ubuntu
---

### Post by kmotawaze on 2014-05-03
I have been trying to solve this problem for a while, and checked Google but did not find anyone with similar problem, and no solutions.

I burnt Ubuntu 9.04 (Desktop) in a CD, then I restarted the computer and boot from CD. Everything goes fine, it asks me to choose the language, I choose English, then it shows the options, for example "Try Ubuntu...", "Install Ubuntu" etc..

Now this is as far as I can go with the installation process, when I choose either Try Ubuntu, or Install Ubuntu, it pauses for 2 - 3 seconds, then the computer restarts and repeats the above process..

I've no idea what the problem is, I thought maybe the ISO was corrupt, so I downloaded Ubuntu 9.04 (Alternate) version, and then mounted the ISO to my USB, once again, everything goes fine, just like the CD, but when I choose either of the two options, the computer just restarts.

Does anyone know what the problem might be?

To add an important note - I downloaded Virtual Box, it seems to work perfectly there, both options work, I even installed it, everything is good, but I want to install it along side my Windows 7.

If anyone could help, it would be appreciated.

If you need any more information, please ask.

Regards

Khalid.

---

### Post by kc1di on 2014-05-03
Hi kmotawaze and Welcome to Ubuntu forums, 

I'm not sure what the problem is , but if you are indeed trying to install version 9.04 that version has bee obsolete for a number of years now and is no longer supported.  You would be better off downloading version 12.04 or 14.04.  If you chose that version because your hardware is old, then you would be better of trying Lubuntu - again in version either 12.04 or 14.04.  good luck.

---

### Post by LastDino on 2014-05-03
Try newer version, if system config is low, go for Lubuntu or Xubuntu, but pick one of the 14.04 LTS versions. I think in your case ISO/CD/DVD might be corrupted.

---

### Post by kmotawaze on 2014-05-03
This is a requirement, so I cannot change the version. I wish I was more familiar with Ubuntu installation method, but I'm totally oblivious.

Do you think a corrupt ISO would work in Virtual Machine but not in boot?

---

### Post by kmotawaze on 2014-05-03
As a last resort I will install the latest, but for now, I'm still trying to figure this out, it would be a good learning experience.

---

### Post by mastablasta on 2014-05-03
> **kmotawaze said:**
> This is a requirement, so I cannot change the version. I wish I was more familiar with Ubuntu installation method, but I'm totally oblivious.

Do you think a corrupt ISO would work in Virtual Machine but not in boot?

Virtual mashicne - see what you wrote here is just that a virtual computer. virtual computer is using windows drivers for the most part to make things work.

now in linux drivers are part of the kernel (built into it). so if you are using a version from April 2009 on a computer from 2013 or this year it's just asking for trouble. i mean how can you expect drivers from 2009 to support your new computer? furthermore the version is no longer supported for a long time now. since linux islagging with hardware support evencomputer form 2009 won't likely be supported by this 9.04 version.

so as others said try 12.04 or better yet 14.04.  you say 9.04 is a requirement. a requirement for what? education? did you see any recent uni programs where win98 or XP is a requirement? or vista (though at leats vista is supported still)? 8.04 was previous LTS and i think for server  verison it support expired a year ago. is it for a server use? 

just use the new version - if you explained what requirements and why you need 9.04 others might point you into "how to use the latest 14.04 LTS and get away with it".

since 2009 we have computers with UEFI., secure boot, GPT partitioning and whatnot. and all those do not work on 9.04. of course virtualbox works in adifferent way so instll there might work an dbe supported. you can probably set up a Pentium II mascine in there and install something to it.

---

### Post by LastDino on 2014-05-03
+1

Either way, I think newer version will answer to lot of doubts.

---

### Post by Mark Phelps on 2014-05-03
> This is a requirement, so I cannot change the version.Understand ...

So, let's first look at what your drive has in terms of existing partitions. From the Ubuntu in Virtualbox, open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one), and post the results back here.

---

