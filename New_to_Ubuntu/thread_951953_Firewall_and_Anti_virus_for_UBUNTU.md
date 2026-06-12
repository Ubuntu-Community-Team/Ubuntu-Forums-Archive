---
title: "Firewall and Anti virus for UBUNTU"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by PhilOHara on 2008-10-18
Hi I have recently downloaded and run the live CD of ubuntu 8.04 64 bit version and love what I see. Before I install it I am wondering about the firewall and anti virus for 64 bit OS. I saw something called fire starter in the repos but no anti virus can I just use AVAST 64bit like I run on my Windows 64 bit OS.
What are other people using...also what spyware prog can I use?
Any information is appreciated?
And one other thing I run a AMD 64 bit motherboard 1.8Ghz with only 1 gig, I notice at intermittent times CPU usage goes to 100 and I freeze for a while then everything goes back to normal.
Would another meg of RAM be useful and I read 2 meg is standard for 64 bit systems?    regards Phil

---

### Post by Mazza558 on 2008-10-18
For everyday usage, you don't need a firewall/antivirus. Ubuntu is secure out of the box and has a firewall built-in. However, if you work with Windows PCs a lot, you might want to get ClamAV - it's in Add/remove programs and will let you scan files for Windows PCs, just in case you accidentally pass one on. There are no known Ubuntu viruses that are circulating the web.

---

### Post by GSMX on 2008-10-18
> **PhilOHara said:**
> 
And one other thing I run a AMD 64 bit motherboard 1.8Ghz with only 1 meg ram, I notice at intermittent times CPU usage goes to 100 and I freeze for a while then everything goes back to normal.
Would another meg of RAM be useful and I read 2 meg is standard for 64 bit systems?    regards Phil

1 mb of ram??? i hope you're kidding... maybe you mean 1 gb of ram. Because if you'd have 1mb, you're 63 below the MINIMUM requirements (384 is recommended). And yes, it's common for 64bit to have somewhere between 2 and 4 gb of ram, but it shouldn't be the problem. Maybe you could give some more information, what program is causing the hang?

---

### Post by gn2 on 2008-10-18
You should have a read of [this]("http://ubuntuforums.org/showthread.php?t=510812") to better understand security in Ubuntu.

The slowdowns you experienced are likely to have been due to using the Live CD.
1gb of RAM is plenty for most tasks.

---

### Post by oldos2er on 2008-10-18
You're already running a firewall called iptables (or is it ufw now?). Firestarter is just a GUI front-end for iptables, and it's not being updated. Also, most Linux anti-virus programs only check for Win* viruses.

---

### Post by sneeks on 2008-10-18
you could also try the avg for Linux,but i have not had much success with it,but have had clam working fine.
firestarter is an Linux firewall but i could never get it to run right in gutsy,maybe hardy will be better.
but as the last bloke said,for general usage you will be fine.
an example....
my son had xp for a while and he managed to cook it about every week.
he has now has hardy for almost a year and it works.
he has also found that he is now the tech guy in school,he knows no more than any other student but he is now more aware of what he does.
nuff said...

---

### Post by speedzor on 2008-10-18
somethings wrong here.

you said the **_CPU_** usage is op to 100%.
CPU = processor

has not that much to do with RAM-memory. You probably should better think about buying a better processor.
And even though, 2GB of RAM is important..

further: there are no viruses for linux, so an antivirus isn't required. And standard, ubuntu has a firewall on-board called IPtables, and firestarter is just a GUI for this. This firewall is automatically enabled.

---

### Post by PhilOHara on 2008-10-18
uuhhh yes 1 gig....

---

### Post by lisati on 2008-10-18
> **sneeks said:**
> you could also try the avg for Linux,but i have not had much success with it,but have had clam working fine.


A couple of important notes about AVG free can be found [here]("http://ubuntuforums.org/showpost.php?p=5586774&postcount=1") and [here]("http://ubuntuforums.org/showpost.php?p=5939398&postcount=10")

---

