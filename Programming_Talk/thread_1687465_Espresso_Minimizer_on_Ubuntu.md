---
title: "Espresso Minimizer on Ubuntu"
date: 2011-02-13
forum: Programming Talk
---

### Post by Justin C. on 2011-02-13
I know it's not technically programming, but I figured that this would be a good place to ask. I'm trying to get the circuit minimization software espresso to run under Ubuntu. Does anyone have any experience doing this? I would appreciate the help.

---

### Post by Zugzwang on 2011-02-14
Actually, Espresso compiles quite well if I remember, but you will need to apply some fixes yourself to the source code.

In particular, there are some "#include"s missing and in some C functions they locally declare that some other function exists. In the latter case, it suffices to move the function declaration out of the function body (and putting it in front of it).

---

### Post by Justin C. on 2011-02-25
I actually ended up finding a pre-made espresso.linux file that runs like a charm from the terminal, so all is well.

---

