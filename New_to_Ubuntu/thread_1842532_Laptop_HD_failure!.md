---
title: "Laptop HD failure!"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by jeremy101 on 2011-09-11
Help! Whenever I boot up my Samsung R480 laptop, the BIOS throws up this message at me after the splash screen and before it boots:

```

SMART Failure Predicted on Hard Disk 0: WDC WD5000BEVT-352AT0-(S1)

WARNING: Immediately back-up your data and replace your hard disk drive. A failure may be imminent.

Press F1 to Continue
```
:shock: What do I do? I don't have any money for a new HDD and I would like to see if Redo Backup and Recovery or something like Puppy Linux can fix the problem. Thank you! If this is the wrong way to go, what distribution can fix this problem? Do I have to specially format it? :sad:

---

### Post by Joebewan on 2011-09-11
No warranty ???

I'd follow the advice and back up YESTERDAY.  Then run the diagnostics from the laptop manufacturer and contact support with the results.

If laptop manufacturer's warranty is out, run drive manufacturer's diagnostics and contact their support.

Yes, there are other diags you can run, but ultimately if you have any warranty, the manufacturer will want their diags run before honoring it.

If you are completely out of warranty altogether, save your pennies because you're going to need a new drive probably sooner than later.

No way would I trust a resurrected drive with my data.

---

### Post by audiomick on 2011-09-11
The SMART data is the drive's own monitoring. It is below anything else.

[http://en.wikipedia.org/wiki/S.M.A.R.T.](http://en.wikipedia.org/wiki/S.M.A.R.T.)

If your machine is reporting that the SMART data says the drive is heading for a fail, the only sensible thing to do is believe it. If you can't afford a new drive, buy a bucket load of CD-R discs and back up anything that is on the drive that is really important. Do this now.

A different OS, or a re-install or whatever, will not help. This is a mechanical issue, not a software issue.

---

### Post by jeremy101 on 2011-09-11
> Predictable failures: These failures result from slow processes such as mechanical wear and gradual degradation of storage surfaces. Monitoring can determine when such failures are becoming more likely.

Mechanical failures account for about 60% of all drive failures. While the eventual failure may be catastrophic, most mechanical failures result from gradual wear and there are usually certain indications that failure is imminent. These may include increased heat output, increased noise level, problems with reading and writing of data, an increase in the number of damaged disk sectors.
This HD has a lot of bad sectors on it! BTW, I did backup all my data on this drive as soon as I saw this!

---

### Post by audiomick on 2011-09-12
> **jeremy101 said:**
> ... I did backup all my data on this drive as soon as I saw this!

Well done. I hope you can afford to replace the drive soon. Good luck!

---

### Post by jeremy101 on 2011-09-12
Is there a way to get rid of the bad sectors?

---

### Post by philinux on 2011-09-12
> **jeremy101 said:**
> Is there a way to get rid of the bad sectors?

The HD itself has already remapped the bad sectors. There is probably now no more spare sectors available. You need to replace the drive. Even a second hand drive would do.

From the SMART page.
> Count of reallocated sectors. When the hard drive finds a read/write/verification error, it marks that sector as "reallocated" and transfers data to a special reserved area (spare area). This process is also known as remapping, and reallocated sectors are called "remaps". The raw value normally represents a count of the bad sectors that have been found and remapped. Thus, the higher the attribute value, the more sectors the drive has had to reallocate. This allows a drive with bad sectors to continue operation, however, a drive which has had any reallocations at all is significantly more likely to fail in the near future.[2] While primarily used as a metric of the life-expectancy of the drive, this number also affects performance. As the count of reallocated sectors increases, the read/write speed tends to become worse because the drive head is forced to seek to the reserved area whenever a remap is accessed. A workaround which will preserve drive speed at the expense of capacity is to create a disk partition over the region which contains remaps and instruct the operating system to not use that partition.

---

### Post by Mark Phelps on 2011-09-12
> **jeremy101 said:**
> Is there a way to get rid of the bad sectors?

Not really ...

There are disk utilities you can run (ALL that I know require MS Windows) that will attempt to copy the info from the bad sectors into good sectors, and then mark the bad sectors as unusable.

One of the best that USED to be around was known as Spinrite.  But, I haven't seen that around in years.

But, this doesn't really fix them.  At best, it only buys you some time needed to back off the drive.

And sometimes, even that does not work.  I had a WDC drive fail this weekend. I downloaded the WDC drive utility, ran it, and even IT was unable to handle the bad sectors.  So, in some cases, even the manufacturer's own software will not save you.

---

### Post by lkraemer on 2011-09-12
As previously suggested I'd run the drive manufacturer's diagnostics to
see what it tells you.  Then if you want, you can run Spinrite to see
if it can repair the drive.  Spinrite 6 is supposed to be on the Hiren's
Boot CD.  Other than that you can always try using dd to determine more about
the drive.

[http://www2.uic.edu/~aciani1/sector_blues.html](http://www2.uic.edu/~aciani1/sector_blues.html)

[http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html)

[http://zerinsakech.wordpress.com/2011/04/20/how-to-repair-bad-sectors-on-hard-drive/](http://zerinsakech.wordpress.com/2011/04/20/how-to-repair-bad-sectors-on-hard-drive/)

[http://www.linuxjournal.com/article/193](http://www.linuxjournal.com/article/193)

Also there is hdd regenerator.

[http://www.gold-software.com/download7605.html](http://www.gold-software.com/download7605.html)

There is this program, which is a freeware replacement software for hdd regenerator:

[http://www.hdat2.com/](http://www.hdat2.com/)


lk

---

### Post by mycroft on 2011-09-15
You might also be able to salvage something using 'ddrescue', as described here: [https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

---

### Post by egalvan on 2011-09-20
> **Mark Phelps said:**
> 

One of the best that USED to be around was known as Spinrite.  But, I haven't seen that around in years.


Steve Gibson is still around, still selling his SpinRite.

[http://www.grc.com/](http://www.grc.com/)

note that it was last up-dated July 2004, so it's a bit long in the tooth.

---

### Post by jeremy101 on 2011-09-20
I did find a program called HDD Regenerator, which is supposed to repair bad sectors on your HDD.

---

