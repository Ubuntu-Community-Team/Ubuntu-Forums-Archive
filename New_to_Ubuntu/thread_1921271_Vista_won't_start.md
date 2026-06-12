---
title: "Vista won't start"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by Momof9Blessings on 2012-02-06
A few weeks ago, my daughter's laptop had the black screen with a flashing cursor, it would show up after the Windows welcome screen.....  In all I found, I needed to do a reset to factory settings....   

So I put in my live Ubuntu 11.10 cd and she backed up all of her important photos etc....  

A few days ago, one of my other daughter's was watching something on the laptop and it crashed or something....  when we try to start it asks us to Launch repair....  then we get this error message, "cannot repair this computer automatically" and a message about recently attaching a device to remove and restart.... but nothing is attached (including power cord).  I do remember and seeing this problem before I did the reset to factory settings....  Startup Repair does nothing either.....

Is this problem going to keep on happening?  

I am going to put in the Ubuntu disc again, so she can save anything new she has put on her laptop.....  

My husband wondered if it was a problem with the hard drive (or bios).... 

Would this laptop be able to be dual booted or linux only....  getting frustrated with having to fix the same "windows" problem....

If I do put linux only.... how do we do that???

(I am so tempted to make my "new" laptop linux only when I get it - windows is SOOOOO annoying)..... LOL

Thank you

---

### Post by TeoBigusGeekus on 2012-02-06
Have you had the laptop cleaned recently?
If it's accumulated dust, then whatever os you put in it won't help the situation.
I'm saying this, because ~6 months ago I had the same problems with my laptop: random crashes in both linux and windows; eventually, the graphics card (on board) was fried and I threw the whole thing away.
Had I bothered to get the laptop cleaned, non of this would have happened.

---

### Post by donkyhotay on 2012-02-06
> **Momof9Blessings said:**
> A few weeks ago, my daughter's laptop had the black screen with a flashing cursor, it would show up after the Windows welcome screen.....  In all I found, I needed to do a reset to factory settings....   

So I put in my live Ubuntu 11.10 cd and she backed up all of her important photos etc....  

A few days ago, one of my other daughter's was watching something on the laptop and it crashed or something....  when we try to start it asks us to Launch repair....  then we get this error message, "cannot repair this computer automatically" and a message about recently attaching a device to remove and restart.... but nothing is attached (including power cord).  I do remember and seeing this problem before I did the reset to factory settings....  Startup Repair does nothing either.....

Is this problem going to keep on happening?  

I am going to put in the Ubuntu disc again, so she can save anything new she has put on her laptop.....  

My husband wondered if it was a problem with the hard drive (or bios).... 

Would this laptop be able to be dual booted or linux only....  getting frustrated with having to fix the same "windows" problem....

If I do put linux only.... how do we do that???

(I am so tempted to make my "new" laptop linux only when I get it - windows is SOOOOO annoying)..... LOL

Thank you

There are lots of possibilities. Personally I'd probably run a HW diagnostic if you can (some systems have onboard diagnostic systems). OS corruption and/or viruses happens from time to time but generally if it happens twice within a short period of time it's a good idea to look at the HW rather then the OS or installed software.

---

### Post by Momof9Blessings on 2012-02-06
I just blew canned air into the laptop vents.... not sure how much that will help (it is about 4 years old).....

How do I do the diagnostics?  I am trying to figure out if I can do it with the Ubuntu 11.10 disc....  Windows won't start....

---

### Post by Momof9Blessings on 2012-02-06
ram check works fine..... ca't figure out how to do anything else.... yet

---

### Post by Ms. Daisy on 2012-02-06
FWIW, I used canned air to periodically clean an old computer of mine throughout its lifetime.  However when I took it apart to replace the hard drive recently I discovered an insane amount of nasty funk that would make a grown man squirm.  You may consider taking the laptop apart to really get it clean. Or take it somewhere if you're not comfortable doing it.

As for checking the drive, I **definitely **recommend that. From what you describe I suspect hard drive failure.  Use Gparted / disk utility from the live Ubuntu CD.

[http://www.ubuntubuzz.com/2010/06/ubuntu-1004-disk-utility-tools_28.html](http://www.ubuntubuzz.com/2010/06/ubuntu-1004-disk-utility-tools_28.html)

---

### Post by Mark Phelps on 2012-02-07
> **Momof9Blessings said:**
> How do I do the diagnostics? 
Possibly, the diagnostics folks are talking about is the MS Windows utility to check the drive for damaged system files.  To do that, you boot from a Vista DVD, open a command line, and enter "sfc /scannow".  If you don't have a Vista DVD, that makes this very difficult to do. 

> I am trying to figure out if I can do it with the Ubuntu 11.10 disc....
Basically -- NO. While you CAN run this routine from a command line while booted into the Windows desktop, it generally does NOT work.  You really have to boot into a Vista (or Win7) DVD to do this.

---

### Post by donkyhotay on 2012-02-09
Some computers have onboard diagnostics built into the motherboard, might try these if your computer has them (will have to read HW documention to find out). My HP system has F9 for diagnostics for example. Making a diagnostic boot disc would probably be a better option though.

---

