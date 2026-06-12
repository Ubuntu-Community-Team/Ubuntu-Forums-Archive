---
title: "Windows: Inherit Structual Issues?"
date: 2012-05-01
forum: Recurring Discussions
---

### Post by OpenSourceRules on 2012-05-01
Registry, file systems, updating methods, restoration points, are a few things that have made Windows exceptionally sluggish.  
Windows XP would be considered lightweight today, but performance decreases after upgrading from package two to package three..  
Certainly keeping old files won't help much; even a simple clean-up of apt-get files in Linux speeds things up. 
It sounds to me that the Windows developer are just decorating things up rather than changing the whole structure.
Imagine Windows on Ext4 or JFS.....

---

### Post by wolfen69 on 2012-05-01
You probably won't get a lot of responses to your observations. The things you speak of can lead to bashing, and that's not allowed here. Plus, a lot of people here dual boot for various reasons.

I don't like windows, and am going to leave it at that.

---

### Post by Copper Bezel on 2012-05-02
[QUOTE=OpenSourceRules]It sounds to me that the Windows developer are just decorating things up rather than changing the whole structure.
Imagine Windows on Ext4 or JFS.....[/QUOTE]
No, they most certainly aren't. Windows 8 depends on a completely different way of writing applications - aren't Metro apps architecture-independent? (Even Android can't pull that for some apps, despite the Java base.) Win 8 also *does* use a new filesystem. I don't know how it handles the registry, but that's changed quite a bit from XP to 7, too, and it's unavoidable that it *has* a registry so long as it runs commercial apps with per-device licenses, which Microsoft will *always be required to do by its developer base*. 

I'll actually be quite surprised if the anachronistic per-app update method persists into 8 - particularly for Metro apps, which are provided through MS. And what "old files" are you referring to?

So, "no." It's Windows, it's ugly (at least in desktop mode,) it's commercial and constrictive, it's fat as hell (though I wonder how much the backwards-incompatible ARM port shaves off) and so on, but it's not any of the specific things you're saying about it.

---

### Post by MisterGaribaldi on 2012-05-02
Um, sorry, it's not correct to say Microsoft *cannot* get rid of the Registry. They totally can get rid of it whenever they want to. It's a question of whether or not they're willing to pay the price associated with that kind of decision.

The Registry has been a part of the Win32/Win64 environment for the last 20+ years, ever since the (bad old) days of WinNT 3.x. It's been fully a part since 1995, and it's one of those things that has improved with age and experience, but as we all know still has some issues.

If Microsoft were to get rid of The Registry, they would have to accept a break with compatibility for essentially all existing software written for Windows. To be honest, I've seen and heard of nothing which suggests to me Microsoft even *wants* to get rid of the Registry, much less is going to.

Microsoft and Apple are polar opposites in this respect, because Microsoft is (relatively) paranoid about backward compatibility, and Apple really isn't, and doesn't mind changing things (and breaking every egg in the kitchen in the process) if they feel there's a benefit.

To this day, Windows still has fixed drive letters. That is an MS-DOS construct hailing from the 1980s! If they're willing to hang onto drive letters for better than 30 years... I mean, geez.

Good luck trying to convince them or anybody connected to that ecosystem to change. Me, I'll stick with my Mac and my Linux-based server and router, tyvm.

---

### Post by Copper Bezel on 2012-05-03
Hmm. I guess it depends on what you mean by "the" registry. I mean, Microsoft could, in a fit of self-loathing, trivially change the registry so that it had no backwards compatibility, but was still a system registry for the new apps that would support it. I was arguing that Windows needs *a* registry. You're saying that what matters is that it's *the* registry. You're probably more right than I am. There are, reasonably, other ways of solving the same problem.

[QUOTE=MisterGaribaldi]If Microsoft were to get rid of The Registry, they would have to accept a break with compatibility for essentially all existing software written for Windows.[/QUOTE]
But Windows 8 ARM is already doing that, and developers have to choose between form and substance even on the desktop version. I mean, I get it, I know that everyone is going to use Win 8 entirely through the desktop app and Metro will be a bad dream someone was freaking out about. But the way it's being pushed now, Metro is being treated as the new face of the OS. If things really go the route of the ARM version, then it'll be a smashing chance to lose those drive letters.

---

### Post by mamamia88 on 2012-05-03
When I used windows I would just run ccleaner every month or so when I wasn't busy.    I would clean everything including the registry and I never had any significant slowdown.   Sure it can be a pain in the *** if you don't know what you are doing but 2 or 3 clicks once every month or so isn't going to kill anyone.

---

### Post by *^kyfds( on 2012-05-03
> **mamamia88 said:**
> When I used windows I would just run ccleaner every month or so when I wasn't busy.    I would clean everything including the registry and I never had any significant slowdown.   Sure it can be a pain in the *** if you don't know what you are doing but 2 or 3 clicks once every month or so isn't going to kill anyone.

+1

Ccleaner's a great tool if you're having problems with your registry.

A mate of mine asked me to fix his PC when it had a slow down, and Ccleaner scanned for about 20 minutes removed just over 3.3 gigabytes of temporary files and crap from the registry.

(incidentally, he also had 669 infected files on his computer)

---

