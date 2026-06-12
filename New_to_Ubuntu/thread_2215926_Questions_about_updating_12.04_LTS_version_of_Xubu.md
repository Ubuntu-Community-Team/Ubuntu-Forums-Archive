---
title: "Questions about updating 12.04 LTS version of Xubuntu"
date: 2014-04-09
forum: New to Ubuntu
---

### Post by hamstermoon on 2014-04-09
Hello,

I'm currently running Precise (12.04 LTS) on my netbook, and very good it is too. What I am wondering is, if to move to the next LTS (Trusty) I am going to get a prompt to do this and it will automatically do it for me, or whether I will just have to do an install myself.

My other question is, how different is the beta from the actual release and will it update itself to be the actual release if I install it? I have time on my hands now but will be really busy once Trusty comes out and it would be nice to be able to do a full reinstall now rather than having to hurry it later.

---

### Post by Elfy on 2014-04-09
ok so ... 

When Trusty releases you will be notified of it, you will have to tell it to do it thought ;)

The beta is pretty much the same as the final release will be - we're trying to get some last minute issues sorted at the moment.

You can upgrade to the current state of trusty now and if you do so - then updates as they come through will get you the same as the final. I've been doing that for years.

There are 2 ways to upgrade (assuming you only have one installed system on the machine) - either with the update manager or with a downloaded image.

Both methods are detailed on testcases - so not only could you get the upgrade done, but you can test the upgrade for the Xubuntu community as well ;) - that includes you :p

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/65285/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/65285/testcases) for 64 bit

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/65286/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/65286/testcases) for 32 bit

You will see at the bottom of those - LTS Desktop Upgrade (Precise) which is what you want to be looking at.

---

### Post by slickymaster on 2014-04-09
> **Elfy said:**
> ok so ... 

When Trusty releases you will be notified of it, you will have to tell it to do it thought ;)

The beta is pretty much the same as the final release will be - we're trying to get some last minute issues sorted at the moment.

You can upgrade to the current state of trusty now and if you do so - then updates as they come through will get you the same as the final. I've been doing that for years.

There are 2 ways to upgrade (assuming you only have one installed system on the machine) - either with the update manager or with a downloaded image.

Both methods are detailed on testcases - so not only could you get the upgrade done, but you can test the upgrade for the Xubuntu community as well ;) - that includes you :p

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/65285/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/65285/testcases) for 64 bit

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/65286/testcases](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/65286/testcases) for 32 bit

You will see at the bottom of those - LTS Desktop Upgrade (Precise) which is what you want to be looking at.

Just a small detail, only results actually reported to the tracker count so please don't forget to login in the tracker using your UbuntuOne SSO account. See the attach below.
[ATTACH=CONFIG]251857[/ATTACH]

---

### Post by Warren Hill on 2014-04-09
If you want to keep a super stable system I'd wait for the 14.04.1 release scheduled for Aug 21.

When a new release comes out there are usually a few initial problems and they are usually fixed by the '.1' release.

That said if you are itching for Trusty -- Only 9 more days.

---

### Post by hamstermoon on 2014-04-09
That is good news. I will sit down later today and try for an upgrade (if that fails I can always reinstall!).

---

### Post by monkeybrain20122 on 2014-04-09
My suggestion is don't go the update manager route. Save your data and do a fresh install. "upgrade" this way takes a long time (hours), many things can go wrong and leave you with a messy, broken system It is very likely to fail if you have modified your system so that it deviates from a prinstine Ubuntu installation(using ppas, installing proprietary driver, installing third party software , tweaking some system files etc) To make it easy in the future make a separate /home partition.

Secondly I don't think it is a good idea to upgrade the first day a new release becomes final. It will be buggy and new bugs will be discovered. I would wait at least a month before I use 14.04 as my 'real system' (a partition for testing and filing bug reports is ok) I find this behaviour of update manager to encourage people to trade in their working system to something barely stable to be irresponsible and risky, so as a rule I turn off notification  for people I install Ubuntu for in case they click it by mistake.

---

