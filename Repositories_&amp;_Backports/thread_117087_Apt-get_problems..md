---
title: "Apt-get problems."
date: 2006-01-14
forum: Repositories &amp; Backports
---

### Post by clueless on 2006-01-14
Hello everyone,

I have ubuntu installed a couple of months now and I have installed a lot of programs with apt-get, including xfce4, kde etc., anyway I have a lot of packages installed. Some week ago I installed some more packages, guitar tablature programs, one of which, but I don't know which, had lilypond something as a dependency. And that's where problems began. Lilypond was not installed and everytime I tried to install a new package apt-get gave me an error message at the end concerning lilypond. I removed all packages with the guitar tablatures but the lilypond-something package wasn't removed. I tried removing it with apt but nothing, a dependency named lilypond-data remains and cannot be removed because I get the following message (from synaptic) whether I try remove or complete remove: "dpkg: error processing lilypond-data (--remove): Package is in a very inconsistent state - you should reinstall it before attempting removal."

Then synaptic closes and when I rerun it it gives me the message: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." and the I can do nothing since I don't get a list of programs, it is completely blank. After a reboot synaptic will run again but with same results. And I cannot install any more software because it exits with this error nor can I remove any (I want to remove thunderbird but it can't be done). Running dpkg --configure -a does nothing to resolve the problem. Reinstalling the program lilypond or tablature programs doesn't work either. Is there a way solving this without having to reinstall ubuntu?

---

### Post by clueless on 2006-01-14
Hmm it appears I found the solution...

I reinstalled lilypond using synaptic, plus lilypond-data and its gui, I think it's called gtk-lillypond or something like that. The installation finished with no errors reported, so I think that it's ok.

I hope this will help somebody.

---

### Post by Rhadamanthos on 2007-03-25
I had the same problem, I run some fairly unstable software and during a system update, my system hardlocked. So, when I rebooted it, nautilus-data was in "a very inconsistent state" (unsurprisingly)

Thanks for telling me about using synaptic to resolve this, dpkg probably can but I couldn't figure out how.

Anyhow, the exact steps I followed to fix this problem were:

sudo synaptic
A warning pops up telling me 1 package on my system is broken and to use the "broken" filter to locate it
Select "custom filters"
Select "broken"
Select "nautilus"
Mark "nautilus" for reinstallation
Apply

Since the package downloads had already completed, it used the existing upgrades to Nautilus to fix the errors.

---

### Post by baidaraka on 2007-04-05
Hi,
I am very much new user to linux as well as ubuntu, I am facing the problems mentioned as under

> 
root@sarthor:~# apt-get -y install macchanger
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  ymessenger: Depends: libgdk-pixbuf2 (>= 0.13.0) but it is not going to be installed
              Depends: libgtk1.2 (>= 1.2.0) but it is not going to be installed
              Depends: libssl0.9.6 but it is not installable
              Depends: xlibs (> 3.3.6) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Any help will be appreciated.
Thank You.

---

