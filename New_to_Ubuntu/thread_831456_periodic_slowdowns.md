---
title: "periodic slowdowns"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by lobo-tuerto on 2008-06-16
Hi guys,


I have HP dv9000 laptop. I was using Ubuntu 7.10 without any problems. Now that I have moved to 8.04 I'm experiencing an annoying problem.

When using some programs (specially the flash player in FF) I experience periodic slowdowns. The program that shows at top in my conky window is xorg, alongside with firefox, and if rythmbox is open, that one takes a big share too. After 30 secs or 1 min the processor is again at "normal" load, but never as it was when I was using Gutsy Gibbon.

Anyone knows what can be causing this periodic slowdowns? I can't even play Warcraft3 no more, the periodic slowdowns affects my game and it basically freezes (it's like 1 frame per second). After 1 slowdown has passed, the next one coming is worst, as I said this didn't happen in 7.10 (when playing Warcraft3).

Any advice or tips will help.
Help, I'm a desperate Ubuntu user. :(


It's the only problem I've got with this new version.

---

### Post by cardinals_fan on 2008-06-16
Firefox is slow.

---

### Post by lobo-tuerto on 2008-06-16
Yeah I know, but sadly, Firefox isn't used as the engine for Warcraft3, and I'm getting the periodic slowdowns there as well.

And as a sidenote, I wasn't having any problems with Firefox in 7.10.

It has something to do with xorg and the new 8.04.

---

### Post by lobo-tuerto on 2008-06-16
Seems like it might have something to do with this:
[http://ubuntuforums.org/showthread.php?t=809706](http://ubuntuforums.org/showthread.php?t=809706)

How do I tell what kernel version do I have?
How can I change it to .16?

The guy in the post seems to not have any problems with it.


Help please!

---

### Post by lobo-tuerto on 2008-06-17
Am I the only one suffering from this problem?

No one can help?

---

### Post by lobo-tuerto on 2008-06-23
Arghhhh!!!!

---

### Post by lobo-tuerto on 2008-06-23
I think is a general problem with Ubuntu 8.04, maybe a driver-hardware issues.

I have a thread open, and nobody seems to care.
[http://ubuntuforums.org/showthread.php?t=831456](http://ubuntuforums.org/showthread.php?t=831456)
(lol a guy even suggested that the problem was FF3 being too slow... wtf I got a 2gb ram t5500 core 2 duo laptop).

It's obvious that FF3 can't consume so much processor and memory power. But everynow and then my PC freezes for a little while, getting the CPU to 98%-100% use.

When I was using Ubuntu 7.10 I had none of these problems with FF3b5 open with LOTS of tabs and Opera together while playing music in Rhythmbox and programming in Netbeans.

Now if I visit a site like YouTube (yeah flashplayers seems to be one of the problems in the equation) and have Rhythmbox open, I start to get periodic freezes.

Oh, by the way, XORG appears in the top processes too a lot, when the CPU gets to 100%. In fact when the CPU reaches the 100% mark, the percentage is divided up between the processes that are running, for example a tipical output of top (that I can see in conky) would be:

Firefox: 42%
Rhythmbox: 36%
xorg: 22%

And that's too much for process that should be at least at 2%, because they are doing basically nothing to consume an Intel Core 2 Duo T5500.

Any ideas?

---

### Post by Sef on 2008-06-23
> How do I tell what kernel version do I have?

```
uname -r
```

That will give you your kernel version.

---

### Post by X-dark on 2008-06-27
Try putting any CD in your CD-ROM drive.

---

### Post by jck77 on 2008-07-04
Im having the same issue, As soon as I run the dist-upgrade....

So I assume is firefox 3 with flash player beta 10. thats my case....  I change the plugin from beta 10 to the stable 9 and the problem was fixed. try that if is your case. btw I'm trying to use flash player 10 and fix this issue but i don't know why is this happening. maybe a bug because of beta version? dunno....

let us know if you find something else.

peace

---

### Post by lobo-tuerto on 2008-07-09
No putting a CD didn't help.

And it's not just the flashplayer, but I acknowledge it's a "part" of the equation. Because xorg, and rhythmbox have something to do with it too.

That's why I said I think this is a driver-hardware problem.

Even the "Energy management" settings are poorer in Hardy Heron. In Gutsy Gibbon it would let me control the brightness of my laptop's monitor, not so in Ubuntu 8.04.


Anyone else have any tips?

---

