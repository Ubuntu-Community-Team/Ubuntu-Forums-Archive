---
title: "Ubuntu installed on 8gb FlashDrive"
date: 2013-08-12
forum: New to Ubuntu
---

### Post by maurice3 on 2013-08-12
I have a very simple question, a buddy of mine was running ubuntu 13.04 off of his flashdrive on my pc. I have a 8gb PNY FlashDrive and it is bootable. My question is, would it be okay to install ubuntu onto that without any lag issue or anything, because there was some lag on the live cd? I put it on my 64gb flashdrive and worked great.

Also, is there any other linux distro that can use wine and would leave me with at least 5gb of storage?Work smooth?

---

### Post by DuckHook on 2013-08-12
It works in theory, but you will find that a lot of factors determine whether you will have a happy experience or not.

Speed of you base system.
Speed of USB port.
Speed of flash drive.

64GB flash tends to be made with fast up-to-date memory so this is one reason you like it. Don't know about your 8GB drive, but it doesn't hurt to try it out and see.

For good instructions on installing, see [here]("http://ubuntuforums.org/showthread.php?p=12363705#post12363705").

Re: WINE

As far as I know, WINE should work on any distro because it is basically an app that maps Windows system calls over to equivalent Linux calls. It will leave you all of the storage that you have on your HDD, or perhaps I am not getting what your question is. How smoothly it works is not a function of the distro or of WINE, but of how well the app behaves in the WINE environment. You will get wildly varying mileage depending on a combination of the app and your HW.

---

### Post by maurice3 on 2013-08-12
> **DuckHook said:**
> It works in theory, but you will find that a lot of factors determine whether you will have a happy experience or not.

Speed of you base system.
Speed of USB port.
Speed of flash drive.

64GB flash tends to be made with fast up-to-date memory so this is one reason you like it. Don't know about your 8GB drive, but it doesn't hurt to try it out and see.

For good instructions on installing, see [here]("http://ubuntuforums.org/showthread.php?p=12363705#post12363705").

Re: WINE

As far as I know, WINE should work on any distro because it is basically an app that maps Windows system calls over to equivalent Linux calls. It will leave you all of the storage that you have on your HDD, or perhaps I am not getting what your question is. How smoothly it works is not a function of the distro or of WINE, but of how well the app behaves in the WINE environment. You will get wildly varying mileage depending on a combination of the app and your HW.

So I have xubuntu, will wine work with it?

---

### Post by DuckHook on 2013-08-12
> **maurice3 said:**
> So I have xubuntu, will wine work with it?

Yes.

Before installing, you may wish to understand the security risks inherent in WINE, and check WINE application database for the apps you intend to run. If they are poorly supported, you will have an awful experience and may as well not run WINE. In that case, you may wish to explore a VM instead (if you have sufficiently powerful HW to support it).

One of the best security gurus on this forum has written a primer on security, part of which deals with WINE. The sticky is [here]("http://ubuntuforums.org/showthread.php?t=510812"). Just scroll down to the section dealing with WINE. WINE app database is [here]("http://appdb.winehq.org/").

---

### Post by squakie on 2013-08-12
+1.  Something to keep in mind is if you are going to be running from a USB flash drive and want to install applications and have it remember changes, etc., you have to set it up with what is called persistence.  If you don't see that in any how-to you want to follow, post back here before using that how-to.  Basically, you set aside "x" amount of space to be used for persistence.  In the case of an 8gb flash drive, I suspect your experience would probably not be to your liking because in my experience there just isn't much space left for persistence.  I would really suggest at least a 16gb flash drive or larger.  However, as DuckHook has said you can always try it and see.  Just don't be too disapointed if the results aren't what you want.  Some of us have tried to play-it-forward with hardware we aren't using - perhaps someone can offer you one if you can't afford it.  Eve the class-10 flash drives at Micro Center are pretty cheaply priced.

EDIT:  My bad - I forgot you can do a full install to a 16gb of larger flash drive in which case I don't think you have to worry about persistence.

---

