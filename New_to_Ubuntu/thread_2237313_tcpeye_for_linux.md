---
title: "tcpeye for linux"
date: 2014-08-01
forum: New to Ubuntu
---

### Post by wimpy2 on 2014-08-01
I've looked for an equivalent program in Lubuntu, without success. I suppose it might still be possible to run the Windows version through Wine, but is there a Linux version that I've missed?

---

### Post by coldcritter64 on 2014-08-01
I'm not familiar with tcpeye or its functions but I did find this link with couple of alternatives, hope it helps. Cheers
[http://alternativeto.net/software/tcpeye/?platform=linux](http://alternativeto.net/software/tcpeye/?platform=linux).

---

### Post by Vladlenin5000 on 2014-08-01
I strongly advise against bloating your system with an OS emulator plus the emulated software for something so basic that can be done with a few commands in Linux. I suggest you ask in the "Networking & Wireless" section - where the experts are - about what you can use to monitor ports. You can mention tcpeye to better illustrate your intended use.

---

### Post by ian-weisser on 2014-08-01
There is no *single* replacement for tcpeye, since much of what tcpeye seems to provide is (I think) rather unhelpful eye candy.

Linux provides excellent tools to monitor and control the applications that use your system's networking ports (socket connections). 

For the most useful list of tcp/udp ports in use, no additional software is needed. See the terminal's **netstat** command. The output is tremendously configurable.
```
man netstat
```

Do some searching for 'netstat' in this forum, and you will discover many suggested configurations and uses.

Personally, I use '**sudo netstat -tulpn**'when auditing listening applications.
Auditing outbound connections is not difficult, open source software makes it easy to discover what a process is, why it's required, and what it talks to.

---

### Post by wimpy2 on 2014-08-01
What I would like is something that will monitor all Internet connections from this PC in a continuous (continual) graphical way.  Tcpeye does this quite well and often shows whether you have been unlucky enough to pick up malware that steals your bandwidth. Command line - netstat -tulpn -   seems to do the job, but on a one time basis. I would have to remember to rerun it every now and then. I'll do some more reading on the subject, and then head on over to the Networking and Wireless section. My thanks to everyone that replied. I am grateful for your advice and expertise. UPDATE: I've since come across a deb package called NetActivityview, which seems to be a GUI to netstat. It does just what I wanted, so I'll mark this thread as "Solved"

---

### Post by ian-weisser on 2014-08-01
Linux systems work *differently* than Windows systems do. Protection and recovery from a compromised system obeys similar principles, of course, but the details and best practices differ. 

Monitoring your network connections is much too late in the causal chain to be very useful ("Oh, look! My system needs to be laboriously wiped and reinstalled now!"), and seems likely to be fraught with false positives. Depending upon your needs, there may be easier and more effective ways.

---

### Post by wimpy2 on 2014-08-01
> **ian-weisser said:**
> 
Monitoring your network connections is much too late in the causal chain to be very useful ("Oh, look! My system needs to be laboriously wiped and reinstalled now!"), and seems likely to be fraught with false positives. Depending upon your needs, there may be easier and more effective ways.

I disagree with your statement about it being much to late. The payload for the malware that I am hoping to catch is precisely their access to the internet. If you pull the plug at the first signs, you buy time to put matters right. You can then investigate and consult those who might be able to give you answers. As far as my needs are concerned, I thought I had set them out reasonably clearly and your reply certainly helped a great deal.

---

### Post by The Cog on 2014-08-02
You may be interested in iftop (text-mode) or etherape (graphical) for real-time monitoring of network activity.

---

### Post by wimpy2 on 2014-08-16
Thanks for the reply. I'm sorry to have missed it, earlier. I did try etherape but ran into an old problem. It has to be run as root. Not a big deal, but Net activity viewer gives me what I wanted and runs straight from the desktop. Iftop also, seems to need to be run as root, but it does have virtually the same information as Netactview.

---

