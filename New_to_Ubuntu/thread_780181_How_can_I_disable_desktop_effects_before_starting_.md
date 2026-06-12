---
title: "How can I disable desktop effects before starting a game?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by the8thstar on 2008-05-03
Hello,

I have installed Warcraft 3: ROR and TFT on my machine. The game runs fine under the lastest version of Wine. However, I'm experiencing terrible flicker artefacts when the desktop effects are on.

So, my question is: is there a way to get a script that does the following:

1. Turn desktop effects off
2. Start the game
3. Turn the effects back on when the game exits

Alternatively, is there a tweak to make everyone happy and keep playing with the desktop effects activated?

Thanks for your timely answer.

---

### Post by lswest on 2008-05-03
well, you can write a script that does this:
metacity --replace (kills compiz)
wine [game]
then you will have to figure out a way to tell it to run "compiz --replace" when the game ends, i'm not sure on how to do that.

---

### Post by the8thstar on 2008-05-03
Thanks **lswest**. I will try and put these instructions into an .sh file to see how I can roll these on.

---

### Post by lswest on 2008-05-03
no problem, and thanks for the thanks.  But i'm not sure how well it would work in a script, since the metacity --replace keeps the terminal open, i'm not sure if you'll be able to run any commands after that.  I just manually type it into a console when i start a game (i hardly ever do that though).  Well, good luck, and maybe someone else on the forum who has more skills with BASH than i do can help you out.

hope it goes well,
Lswest

---

### Post by linfidel on 2008-05-03
> **lswest said:**
> no problem, and thanks for the thanks.  But i'm not sure how well it would work in a script, since the metacity --replace keeps the terminal open, i'm not sure if you'll be able to run any commands after that.  I just manually type it into a console when i start a game (i hardly ever do that though).  Well, good luck, and maybe someone else on the forum who has more skills with BASH than i do can help you out.
  
Usually you can put a trailing ampersand to run the program in the background, like this:
metacity --replace&

Then, I believe, you can close the terminal and the program will continue to run.

---

### Post by lswest on 2008-05-03
> **linfidel said:**
> Usually you can put a trailing ampersand to run the program in the background, like this:
metacity --replace&

Then, I believe, you can close the terminal and the program will continue to run.

hmm, that might solve the problem of trying to run multiple commands afterwards in the same terminal, silly me, i should have thought of that.

---

### Post by dondad on 2008-05-03
> **the8thstar said:**
> Hello,

I have installed Warcraft 3: ROR and TFT on my machine. The game runs fine under the lastest version of Wine. However, I'm experiencing terrible flicker artefacts when the desktop effects are on.

So, my question is: is there a way to get a script that does the following:

1. Turn desktop effects off
2. Start the game
3. Turn the effects back on when the game exits

Alternatively, is there a tweak to make everyone happy and keep playing with the desktop effects activated?

Thanks for your timely answer.



You could also install the compiz icon. It lets you select metacity/compiz as well as the decorator.

---

### Post by linfidel on 2008-05-03
> **lswest said:**
> hmm, that might solve the problem of trying to run multiple commands afterwards in the same terminal, silly me, i should have thought of that.
Sometimes the simple solutions are forgotten.  :)

---

