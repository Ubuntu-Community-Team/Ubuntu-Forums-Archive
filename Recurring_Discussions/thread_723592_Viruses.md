---
title: "Viruses"
date: 2008-03-13
forum: Recurring Discussions
---

### Post by drjulesd on 2008-03-13
Just a quick question...When i used to use Windows 18 months ago, I was forever running virus checks, had to be careful what i downloaded, run spyware/adware software...and so on.  How is it that Ubuntu doesn't have any of these issues?  Don't get me wrong, very thankful of this, but just curious!  Lamens terms if a bit of a techy response please!  Many thanks.

---

### Post by jan quark on 2008-03-13
check this out:

[https://help.ubuntu.com/community/Antivirus?highlight=%28virus%29](https://help.ubuntu.com/community/Antivirus?highlight=%28virus%29)
[https://help.ubuntu.com/community/Linuxvirus?highlight=%28virus%29](https://help.ubuntu.com/community/Linuxvirus?highlight=%28virus%29)

---

### Post by {BzF}~JOKesTER on 2008-03-13
Main Reason Is That Most Virus Writers Don't Bother To Target Linux - Most Of Us Are Smart Enough To Get Them Back!!!!
- Plus Linux Is More Secure...

I've Not Ever Been Infected - I Don't Think Any Of US On This Site Ever Have -

However If Your Truly Obsessed Here's A Great Free Anti virus For Ubuntu :

[http://free.grisoft.com/doc/5390/us/frt/0?prd=afl](http://free.grisoft.com/doc/5390/us/frt/0?prd=afl)

---

### Post by kellemes on 2008-03-13
No, not really..
Just don't neglect the mechanism of privileges, [RootSudo]("https://help.ubuntu.com/community/RootSudo") and setting-up your firewall.

---

### Post by Eclipse. on 2008-03-13
Linux is alot more safer than windows.There is only about 5 known viruses for linux and none have been in the wild, just in labs.

Basicly you dont need any av's.

---

### Post by The Titan on 2008-03-13
isn't it completely plausible to write a virus for Linux, just not as effective as for windows so nobody does?

---

### Post by ninjarat on 2008-03-13
Because Windows security is absolute garbage, thanks to a huge number of fundamental design flaws, especially in memory management, the registry, and networking.  These all combined make it a wonderland of freedom and destructive glory for viruses.  Not only does the Linux kernel have virtually no bugs, but every component of the GNU system is crafted to be absolutely water tight.

I think the main difference is that Linux was derived from Unix, which at the time was proprietary.  Linus Torvalds created it for his own amusement.  Then Richard Stallman created the GNU system with his team making a complete operating system skeleton.  But from the beginning it was designed as a multitasking and multiuser system with perfection in mind.  For example, X, which is the most popular GUI system for Unix-like systems (Linux, MacOS, etc.) is actually a server.  Because of this, all networking that involves direct GUI communication and inter-terminal communications automatically has proxy level protection just because of the basic design.  And this is only a single example of how the security is better.

Windows was started as a system for the common end user.  At the time it was started, none of this was very important to the common user, so adding that would have just been system bloat.  The problem is that it's important now.  And the reason why this is a very serious issue is that Microsoft considers it to be inefficient productivity wise, and has said so, to go back and redesign some of the core components of their system, merely because of how many man-hours and how much cash it would take.  However the thing they hadn't anticipated was that this would make their system more and more unreliable through revisions, because the Kernel is literally almost 25 years old since they redid anything important.  Vista, for example, despite how glossy it is on the surface, is literally supported on a structure of 25 year old rickety software technology upon which the biggest change was merely to port the code to run on newer hardware.  And they don't even bother to port older versions of DirectX to newer systems for instance.

So in summary, design flaws (especially networking and registry) and failure to redesign as they are discovered is and will be the Windows collapse, and the reason it gets SO MANY VIRUSES.  If you have ONE LOOK at ANYONE ELSES SECURITY you will NEVER WANT TO GO BACK.  If Vista doesn't do it, the next one will or I must be even crazier than I thought.  GNU/Linux systems on the other hand are designed and redesigned when called for with everything planned out for current and possible future technology.

Make sense?  Too much rambling?

Peace.
:guitar:

---

### Post by kellemes on 2008-03-13
> **ninjarat said:**
> Make sense?  Too much rambling?

Yeah to both.. ;-)

---

### Post by ubuntu27 on 2008-03-13
> **The Titan said:**
> isn't it completely plausible to write a virus for Linux, just not as effective as for windows so nobody does?

People already tried to write virus for GNU/Linux but they didn't succeed in spreading it. Linux is just more secure. 
But keep in mind that if a user is an "idiot" or not careful, their computer could get infect somehow.

A lot have been discussed in the [Ubuntu GNU/Linux Security Discussion Forum]("http://ubuntuforums.org/forumdisplay.php?f=322").

To summarize:

+Linux is more secure
+Linux users are usually more knowledgeable
+There are more Windows box in Desktop computers, so virus makers are more interested in them 
(It is worth nothing that there are more Linux computers on the Server Market)
+Windows is really insecure, bad design.

---

### Post by FreewheelinFrank on 2008-03-13
Ah virus scans!

I sometimes boot into Windows just to play a bit of HL2, or to run a virus scan or two. Just nostalgia, you understand!

---

### Post by p_quarles on 2008-03-13
Moved to Recurring Discussions. 

Good overviews on this topic can be found in these posts:
[http://ubuntuforums.org/showthread.php?t=694198](http://ubuntuforums.org/showthread.php?t=694198)
[http://ubuntuforums.org/showthread.php?t=131616](http://ubuntuforums.org/showthread.php?t=131616)

---

### Post by aysiu on 2008-03-13
Self-replicating viruses won't work well in Ubuntu, but malware dependent on social engineering greatly depends on the desirability and gullibility of the target for the malware-writers.

---

### Post by rune0077 on 2008-03-13
> **aysiu said:**
> Self-replicating viruses won't work well in Ubuntu, but malware dependent on social engineering greatly depends on the desirability and gullibility of the target for the malware-writers.

[http://en.wikipedia.org/wiki/Morris_Worm](http://en.wikipedia.org/wiki/Morris_Worm)

Yes, I know, this was ages ago, but the *nix architecture has not changed drastically since then (though obviously, this particular security hole has long since been closed). Just to say, it is possible for self-replicating viruses to spread across a Linux-system, as long as there's security holes to exploit.

---

### Post by aysiu on 2008-03-13
> **rune0077 said:**
> [http://en.wikipedia.org/wiki/Morris_Worm](http://en.wikipedia.org/wiki/Morris_Worm)

Yes, I know, this was ages ago, but the *nix architecture has not changed drastically since then (though obviously, this particular security hole has long since been closed). Just to say, it is possible for self-replicating viruses to spread across a Linux-system, as long as there's security holes to exploit.
That hasn't been patched?

---

### Post by p_quarles on 2008-03-13
> **rune0077 said:**
> [http://en.wikipedia.org/wiki/Morris_Worm](http://en.wikipedia.org/wiki/Morris_Worm)

Yes, I know, this was ages ago, but the *nix architecture has not changed drastically since then (though obviously, this particular security hole has long since been closed). Just to say, it is possible for self-replicating viruses to spread across a Linux-system, as long as there's security holes to exploit.
Yeah, that's true enough, and the recent remote root access exploit is the kind of thing that would allow that. 

But, it's still not the same as the situation with Windows. Self-replicating viruses are so prevalent in that system precisely because you don't need an exploit to gain root access to the machines of most home users and many enterprise users. There are other reasons as well -- including the fact that GNU/Linux source code can be viewed by anyone with an interest in its security -- but the fact of default privilege separation is the biggest factor (imho).

---

### Post by aysiu on 2008-03-13
Also, in this context, running anti-virus doesn't prevent security holes from being exploited. That's what patches are for.

---

### Post by Sef on 2008-03-13
> Linus Torvalds created it for his own amusement. Then Richard Stallman created the GNU system with his team making a complete operating system skeleton.

Actually it is the opposite.  Stallman had created everything for a complete system, but the kernel.  Then Torvalds created the kernel.

---

### Post by rune0077 on 2008-03-13
> **aysiu said:**
> That hasn't been patched?

Yeah it has, long time ago of course. It was just an example.

> **p_quarles said:**
> Yeah, that's true enough, and the recent remote root access exploit is the kind of thing that would allow that. 

But, it's still not the same as the situation with Windows. Self-replicating viruses are so prevalent in that system precisely because you don't need an exploit to gain root access to the machines of most home users and many enterprise users. There are other reasons as well -- including the fact that GNU/Linux source code can be viewed by anyone with an interest in its security -- but the fact of default privilege separation is the biggest factor (imho).

Absolutely. I'm not trying to say that Linux is as bad as Windows (not even by a long shot), or even bad at all, just that there's no such thing as 100% secure. Still, you could probably easily run a Linux system for years and years without ever running into a virus or a threat. After a clean install of Windows it rarely takes more than a few weeks before your anti-spyware starts reporting suspicious files.

---

### Post by aysiu on 2008-03-13
> **rune0077 said:**
> After a clean install of Windows it rarely takes more than a few weeks before your anti-spyware starts reporting suspicious files. That's why I urge Windows users to run as limited user instead of administrator. Few listen, and the rest would rather have "convenience" + multiple malware scanners + occasional Windows reinstalls to "incovenience" and effective security.

---

### Post by rune0077 on 2008-03-13
> **aysiu said:**
> That's why I urge Windows users to run as limited user instead of administrator. Few listen, and the rest would rather have "convenience" + multiple malware scanners + occasional Windows reinstalls to "incovenience" and effective security.

That's my mothers attitude to Windows to (and she is not by any means a computer illiterate): I try to tell her that the reason her computer isn't responding as fast as it used to, is almost certainly because she got spyware on it, and she replies "Oh well, as long as it still works".

---

