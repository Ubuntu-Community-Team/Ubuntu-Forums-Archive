---
title: "upgrading ubuntu server 10.0.4 to 14.0.4"
date: 2016-10-04
forum: New to Ubuntu
---

### Post by bakshi23 on 2016-10-04
I have a server running ubuntu server 10.0.4, I want to upgrade it to the ubuntu 14.0.4 but I am not able to fetch the repos.


Please help me out

---

### Post by ian-weisser on 2016-10-04
10.04 repositories were retired in 2015, so it is not surprising that your system cannot fetch updates from them.

Must it be an upgrade? 
The only tested, supported path requires upgrading to 12.04, then to 14.04. If you are wise and test after each upgrade, that's most of an entire day. 

Alternately, a new install of 14.04 (or, better, 16.04) seems likely to be much faster and simpler.

---

### Post by TheFu on 2016-10-04
Welcome to the forums.

a) Support for 10.04 ended 1.5 yrs ago, dude. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) - look over the entire page so you don't get caught off guard next time. Not all x.x.1 point versions are supported the entire 5 yrs. The specific kernel line matters on LTS releases.

b) The upgrade path would have been 10.04 --> 12.04 --> 14.04 --> 16.04  (LTS to LTS to LTS), though recently they've tried to remove the LTS-to-LTS upgrade mandate.

c) 16.04 is the current, newest, LTS. You really should deploy that to get the longest support.  If possible. It isn't always possible.

d) being unpatched for 1.5 yrs is scary.

e) Things change a little with each release. As the years go on, people here forget each of the major hassles from release to release so it is best to migrate when everyone else is migrating too - perhaps 2-4 months after. That way, issues and the solutions are fresh in our minds.  The main thing I recall with 12.04 was that resolv.conf management was moved into the interfaces file - any changes made directly were lost. That is still true today with 16.04.  With 14.04, there was a huge apache upgrade. Lots of things changed.

f) have you considered doing a fresh install and moving over the settings for each of the services? That many upgrades can get a little *crufty*.  Also, running each inside a different VM would aid with security (with 12.xx, VMs became really good), but adds complexity if you don't do this all the time.

I'm working on my 12.04 --> 14.04 --> 16.04 migration for the last 12.xx server here this fall. Support ends next spring, so I want/need to move in the next few months. That 12.04 box here is crufty - will need a fresh reload from scratch and migration of about 20 services. Not fun, but the canonical team couldn't possibly handle all the specialized settings that machine has.

Sorry I don't have the answer you seek.  Others have asked similar questions here. I don't recall the answers, but thought it had to do with burning a CD with the next LTS version and installing that in some special way. Search these forums and good luck.

---

