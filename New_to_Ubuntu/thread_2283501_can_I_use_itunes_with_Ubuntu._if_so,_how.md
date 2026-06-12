---
title: "can I use itunes with Ubuntu. if so, how?"
date: 2015-06-22
forum: New to Ubuntu
---

### Post by Ron_Williams on 2015-06-22
I'm using a new system 76 with ubuntu only. would like to use itunes.

---

### Post by sandyd on 2015-06-22
Itunes 12 doesn't seem to [work very well in WINE]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=32014")

As a result, I would reccomend running ITunes in a Virtual Machine, probably through virtualbox or similar.

---

### Post by slickymaster on 2015-06-22
Hi Ron_Williams, welcome to the forums.

iTunes is compatible only with Mac OS and Windows operating systems. Besides virtualization, the only way you have to use iTunes in a Ubuntu system would be using using PlayOnLinux```
sudo apt-get install playonlinux
```Once installed just open PlayOnLinux and search for iTunes in its searchbar.

---

### Post by wildmanne39 on 2015-06-22
> **sandyd said:**
> Itunes 12 doesn't seem to [work very well in WINE]("https://appdb.winehq.org/objectManager.php?sClass=version&iId=32014")

As a result, I would reccomend running ITunes in a Virtual Machine, probably through virtualbox or similar.+1 this is your best option in my opinion.

---

### Post by Quarkrad on 2015-06-22
I've been looking at this since ubuntu 8.04 and played/tested various solutions.  The best I have found is running itunes/windows in Virtualbox - having said that, I have gone back to dual booting with windows (7) purely to have itunes in it's native environment. I have looked at various open source alternatives too but some have come and gone - at the end of the day itunes is going to be around as long as Apple is around so for all it's failings, itunes is very good at what is does and your music environment will remain consistent.  For me, I have gone Windows - Ubuntu - Windows.  (itunes is the only reason I dual boot - I'm 99.9% ubuntu).

---

### Post by Ty_Scheun on 2015-06-23
There are currently 4 ways to get iTunes:

1. Installing PlayOnLinux via [Ubuntu Software Center]("https://apps.ubuntu.com/cat/applications/playonlinux/") by going to terminal and typing in: ```
sudo apt-get install playonlinux
```

2. Installing Wine via the [Ubuntu Software Center]("https://apps.ubuntu.com/cat/applications/wine1.4-i386/") or by adding the PPA repo:
```
[FONT=courier new][COLOR=#333333]sudo add-apt-repository ppa:ubuntu-wine/ppa[/COLOR][/FONT]
```
then, ```
[FONT=courier new][COLOR=#333333]sudo apt-get update; sudo apt-get install wine1.7[/COLOR][/FONT]
```

3. Using [Virtualbox]("https://apps.ubuntu.com/cat/applications/hostedvirtualbox/") or other virtualization tool to virtualize Mac OS X or Windows

4. Dual-boot with Windows or build a Hackintosh. Instruction for dual-boot Windows are right [here]("http://lifehacker.com/5403100/dual-boot-windows-7-and-ubuntu-in-perfect-harmony")

Hope it works!

---

### Post by monkeybrain20122 on 2015-06-24
Why don't you use a native Linux program instead?

---

### Post by Ron_Williams on 2015-06-24
Thanks, folks.  appreciate the info.

Being computer* semi-literate* I think mt solution will be to use my wife's computer.:mrgreen:

Problem solved.

---

### Post by GrouchyGaijin on 2015-06-25
> **Ron_Williams said:**
> Thanks, folks.  appreciate the info.

Being computer* semi-literate* I think mt solution will be to use my wife's computer.:mrgreen:

Problem solved.

That is probably the best idea in my opinion .
Setting up a VM just to run iTunes seems like a hassle.
As far as I know, Play On Linux or WINE won't allow you to actually sync your iphone, if that is why you want to run iTunes.

---

### Post by GrouchyGaijin on 2015-06-25
> **Quarkrad said:**
>  I have gone back to dual booting with windows (7) purely to have itunes in it's native environment.   (itunes is the only reason I dual boot - I'm 99.9% ubuntu).

What is it exactly that iTunes does better for you than any native Linux client?  The only advantage I can see to iTunes is that you can sync an iPhone.

---

### Post by Quarkrad on 2015-06-26
A host of small things - but I must say when it works, itunes in Virtualbox is very good.  When running windows/itunes in VB it dragged my host system down too much (i5, 8gb ram). I have a large library so stored it on a separate partition on my HD and accessed it via the shared folder setting in VB - sometimes itunes lost some/many of the links to files.  I had to manually re link them.  Sometimes (always seemed to be when I needed it quickly) there were issues with itunes seeing the ipod via the host/VB.  So .... small things but when I needed to 'just work' I sometimes had issues. So ... I now dual boot and have a win7 partition just for itunes and it works all the time.  Over the years Apple/itunes/ipod is not always as user friendly (to Linux) as they could be.

---

### Post by GrouchyGaijin on 2015-06-26
If it works for you then that is all that matters.  I have an iPhone and do not sync it with my computer.  I did try in the beginning, but then gave up.  Of course I do not use my phone to listen to music.

---

### Post by MoFro624 on 2015-06-27
I have tried the Wine method and VB for iTunes. I haven't tried many of the native linux software besides the stock Rhythm Box. I liked it just didn't put a lot of time into the ID tags. Right now I'm dual booted Windows 7 and Ubuntu for iTunes (seems to be the best for now) and my games (Marvel Heroes 2015, WoW and Star Wars).

---

