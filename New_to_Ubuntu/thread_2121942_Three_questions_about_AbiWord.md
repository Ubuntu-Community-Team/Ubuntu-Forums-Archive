---
title: "Three questions about AbiWord"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by Vladimir Pavic on 2013-03-03
Dear friends,

1) How to install Croatian spellchecker in AbyWord and how to activate it? I run Ubuntu 10.04.
2) How to upgrade it to the latest version?
3) How to customize the toollbars?

Thank you

---

### Post by Impavidus on 2013-03-03
You need the package **myspell-hr** from the repositories. It will get updated automatically. You can use it by selecting the language in abiword via tools>select language. Maybe you have to activate the spell checker via edit>preferences>spell checker. At least, it is available in 12.04, I don't know about 10.04, but as 10.04 is almost end of life it would be a good idea to move to 12.04 anyway.

I don't know about customizing the toolbars.

---

### Post by Vladimir Pavic on 2013-03-03
It is true that 10.04. is at the end of life. Does it mean that it is going to be unusable (unoperable)? Will I be able to use it for next five years? I am attached to 10.04. I tried 12.04. but I don&#8217;t like it at all.

---

### Post by JKyleOKC on 2013-03-03
You will be able to continue to use it, but will no longer receive any security updates. I'm almost in the same boat, as I prefer 10.04 also, but will probably do the upgrade in another month (after backing up everything on this 10.04 box including eight large VMs).

---

### Post by Toz on 2013-03-03
Dobar dan Vladimir.
Yes, 10.04 will be end-of-life next month. Although the operating system should still work, it won't be receiving any further updates. If you don't like the direction that Ubuntu has gone in with 12.04, there are options. Have a look at [Xubuntu]("http://xubuntu.org/") (Xfce), [Kubuntu]("http://www.kubuntu.org/") (kde) and [Lubuntu]("http://lubuntu.net/") (lxde). They are based on Ubuntu but use different desktop environments.

More information [here]("http://www.ubuntu.com/project/about-ubuntu/derivatives").

---

### Post by Vladimir Pavic on 2013-03-04
Dear jKileOKC and Toz,

Thank you for info help. I prefer to stick to 10.04. till 'the end of my life'. If I wont be able to receive any security updates, does that mean that the system will be vulnerable to hackers' attacks or what ...?

---

### Post by mörgæs on 2013-03-04
Yes.

I would suggest that you try Xubuntu 12.10 with Libre Office before making a decision.

---

### Post by Toz on 2013-03-04
> **Vladimir Pavic said:**
> If I wont be able to receive any security updates, does that mean that the system will be vulnerable to hackers' attacks or what ...?

There are those who would say that any and every system is always vulnerable. However, in your case, if you choose to run 10.04 after its EOL date, off the top of my head you can expect the following:

1. No security updates (e.g. if a potential security hole/flaw is doscovered - think Java - you will not receive any patches).
2. The official repositories are taken off-line, so you are unable to add new software (You can point your sources to the archive location to maintain this functionality. See [here]("http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release")).
3. You will have a more difficult time getting support even from these forums because most people would have already upgraded from 10.04 and/or would first suggest upgrading.
4. ..... (others may have additional points to add)

---

### Post by ajgreeny on 2013-03-04
The other alternative is to use Ubuntu 12.04, but instead of unity, have a long look at the nearest thing to the old gnome-2 that you are going to get, the gnome-classic desktop.

All details of how to get it are at [12.04 LTS Precise Classic]("http://ubuntuforums.org/showthread.php?t=1966370").  There are some minor differences, but it is the best available for 12.04, if you really must have a desktop just like 10.04.

---

### Post by JKyleOKC on 2013-03-04
> **Vladimir Pavic said:**
> Dear jKileOKC and Toz,

Thank you for info help. I prefer to stick to 10.04. till 'the end of my life'. If I wont be able to receive any security updates, does that mean that the system will be vulnerable to hackers' attacks or what ...?It **may** be vulnerable, and the probability of that happening is very high. The initial problem, though, will be the inability to install additional software plus the difficulty of receiving support.

I use Xubuntu rather than the main Ubuntu version, and have since 7.04, so I don't see major differences between 10.04 and 12.04 on the desktop. In my two-machine LAN, one is on Lucid and the other is on Precise, with no significant differences in the look and feel. The main thing holding up my switch from Lucid to Precise on that older machine is a matter of backing up some 300 GiB of virtual disks that are there, and reluctance to attempt a distro upgrade in place rather than doing a clean install, because of the complexity of my configuration there... A clean install would require at least a month of fiddling to restore smooth operation!

---

### Post by Cheesemill on 2013-03-04
Upgrading to a later version will also give you a newer version of Abiword.

You can see which version of Abiword is in the repositories for different versions of Ubuntu by searching the Ubuntu package database...
[http://packages.ubuntu.com/search?keywords=abiword&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=abiword&searchon=names&exact=1&suite=all&section=all)

---

### Post by Vladimir Pavic on 2013-03-04
**Thank you all.** I am finally convinced to switch to Ubuntu 12.04. 
Now, I am facing fiddling a few weeks to get to smooth operation. Ugh ...

Hm. How shall I mark this thread as SOLVED?

---

### Post by ajgreeny on 2013-03-04
> **Cheesemill said:**
> Upgrading to a later version will also give you a newer version of Abiword.

You can see which version of Abiword is in the repositories for different versions of Ubuntu by searching the Ubuntu package database...
[http://packages.ubuntu.com/search?keywords=abiword&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=abiword&searchon=names&exact=1&suite=all&section=all)

However, be warned that the new version, abiword_2.9.2 in the 12.04 and possibly also 12.10 is incredibly unstable and buggy, and not of any use in real life; it will not scroll large files, and crashes a lot.

There is a ppa [https://launchpad.net/~mrpouit/+archive/ppa](https://launchpad.net/~mrpouit/+archive/ppa) for a version which is called abiword_2.9.2+svn20120213really2.8.6-0ubuntu0.1~ppa1_i386.deb.  It is the old version compiled to look like, and take the place of the new version in later versions of ubuntu, and it works well!

---

### Post by Toz on 2013-03-04
> **Vladimir Pavic said:**
> Hm. How shall I mark this thread as SOLVED?
The plug-in that adds the ability to mark threads solved does not yet work with this new version of VB. In the meantime, simply edit your first post and add the words "[Solved]" to the beginning of the title.

---

### Post by ManamiVixen on 2013-03-04
If you like the gnome interface, you can install gnome-session-fallback in 12.04 and it will give you an 10.04 style interface! :)

---

### Post by Vladimir Pavic on 2013-03-05
> **ManamiVixen said:**
> If you like the gnome interface, you can install gnome-session-fallback in 12.04 and it will give you an 10.04 style interface! :)

**Ha! This is for me. Thank you.**

---

### Post by mörgæs on 2013-03-05
> **Vladimir Pavic said:**
> **Thank you all.** I am finally convinced to switch to Ubuntu 12.04. 
Now, I am facing fiddling a few weeks to get to smooth operation. Ugh ...

Hm. How shall I mark this thread as SOLVED?

Done it for you (marked the real SOLVED flag, not just the letters).

---

