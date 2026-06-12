---
title: "Mounted ubuntu parititon from a linux mint live CD; now read-only"
date: 2011-01-01
forum: Programming Talk
---

### Post by vik_2010 on 2011-01-01
Hey, I posted this on another section of this forum, but I'm also posting here because I respect the abilities of the people here:

I've been running ubuntu for a while, but I decided today I'd check out linux mint.

I created a live cd, and ran it. During my test, I discovered I could mount my linux partition and access my files there.

I thought this was neat, so I opened up a couple files. I didn't make  any changes; i just opened them. I also opened GParted, but I don't  think that makes any difference.

However, when I ended my session and rebooted Ubuntu, the partiition had suddenly become read-only, and I couldn't load it. 

I then rebooted my linux mint live cd. I could no longer open that  partition, and sudo stat said the size of the partition (I think i  checked the partition in /dev/sda3, where ubuntu is located) was 0.

That can't be right, though, because GParted states that sda3 has some 22 gibi of data on it.

Can anyone help me out?

Best,

-Vikram

---

### Post by Elfy on 2011-01-01
Please do not post duplicates.

---

