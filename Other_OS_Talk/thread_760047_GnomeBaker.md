---
title: "GnomeBaker"
date: 2008-04-19
forum: Other OS Talk
---

### Post by Bungo Pony on 2008-04-19
That's what's used in Nautilus, correct?

Why can't this thing burn Audio CDs? It asks me what kind of CD to burn, and I click on "Audio CD". I give it the tracks I want ,and it burns a data CD. Completely useless :S

---

### Post by em3raldxiii on 2008-04-19
Well, this isn't exactly answering your question, but 1. I've never used gnomebaker to burn audio cds (although I am sure it can), and 2. I use an app called K3B instead because it's a much more elegant application.

```
sudo aptitude install k3b
```

The application is part of the KDE suite of apps, but it works perfectly fine on your Gnome desktop.  It will likely install an array of KDE libraries and other dependencies at the same time, but it's worth it -- a very nice application.

Also, I believe that either Serpentine or Juicer will work for burning audio CDs (and they should be installed by default on your Gnome system).

You can also consult the manual that goes with gnomebaker - it's probably as simple as typing:

```
man gnomebaker
```

I can't verify this 'cuz I am at work.

But trust me, you will probably really like K3B.

---

### Post by ad_267 on 2008-04-19
If you're using Nautilus in 7.10 then no, it does not use GnomeBaker. I believe GnomeBaker is included by default in 8.04 but it isn't in 7.10. Nautilus has it's own burning tools that are only really useful for burning data cds.

If you put in a blank cd and select make audio cd it should open up Serpentine, not nautilus. Make sure that if you go to System - Preferences - Removable Drives and Media, command for audio cds is set to serpentine

You can use Serpentine or GnomeBaker to make audio cds.

---

### Post by Bungo Pony on 2008-04-19
> If you put in a blank cd and select make audio cd it should open up Serpentine, 

It definately doesn't do that even though it's set to open Serpentine - I checked. :confused:

I used K3B to burn my audio CD. Thankfully it works in Gutsy because it crashed almost instantly in Feisty.

---

### Post by em3raldxiii on 2008-04-20
I'm glad K3B worked for ya.  Strange that it crashed on Feisty for you ... I had used it with no trouble whatsoever on Feisty ???  Weird.  Apparently 8.04 is going to use a different CD burning app again, so perhaps it will be better.

---

### Post by pelle.k on 2008-04-20
> I believe GnomeBaker is included by default in 8.04
No it isn't, because it's considered somewhat old and buggy. Brasero is included in 8.04.

---

### Post by FuturePilot on 2008-04-20
From what I've heard, the Gnome Baker project is just about dead.
I like Brasero.
If you're burning from Nautilus, that's Nautilus's own little CD burner plugin.

---

### Post by seanc7 on 2008-04-20
IMO, K3B is the slickest and most feature-rich CD/DVD burning app for someone that wants a GUI to burn discs.

I tried Gnomebaker, it's good but it seems to be lacking a few things that K3B has by default. 

K3B is worth the extra space taken by the KDE libraries and dependencies.

---

### Post by wolfen69 on 2008-04-20
> **seanc7 said:**
> IMO, K3B is the slickest and most feature-rich CD/DVD burning app for someone that wants a GUI to burn discs.

I tried Gnomebaker, it's good but it seems to be lacking a few things that K3B has by default. 

K3B is worth the extra space taken by the KDE libraries and dependencies.

i agree. K3B has never failed me. it's awesome.

---

### Post by em3raldxiii on 2008-04-20
... when will there be a G3B?  hehe ;)

---

