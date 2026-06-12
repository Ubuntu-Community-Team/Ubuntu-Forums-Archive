---
title: "How safe is running XP within Ubuntu"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by wariskampar on 2008-07-04
I've been using XP through VirtualBox for a few days now. I use it mainly to sync my music to IPOD and searching Album Art (from Amazon using IE). My XP is updated and I've installed AVAST to reinforce the security. Is there possibility I might get infected and damage my UBUNTU file sys, files etc. XP image is located in /home which is on dedicated partition. How to prevent Ubuntu from being infected?

---

### Post by fatality_uk on 2008-07-04
Anything is possible, but in this case you have nothing to worry about. A Windows virus can not crawl across a virtual machine into your host operating system

---

### Post by sayakb on 2008-07-04
All of the Virtual machine's data is in the virtual HDD (For Virtualbox, its a VDI file). In case you get infected in XP and you have read+write access to some of your Ubuntu files, the Ubuntu files might get infected. But that will not actually harm your computer since neither do Win32 executables, nor Windows autorun scripts execute on Ubuntu, unless asked to do so. Worst case, you might have some damaged executables in the Wine's drive_c or the Windows folder in it if you run an infected executable with Wine..

---

### Post by clive littlewood on 2008-07-04
Hi

Try Amarok to sync your ipod (both ways unlike itunes) + a great player

Also has Album art feature.

Clive

---

### Post by t0p on 2008-07-04
> **wariskampar said:**
> Is there possibility I might get infected and damage my UBUNTU file sys, files etc. XP image is located in /home which is on dedicated partition. How to prevent Ubuntu from being infected?

To begin with: there are very few viruses in the wild that target Linux; and even fewer affecting both XP and Linux.  I'm tempted to say there are none, but only a fool says never.  All the same, the chances of coming across a virus that will infect your virtual XP partition in order to cross the divide and infect your Ubuntu installation are miniscule.

In addition, the fact that your XP installation is running in a virtual box makes your hypothetical infection even less likely.  I'm no expert, but people who know a lot more than me on the subject say the infection is "impossible".  You should draw comfort from that.  And seriously: it's not worth getting stressed over.  You took a massive step in securing your system when you installed Ubuntu.

---

### Post by AlanR8 on 2008-07-04
Having just installed XP in Virtualbox myself, I was wondering should I install anti spy ware and virus software on the XP virtual machine?

---

### Post by Canis familiaris on 2008-07-04
> **AlanR8 said:**
> Having just installed XP in Virtualbox myself, I was wondering should I install anti spy ware and virus software on the XP virtual machine?

Install the anti-spyware and run the Windows VM in a limited account. This will do.

---

### Post by billgoldberg on 2008-07-04
If the malware somehow gets out of the virtual harddrive, it won't do anything since windows viruses can't do any damage on a ubuntu install.

---

### Post by ChameleonDave on 2008-07-04
The question of Ubuntu becoming infected is a red herring.  The real problem is that if you give your virtual machine write access to a part of your hard drive, files could be deleted or corrupted by any malware on your Windows installation.

For that reason, I don't leave my virtual machine running unnecessarily (you can freeze it at any time if you don't want to shut it down), and I take the normal Windows security precautions (firewall, anti-virus, anti-spyware, and care with what I install).

However, it is best not to get paranoid.  Do what you need to do, without fear.  Don't be like my mother-in-law, scared to connect to the internet.

---

### Post by newbuntuxx on 2008-07-04
A virus in a guest XP machine on a host ubuntu machine will do nothing to your ubuntu installation. 

However, if you have a shared folder and you gave XP permission to read AND WRITE to/from that folder, then, the contents of that folder MAY (a big MAY here) be damaged

I think someone should actually try out such sceniores and let us know what the results are.

That is:

1. Run windows virues through wine, and see what happens to the wine installation, to the ubuntu installation?
2. Give wine Root access and repeat the above
3. Run windows virues in XP guest on ubuntu host using virtual box. Note what happens to the virtual box installation and to ubuntu installation?
4. Give virtual box root access and repeat the above.


i'll be getting another decent pc, and with the help of a kvm switch, i think i will be carrying out the above tests. However, I do need some kind of software that will take a snapshot of my ubuntu installation before i run the test, and after, and then compare the snapshots to see if they are different. That is, if any files are deleted, or corrupt etc....Is there such a software?

---

### Post by imbjr on 2008-07-04
> **t0p said:**
> To begin with: there are very few viruses in the wild that target Linux; and even fewer affecting both XP and Linux.

The threat of cross-platform infection is increasing, so no matter what OS you run, there is always a risk of compromise.

---

