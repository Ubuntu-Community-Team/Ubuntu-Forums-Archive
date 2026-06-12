---
title: "hard disk falure immenent"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by rickwireman on 2012-01-31
as soon as i got ubuntu installed i keep getting the message shell  problem detected with hdd i cliked examine and it says hdd falure is immenent i wiped out all my disk data when i installed it what should i do

---

### Post by Metaxa on 2012-01-31
Sounds like you may want to buy a new Hard drive and install ubuntu on it.




Metaxa

---

### Post by gradinaruvasile on 2012-01-31
> **rickwireman said:**
> as soon as i got ubuntu installed i keep getting the message shell  problem detected with hdd i cliked examine and it says hdd falure is immenent i wiped out all my disk data when i installed it what should i do

This means that your disks SMART system reports errors ( typically Current pending sector count (197)/uncorrectable sector count(198) indicators in SMART data are high). Its not a 100% fullproof method but quite close, and i have seen this error on many failing hard drives that caused frequent bsods in Windows or in my case, systemn freezes on Linux.
(for example either of these indicators is greater than 1, hardware RAID adapters freak out and mark the disk as bad)

Sometimes the errors can be corrected by reformatting the hdd in question a few times - in Linux terms, overwriting the whole device with something (zeros will do).

Open disk utility and read the smart data if you want more precise information.

---

### Post by RedRat on 2012-01-31
Metaxa is right. Hard drives are not terribly expensive, reasonable size disks are now available for well under $100, I have seen some under $50. Be glad that you got a warning, I have had failures without warning and trying to recover files is a pain.

---

### Post by BlinkinCat on 2012-01-31
It was my understanding that due to the recent floods in Thailand, H.D.D's have gone up in price - don't know how long that will last though - :)

---

### Post by RedRat on 2012-01-31
> **BlinkinCat said:**
> It was my understanding that due to the recent floods in Thailand, H.D.D's have gone up in price - don't know how long that will last though - :)

Well he/she is pretty much over a barrel here. The drive is about to fail, who knows exactly when. Depending on the computer and its age, I would opt for a new drive and perhaps have to pay slightly more. Though I have seen those cheaper hard drives within the past month. I don't know where [rickwireman]("http://ubuntuforums.org/member.php?u=1539902") is located but here in the US, I would check out the online retailers, e.g. NewEgg.com.

---

