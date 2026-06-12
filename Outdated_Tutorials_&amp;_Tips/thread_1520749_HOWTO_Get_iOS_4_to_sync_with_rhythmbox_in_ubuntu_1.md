---
title: "HOWTO: Get iOS 4 to sync with rhythmbox in ubuntu 10.04"
date: 2010-06-29
forum: Outdated Tutorials &amp; Tips
---

### Post by tekkidd on 2010-06-29
Well with the release of iOS 4, many Ubuntu users are complaining of incompatibility with between rhythmbox and the new update. Here is a simple way to fix that:

1. Open up synaptic

2. Go to the Repositories  (Under Settings)

3. Add this source: ```
**ppa:pmcenery/ppa**
``` (from [https://launchpad.net/~pmcenery/+archive/ppa](https://launchpad.net/~pmcenery/+archive/ppa))

4. Click Close and then click the Reload button at the top left

5. After it is done reloading search for:  
libimobiledevice1

6. It will give you two results, install both. 

7. Now after installing, close synaptic and open up the terminal and type in ```
sudo apt-get dist-upgrade
```

8. After the upgrade Ubuntu 10.04 will have iOS 4 support!!

---

### Post by TheDoc777 on 2010-07-10
Thanks for the info! The only thing I had problems with was how to make my iPod Touch show up in Rhythmbox, or at least show up as a separate drive. Any ideas?

---

### Post by tekkidd on 2010-07-26
iFuse could not be installed, it should be installed by default but somtimes in blows out 

```
sudo apt-get install ifuse
```

---

### Post by yotama9 on 2010-07-31
Hi. 

I tried this on my machine for my ipod touch but it didn't work. rhythmbox keep asking me to initialize my ipod. 

Any thoughts?

Thanks.

---

### Post by digitalchemystery on 2010-08-01
In order for this to work, you might need to first transfer one track to your iP(od|hone) with iTune. It sucks, but it has worked on the devices I've tried.

---

### Post by yotama9 on 2010-08-02
I'll try. I allready have several podcast episodes I have downloaded directly from my devices so I allow to mysel to be skeptical.

Thanks, I'll post again this evening.

---

### Post by yotama9 on 2010-08-09
Hi. 

I'm sorry, it took me sometime to get the connection cable from my office back home. 

It does work, thank you. 

It is the last time I'll buy apple products. (well, it least for the next few months/years)

Yotam

---

### Post by Joan A. on 2010-08-15
It didn't work in my computer. I have done all it is said in this post and I have installed **ifuse** too. Unfortunately, it didn't work. In addition to this, I have a question: It is nececessary to uninstall **libimobiledevice0** packages?

---

### Post by kushelmex on 2010-08-17
Very useful tnks!

---

### Post by mjpoetic on 2010-08-24
> **Joan A. said:**
> It didn't work in my computer. I have done all it is said in this post and I have installed **ifuse** too. Unfortunately, it didn't work. In addition to this, I have a question: It is nececessary to uninstall **libimobiledevice0** packages?

I don't know if you already figured this one out, but YES is the answer. I had to remove libimobiledevice0 to get my iPhone 3GS working with Rhythmbox again after upgrading to iOS4.

---

### Post by mr_luksom on 2010-09-05
Does anyone know if this is applicable to iOS4.0.2?

I have install libimobiledevice1 1.0.1 (from ppa as per above), I have iFuse (doesn't mount).

In the process of installing libimobiledevice1 I had to remove libimobiledevice0-dev (complained of a common file).

No luck. I can navigate through the phone in nautilus, but that is it. Does not show up in rhythmbox, gtkpod or even amarok.

I've tried the latest libimobiledevice 1.0.2 - compiling from source. Being a n00b, that failed entirely (cannot see 1.0.2 in synaptic)...

Any pointers would be appreciated.

---

### Post by margiwarg on 2010-09-29
Yay it worked! Thanks so much for putting this info out there. I will never make the mistake of updating my ipod software again.

---

