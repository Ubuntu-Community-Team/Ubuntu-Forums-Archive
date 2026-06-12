---
title: "Bad sectors"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by disabled20191128 on 2012-06-09
I have noticed that i have some bad sectors on my hdd is there any way repairing them or disabling them ?

---

### Post by codemaniac on 2012-06-09
How you have checked your hdd has bad sectors , i mean what tool you have used ?

You can always cross check with other utilities in order to be confirmed that these are not false alarms .

[http://ubuntu-rescue-remix.org/node/50](http://ubuntu-rescue-remix.org/node/50)

You can also monitor your /var/log/messages for any read/write error when doing any disk operations .

---

### Post by disabled20191128 on 2012-06-09
I checked the hdd with S.M.A.R.T in disk utility

---

### Post by Jimmyfj on 2012-06-09
In my experience S.M.A.R.T. isn't all that reliable, you'll need more advanced tools than just S.M.A.R.T.

Here I'll guide you to some knowledge about disk drives in Linux:

[http://www.linuxjournal.com/article/193](http://www.linuxjournal.com/article/193)

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://alicious.com/linux-hard-drive-recovery-repair/](http://alicious.com/linux-hard-drive-recovery-repair/)

Last link is a site where you can find even more info and programs.

Lastly the google site I searched and the search-string used.

[https://www.google.com/search?q=linux+disk+utilities&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs](https://www.google.com/search?q=linux+disk+utilities&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs).

/Jimmy

---

### Post by Paqman on 2012-06-09
> **Dennisgre said:**
> is there any way repairing them or disabling them ?

There's no way to repair them. The drive has detected them and marked them as bad. When it does that it automatically takes them out of use, and replaces them from the pool of spares. You don't need to do anything.

Don't worry too much about it. It's normal for a drive to accrue bad sectors in use. As long as the number stays low (say <5) and isn't increasing then you've got nothing to worry about. Most disks I've owned have ended up with a couple of bad sectors after a while.

However, now would be a good time to review your backup plan. Make sure you have a system that will save your data if (when!) a hard drive dies. They aren't particularly reliable.

---

### Post by philinux on 2012-06-09
> **Paqman said:**
> There's no way to repair them. The drive has detected them and marked them as bad. When it does that it automatically takes them out of use, and replaces them from the pool of spares. You don't need to do anything.

Don't worry too much about it. It's normal for a drive to accrue bad sectors in use. As long as the number stays low (say <5) and isn't increasing then you've got nothing to worry about. Most disks I've owned have ended up with a couple of bad sectors after a while.

However, now would be a good time to review your backup plan. Make sure you have a system that will save your data if (when!) a hard drive dies. They aren't particularly reliable.

We had a laptop with 200+ bad sectors. No read write errors until they started growing exponentially lol. The disk did then fail completely.

---

### Post by MichaelGld on 2012-06-09
> **Dennisgre said:**
> I have noticed that i have some bad sectors on my hdd is there any way repairing them or disabling them ?

Try Spinrite. [http://www.grc.com/sr/spinrite.htm]("http://www.grc.com/sr/spinrite.htm")

---

### Post by Paqman on 2012-06-09
> **philinux said:**
> We had a laptop with 200+ bad sectors. No read write errors until they started growing exponentially lol. The disk did then fail completely.

We've had a few people post threads up here with similar stories ("My disk has 14,356 bad sectors. Should I be worried?").

There have been some interesting papers come out of Google giving the average time to failure after detection of the first bad sector. I'm not sure whether they were positively asserting there was a causal link, or if the appearance of bad sectors was just being treated as a proxy for disk age.

---

### Post by Mark Phelps on 2012-06-09
> **MichaelGld said:**
> Try Spinrite. [http://www.grc.com/sr/spinrite.htm]("http://www.grc.com/sr/spinrite.htm")

Despite what Spinrite claims, it can NOT repair bad sectors.  Failing sectors is a Hardware problem; Spinrite is Software.

There is no way to repair bad sectors on a drive.

---

### Post by sammiev on 2012-06-09
I have been like this forever but Win7 tells me my HD is 100%. So take it for what it worth. :)

---

### Post by disabled20191128 on 2012-06-10
Thank you for your replies! I guess I will have to backup my hdd :)

---

