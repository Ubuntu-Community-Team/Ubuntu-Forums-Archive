---
title: "Can't get Ubuntu to run more than an hour without crashing"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by MadScientistMatt on 2012-01-17
I'm a newbie to Linux, but have been using computers since the Commodore 64. They've always been a means to an end, though - I've installed cards and memory before but I've never been a really hardcore user. And my biggest skill with them, it appears, is creating bizarre and inexplicable errors. I once received a passing grade in a computer science 101 class for handing in a program that wouldn't run, because even the teacher couldn't figure out why. That kind of put a stop to my desire to write any sort of code.
 
Ok, enough boring background. After having a TDSS rootkit on a ~5 year old eMachines computer with an Athlon 64 processor and around 1 gig RAM, and finding the rootkit wasn't playing fair, hiding from several antivirus scanners and refusing to let others run, I decided I wouldn't play fair either. I backed up my data and decided to finally give Linux a try, and see if its malware resistance and stability were all they were cracked up to be. The computer seemed to have been running perfectly fine before the rootkit infestation.
 
Unfortunately, my talent for creating bizarre errors held true. I tried to load Ubuntu 11.10 from a Live CD. The Live CD install crashed on me a few times, but I thought it might be a bit more stable once it was running off my hard drive, I went ahead and installed it, reformatting the drive. I imagined my little annoying rootkit screaming in agony as the install process began. Unfortunately, the crash issues continued after installation, and I tried using 10.10 to see if an older version might be more stable. No dice - the problem is the same on 10.10.
 
Now for a description of the crashes. The screen suddenly gets covered with a repeating pattern based on a small portion of what it was displaying on the same line, in a diagonal-bar effect. The machine totally locks up. There's no sort of text error message giving useful information about what happened, no sort of error message giving information only a guru could comprehend about what happened, not even some sort of confoundingly useless "Critical error" message that gives no useful information other than that the computer is vaguely aware something bad happened. The longest it has gone without a crash is about an hour, the shortest time about 5 minutes, with 5-15 minutes being the norm.
 
I don't even know where to begin troubleshooting this, so I'm hoping someone here recognizes this pattern of crashing and can offer advice. The only thing I could think of was that I'd seen a similar garbage screen back in the MS-DOS days when I attempted to salvave memory out of a 286 and stuff it into a 486 that drove it at more than twice its rated speed, overheated the ICs, and caused the system to lock up. I'm currently running the memory test program off the Live CD, had it running for about 2 hours and 5 passes through the RAM, no errors turning up so far.
 
Please help. I hope I haven't managed to brick a computer by putting Linux on it. Seems with how straightforward the install was, it takes my kind of perverse talent to do that sort of thing nowadays.

---

### Post by VraiChevalier on 2012-01-17
> **MadScientistMatt said:**
> I'm currently running the memory test program off the Live CD, had it running for about 2 hours and 5 passes through the RAM, no errors turning up so far.

I was going to suggest that. I would even let it run overnight.

Second thing I would check out would be any type of overheating problem. Could even be the thermal paste on the processor has dried out. Could also be the graphics chip or card overheating. 

I am suspicious of a hardware problem whereas it happens with both the LiveCD and a hard drive install.

---

### Post by QIII on 2012-01-17
Rootkits are not necessarily crushed like bugs by Linux (that's a myth, like many other myths that might give one the impression that Linux is impervious to any form or security or malware risk) and they can be persistent even through reformatting.  

I would get it to boot up once and hope you can install chkrootkit -- and then run it.

Eliminate that.

Beyond that, my impression is also a thermal fault in the hardware, since it happens in a Live CD session too.  Make sure it's not your pesky rootkit (and chkrootkit isn't 100% effective at identifying problems) and then we'll work on tracking down the problem.  Could be something simple, could be a capacitor on the mobo and you'll have to head to your local computer store.

---

### Post by MadScientistMatt on 2012-01-18
Thank you for your replies! It seems weird that I'd develop a hardware fault at the exact same time that I tried to install Linux, but it would also be consistent with my bad luck with computers. (I once tried to offload an unwanted computer at a used computer store. The tech at the store tried to turn it on and the power supply promptly caught fire. That computer had been built at a rather shady shop and given me no end of trouble, so I wasn't too surprised...) The graphics card seems a bit unlikely - I forgot to mention that, among other things, the Caps Lock and Num Lock stop responding when the crash happens, so the crash doesn't seem to be confined to the graphics card. But I'll pursue the thermal angle now. I've got the computer up and running the memory test and I'll leave it going all night.
 
I wonder if I'll have the same crashed pattern of lines on the monitor after running the memory test all night.  If the memory test *doesn't* crash the system, is that a useful data point about what the problem might be? I'll check it for blown capacitors too, and anything in there running oddly hot.
 
QIII: Where do I get chkrootkit? Can I download it from a Windows box and bring it in over a CD or USB stick? I'm kind of surprised if a rootkit could survive a hard disc format and an install with a totally different OS, but if there's a way for it to happen, it would make sense for the rootkit to be trying to have the last laugh. So I'll definitely look into that once I can try using chkrootkit. And I know Linux isn't immune to malware, just has less malware written for it in the wild, and I get the impression it has fewer security vulnerabilities.

---

### Post by QIII on 2012-01-18
rkhunter and chkrootkit are available in the repos.

And yes, rootkits can survive reformatting and reinstallation.  There  are even proofs of concept where a "rootkit" actually becomes resident  in a motherboard's BIOS.

(I'm pulling my soapbox up now.)

Linux is, by some measures, more secure than Windows, but it is not bullet proof by any means.

There is a misconception that Linux is somehow safer by virtue of its  obscurity or that nobody targets it because it's not worth it by market  share.  You can see how absurd that sounds when you consider that the  lion's share of the internet backbone and corporate servers run on  Linux.  There is a HUGE motivation to hack Linux.  HUGE.  Linux systems  are attacked and compromised all the time -- particularly when people  arrogantly assume they are safe and don't take proper precautions.

Home users who use things like VNC without SSH often fall prey to  cracks.  I understand that is one of the most common cracking  complaints/problems raised here.

Here's an interesting little wiki entry about Linux security (Ubuntu centric):

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

"I don't need a firewall" is one of the most common myths.  Yes, you do  -- or Linux' "firewall" implementation in iptables.  For the machine I  am on right now, I have all ports locked down in and out (not default, I  mean set to "deny" using gufw), with a very select few allowing traffic  out only.  That's behind my secured router.  You have to deploy security in depth.

(Putting soap box away.)

As for a hardware fault showing up when you install a new OS -- which is by far the most likely scenario, not the efforts of nefarious agents to steal you pictures of Uncle Bill and Aunt Mae -- well, those sorts of things often appear during power up or power down.  Some thermal faults don't happen until something cools down and is subsequently reheated, causing it to break.  It's an old joke:  "When I shut down and turned it back on, something was broken!"  "Well, don't ever shut down."

---

### Post by MadScientistMatt on 2012-01-19
Ran a memory check overnight, still nothing comes up (and FWIW, the memory check program doesn't crash). Guess I'll need to check for an overheating processor or the other issues mentioned, like damaged capacitors, next.
 
Thanks for the link about the security basics. I have no intention of letting my guard down because I'm trying to go to Linux - just an expectation that switching from XP's "run everything as root" approach has got to be something of an improvement. I'm not quite sure what the repos are though. I work with the hardware side of race car electronics at my day job, so I've got a pretty good feel for spotting things like a bad capacitor. But when it comes to Linux, I don't know a sudo from sudoku.

---

### Post by QIII on 2012-01-19
Repo = repository, which is where the pre-packaged software is kept.

Sort out the electronics if that's the problem and come on back.

May the Electro Gods be merciful and not hand you a large expense!

---

