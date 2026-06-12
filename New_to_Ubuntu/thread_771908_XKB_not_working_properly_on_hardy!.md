---
title: "XKB not working properly on hardy!"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by DexterLB on 2008-04-28
Yesterday I upgraded to Hardy, but when I logged in, I got the message that tells me of an error in the xkb library. Anyway, I fixed it, but now when I go to System>Preferences>Keyboard, and I click on Layout, set up my second layout (russian phonetic) and go to layout options to set ctrl+shift to change layouts.

BUT it works only for this session. When I restart the PC, it works no more. And when I go to layout options, the tick on "ctrl+shift changes group" is still there. And when I remove it and put it back, again everything starts to function properly.

Question: how can I fix it so it won't require to remove and put again that tick every time I login?

P.S. on Gutsy everything was fine :confused:

---

### Post by DexterLB on 2008-04-28
Is it possible to edit one of the config files and enter something like 'xkboptions grp:ctrl_shift'

---

### Post by DexterLB on 2008-04-28
Halloooooooo!?!?!!??

---

### Post by DexterLB on 2008-04-28
I also discovered that everything fixes when I go to gconf editor, desktop>gnome>peripherials>keyboard>kbd and I change or even click on a key. But no processes start. I think it does something in the operative memory. Any ideas?

---

