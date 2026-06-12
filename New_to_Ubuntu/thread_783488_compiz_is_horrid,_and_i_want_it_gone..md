---
title: "compiz is horrid, and i want it gone."
date: 2008-05-05
forum: New to Ubuntu
---

### Post by fignig on 2008-05-05
how do i remove compiz from my life? i want good commands that actually work in helping me to remove compiz totally and all of it's little "horrid sections" or w/e. i just want compiz gone, and i hate it.

---

### Post by superbenny on 2008-05-05
sudo aptitude remove compiz compiz-core compiz-plugins

that should just about do it...you could of course just do it in synaptic...

---

### Post by st33med on 2008-05-05
Well, to disable it just go to System>>Preferences>>Appearances and go to the Visual Effects tab and click None.

Just out of curiosity, what did you not like?

---

### Post by Xiong Chiamiov on 2008-05-05
> **superbenny said:**
> sudo aptitude remove compiz compiz-core compiz-plugins

that should just about do it...you could of course just do it in synaptic...

Or replace remove with purge to get rid of the configuration files as well.

---

### Post by fignig on 2008-05-05
> **st33med said:**
> Well, to disable it just go to System>>Preferences>>Appearances and go to the Visual Effects tab and click None.

Just out of curiosity, what did you not like?

lol, how much time do you have? i hated everything about it. i hate the problem that it caused when my desktop resolution went to 640x480 and it took me hours to fix. i hate when i close it, all of the boxes are unchecked, so it's pretty much doing nothing. i hate how it works, b/c it doesn't... and i hate the programmer for making such a stupid program, it doesn't work, and i can't seem to get it to work. and everytime i try to enable something it takes away the top line to every window. i can't close or move anything...I HATE COMPIZ, unless i knew how to work it. lol.

---

### Post by st33med on 2008-05-05
Sounds like a valid complaint to me :D

Anyways, it could be your video card that is having trouble with it. Is it an ATI gpu? Because I know those give major compiz headaches.

---

### Post by Joeb454 on 2008-05-05
You say it doesn't work - I have to disagree - it does work :)

Though sadly it doesn't work for you :(

---

### Post by Tatty on 2008-05-05
> **fignig said:**
> I HATE COMPIZ, unless i knew how to work it. lol.

Lol sounds like you have troubleshot the problem there already ;)

Compiz works fine for me, I think it is an excellent piece of software/eye candy.

---

### Post by BlackSwordD2 on 2008-05-05
> **fignig said:**
> lol, how much time do you have? i hated everything about it. i hate the problem that it caused when my desktop resolution went to 640x480 and it took me hours to fix. i hate when i close it, all of the boxes are unchecked, so it's pretty much doing nothing. i hate how it works, b/c it doesn't... and i hate the programmer for making such a stupid program, it doesn't work, and i can't seem to get it to work. and everytime i try to enable something it takes away the top line to every window. i can't close or move anything...I HATE COMPIZ, unless i knew how to work it. lol.

i know some of your pain being completly new to all this, but i found some solutions to those problems.

for me the boxes only become unchecked when i try to use dual boot but they stay when i keep to Ubuntu

and to keep the top line there its a similar problem to before, if you just stay in Ubuntu it stays where it is and to fix it all you haev to do is go to Appearances and move the check box from None to Extra

why it does these things is beyond me, but for me everything compiz offers far outweighs these easy to fix problems

---

### Post by fignig on 2008-05-05
> **st33med said:**
> Sounds like a valid complaint to me :D

Anyways, it could be your video card that is having trouble with it. Is it an ATI gpu? Because I know those give major compiz headaches.

no, i'm currently using a 7600 nvidia card. 256mb

---

### Post by Joeb454 on 2008-05-05
Do you have the restricted drivers enabled?

---

### Post by fignig on 2008-05-05
> **Joeb454 said:**
> Do you have the restricted drivers enabled?

how do i figure that out?

---

### Post by BlackSwordD2 on 2008-05-05
> **fignig said:**
> ubuntu 8.04 hardy is the only OS i have on this computer

i completely agree, but im only weening.

still those solutions should still work

---

### Post by fignig on 2008-05-05
i like how fast ppl post back on these ubuntu forums, the only problem i have are the solutions u give me, and how u tell these "solutions" most of them don't really work, or the instructions are too vague. i wish ppl would just post a good solid answer, instead of dancing around the answer...

i would like to know how to remove compiz from my computer

and how to reinstall it, for future reference..

---

### Post by Tatty on 2008-05-05
> **fignig said:**
> how do i figure that out?

System->Administration->Hardware Drivers.

---

### Post by SunnyRabbiera on 2008-05-05
For me I think compiz is pretty decent, its certainly better then aero and unlike aero you can remove it without causing any real issues...
I hate the way aero is just taked on the way it is, with no concern for those who dont like it...

---

### Post by BlackSwordD2 on 2008-05-05
> **fignig said:**
> i like how fast ppl post back on these ubuntu forums, the only problem i have are the solutions u give me, and how u tell these "solutions" most of them don't really work, or the instructions are too vague. i wish ppl would just post a good solid answer, instead of dancing around the answer...

i would like to know how to remove compiz from my computer

and how to reinstall it, for future reference..

use your Synaptic Pakage Manager, search for Compiz, select compiz-core and it will prompt if you want to mark so-and-so click mark and remove all those (these will be all the darkened boxes, were it me i'd stop there but you could delete the other compiz associated programs in the list as well i guess)

---

