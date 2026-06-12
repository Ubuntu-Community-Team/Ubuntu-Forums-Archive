---
title: "Help with desktop glitches"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by cowchpotato258 on 2008-05-22
Hey everybody. I posted this in the "general help" section, and only got one reply, and it didn't solve my problem, and my thread was soon pushed to the back of the forum. I was thinking maybe this is becasue I posted in the wrong section, because it was more a beginner help thing than a genersal help thing. And yes, I know reposting and double posting are sins on forums. I just thought I had it in the wrong place and I kind of need my laptop running correctly for school, It's not that I'm impatient, I swear!

    Apologies aside, here's my problem: Every once in awhile, and particularly on the desktop, I cannot double click an item, and the only way I can even SELECT the item is by dragging my mouse and highlighting it like that. But then sometimes (most of the times, actually) The little highlight rectangles won't disappear after I've let go of the mouse and I'll end up with 2-3 of those annoying rectangles on my desktop, while in the mean time can STILL not double click items on my desktop. I also have problems right-clicking these items. I can really only highlight them, and as previously stated, that just makes a mess of my screen. 

   The only way I've found to get around it is to go to places->desktop and the icons behave normally there. However even in the File Browser I'll have these problems from time to time, and I have to close and re-open the browser. I'm currently running 8.4 (hardy heron?) and I'm a first time user. Please help. I really like Ubuntu much better than XP and there's no way I'm switching back but with these glitches I'm kinda stuck. It's probably something I did/am doing wrong. 
   
   Somebody said it might be Compiz Fusion and my desktop effects, but I had been having this problem before I even used compiz or desktop effects. In fact I had the problem when I was using the Live CD. I figured this was just because I was also running a fried version of windows XP, and because it was only a demo and may have a few bugs. I figured a full installation would fix it, so I formatted my HD and installed Ubuntu fully. I have a feeling it may be that some hardware is outdated or some drivers are buggy. How can I test for that and determine what I need to Buy or Install?

---

### Post by Lord Xeb on 2008-05-22
Have you installed the restricted drivers  for ATI cards (if you are using an ATI card)? Have you configured Compiz?

---

### Post by cowchpotato258 on 2008-05-22
First of all, thanks for your quick response. Well I have configured compiz, but I'm not sure about what kind of card I have, since I got the laptop from my mom (She managed to get a bad virus, got fed up with it and told me if I could fix it I could have it). I'm assuming there's some place I can check for this. I'm almost completely sure it's just that I'm using generic drivers automatically downloaded as opposed to proper ones. How can I check to see what kind of card I have, and then where can I get the proper drivers? If anything I'm prepared to buy a new card, as long as the price is within reason. Anything to get my laptop running at this point.

---

### Post by gsiliceo on 2008-05-22
Please use paragraphs next time, yeah its a problem with ati drivers.

---

### Post by cowchpotato258 on 2008-05-22
> **gsiliceo said:**
> Please use paragraphs next time, yeah its a problem with ati drivers.
Thanks alot, and I edited my post to make it more readable.
As soon as you posted that I looked up and realized how terrible it looked. Ha. Sorry about that!
I'll look up and install these ATI drivers, and I'll post the result here.

---

### Post by PPAAUULL on 2008-05-22
If it is something to do with ATI drivers I might suggest Envy to get those drivers working and setup.

---

### Post by cowchpotato258 on 2008-05-22
> **PPAAUULL said:**
> If it is something to do with ATI drivers I might suggest Envy to get those drivers working and setup.
Thanks alot. I'm gonna try right now.

EDIT:
I installed the text interface version of Envy. ATI drivers wouldn't install because apparently I don't have an ATI card. the only other option was install Nvidia drivers so I installed those. And I'm still having the same problems.

EDIT AGAIN:
I've done some homework, figured out my graphics card, and looked it up to see if it was supported by desktop effects. Upon looking up my Graphics card in the wiki, I found this:
nVidia GeForce FX5200go 64Mb (with latest nvidia-glx-1.0.8178 and nvidia-kernel-1.0.8178-r3, no direct rendering) 
So apparently it works as long as I have nvidia-glx-1.0.8178 and nvidia-kernel-1.0.8178-r3. Did using Envy to install Nvidia drivers give me both of those things? And what does it mean by "No Direct Rendering?" Would I do myself good to get a new card at this point or is my problem something else?

EDIT AGAIN AGAIN:
Tried using the GUI version of Envy. Didn't suspect the result would be any different than that of the text interface version. My suspicions were correct. Still no luck. However I figured out more about my problem. It appears I can use all desktop items freely UNTIL I try to highlight. No matter where on my screen, If I highlight by dragging my mouse, the glitch I described occurs.

---

