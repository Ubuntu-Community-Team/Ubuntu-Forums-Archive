---
title: "Install 12.04 in partition"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by matbluvenger on 2012-02-29
Hey all. I'm still working out the bugs of how everything works and how I can get everything I can out of my system.

I was wondering, is it possible (on a system that already has 11.10) to create a partition and install 12.04 on there without affecting the main partition (i.e. 11.10)

So, to summarize (since I'm sure I'm not making the greatest amount of sense):

1) Can I install 12.04 in a partition alongside a partition that has 11.10?
2) Can it be done without affecting what I'm working with now?
3) How do I go about creating new partitions?
4) If all of this gets done, how do I go about booting from the new 12.04 partition?

Sorry for the extreme noobiness. I swear I'm reading everything I can find on Linux/Ubuntu/Python... there's just so much. I should have done this years ago! :D

---

### Post by pootan on 2012-02-29
1) Yes
2) Yes
3) You will be given the option to install alongside your existing Ubuntu installion. Make sure you read the options carefully.
4) The new Ubuntu will install a bootloader that will let you choose between the two Ubuntu installs when you boot up.

---

### Post by LowSky on 2012-02-29
If you just want to test it, you might be better off using 12.04 in a virtual machine.

---

### Post by Mark Phelps on 2012-02-29
If you're still "working out the bugs", installing 12.04 is a really BAD idea.  It's only now entering Beta testing, meaning there are still going to be bugs.  Hard enough dealing with bugs in a stable release; you don't want to have to be dealing with bugs in a pre-release version.

---

### Post by matbluvenger on 2012-02-29
Thank you guys for the quick replies! I love that I can post a question, go to sleep, and wake up to solutions!

Okay I figured it was so easy that the installer prompts me to do what I wanted to... I just wanted to make sure. When I first installed 11.10 I had to do a couple clean reinstalls before my tweaking didn't break things :D

But if the beta requires a bit more experience I'll just wait for the full LTS release in April. For now I'll just learn more about and mess around with Gnome3, Xubuntu, Lubuntu, and Kubuntu. Also teaching myself Python!

---

### Post by Mark Phelps on 2012-02-29
Just so you know ... installing a beta really has little to do with your "experience", although, if you have a LOT of that, fixing the bugs that arise is likely to be a lot easier.

The REAL problem with upgrading to pre-release versions from others is there is STILL no version roll-back capability in Ubuntu. What this means is, if you're currently using a stable version and it's working well, and then you upgrade to a new version (pre-release or otherwise), there is no simple way to "restore" the previous, working version.

The risk you take when going from a stable version to a pre-release version, is that the latter is known to be buggy, and if one of those trashes your system, you can't just restore the older version to get a working system back.

That's why I generally advise folks NOT to jump into pre-release versions.

---

