---
title: "How secure is Linux?"
date: 2012-10-15
forum: Recurring Discussions
---

### Post by ArminasAnarchy on 2012-10-15
So, someone comes up to you, and is shoulder surfing you going about  your everyday PC use. Suddenly you hear they cry, "Ah, that's not  Windows! What is it?!". An explanation that you're running Linux is  likely to be met with a blank stare and a follow up question; "What's  that? Why are you using it?" (assuming we're talking about Joe Public  here).

One of the points frequently made about Linux is not only do few people  bother writing malicious code for it - the malicious code is going to  have a tough time getting into your system. Long term, a computer  running Linux might need reformatting for cosmetic reasons, but  decreasing performance is unlikely to become an issue (whereas 1/2  months of Windows use drags the PC down).

But just how secure is Linux? I think there might be a firewall running  with the system, but for users installing and wanting a working system  out of the box (read: myself), configuring it isn't something you bother  with. As far as I'm aware, no one bothers running any AV software  either (hopefully I can get a poll up on this issue). Certainly I don't,  though coming over from Windows, it's something I'm considering.

Just want to throw this one wide open really, and hear the opinions of ordinary users. [IMG]http://www.kubuntuforums.net/images/smilies/smiley.gif[/IMG]

---

### Post by mike acker on 2012-10-15
this reference
[http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/](http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/)

...is a little dated but nonetheless insightful

Linux { IMHO } ... is not likely to install anything unless the system owner approves it.

this would not cover data. possibly in the form of scripts or byte code that might be dropped into your browser. abusing the plug-in mechanism possibly, or maybe another way ...  I would use a separate user logon for any sensitive web app e.g. Turbotax, e/bill pay ...

which leads to a Big Concern today ,that being that hackers are trying harder to get malware into the distribution channel... "app store" for phones ... 

worse it seems the "firmware" in hardware devices may be a target. it's a topic i love to chew on { but it doesn't always make the sysops happy :-( }

note that there is now some concern here in Linux Land over the new INTEL firmware designed to make sure op-sys components are properly signed before they are loaded ...

remember: a digital signature not only authenticates the sender -- it also insure the content of the transmittal not altered somewhere along the way

---

### Post by Jakin on 2012-10-15
The only real danger, is unknowingly accepting an infected file, and then sharing it with a windows user/machine.

Anti-virus could come in handy for making sure that file is safe before sharing- however it will have minimal at best- use on linux itself.

---

### Post by KiwiNZ on 2012-10-15
I reinforce what Jakin has said. If you are a mixed OS Network then you could pass on and infect other machines with Malware etc.

As for the bigger picture, Linux is as secure as the users usage habits just like any other OS it can be attacked, it can be infected.

---

### Post by Paqman on 2012-10-15
Any OS is likely to only be as secure as the applications it runs. Exploits against parts of an OS are rare, exploits in applications are dime a dozen.

---

### Post by lykwydchykyn on 2012-10-15
There seems to be a pervasive notion that "Anti-Virus" means "any kind of security software", and that as Linux users don't use "Anti-virus" they don't have or need any sort of security software.  This is not true.

Ubuntu comes with apparmor, for instance, and you can obtain rootkit scanners like chkrootkit and rkhunter from the repositories.  These programs address actual threats that are known to exist on the Linux platform; "viruses" are not real problems for Linux.  Very very few even exist, and as far as I'm aware, they all rely on long-since-patched flaws.  But there are more security threats out there than just "viruses".

---

