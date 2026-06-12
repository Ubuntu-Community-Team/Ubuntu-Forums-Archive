---
title: "Problems with Hardy, Power Managementm, and Netlogo"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by K8A on 2008-06-12
Hi all--
I upgraded to Hardy about a month ago, and I've been having a steady stream of difficulties ever since. There are two that are particularly vexing, and have repelled all my attempts to fix them.

1) Netlogo--this is a java-based program that I use for my research. When I try to launch it, the window will open, but then it hangs forever. I get no error messages. All of my other Java-based programs work (thanks to a fix I found on another thread). Only Netlogo is hanging.

2) Power-management--my machine sometimes fails to hibernate when I shut the lid. This problem is REALLY inconsistent--sometimes it is fine, sometimes it looks/sounds fine but gives me a "failed to hibernate" message, and sometimes it legitimately fails to hibernate.

Ideas?

---

### Post by K8A on 2008-06-12
By the way--Netlogo worked fine under Gutsy. The power management has always been a bit spotty, but it has gotten much worse under Hardy, and the "fail to hibernate" messages while actually hibernating is new.

---

### Post by rcoconnell on 2008-06-12
I've done a bit of tinkering on K8A's machine, so I thought I'd add the following:

The machine in question is a Thinkpad T30, recently "upgraded" from Gutsy to Hardy.  I've applied the two Suspend/Resume fixes mentioned at [Thinkwiki]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.04_%28Hardy_Heron%29_on_a_ThinkPad_T30"), but the machine is still not suspending reliably.

The sound system is also non-functional -- the volume control appears as usual, but no sound comes out.  Everything looks normal in alsamixer, though I don't know if that's relevant any more.  The volume buttons on the thinkpad are also non-functional.  Is the Comprehensive Sound Guide still relevant, in these bold (and beta-licious) days of PulseAudio?

Finally, we've been thinking about simply downgrading the machine to Gutsy or reinstalling.  Unfortunately, it took a lot of work to get the machine working well in Gutsy, and I'd rather not completely flush that.  So my questions are:

1.  If one is going to downgrade, what directories are of interest?  I've seen mentions of home and /etc, but are there others I should be worried about?

2.  What degree of success can one hope for if one then restores those directories?  Would we be completely hosed trying to restore them from Hardy to Gutsy?  What about from a Hardy upgrade to a fresh install of Hardy?  Would restoring the /etc directory negate any benefits of reinstalling?

3.  Does a reinstall wipe the home directory?

4.  Can we replicate the benefits of reinstalling by completely removing and reinstalling some set of packages through Synaptic?  If so, which ones would be of interest?  I don't know which sound modules are doing the heavy-lifting any more, and I don't know if the sleep issue is related to the kernel or what.

Thanks,
ross

---

### Post by gr4nf on 2008-06-12
To fix your sound, the following may work:
```

sudo apt-get install alsa

```
if downgrading, you will want:
/etc
/home
/pmi (if you have one)
/root (maybe. only if there's stuff in it.)

and that should be all. yes, a reinstall will wipe everything.

---

