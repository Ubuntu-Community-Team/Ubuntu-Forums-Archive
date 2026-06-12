---
title: "Hardy Heron Sound Problem"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by andylyon11 on 2008-04-29
Hey people, been using Ubuntu for about 4 weeks now so am very new to it. Liking 99% of it at the mo. I updated to the new version as soon as it was released the other day but now I have a small problem. My sound doesnt go as near as loud as it did do when version 7.10 was installed.

Has anyone else suffered this problem or is it just me? Is there a solution. Any help will be appreciated.

PS. I am running an Acer Aspire 5634 which otherwise works perfectly.

Thanks

---

### Post by mapes12 on 2008-04-29
Open a terminal window and type: alsamixer at the command prompt. Then try setting your sound from there.

---

### Post by andylyon11 on 2008-04-29
Brilliant thanks, this worked, why is it like this in the new version?

---

### Post by mapes12 on 2008-04-29
Cool!

Don't know why Hardy does this but a little tinkering under the hood post upgrade sometimes harmonizes everything.

Good luck.

Mark

---

### Post by Sponzenbroekske on 2008-04-29
TIP: go to system>preferences>control center>sound 
there you can change deault mixer track i changed it to HDA intel and now i can use my keybinds (Fn uparrow, Fn downarrow) for changing the volume, else i was commited to use the alsamixergui.

---

