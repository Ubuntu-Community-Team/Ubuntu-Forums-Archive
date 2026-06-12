---
title: "Am I Running the &quot;Right&quot; Kernel?"
date: 2013-04-24
forum: New to Ubuntu
---

### Post by thatstheway on 2013-04-24
[FONT=arial][SIZE=2]I just did a reinstall of Ubuntu 12.04 (Because I broke something, whoo hoo) and after installing a few automatic updates I had a broken-package error related to [COLOR=#000000]linux-image-3.5.0-27-generic: it downloaded, but would not install. I believe I've solved this by switching servers, in Software Sources, using the Best Server process. That is, after doing so, [/COLOR]all broken-package-related errors vanished (notification in the top menu, errors starting Sofware Center, etc.)

However, when I booted up the next morning I got an error message (I don't recall the exact wording) "The system encountered a problem, do you want to report it?" and when I said "yes," the system started pulling together a bug report about being unable to install [COLOR=#000000]linux-image-3.5.0-27-generic[/COLOR]. Since I had no other "symptoms," this didn't seem like a problem, so I restarted, thinking, "maybe this error will just go away" and the error didn't return. 

But I'm running [COLOR=#000000]linux-image-3.5.0-23-generic, not [/COLOR][COLOR=#000000]linux-image-3.5.0-27-generic. If I look at Synaptic and do a search on "linux-image-3.5.0" I get [/COLOR]9 different hits, ranging from 18 to 27, and only #23 is installed.

Why do I have all of these different kernel images? 

Should I be running #27? 

Happy to leave things alone since they work, but I'm wondering if #27 will be [SIZE=2]"called for" at [SIZE=2]some point in the futur[SIZE=2]e and this error will return[/SIZE][/SIZE][/SIZE]. Thanks! 



[/SIZE][/FONT]

---

### Post by col48 on 2013-04-24
I think I'd leave things alone and hope that #28 will install and that you can run it with no issues.  It's probably best and safest to run the latest from a security and reduced-bug perspective.

But I'm no expert....

I surmise that #23 was the latest/current one when the medium was built from which did the install was done.  No need to have any older ones at that point.

---

### Post by ibjsb4 on 2013-04-24
I would think that if you look at upgrades in synaptic (status>upgradeable) it would show the available kernel upgrade.

If not, reload package information in synaptic (Ctrl + r).

Myself, Im still running the 3.2 kernel.  Maybe one day Ill move on to the 3.5, but I don't see it as a big deal since my system is working fine.

---

### Post by grahammechanical on 2013-04-24
Those kernel images are all Linux 3.5.0 series kernels. They are Ubuntu updated/bug fixed versions. The old kernels are not removed. This is so we can boot into one of them if the newly installed kernel breaks on your machine. The issue you have is that the kernel 3.5.0-27 did not completely install. So, you are still using 3.5.0-23.

If you search Synaptic for linux-image-3.5.0-27 and right click the line you may see that it is marked to be upgraded. It might have a grey icon to indicate that it needs to be re-installed.

Regards.

---

### Post by thatstheway on 2013-04-24
Thanks ibjsb4 -- Reloaded the package info, but under status I don't see Upgradeable. Perhaps this is more confirmation that leaving things alone is the way to go. Still, wondering if I'm missing out by not running #27...

---

### Post by thatstheway on 2013-04-24
Thanks grahammechanical -- right-clicking the line doesn't show that it's marked to be upgraded, and doesn't show an icon that it needs to be reinstalled. So, this could be more reason to let things be. What was interesting is that for a while it was sitting in Software Update, downloaded but not installed. That was when I had a broken-package condition. Now that I've fixed the broken-package condition, it no longer sits in Software Update. It's as though the system has given up trying to install this thing. And if that's true, there may be a good reason for it... It's a mystery to me!

---

