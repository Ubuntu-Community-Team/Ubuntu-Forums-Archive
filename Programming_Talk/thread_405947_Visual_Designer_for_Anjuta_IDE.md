---
title: "Visual Designer for Anjuta IDE"
date: 2007-04-10
forum: Programming Talk
---

### Post by EverHardy on 2007-04-10
Hi EveryBuddy@UbuntuForums

I'm trying to write a simple 'c' based program using anjuta ide. I want to design simple one button window executing some 'c' code behind the scenes just to start learning[B] 'c' based visual design on ubuntu (feisty fawn).
[/B]
Is there any tutorials for beginners ?

I've installed monodevelop (and also stetic), but don't know if I can use stetic from Anjuta ?

I read somewhere that Anjuta has got it's built in visual designer (glade), but I get some error messages in anjuta, whenever I try to use gui designer for a 'c' based project. Perhaps, I don't know how to use that gui designer or I haven't installed it. how can I find what's wrong, if  glade doesn't come pre-installed with anjuta in ubuntu (feisty fawn) then what is the package name for glade (using synaptic ) ?

with regards
EverHardy

---

### Post by j_g on 2007-04-10
glade3

But the package of Anjuta in the Ubuntu repositories is an older version that uses an older version of glade (which is not recommended). My advise is to dump Anjuta.

---

### Post by Jmccaffrey on 2007-04-10
Glade is a seperate program for developing interfaces portably.  Glade will allow you to graphically create an interface and save it in an XML format.  Then in your C code you simply link to glade, include a header, and load the glade XML file.  Google "glade tutorial" for more information.

---

### Post by EverHardy on 2007-04-11
First of all, thanks (j_g & Jmccaffrey) for your reply.

j_g, if can you please explain in brief what's wrong with anjuta and what else would you suggest I should replace it with ?

[My aim is to get a decent C development ide with visual designer (and cross-platform development capability,if possible)]

with regards
EverHardy

---

