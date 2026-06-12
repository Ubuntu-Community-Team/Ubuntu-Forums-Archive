---
title: "Vista burned DVD-rom shows up as Blank Disc."
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Shaded Spriter on 2008-05-24
I have tryed it on both my tower and laptop and for some reason ubuntu won't read any of the Data on the discs.

it doesn't detect anything on my tower - but shows up as a blank disc on my laptop (which can burn DVDs.)

---

### Post by sayakb on 2008-05-24
Which application did you use to burn the disks? Did you use the default vista disk burning utility? If yes, then use an alternate application since the CDs/DVDs created by the default Vista CD/DVD creator is not always compatible with all OSs

---

### Post by HotShotDJ on 2008-05-24
> **Shaded Spriter said:**
> it doesn't detect anything on my tower - but shows up as a blank disc on my laptop (which can burn DVDs.)I'm taking a guess here... but I suspect that Vista burned those DVD's using UDF rather than standard ISO 9660.  You can work with UDF disks using udftools (install via synaptic), the last I knew, it was a command-line only tool set.  You may want to go back into Vista and reburn the files to DVD using a standard file system.

---

### Post by Shaded Spriter on 2008-05-24
It was burned with the Vista default utility unfortunately.

---

### Post by HotShotDJ on 2008-05-24
> **Shaded Spriter said:**
> It was burned with the Vista default utility unfortunately.In that case, you COULD install the udftools and mess around with it that way. However, if you have access to a Windows machine, you might be better served by using Windows to get the data and then reburn it using a standard file-system (don't you just LOVE how Microsoft refuses to comply with well established standards while talking about interoperability out of the other side of their lying mouths?)

---

### Post by Shaded Spriter on 2008-05-24
I will re-burn them...thank you for your help.

---

### Post by mc4man on 2008-05-24
When you reburn , vista defaults to udf 2.50 or 2.60 ( I Forget) It isn't obviously stated but look for burn options. Udf 1.02 will be fine on ubuntu

---

### Post by HotShotDJ on 2008-05-24
> **mc4man said:**
> Udf 1.02 will be fine on ubuntuAre you sure about this?  I'm not disagreeing with you... I have just operated all these years under the assumption that UDF should be avoided at all costs and have stuck with ISO 9660 for data cd/dvd's.

---

### Post by mc4man on 2008-05-24
I think your right about cd's, let me do a ck. ck .on data dvd, any way for vista the list of available modes is in help and support -  which cd or dvd format to use
For cd's you have to choose (in vista ) the mastered format for compatibilty

edit  finalized cds are iso9960 (cdrom mode1) data dvds are iso 9960,udf (1.02 for compatibility)
All of those fall under the mastered format in vista

---

### Post by stalkier on 2008-05-24
I also suggest not using a multisession option. A lot of times you have to click the box to make it NOT a multisession.

---

