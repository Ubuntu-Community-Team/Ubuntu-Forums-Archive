---
title: "Monodevelop broken in Intrepid?"
date: 2009-02-14
forum: Programming Talk
---

### Post by cdekter on 2009-02-14
I just tried to install and run monodevelop on two separate PCs (one laptop, one desktop) running Intrepid, and on both the splash screen comes up and then the app just starts chewing up all available ram and spinning one of the CPUs (100% usage on one core). Anyone seen this before and know how to fix it? I've tried reinstalling. I've even built monodevelop 2 from the source and it has the same problem!

---

### Post by lavinog on 2009-02-17
it comes up on my system, I just installed it on a intrepid 64 setup.
what happens when you load it from the commandline?

---

### Post by cdekter on 2009-02-17
I'm on 64 bit too... When run from the command line I get the following message, then nothing:

```
WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so.
Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.

```

---

### Post by lavinog on 2009-02-17
I get that message too, but the IDE still comes up.
maybe try monodevelop -~
for debug info

has it worked in the past? Could there be a reference to a project that doesn't exist?

---

### Post by cdekter on 2009-02-20
It has indeed worked in the past... been a while since I tried it out though. I don't have any Monodevelop projects, and had the issue on two totally separate PCs.

---

### Post by hellfeuer on 2009-03-03
I'm having the same issue. Any fixes??
Heres what I get with monodevelop -~

WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.
ParsingMode = Both
BreakSingleDashManyLettersIntoManyOptions = False
EndOptionProcessingWithDoubleDash = True
DontSplitOnCommas = False

It was stuck here for a while, then I Ctrl-C'd.

---

### Post by cdekter on 2009-03-03
Might be time to post a bug report on this one, if it hasn't already been done.

---

### Post by rezonant on 2009-04-25
Same problem here. I did find a bug report, which managed to stay in the New state all the way up to Jaunty's release!! Sigh.

There's Mono 2 packages at [http://eric.extremeboredom.net/2008/10/15/296](http://eric.extremeboredom.net/2008/10/15/296) that I tried, but unfortunately they too have the same issue.

---

