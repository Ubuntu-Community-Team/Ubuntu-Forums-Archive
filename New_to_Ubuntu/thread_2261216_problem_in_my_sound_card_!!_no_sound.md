---
title: "problem in my sound card !! no sound"
date: 2015-01-17
forum: New to Ubuntu
---

### Post by recioui_mouadh on 2015-01-17
hello everybody
i have two sound cards , one is internal and the other is external 
the internal works perfectly !! but the external doesn't work ! despite it appears on the sound preferences 

[IMG]https://scontent-b-cdg.xx.fbcdn.net/hphotos-xpf1/v/t1.0-9/s370x247/10926457_1681830372043689_2807570338143627771_n.jpg?oh=6bbd073b8b6d0dea96c05e868b0dfbf4&oe=55641CEF[/IMG]
first one is my internal card ( built in ) it works perfectly  , and the second( high definition audio controller ) is the external ( which doesn't work) 
[IMG]https://scontent-b-cdg.xx.fbcdn.net/hphotos-xap1/v/t1.0-9/s370x247/10801657_1681830375377022_1375476321642239002_n.jpg?oh=555a3b35aa883567b87d4b991bb9208f&oe=5568B60A[/IMG]
i've tried changing some settings but no sound !! 

any suggestion ?

---

### Post by Rob Sayer on 2015-01-17
Those pics don't do anything when clicked and I sure as frak can't read them very well.

Please paste into terminal:

sudo aplay -l

and post the results here using [CODE] tags.

---

### Post by grahammechanical on 2015-01-17
You may need to go into the BIOS/UEFI settings utility to activate the external sound card. You may need to de-activate the onboard sound card.

Regards.

---

