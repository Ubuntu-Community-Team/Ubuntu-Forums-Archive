---
title: "I can only burn cd's in windows"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by santiagorf on 2008-07-10
Hi all,

I have SATA DVD writer that fails burning with Brasero and GnomeBaker in Xubuntu. However, in windows xp with CDBurnerXP works well, but it fails burning with Nero.
Is it a compatibility problem with ubuntu, if not, what other software can I try?

thank you!!
Santiagorf

ps: The GnomeBaker's log is attached.
ps: The DVD driver is LG GH20LS10.

---

### Post by timcredible on 2008-07-10
k3b is the best cd burning tool for linux.  it's in the repos.

---

### Post by kestrel1 on 2008-07-10
I would try K3B as sugested above.
To install from a terminal:
```
sudo apt-get install k3b
```
May not show up in menu's.
Just create a launcher, using k3b as the command.

---

### Post by avtolle on 2008-07-10
Since the problem involves, as I understand it, the SATA DVD drive, installing k3b (an excellent program, by the way) may not solve the problem. He should give it a try and see, but be aware it may not solve the problem.

---

### Post by sydbat on 2008-07-10
And the OP mentioned Nero in Windows would not burn a CD/DVD either. Might be a problem with recognizing the drive?

---

### Post by rickycodie on 2008-07-10
i agree with sydbat, it would seem that this is the case

---

### Post by santiagorf on 2008-07-10
I'have tried burning with k3b, but I still have the same problem...

---

### Post by avtolle on 2008-07-10
I suspected that would happen. It appears that your DVD burner is not being recognized by the system (both from the Brasero log you posted as well as from your experience with Nero). That's where my ability to provide further assistance ends, regrettably.

---

### Post by suri.mahendra on 2008-07-10
Hi,
 I'm looking for a SATA DVD burner and I was looking at LG but before I made the purchase I kicked LG an email about LINUX support.  They laughed at me.

One problem maybe that the drive may not work with LINUX.
You may not have mp3 support enabled.  If this is the case, with K3B under Xubuntu you should get some sort of flag about only supporting MPEG I and II formats.
Or the drive may just be a piece of crap.

I just switched to Hardy.  With Fedora to ensure you have mp3 support you had to download the K3B nonfree package.

Try burning with and IDE drive and see what happens

---

