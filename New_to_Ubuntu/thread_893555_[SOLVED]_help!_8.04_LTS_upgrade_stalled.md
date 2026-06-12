---
title: "[SOLVED] help! 8.04 LTS upgrade stalled"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-08-18
Hi
I did a search on this but the other persons post about this issue wasn't resolved so I'm starting a new post

I have attempted an upgrade to 8.04 but it is stalled at the upgrades section at:

Indexing new version of config file /etc beloocs/iso-639.def...
Generating locales...
en _AU.UF8...

It says the rest of the install should take 20 minutes but its been saying that for an hour!

What do I need to do to either:
stop the upgrade and return to my original system
force the update to continue

thnaks in advance

---

### Post by kansasnoob on 2008-08-18
I know this is not what you want to hear, but my success rate with upgrades has been about 50/50. Half the time they work and the other half I end up having to do a clean install!

Wish I had a better answer:(

---

### Post by LTFC2020 on 2008-08-18
sudo killall locale-gen

I tried this that I found after a google search but no change

---

### Post by LTFC2020 on 2008-08-18
much tinkering later.... solved

---

### Post by coco banderos on 2008-08-19
I'm in the same spot.  Can you post what you did to solve this?

---

### Post by LTFC2020 on 2008-08-19
I was premature in thinking this had solved the problem
it continued the install but there were so mant subsequent issues I downloaded the .iso and did a complete install from scratch

---

### Post by LTFC2020 on 2008-08-19
sorry if this is too late for you but...
check out the bottom of my testimonials post
it has the fix to the locales problem

[http://ubuntuforums.org/showthread.php?t=894222](http://ubuntuforums.org/showthread.php?t=894222)

---

### Post by DougieFresh4U on 2008-08-19
Some times I do things the "hacky: way.
If  one of my upgrade goes awry, and I am doing it via terminal, I have shut terminal down then fire it back up and
sudo apt-get -f install
and it will pick up again and continue. 
Please this is not a recommended  way, but it has saved me from a major trauma
Just my little thought

---

