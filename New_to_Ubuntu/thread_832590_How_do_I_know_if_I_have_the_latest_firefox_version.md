---
title: "How do I know if I have the latest firefox version?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by swimm3r137@gmail.com on 2008-06-17
Hi,

I have ubuntu 8.04 and obviously it came with firefox 3 beta 5 on it.  But, since the official new upgrade to firefox 3 is available today, I was wondering how I would figure out if ubuntu automatically updated it without me knowing to the latest version or not?  Cuz I wan't the version that came out today!  how do I do that =)

---

### Post by coolbrook on 2008-06-17
Nothing in Ubuntu will update without your permission.

---

### Post by neurostu on 2008-06-17
Firefox 3 will be packaged into a deb file soon and uploaded to the Ubuntu repositories. The upgrade will happen seamlessly and easily.  It might take a few days.

If you want to try to install the latest version yourself you can, but trust me when I say it will be more trouble then its worth seeing as how Ubuntu will automatically install it for you in a day or two.

---

### Post by kansasnoob on 2008-06-17
IMO, just open System > Administration > Software Sources and click on the Updates tab. If only Important Security Updates & Recommended Updates are checked then you still have RC2 (which came about one week later for those with the aforementioned default updates checked).

If you have Pre-Released Updates selected you may have it, but I've found for nOObs like me it's better to wait for the "Recommended Updates". There is generally a delay of only a few days (weeks at the worst) and then all the bugs have been worked out.

If you choose to receive Pre-Released and Unsupported Updates don't be surprised if something breaks.

---

### Post by neurostu on 2008-06-17
To figure out what version your running click Help-->About Mozilla Firefox

---

### Post by swimm3r137@gmail.com on 2008-06-17
> **neurostu said:**
> To figure out what version your running click Help-->About Mozilla Firefox


Is this the version that was released today?

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9) Gecko/2008061017 Firefox/3.0

---

### Post by kansasnoob on 2008-06-17
> **neurostu said:**
> Firefox 3 will be packaged into a deb file soon and uploaded to the Ubuntu repositories. The upgrade will happen seamlessly and easily.  It might take a few days.

If you want to try to install the latest version yourself you can, but trust me when I say it will be more trouble then its worth seeing as how Ubuntu will automatically install it for you in a day or two.

Absolutely right. I tried updating my Win XP FF twice today and the servers were over capacity. Just be patient!

---

### Post by neurostu on 2008-06-17
> **kansasnoob said:**
> Absolutely right. I tried updating my Win XP FF twice today and the servers were over capacity. Just be patient!

Its because of their "Download day" thingy... the servers are getting slammed today.

---

### Post by Happy_Man on 2008-06-17
Uh, I'm pretty sure the devs pushed out FF3 final today. Try upgrading and see.

---

### Post by Jshaw on 2008-06-17
Speaking of Download Day, I just managed to get onto the site, I got 3.0 running on XP and Ubuntu. Just go sudo apt-get update and you should see it.

---

### Post by Metaleks on 2008-06-17
> **swimm3r137@gmail.com said:**
> Hi,

I have ubuntu 8.04 and obviously it came with firefox 3 beta 5 on it.  But, since the official new upgrade to firefox 3 is available today, I was wondering how I would figure out if ubuntu automatically updated it without me knowing to the latest version or not?  Cuz I wan't the version that came out today!  how do I do that =)
That version is in the repositories right now.  To check your firefox version go into your terminal and enter:
```
firefox --version
```
Hope that helps.

---

