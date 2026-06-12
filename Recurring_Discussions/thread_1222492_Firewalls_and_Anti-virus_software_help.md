---
title: "Firewalls and Anti-virus software help"
date: 2009-07-24
forum: Recurring Discussions
---

### Post by Commisar Jimp on 2009-07-24
I know Linux isn't supposed to be the virus magnet that my old Vista was, but I'd still like to know a bit about security, specifically firewalls and anti-virus programs. Does Ubuntu come with any, if not what are good ones and how do they work?

---

### Post by philcamlin on 2009-07-25
you dont need any virus checkers because there are no viruses for ubuntu but i would get firestarter as a firewall

sudo apt-get install firestarter

---

### Post by Commisar Jimp on 2009-07-25
Thanks that works great

---

### Post by aysiu on 2009-07-25
Read the security sticky:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

It has everything a new user could possibly want to know about security (and probably a lot more).

---

### Post by MelDJ on 2009-07-28
there are antivrus software available for ubuntu. There would be of no use for you as ubuntu does not have viruses :D. Anyway you could use them to scan your windows drives. you can get Avast, panda, Avg antivirus for ubuntu from their respective sites. A ore detailed explanation can be read here: 
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus). Hope it helps:KS

---

### Post by lisati on 2009-07-28
> **MelDJ said:**
> there are antivrus software available for ubuntu. There would be of no use for you as ubuntu does not have viruses
Stand by for the dissenters! 

I've yet to encounter malware that will hurt Ubuntu, but have read anecdotal evidence that it does exist. With a little care and good sense, they shouldn't be a problem. 

The value in having AV software installed in Ubuntu lies more in keeping Windows installations that you might have contact with safe.

---

### Post by QIII on 2009-07-28
There are roughly 800 Linux viruses in the wild, according to those who research such things.  Compare that, of course, to hundreds of thousands of viruses, malware, trojans, etc for Windows.

Most of the Linux ones are targeted at servers (since, in the case of Ubuntu, there are no open ports by default in non-server applications) and have only had very limited success.  It is difficult in the extreme to infect a Linux machine, but not entirely impossible.

It is highly unlikely that you will need to worry about viruses and malware, but it is not outside the realm of possibility.  Being arrogant as a community and poo-pooing the threat is asking for trouble.  But I don't think that is the case at this point, since thousands of developers go over and over the code all the time to tidy up holes.  

Still, all it takes is for one PFY sitting in his mother's basement in Des Moines to go "Wow, I didn't think you could do THAT!" to have us all eating our words.  Safe today does not mean safe tomorrow.

It does not hurt to be vigilant against the extremely remote chance that we may wake up tomorrow with a problem.

---

### Post by sandeepraj on 2009-07-28
i some where read that my virus of linux targetted a sector of kernal which was left open. but when they found about it they updated kernal and closed that sector.. so about 80% of virus cant effect the computer

---

### Post by MelDJ on 2009-07-28
> **lisati said:**
> Stand by for the dissenters! 

I've yet to encounter malware that will hurt Ubuntu, but have read anecdotal evidence that it does exist. With a little care and good sense, they shouldn't be a problem. 

The value in having AV software installed in Ubuntu lies more in keeping Windows installations that you might have contact with safe.

Yeah. agree with you. I meant there aren't harmful viruses :)

---

### Post by HotShotDJ on 2009-07-28
> **lisati said:**
> but have read anecdotal evidence that it does exist.Where?
> **QIII said:**
> There are roughly 800 Linux viruses in the wild, according to those who research such things.Says who?
> **sandeepraj said:**
> i some where read that my virus of linux targetted a sector of kernal which was left open.Which virus? Where did you read this?

All I ever see are unsupported assertions regarding the potential for Linux viruses. The following short article provides a good, easy to understand, explanation of why viruses are not a problem for Linux: [http://librenix.com/?inode=21](http://librenix.com/?inode=21)

---

### Post by QIII on 2009-07-28
Says who?

Kaspersky for one.

They listed 712 in 2005.

Bliss appeared in 1997, although it died pretty quickly.

Most are dealt with quickly because of the Linux community's ability to react much more nimbly than Microsoft.

As I said, it is extremely difficult for Linux machines to be infected.  That does not mean malware is not out there and it does not mean we can just drop our pants and cop a squat for a little relief in the jungle when there are snipers in the trees.

When you consider the ratio of 800 to several hundred thousand, the comparative incidence is low.  But it is not zero.

---

### Post by MelDJ on 2009-07-28
i think much of this is explained here [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
there's even the kaspersky guy's quote

---

### Post by QIII on 2009-07-28
> **MelDJ said:**
> i think much of this is explained here [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
there's even the kaspersky guy's quote

All of that is, of course, exactly what I was saying.  But that puts it more succinctly.

---

### Post by sydbat on 2009-07-29
I'd be leery of any money making company telling you that there is a large threat. Seriously. They want you to buy their product so they **will** manipulate the "facts" to their advantage.

Also, there is no mention of specifics with this 800+ malware claim. What are they? The list in the wikipedia article, while claiming to only be partial, still does not link to ANY source that has a comprehensive list. Dodgy at best.

According to this site ([viruslist.com]("http://www.viruslist.com/en/viruslistfind?objs=virus&words=linux")), there are 100 chunks of known malware for Linux. Compare that to the same site and [Windows malware]("http://www.viruslist.com/en/viruslistfind?objs=virus&words=windows"). These are considered current malware accessed from Kaspersky. So, they (Kaspersky) are lying when they claim 800+ for Linux (see my comment above as to why).

---

### Post by bodhi.zazen on 2009-07-30
Linux is not windows. Both have malware.

See the security link aysiu posted 5 days ago.

The way of Windows - Closed source, many security holes, relies on 3rd party fee-for-service applications to plug holes, source code goes undocumented and unpatched for decades.

So while there  are hundreds of thousands of know viruses the source code remains unpatched and you remain vulnerable.

The way of Linux - Open source, fewer security holes, does not rely on 3rd party fee-for-service applications, documented security holes are patched.

So while there are  a few hundred reported Linux viruses, assuming your system is up to date, those vulnerabilities were patched many years ago and you are invulnerable to them.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by sydbat on 2009-07-30
> **bodhi.zazen said:**
> Linux is not windows. Both have malware.

See the security link aysiu posted 5 days ago.

The way of Windows - Closed source, many security holes, relies on 3rd party fee-for-service applications to plug holes, source code goes undocumented and unpatched for decades.

So while there  are hundreds of thousands of know viruses the source code remains unpatched and you remain vulnerable.

The way of Linux - Open source, fewer security holes, does not rely on 3rd party fee-for-service applications, documented security holes are patched.

So while there are  a few hundred reported Linux viruses, assuming your system is up to date, those vulnerabilities were patched many years ago and you are invulnerable to them.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)Thank you. infinity +1

---

