---
title: "firefox 3 and gmail cpu usage"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by wolfie2x on 2008-09-24
I'm seeing unusually high cpu usages in gmail on FF 3.0.1 + ubuntu 8.04.1. 

Everytime I hit 'refresh' in gmail (not in FF), cpu hits full (on one core) for about 4-5 seconds, and the page feels very sluggish. Doing the same on opera almost creates no cpu spike at all.

Is this a known issue? Can somebody pls try this and let me know? It's annoying!

another observation: cpu spike seems to be related to the page size. If I resize ff to see only 2-3 emails (in the list), no spike; if I resize to have around 20-25 emails, major spike. Something to do with gmail rendering?

---

### Post by bangmalley on 2008-09-26
i experienced that spike too, but only for 1-2 seconds and the page still smooth.
try updating to firefox 3.0.3 using update manager.

---

### Post by I Use Dial on 2008-09-26
I have had the same experience in XP.  Opera is just a better browser, but unfortunately like half of the web pages don't work very well with it and I experience regular plugin issues.

---

### Post by anotherdisciple on 2008-09-26
Well Gmail is in beta ;) haha... jk

---

### Post by khm on 2009-05-13
I like to leave one tab of my browser at work on gmail.  If I leave this tab open, my cpu usage averages 70-95%. Without the gmail tab open, my cpu usage will average 1-5%. Why?

---

### Post by superprash2003 on 2009-05-13
which version of ubuntu?

---

### Post by khm on 2009-05-14
> **superprash2003 said:**
> which version of ubuntu?

I'm on 9.04 32-bit. Swiftfox 3.0.4

---

### Post by pconwell on 2009-06-19
I'm still having KHM's problem. Has anyone found the solution.

I've tried multiple, multiple scenarios with multiple users, single users, add-ons, labs, settings... just about everything I can think of. After trying all kinds of combinations, Here is what I found for my particular setup :

Firefox 3.0.11
Ubuntu 9.04 with full updates

_Not causing a problem:_
Gears
Better Gmail 2
Remember the Milk
Labs
any combination of settings
'Older Version'

_Causing a problem:_
'Newer Version'

I hope this helps someone much smarter than I narrow down the problem.

Thanks.

---

### Post by khm on 2009-06-26
The cause of the problem is Better Gmail. Disable or uninstall this firefox add-on and all will be fixed.

---

### Post by kcarnold on 2009-07-03
Perhaps Better Gmail casuses the problem for some people, but I uninstalled it a long time ago and have consistently seen Fx with Gmail take ~30% cpu while idle.

A [old thread]("http://groups.google.com/group/Gmail-Help-Reading-Messages-en/browse_thread/thread/93eeec13fe611129/3bc9acaa7cc3322d?lnk=gst&q=") suggests clearing your cache, but even if that does work (which it might), it's obviously not a long-term solution.

I lack tools to debug this. Is there something like "top" for Firefox? (Seems like a kinda necessary thing, if the browser is becoming the OS.)

---

### Post by khm on 2009-07-21
I'm still inclined to think it's caused by Better Gmail... or more simply Greasemonkey. I would first try starting firefox in [safe mode]("http://support.mozilla.com/en-US/kb/safe+mode"). This will disable all add-ons. If the problem disappears in safe-mode it's most likely one of your add-ons... and I'm guessing it's going to be one that's using one or more Greasemonkey scripts.

---

### Post by Vesperatus on 2009-07-29
Firefox 3.0.12 here with Jaunty.

I dont know what update I installed this morning but now, whenever I have a gmail tab opened, my cpu will hit 60% and stay there. Firefox becomes very slow. I add some addons, firebug ( disabled in gmail ), gmail notifier. Disabled all of that and at some point, my cpu will go to 60%.

I use the in-browser gchat a lot so i'm wondering if that is the cause.

---

### Post by Gatemaze on 2009-09-26
just to wake up this thread... ubuntu 8.04, 64bit, FF 3.0.14... gmail page has my cpu running at 60% and the page is overall slaggish...

noticed that on the gmail page the following process goes mental (occupying 70% or more of the cpu time)
```

/usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7

```

cheers

---

### Post by Vesperatus on 2009-09-26
You wouldn't happen to have issues playing flash videos also would you ?

---

### Post by wolfie2x on 2009-09-26
> **Gatemaze said:**
> just to wake up this thread... ubuntu 8.04, 64bit, FF 3.0.14... gmail page has my cpu running at 60% and the page is overall slaggish...

Switch to FF 3.5.2 if possible. Much better browser. Low memory footprint, feels much faster & gmail works fine with no issues.

---

### Post by Vesperatus on 2009-09-26
> **wolfie2x said:**
> Switch to FF 3.5.2 if possible. Much better browser. Low memory footprint, feels much faster & gmail works fine with no issues.

Firefox 3.5.2 here. No way to get flash nor gmail working correctly. After a couple of minutes, 60 to 70 % cpu.

---

### Post by Gatemaze on 2009-09-27
> **Vesperatus said:**
> You wouldn't happen to have issues playing flash videos also would you ?

No, none. Flash is working perfectly fine... Are you running amd64 and do you have flash issues?

---

### Post by Vesperatus on 2009-09-27
None, running intel core 2 duo. 

My flash is messed up and I tried pretty much all tips I could find on ubuntu. If I disable gtalk on the gmail page, my firefox wont go up in cpu usage. If stays low if, in the add-ons section, I disable the flash. 

Can you try to disable flash and go on the gmail page and see if it "fixes" you issues?

---

### Post by Vesperatus on 2009-11-05
9.10 solved my flash issues. On of the 1834 downloaded packages did anyway ;)

---

