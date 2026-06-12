---
title: "where do programs get &quot;installed&quot; to?"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by navidad on 2008-04-23
Solution: type "which PROGRAM_NAME" in the terminal to find it's location


First post here, so be gentle :)

Just booted up Ubuntu for the first time a few hours ago. I'm trying to go with a lightweight setup, and have openbox and pypanel running right now.

I wanted to give Kazehakase a try as a browser, so I ran:
   [COLOR="Navy"]sudo aptitude install kazehakase[/COLOR]

Afterwards, it was easy enough to type "kazehakase" from the terminal to start it up. Now I want to add it to the openbox right-click menu, and all of a sudden I get stumped. I truly have no idea which folder I should even start looking through to find kazehakase (sad I know)... usr, etc, var, sys, opt, ...??

Is there maybe a guide somewhere on these forums to show what kinds of things get put into all these folders?

Thanks!!

---

### Post by Monicker on 2008-04-23
> **navidad said:**
> First post here, so be gentle :)

Just booted up Ubuntu for the first time a few hours ago. I'm trying to go with a lightweight setup, and have openbox and pypanel running right now.

I wanted to give Kazehakase a try as a browser, so I ran:
   [COLOR="Navy"]sudo aptitude install kazehakase[/COLOR]

Afterwards, it was easy enough to type "kazehakase" from the terminal to start it up. Now I want to add it to the openbox right-click menu, and all of a sudden I get stumped. I truly have no idea which folder I should even start looking through to find kazehakase (sad I know)... usr, etc, var, sys, opt, ...??

Is there maybe a guide somewhere on these forums to show what kinds of things get put into all these folders?

Thanks!!


Run this from a terminal:  which kazehakase

/usr/bin is the most likely location, or /usr/local/bin.

---

### Post by navidad on 2008-04-23
Ha, 2 seconds later, I answer part of my own question. All I had to put in the openbox menu was "kazehakase". I didn't actually have to find anything.

I still would like to know what all these folders are used for though.

---

### Post by SunnyRabbiera on 2008-04-23
applications are usually installed to usr/bin or sometimes usr/lib and maybe /opt.

as for how the linux folder structure its pretty easy to figure out.
bin= Binary files
usr= user
opt= optional
tmp= temporary
lib= libraries
sys= system
share= shared files
dev= development

---

### Post by navidad on 2008-04-23
> **Monicker said:**
> Run this from a terminal:  which kazehakase

/usr/bin is the most likely location, or /usr/local/bin.

Wow, that was the fastest response I've ever seen on forums. I love this place. Thanks!

---

