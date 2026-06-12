---
title: "/usr/sbin/vbetool Start up Crash on Ubuntu 14.04"
date: 2015-02-13
forum: New to Ubuntu
---

### Post by Andrewnicoli91 on 2015-02-13
Hello,

I am experiencing a error/crash at startup. I would like to findout if anyone has shed any light on this issue already and if someone may be able to assist me in fixing it. I truly appreciate everyone who will take the time just to read this thread!!


apt-cache policy vbetool
vbetool:
  Installed: 1.1-3
  Candidate: 1.1-3
  Version table:  *** 1.1-3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages
        100 /var/lib/dpkg/status


Following crash details:
[COLOR=#333333][FONT=Helvetica Neue]ExecutablePath: /usr/sbin/vbetool
[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica Neue]Package vbetool 1.1-3
ProblemType: Crash
[/FONT][/COLOR]Title vbetool crashed with SIGSEGV in wrb()
ApportVersion: 2.14.1-0ubuntu3.6
[COLOR=#333333][FONT=Helvetica Neue]Architecture: amd64
[/FONT][/COLOR]CoreDump - (Binary data)
[COLOR=#333333][FONT=Helvetica Neue]DistroRelease: Ubuntu 9.04[/FONT][/COLOR]
Installation Date(4 days ago)??
Installation Media Ubuntu LTS Trusty Tahr
ProcCmdline vbetool vbestate restore
ProcEnviron
LC_COLLATE=C
Path=(custum,no user)
SegvAnalysis : destination not located in a known VMA region(needed writable region)
SegvReason - Writing unknown VMA
Signal 11
SourcePackage vbetool


Anyone have any idea what this is all about? What is vbetool in the first place? Supposedly I installed it 4 days ago.

Again, thank you in advance for anyone who takes the time to assist a new Ubuntu user.

Andrew

---

### Post by Bucky Ball on 2015-02-13
*Thread moved from **Resolution Centre **to **New to Ubuntu**.*

The ***Resolution Centre*** is for issues regarding forum accounts and forum matters, not general support. You will have better luck here I hope. Good luck. ;)

PS: [This]("http://linux.die.net/man/1/vbetool") might give you some clues about what vbetool is and what it does.

---

### Post by Andrewnicoli91 on 2015-02-13
Thank you, and my apologies.

---

### Post by Bucky Ball on 2015-02-13
All good. Sorry I can't offer more help with your problem. Am unfamiliar with vbetool. ;)

---

