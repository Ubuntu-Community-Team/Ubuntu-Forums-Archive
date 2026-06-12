---
title: "Evolution 3.10.4 --- want to upgrade,  HOW ???"
date: 2015-10-25
forum: New to Ubuntu
---

### Post by cwmoser on 2015-10-25
I have Ubuntu 14.04, have updated and upgraded but cannot get Evolution Mail to upgrade from 3.10.4

I have searched and added the PPA:  sudo add-apt-repository ppa:fta/gnome3
My desktop is MATE - not gnome3

Is the reason I cannot upgrade Evolution because I am using the older gnome MATE instead of gnome3 ???

---

### Post by Vladlenin5000 on 2015-10-25
The PPA you say you have has 3.16. Adding that PPA followed by *sudo apt-get update* and *sudo apt-get upgrade* should be enough to update your Evolution version.

(EDIT)

On a second check I discovered that PPA has versions for 14.10 and 15.04 only. According to [this]("http://pkgs.org/download/evolution") 3.10.4  is the newest you can get for 14.04 or anything else based on 14.04.

---

### Post by cwmoser on 2015-10-28
^
!_____ so much for LTS  :D

I would have thought that LTS would mean LTS - instead of having to go with interim versions to get the
latest version of critical software.

---

### Post by buzzingrobot on 2015-10-28
An LTS, in Ubuntu or elsewhere, is reliable over the long run primarily because it avoids change.  Bug fixes happen. Feature upgrades don't.

Evolution's release sequence follows Gnome's and Gtk3's. Moving to a newer release version built on a newer Gtk invariably means pulling in all those new Gtk dependencies, which would break every other Gtk-based package in the LTS that was built against an earlier Gtk, i.e., all of them.

It would be nice if Evolution devs would backport some of their fixes, but, as far as I know, they seldom do.

---

### Post by Geoffrey_Arndt on 2015-10-28
+1 . . . I can tell buzzingrobot has IT (or related) experience.   

Version changes introduce MANY headaches to companies and orgs with hundreds or thousands of users.   Our company has well  over 50,000 workstations, and they finally upgraded Office 97 in 2007 (yes, 10 years).   

In fact, these companies typically have an organization called the "ITL" . . . Integration Test Lab (with a staff of 2 to 20 or more) just to test upgrade or changed software  (and new apps also).

EDIT:   there are a few exceptions to the above, but most software upgrades DO NOT introduce critical new features despite the marketing & hype.

---

