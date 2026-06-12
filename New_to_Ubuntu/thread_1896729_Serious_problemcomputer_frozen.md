---
title: "Serious problem/computer frozen"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by rawbertb on 2011-12-17
I have an emachine EL-1850 and have installed Kubuntu on it.  I have had no problems until yesterday.  When i started the computer, the screen comes like usual, but then my Skype app screen pops up and the entire system freezes.  I can do nothing except turn off the computer.  I have tried to reload Kubuntu, and it will not reload.  I have tried Ubuntu recovery mode, and all of the four prompts to no avail.  Is there something I can try, or is it time for a new hardrive?

---

### Post by QIII on 2011-12-17
After 35 years of goofing off on computers and working on my sallow, vampire-like complexion in a room away from human contact (or so it seems if you ask my wife), I have found that much scratching of the head and throwing expensive equipment on the floor is often followed by finding the simplest of things to be wrong.  I still do it, so don't take me wrong here.

(The Skype thing may or may not be a red herring.  If you saved your session in Kubuntu, it would effectively have become a "startup app")

See if you can run a live session from the Live CD. If a live  session will run, can you navigate around the hard drive and open files  and such?

Just for giggles and grins, open the case and check that all the fiddly bits are connected tightly.  Is your CPU HSF running? Check the mobo carefully for obvious signs of failure like melted stuff or leaky caps.

Then run the memory test for 12 hours (Sorry.  Depending on how much memory you have, that can take a while to get a thorough check.)

Rule out run-of-the-mill, kick-yourself-in-the-rear-for-not-checking physical stuff. 

Then, consider two things:  bad disk or a stroke of bad luck corrupting an important file.

---

### Post by fdrake on 2011-12-17
> **rawbertb said:**
> I have an emachine EL-1850 and have installed Kubuntu on it.  I have had no problems until yesterday.  When i started the computer, the screen comes like usual, but then my Skype app screen pops up and the entire system freezes.  I can do nothing except turn off the computer.  I have tried to reload Kubuntu, and it will not reload.  I have tried Ubuntu recovery mode, and all of the four prompts to no avail.  Is there something I can try, or is it time for a new hardrive?

enter in [recovery mode]("https://wiki.ubuntu.com/RecoveryMode") and run in the root prompt:"fsck"

---

### Post by QIII on 2011-12-17
Thought he said he had tried recovery mode.

---

### Post by fdrake on 2011-12-17
> **QIII said:**
> Thought he said he had tried recovery mode.

yes he said he did but we don't know what command he tried..

---

### Post by dFlyer on 2011-12-17
Can you boot off a live cd and run disk utility to check your drive to make sure you don't have some bad sectors.

---

### Post by audiomick on 2011-12-17
> **QIII said:**
> After 35 years of goofing off on computers and working on my sallow, vampire-like complexion in a room away from human contact (or so it seems if you ask my wife), I have found that much scratching of the head and throwing expensive equipment on the floor is often followed by finding the simplest of things to be wrong.  I still do it, so don't take me wrong here.

(The Skype thing may or may not be a red herring.  If you saved your session in Kubuntu, it would effectively have become a "startup app")

See if you can run a live session from the Live CD. If a live  session will run, can you navigate around the hard drive and open files  and such?

Just for giggles and grins, open the case and check that all the fiddly bits are connected tightly.  Is your CPU HSF running? Check the mobo carefully for obvious signs of failure like melted stuff or leaky caps.

Then run the memory test for 12 hours (Sorry.  Depending on how much memory you have, that can take a while to get a thorough check.)

Rule out run-of-the-mill, kick-yourself-in-the-rear-for-not-checking physical stuff. 

Then, consider two things:  bad disk or a stroke of bad luck corrupting an important file.

This is really good advice.

---

