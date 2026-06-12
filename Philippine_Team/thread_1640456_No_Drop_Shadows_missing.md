---
title: "No Drop Shadows missing"
date: 2010-12-07
forum: Philippine Team
---

### Post by mdialogo on 2010-12-07
Guys - tulong naman.  Saan ba sa compizconfig settings mapapalabas ang drop shadows ng mga windows?  Sa window decorator ayaw.  Help!!!

---

### Post by mdialogo on 2010-12-07
bump.

i'm using compiz+emerald as window deco.  hindi ba nagwo-work ang window deco sa emerald?  any thoughts?

---

### Post by oobermensch on 2010-12-09
> **mdialogo said:**
> bump.

i'm using compiz+emerald as window deco.  hindi ba nagwo-work ang window deco sa emerald?  any thoughts?

Well, your title might have been a little misleading. When you say "No Drop Shadows Missing", you're saying in tagalog: "Walang drop shadows ang nawawala", which means meron kang drop shadows. :P

Anyway, I'm not yet a hardcore Ubuntu expert, but I've had some experience with Emerald. First of all, are you using a theme that supports the Emerald decorator? Also, make sure you're using emerald instead of the default window decorator. (Which can be found in System  -> Preferences -> Compizconfig -> Window Decorations

In the Window Decorations menu, make sure that "Command" is replaced by "**emerald --replace**" instead of the default "/usr/bin/compiz-decorator".

If those settings are ok, open your Emerald Theme Manager in System -> Preferences -> Emerald Theme Manager. Then click "Edit Themes", then find the "Frame/Shadows" tab. There you can adjust the shadow settings for windows.

---

### Post by mdialogo on 2010-12-09
Thanks it worked! Sorry sa title, hehe.  

(ps: kapag ba nag reply ako to say thanks, is considered a "bump"? Baguhan sa forum.  Anyway, salamat! :)

---

### Post by oobermensch on 2010-12-10
> **mdialogo said:**
> Thanks it worked! Sorry sa title, hehe.  

(ps: kapag ba nag reply ako to say thanks, is considered a "bump"? Baguhan sa forum.  Anyway, salamat! :)

No problem! ;)

---

