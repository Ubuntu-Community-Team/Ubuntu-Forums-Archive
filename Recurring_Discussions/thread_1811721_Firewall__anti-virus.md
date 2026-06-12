---
title: "Firewall / anti-virus"
date: 2011-07-25
forum: Recurring Discussions
---

### Post by jermza on 2011-07-25
I've started noticing, in random screenshots, that Linux users are using firewalls / shields / anti-virus indicators.

Is this something that I should take note of?  (I have none, that I know of.)

---

### Post by MG&amp;TL on 2011-07-25
Depends what you are doing, I suppose. It's not as necessary as in windows, but if you download lots of packages from dodgy sources, it's probably a good idea-how paranoid are you? :D

---

### Post by jermza on 2011-07-25
I'm not paranoid.  My tinfoil hat is packed away.  :-)

I download, almost always, from the Software Centre.  (Other than torrents, that is.)  So I guess I'm safe, then?

But what about websites?  Every now and then, I've heard that certain websites can install stuff in your browser / on your machine.  (I don't visit dodgy sites, but sometimes you stumble across dodgy sites, accidentally.)

---

### Post by MG&amp;TL on 2011-07-25
Installing one isn't going to take up a lot of time or disk space, so go for it. I guess there's quite a few malicious people out there, and I guess about 1 in 50 of those can code, so that's a lot of people. Go for it, if you're worried about it. :)

---

### Post by mikechant on 2011-07-25
There are no known effective viruses for Linux, the only real purpose of running anti-virus on Linux is to avoid passing on infected files to Windows PCs (or your own Windows partition).

As far as your browser is concerned, it's possible it could 'leak' private information (i.e. a website in one tab might be able to see information in another tab), or some other exploit which runs inside the browser; the way to minimise the risk is to always run a supported release of Ubuntu and always apply security updates as soon as possible.

Also, running an Ad-blocker like Ad-block plus in Firefox reduces the risk, since even 'respectable' web sites sometimes serve malicious adverts.

---

### Post by MG&amp;TL on 2011-07-25
You know linux is pretty much devoid of viruses right?

---

### Post by Snowboi on 2011-07-25
> **MG&TL said:**
> You know linux is pretty much devoid of viruses right?

In other words there are no viruses in the wild for linux currently. (that we know of)

[http://en.wikipedia.org/wiki/Linux_malware]("http://en.wikipedia.org/wiki/Linux_malware")

The link above may help you. :popcorn:
I personally do not and never will use an anti-virus or firewall with ubuntu. (besides the firewall which is installed by default called iptables)

Note : You have nothing to fear if you get a virus it is a windows virus and has no effect on your ubuntu installation.
The most a virus could do was create files in your home folder that do nothing but waste little to no memory, unless of course you run it as root. Since mac and linux are so similar viruses like koobface have a tiny effect on ubuntu (just puts some files in your home folder) Koobface is a facebook virus that is installed when you run a java application on a fake youtube website.

---

### Post by MG&amp;TL on 2011-07-25
Incidentally, while mucking around with C++ the other day I managed to accidentally generate an infinite loop that printed a statement repeatedly to a gedit file on the desktop. I stopped it before it did anything, (thank god for compilers and missing semi-colons), but if it had compiled, what would have happened if I had run it? Because in theory it would print characters as fast as it possibly could, filling up my hard disk. Would this happen, and if so how fast?

---

### Post by vahnx on 2011-07-25
> **MG&TL said:**
> Incidentally, while mucking around with C++ the other day I managed to accidentally generate an infinite loop that printed a statement repeatedly to a gedit file on the desktop. I stopped it before it did anything, (thank god for compilers and missing semi-colons), but if it had compiled, what would have happened if I had run it? Because in theory it would print characters as fast as it possibly could, filling up my hard disk. Would this happen, and if so how fast?

I'd think it would probably bog down your system a bit until you manage to kill the process id.

---

### Post by Redblade20XX on 2011-07-25
> **MG&TL said:**
> Incidentally, while mucking around with C++ the other day I managed to accidentally generate an infinite loop that printed a statement repeatedly to a gedit file on the desktop. I stopped it before it did anything, (thank god for compilers and missing semi-colons), but if it had compiled, what would have happened if I had run it? Because in theory it would print characters as fast as it possibly could, filling up my hard disk. Would this happen, and if so how fast?

Kind of reminded me of what happened in my C++ class. All the computers are networked together to allow anyone to login at any computer, so one day during a project someone created an infinite loop by accident and it crashed the entire room. Good times!!! Too bad it didn't happen during the final \\:D/

---

### Post by haqking on 2011-07-25
Turn your firewall on your router or device that connects directly to the internet though it probably is by default.

Dont worry about your dekstop machine so much unless you share files with windows users then you may want to run ClamAV or something similar to prevent virus propogations to those windows dekstops, if you are alone on your network or only have linux machines dont worry and save your resources.

also have a look at confiuguring apparmor and read the security stickys on this forum.

---

