---
title: "laptop battery charging issue"
date: 2013-03-21
forum: New to Ubuntu
---

### Post by jwftm33 on 2013-03-21
I recently install 12.04 using ac adapter for power. I ordered a new battery for my inspioron 6000 off of ebay, when I put the battery in it shows up and says it is charging but the percentage on the battery never has gone up. It actually is slowly going down. My question is is there away to check my laptop to see if there is a problem with my charging system or if i just got a bad battery and need to return it. any help would be appreciated.

---

### Post by DuckHook on 2013-03-21
Such problems are notoriously hard to diagnose. Why did you replace your battery? Was the old one also unable to charge? If so, then my suspicion is that you have a borked charging system in your laptop. I've experienced two such problems before with older Dell laptops. Most people do not have voltmeters at home, so cannot test if any current is going to the battery. You may need to take your laptop into a computer repair shop with adequate testing equipment to be sure. Since charging is a hardwired bare metal process, it would have nothing to do with your OS.

---

### Post by jwftm33 on 2013-03-21
Old battery would not charge, thought it was bad. Is there anyway to run a diagnostic test to see if it is a hardware issue. Older laptop not sure worth taking to shop would charge more than it is worth. works on the ac adapter though.

---

### Post by DuckHook on 2013-03-21
These are exactly the same symptoms I had. Ended up wasting money on a new battery when real problem was borked charging system. I found out by trying the battery on a different machine which charged without problem. Ergo, process of elimination leaves charging system as culprit.  Ubuntu can tell you what the state of your battery is but as far as I know, there is no diagnostic that tells you about the charging system. [This]("http://sourceforge.net/projects/ldiag/") is a brand new project purportedly for system diagnostics, but there is so little info that I have no idea what it does or does not do. You may be able to pinpoint the problem following [this]("http://www.brand-new-battery.com/blog/articles/laptop-battery-does-not-charge.htm") guide found through Google.

---

