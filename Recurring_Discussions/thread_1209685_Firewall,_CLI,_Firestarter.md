---
title: "Firewall, CLI, Firestarter"
date: 2009-07-10
forum: Recurring Discussions
---

### Post by lotusalive on 2009-07-10
Hi All, Am really loving Jaunty... So far, so good.  Have a question about Firewall though.  Does Jaunty have a 'built-in' firewall ?  

I usually use Firestarter because it has a very nice GUI visual-aid, BUT it seems to be that whenever I have CLI installed, Firestarter _crashes_ almost every other second !  What ways can I beef-up my system to prevent the hits and / or Firestarter crashing _so much_ ?

Whenever I 'Lock' Firestarter, I then cannot get out to anywhere...

I don't really know where to start to become a 'security expert' for my 
PC !  I don't really know how to configure Beagle... (Sorry, I thought Beagle used to be a Firewall Program... It must have been GuardDog I was thinking of.)  All leads to information appreciated. Thanks.

---

### Post by whole.grains on 2009-07-10
The built-in firewall is called IPTables. Firestarter is just a way to configure and monitor it.

---

### Post by ibutho on 2009-07-10
> **lotusalive said:**
> Hi All, Am really loving Jaunty... So far, so good.  Have a question about Firewall though.  Does Jaunty have a 'built-in' firewall ?  

I usually use Firestarter because it has a very nice GUI visual-aid, BUT it seems to be that whenever I have CLI installed, Firestarter _crashes_ almost every other second !  What ways can I beef-up my system to prevent the hits and / or Firestarter crashing _so much_ ?

Whenever I 'Lock' Firestarter, I then cannot get out to anywhere...

I don't really know where to start to become a 'security expert' for my 
PC !  I don't really know how to configure Beagle...  All leads to information appreciated. Thanks.

All Linux distros have a built in firewall called iptables/netfilter. Firestarter is just one GUI amongst many for configuring iptables. In Ubuntu you can use ufw (command line) and gufw (the gui) for configuring your firewall.

---

### Post by lotusalive on 2009-07-10
Well that helps !  Thanks whole.grains and ibutho...  What if I were to try ARPtables or ebtables ?  Can I make a real mess, or can I 'mesh' and 'maze' them ?  lol...  I'm also going to try 'guarddog' but don't really understand the configuration requirements for firewalls...

---

### Post by oldos2er on 2009-07-10
> **lotusalive said:**
>  I don't really know where to start to become a 'security expert' for my 
PC 

 If I were you, I'd start here reading the stickies at the top of the forum: [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by lotusalive on 2009-07-10
Thanks oldos2er, I will read.  The 'Security Discussions' threads are thicker than I can wade through, and seem more for 'admins.' 

I'm gonna try to do bodhi.zazen's thread on 'mod evasive' and 'mod ...' and see if that stops the crashing.

---

### Post by MrWES on 2009-07-10
> **lotusalive said:**
> Hi All, Am really loving Jaunty... So far, so good.  Have a question about Firewall though.  Does Jaunty have a 'built-in' firewall ?  

I usually use Firestarter because it has a very nice GUI visual-aid, BUT it seems to be that whenever I have CLI installed, Firestarter _crashes_ almost every other second !  What ways can I beef-up my system to prevent the hits and / or Firestarter crashing _so much_ ?

Whenever I 'Lock' Firestarter, I then cannot get out to anywhere...

I don't really know where to start to become a 'security expert' for my 
PC !  I don't really know how to configure Beagle... (Sorry, I thought Beagle used to be a Firewall Program... It must have been GuardDog I was thinking of.)  All leads to information appreciated. Thanks.

Install ufw (uncomplicated firewall) and it's GUI, Gufw. You can toggle and configure your firewall easily and quickly.

~Bill

---

### Post by lotusalive on 2009-07-10
Thanks MrWes !  Silly me, I did not understand what ibutho was intending for me !  I'll give it go !

---

### Post by lotusalive on 2009-07-12
Before I got much chance to pursue this strengthening of iptables, ufw, gufw, Firestarter, I had another, my 2nd PC Sys Crash in Jaunty, AGAIN upon a _required_ _restart_ after downloads from Synaptics Pkg Mgr.  

This crash, I have no clue WHY it happened, but root suddenly could not be found by grub, and my log-in screen became several purple and green Ubuntu logos across the top of the screen, and 4 one-inch black & white horizontal lines across the bottom half of the screen. The only 'fails' I noticed in the boot log were 'Firestarter' and 'dnsmasq,' the latter of which it claimed was not even installed, yet I had just chosen it as a preference.  I was able to access root for awhile through the 8.04 'Rescue System' shell, and I even was able to remove 'Firestarter' that way...  I went back to Hardy Heron 8.04 Encrypted x86_64, while attempting to rescue my system, but hard to believe, Firestarter is STILL crashing almost every other second !

Before my crash last night, I was getting ready to try the 6-command instructions for an 'Almost Perfect Firewall,' for Jaunty, from one of the members here.  

All suggestions, as always, greatly appreciated.

---

### Post by sloggerkhan on 2009-07-12
Maybe you've made a mess of conflicting firewall software? 
If so, it might be easier clean install ontop? So far as semi-easy to configure + advanced at once, I think firehol is decent.

othwerwise, it sounds like you might have had a disk failure of some kind, at least if you get a GRUB error.

---

### Post by lotusalive on 2009-07-12
I DID remove ebtables and arptables, both, before the crash, lol, realizing, I'd gone the wrong direction, never touched them, except to install and uninstall on the next look.

I do wonder though if perhaps my root partition was large enough at 10MB, since I do have so much fun just loading and looking at software !  Should I make it 20MB next time?  Is that the more standard size for root ?

---

### Post by 3rdalbum on 2009-07-12
> **lotusalive said:**
> I do wonder though if perhaps my root partition was large enough at 10MB, since I do have so much fun just loading and looking at software !  Should I make it 20MB next time?  Is that the more standard size for root ?

20 GiB of disk space for / is much more appropriate if you're going to be downloading lots of software. 10 GiB is fine, but 20 is almost limitless.

If this is a home computer, you don't need to install the most powerful firewall configurators around. Just install Gufw, tell it to block everything incoming, and forget about it until you need to let ports in.

If you already have a firewall in your ADSL/cable router then you don't even need to configure your IPtables firewall - your whole network will already be protected by the router.

Also, I tend not to recommend Firestarter - it's a little confusing, and the log viewer alarms a lot of people ("Oh my god, hackers are trying to connect to my computer, I can see it happening in Firestarter, what do I do?"). Whenever Firestarter is installed and not turned on, I seem to have problems with incoming ports not being accessible, and those problems don't go away by merely removing Firestarter as all FS does is create IPtables rules.

If you have complex security requirements, then I'm sure Firestarter is good and handy; but for personal use you can't go past Gufw.

---

### Post by lotusalive on 2009-07-12
Thanks all for all the info !  Yes, we did just switch from DSL to Cable HSI, (although I'm not sure if it really is installed that way, and am currently working at using the cd (through wine) to show me that it actually IS installed that way.)  Maybe that is why Firestarter (FS) is just unnecessary for me...  I just liked the _visual security_ of FS, 'knowing' I wasn't being 'hacked,' as that seemed such a great problem in v-word...  

I'll use this install until it limits me too much or has a crash, or offers an auto upgrade (lol) !, and then I'll worry about repartitioning again.  I've always wanted a dual-boot, at least for the past 8 months or so, but have been too busy to really sit-down and read to figure it out...

I always partition my Ubuntu installs with this order, hoping I'll get to it:  40GiB ntfs, 2GiB swap, /, home, freespace

but when I insert the W's install disk, it just won't finish installing itself...  And once this became a Linux HD box, it would never go back to installing W's...  (only reason is I need to upgrade my Graphics Card.) So, one of these days I'm going to have to look at and work on the 'hard-way' (tricky) of installing W's post-Ubuntu, har !  (All just for 'fun' !)  I've learned to store everything on USB's, except my installs, lol, but I'll get there...

Thanks again !

---

### Post by handydan918 on 2009-07-12
In fact, for personal use, if you are behind a router, I wouldn't worry about the firewall at all. I have a network of 8-10 boxen behind nothing but a router. No worries.

---

### Post by lotusalive on 2009-07-12
Thanks for the router info...  I'm just really wondering how I have managed to crash Jaunty installs TWICE in the past month, on restart from Synaptics downloads...

---

### Post by lotusalive on 2009-07-14
I'm back in Jaunty 9.04, missed the nice new features too much !:p

---

