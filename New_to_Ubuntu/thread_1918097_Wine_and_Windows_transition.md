---
title: "Wine and Windows transition"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by shockingdave on 2012-01-31
I have linpais and I would like to install wine for my windows programs. Where can I download it? Presently my internet service is on my winxp, so I have to download everything there. Can someone enlighten me about wine, and how this system works, I would like to eventually transition over and eliminate my microsoft, but I still have some business programs that run in windows, can I sucessfully eliminate my windows and still run some of my programs.

---

### Post by Lars Noodén on 2012-01-31
You can find [WINE](apt://wine/) in the Ubuntu software repository and you can download and install it using either Synaptic or the Ubuntu Software Center.

WINE is an implementation of the Windows API on top of Linux.

Now is also a good time to ask about alternate software.  In some cases the tools available on Ubuntu are superior.

---

### Post by cortman on 2012-01-31
> **shockingdave said:**
> Presently my internet service is on my winxp, so I have to download everything there.

If you need to download Ubuntu packages through Windows, you can use apt-offline, or I've written a very simple program that will work with package download scripts. See the "Offline Software Installation - Download with Windows" link in my signature.

---

### Post by Mark Phelps on 2012-01-31
> **shockingdave said:**
> ...can I sucessfully eliminate my windows and still run some of my programs.

The actual answer is at best ... maybe.

You need to go the the WineHQ website, use their application compatibility page, and search for the Windows apps and versions that you want to use.

You will see that each version of each app has a rating -- from Platinum (the best) to Garbage (the worst).  If your app is rated Gargage, it's not going to work in Linux, no matter what you do.

Anything you rely on daily, needs to have a rating of Gold or better to actually be useful.

If you really want to "eliminate" Windows, then you would do better to learn Linux app substitutes, instead of depending on Wine.

---

### Post by shockingdave on 2012-02-02
Closed:
Thanks for the help. 
Signed Dave

---

### Post by kevdog on 2012-02-02
IMO -- wine frankly sucks.  You'd be better of installing a vm or dual booting -- but that's just my experience.

---

