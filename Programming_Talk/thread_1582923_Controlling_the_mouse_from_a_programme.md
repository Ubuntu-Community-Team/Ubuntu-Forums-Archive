---
title: "Controlling the mouse from a programme"
date: 2010-09-27
forum: Programming Talk
---

### Post by oopsie on 2010-09-27
I want to create a programme that interacts with another programme by controlling the mouse pointer. Moving it about, clicking or holding buttons, and so on.

I've spent some time googling, but it's hard to come up with good results, since I'm not really sure what I'm after. The closest I've found so far is when searching for "mouse emulation", but that was more about recording and replaying actions which isn't what I want.

I need to have pixel perfect control over the mouse.

Does anyone have any suggestions about what would work? Or any pointers about what I should be googling? I'm lost :confused:

Any help would be appreciated

---

### Post by lordhaworth on 2010-09-27
I have never really tried anything like this... 

Python - in particular "Pygame" can work on a pixel-by-pixel basis (of course, game programming is closely tied into controls/the mouse cursor). If I were in your position, but had my own very limited knowledge, I would try pygame first and see what is available.

---

### Post by Jeroensum on 2010-09-27
Take a look at wmctrl and devilspie, those 2 apps should be able to accomplish what you want.

---

### Post by oopsie on 2010-09-27
> **Jeroensum said:**
> Take a look at wmctrl and devilspie, those 2 apps should be able to accomplish what you want.

Thank you Jeroensum and lordhaworth! I know what I was asking was unusual, so thanks for posting!!!

In the end I found what I needed. A nice little programme called "xdotool" looks like it'll do 100% what I need.

It was actually Jeroensum's suggestions that started me indirectly on the trail to what I needed. So double thanks to you! :) I've spent almost three hours today trying to find what I wanted, I was beginning to think it didn't exist.

---

### Post by lordhaworth on 2010-09-27
No problem, shame I couldn't be more help - but I am no expert on this kind of coding. Cheers for posting your findings, I would be interested in taking a look myself... I will be of more use next time someone posts a similar question!

---

