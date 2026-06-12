---
title: "[SOLVED] Two issues.."
date: 2008-05-25
forum: New to Ubuntu
---

### Post by sayakb on 2008-05-25
Hello all
I re-installed (for the 3rd time in a row) Xubuntu (last time, updating screwed it all) :(

It seems to work okay now, but the following two issues still bither me:

1. Whenever I open the terminal, the system logs out and returns to GDM (as if X kills itself). Can you suggest me any alternate terminal application that I might use as a replacement?

2. My Celeron 633MHz processor often goes to 100% usage even while a drag a small window around or even it Firefox loads a page (though the RAM usage is around 50% -- that I consider low enough for just 384MB of RAM). Is Xubuntu going too hard on the poor thing? Any way to make xubuntu lighter?

---

### Post by muted1987 on 2008-05-25
have you got compiz enabled that might be making things go slower as you have a old processer it might be better to have no effects

not sure about a terminal program sry

---

### Post by sayakb on 2008-05-25
Compiz doesn't work on intel 810 mobo onboard VGA. So I don't have it either.

---

### Post by linuxguy6 on 2008-05-25
If Xubuntu is going too hard, why not try Ubuntu? Ubuntu works fine with a computer that has 384 MB of memory and a 633 MHz processor.

---

### Post by muted1987 on 2008-05-25
i cant think of anything else to say other than upgrade pc sry

---

### Post by s-lime on 2008-05-25
I believe gnome needs far more CPU and RAM.

But you can switch to xubuntu.

---

### Post by sayakb on 2008-05-25
> **muted1987 said:**
> i cant think of anything else to say other than upgrade pc sry

I have 2 PCs and 2 laptops. One of the PCs being this historic one while the other has a q6600 Core2 Quad (bad contrast).. This is just lying as a junk, and just wanted to get it working, thought that it might work faster than what it does with a crappy XP on it...

---

### Post by sayakb on 2008-05-25
> **s-lime said:**
> I believe gnome needs far more CPU and RAM.

But you can switch to xubuntu.

I am already using Xubuntu with XFCE4..

---

### Post by muted1987 on 2008-05-25
oh ok so its a renovation job 

i take it you dont mind messing with it then

why dont you try disabling any uneeded modules

---

### Post by sayakb on 2008-05-25
Did that already. I'm starting to think that the old box is being overloaded.. Would be trying puppy linux tonight though :)

---

### Post by muted1987 on 2008-05-25
that sounds like a good idea let me know the outcome and if i think of anything ill let you know

---

### Post by BlackDragonBE on 2008-05-25
Why not try IceWM? It handles very well on PC's with few resources.

Cheers

---

### Post by sayakb on 2008-05-25
Yes, but IceWM doesn't have a file manager of it's own.. So I'll just end up using Thunar, won't I?

---

### Post by |Eric| on 2008-05-25
first thing you shoud do is go in the logs  
see what makes it crash 
if there isnt anything in the log (that would be verry suprising)
then it may be that you installed somthing that is demanding in terms of ressources 


when it just crashed open it reverts back to basic promt right ?
try this at the prompt

start Xwindow bare 
prompt# X :0 &
Ctrl+alt+F1 (goes back to prompt)
prompt# xtem &
in that prompt (termial window in X)
xwinprompt# Thunar &


wen your at the prompts if you dont see it type (Enter) key 
it will move that app to bg 


if all that dosent crash & it still works fine try removing any extras ...


a bare xwindows + xterm runs in 32MB ram easy

---

### Post by sayakb on 2008-05-26
I. Firstly, I think I disabled sysklogd, though, I would enable it and post he log here.
2. No, when it crashes, it takes me to GDM, where I login and everything it fine again. I think you're right about the resource demanding issue, since my PC almost freezes even when Firefox opens up a webpage as the CPU usage goes upto 100%

---

### Post by ardvark71 on 2008-05-26
Hi...

I remember your last thread on Xubuntu for this system, looks like my suspicions turned out to be correct. :(

I would try Puppy or any of the other distros that have been offered as suggestions. A while back, I tried Ubuntu on old i810 myself, I know. ;)

Best Regards...

---

### Post by Sinkingships7 on 2008-05-26
Give [Fluxbuntu]("http://fluxbuntu.org/js.html") a shot. Much, MUCH lighter than Xubuntu.

---

### Post by sayakb on 2008-05-26
Thanks for the opinion. I am currently working on OpenBox as advised by an UF member. I would definitely try Fluxbuntu though (the website looks beautiful :D)
Thank you all

---

### Post by eriqjaffe on 2008-05-26
I would recommend that you look into using PCManFM instead of Thunar - I use it on two systems, including a laptop that is far, far less powerful (Pentium II, 366mhz, 128mb RAM) than the system you're trying to resurrect.

Also, Opera is a far more lightweight browser than Firefox.

---

### Post by sayakb on 2008-05-27
I do use Opera. Plus I am struggling with ROX. Is PCManFM better than ROX?

---

### Post by eriqjaffe on 2008-05-27
I prefer it, I just never felt comfortable with ROX.

---

### Post by sayakb on 2008-05-27
Does is support desktop icons? I do need that feature..

---

