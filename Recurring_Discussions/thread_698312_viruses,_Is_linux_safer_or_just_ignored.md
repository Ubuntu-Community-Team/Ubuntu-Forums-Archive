---
title: "viruses, Is linux safer or just ignored?"
date: 2008-02-16
forum: Recurring Discussions
---

### Post by dougleduck on 2008-02-16
Is linux really safer than windows etc? Is there published (preferably quantifiable) evidence showing linux is fundamentally more secure? Or is it a case of theres no 'demand' for linux viruses yet?

I don't want to open up the pandora's box of linux fan boi's preaching about how great it is. :P I already know that.

---

### Post by Spike-X on 2008-02-16
Both.

---

### Post by handy on 2008-02-16
I never use anti-virus software on Linux or Mac OS's as they just don't need it.  I don't serve data to Windows machines so I don't have to protect the recipients.

The following link gives a very good explanation of the situation:

***_[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)_***

---

### Post by MONODA on 2008-02-16
no system is ever 100% secure but linux is quite close to it. ubuntu comes with no open ports by default so you wont have to worry about needing a firewall. many have asked the same question as you and I have to say that I hae read many articles addressing this and saying that linux is raelly more secure but I cant remember the details... so sorry. you could check out:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by peabody on 2008-02-16
This was my response to a thread that came to discuss this subject:

[http://ubuntuforums.org/showpost.php?p=4341242&postcount=22](http://ubuntuforums.org/showpost.php?p=4341242&postcount=22)

Linux isn't bullet proof.  But the notion that computers need their hi-tech security blankees known as anti-virus software has really gone too far in my opinion.

---

### Post by PmDematagoda on 2008-02-16
The two duplicate threads have been merged(along with a few errors on my part, but I fixed them in the end:)).

---

### Post by K.Mandla on 2008-02-16
I've dropped this into Recurring Discussion since it's a discussion that ... recurs. :roll:

---

### Post by dougleduck on 2008-02-16
I realise when I couldn't see it in the main area. I've tried to put a small 'twist' on it.

The articles given are of the type ive read many a time. Perhaps the Linux community, and subsequently the criminal community wanting to exploit OS's, is just too small for any reasonable quantitative analysis.

---

### Post by handy on 2008-02-16
We don't have virus problems, if the *nix OS's were vulnerable then we would have viruses now.  There are plenty of people out there that would enjoy creating a viral epidemic in these *nix systems. 

Linux, BSD, OS X are much safer by design & that is the reason we don't have a problem.

---

### Post by Darkhack on 2008-02-16
In order for a program to actually be a virus it has to self-replicate.  It has to attach itself to programs.  The architecture of Windows allows this kind of behavior.  Linux (and most other UNIX-like systems) do not.  It's simply not possible for applications to self-replicate in that manner.

The second reason is that most applications are installed through the package manager in a secure repository.  Windows users are more likely to visit third-party websites and install unknown executables.

The third reason is stuff like SELinux, AppArmor, and user permissions make the effect of any viruses extremely limited.

As for being ignored.  That has some truth to it.  Virus writers will ignore non-Windows platforms because a lot of malware spreads based on the user being an idiot and installing random stuff.  Most non-Windows users know better.  However, a virus writer could be successful if he managed to create a worm for Linux which self-replicated through a network.  Why infect mom and dad when you can infect major fortune 500 companies?  Although the market share is smaller, there is a lot of it invested in major businesses and servers.

---

### Post by MONODA on 2008-02-16
also since there are so many different distros, it makes it much harder to make a virus to affect all or even a small number. and ubuntu comes out every 6 months making changes in the OS everytime.

---

### Post by aysiu on 2008-02-16
Self-replicating viruses aren't a problem, but trojans and other malware dependent on social engineering *could* be problems if they were developed and if new users weren't savvy enough to resist them.

---

### Post by dougleduck on 2008-02-16
The points all make sense. Ignoring the issue of social engineering, I find it difficult to believe that if there was a bigger market share exploits wouldn't be found.

But I want some hard evidence; I'm a sucker for statistics!

---

### Post by peabody on 2008-02-16
> **dougleduck said:**
> The points all make sense. Ignoring the issue of social engineering, I find it difficult to believe that if there was a bigger market share exploits wouldn't be found.

But I want some hard evidence; I'm a sucker for statistics!

It is good to ignore the social engineering thing.  That's been done; see all the signatures with "don't run any commands with rm in them!" floating around these forums?  I wouldn't really call that a flaw of Linux.

If you look at the CERT, I'm pretty sure you'll find more documented security problems with Linux than Windows.  Yet how many people actually have had their machines taken over by in-the-wild exploits or viruses?  I'm pretty sure if we had a formal poll on these forums, the number would potentially be in the single digits.

More known exploits != less secure.  It's a terrible metric to go by.  When flaws are discovered in Linux, they get patched almost instantly before there's time for any zero-day exploits.  How many exploits are lurking in Windows waiting to be found?

---

### Post by dougleduck on 2008-02-17
Perhaps the only way to know for sure is to wait for the market penetration of linux to increase (assuming it continues to) and see what happens then...or spend several day s searching for articles, which is not going to happen :D.

---

