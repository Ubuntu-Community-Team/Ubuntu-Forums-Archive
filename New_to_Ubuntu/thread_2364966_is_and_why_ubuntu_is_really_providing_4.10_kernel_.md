---
title: "is and why ubuntu is really providing 4.10 kernel to ubutnu 16.04?"
date: 2017-06-30
forum: New to Ubuntu
---

### Post by smit.patil on 2017-06-30
I am noob :confused::confused:to this forum and if I am posting something wrong then please tell me I will remove my post:neutral::neutral:!!

I had checked the pre-released updates and I had updated my Ubuntu mate 16.04 by `sudo apt update && sudo apt upgrade` and now I have 4.10.0-27-generic kernel. before update I had 4.8. something

         smit@smit-Aspire-5742:~$ uname -r
         4.10.0-27-generic

.But whats the point of this new kernel?? even Debian 9 doesn't have 4.10 kernel!! the main think i want to know that **what is the point of the installing 17.04 or any future release until 16.04 is supported if i am getting latest kernel and softwares in 16.04:confused:?? **this doesn't mean that i am not happy with upgrade,in fact I love this upgrade and i was going to install 17.4 but I am curious and confused that should I install 17.04??

thanks in advance for any help:KS:KS

---

### Post by CatKiller on 2017-06-30
You've decided to install a preview kernel from the [Hardware Enablement Stack]("https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack#hwe-16.04-edge"), so yes, you are getting very new kernels.

16.04 is a Long-Term Support release, so no, you do not need to upgrade until after the next LTS (18.04) is released, unless you want the features that are brought in with the intermediate releases. That is the point of the LTS releases. LTS releases will continue to receive security updates and feature updates for some applications for five years.

---

### Post by smit.patil on 2017-06-30
@CatKiller,
thanks for Reply:P

Why canonical releases the non-lts versions like 16.10 and 17.4:confused::confused:??

---

### Post by Michael_McKenney on 2017-06-30
Linux has so many flavors and so many sources.   The purists stay with LTS versions only.   Those are the most stable and long lasting.  Some people want to be on the latest and greatest cutting edge stuff.    It is up to what you will tolerate.   I went to 17.04, the latest and greatest.  Had a lot of problems.    I ended up backing up and doing a clean install of 16.04 LTS.

---

### Post by CatKiller on 2017-06-30
> **smit.patil said:**
> @CatKiller,
thanks for Reply:P

Why canonical releases the non-lts versions like 16.10 and 17.4:confused::confused:??

How would they know that they would be able to offer support for 5 years if it hadn't been tested? That's what the interim releases are for; to get newer versions of stuff out there, being used, and being tested. That way, when the next LTS is released they have a reasonable idea that it all works. That's also what you're doing by running the cutting-edge kernel that you've installed: you're being a guinea pig for the rest of us.

---

### Post by deadflowr on 2017-06-30
> I had checked the pre-released updates 
Everything needed to be said is right there.
Pre-release updates means proposed updates which means updates that are still in testing stage.

I was wondering for a second why you had the newer hwe stack kernel, as that should not make it into the main updates until next month, or so.
But packages in proposed can be installed far earlier, as you can now see.

caveat emptor: packages in proposed are considered unstable and you should only install or enable proposed at your own risk.

> Why canonical releases the non-lts versions like 16.10 and 17.4
It allows newer hardware to work on the longer supported release.
(16.04 gets 5 years support,
16.10, 17.04 only get 9 months)

---

### Post by monkeybrain20122 on 2017-06-30
The proposed repository is not activated by default, you must have activated it yourself. It is under "Developers' option" and has the warning

"Proposed updates are only for testing updates and providing development feedback. Enabling this may introduce instability."

---

### Post by scpatl4now on 2017-07-05
I think the newer kernel has better support for the new Ryzen CPUs (I dont think I know because my new build has one...that I LOVE!).  Thats why I installed 17.04 on my system rather than 16.04.  I guess they have made it work with 16.04.

---

