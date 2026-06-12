---
title: "Cp Command"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Uchiha_madara on 2008-07-13
what is the main job of the Command :

> cp

example :

while configuration the Alsa Driver
> 
cp /downloads/alsa-*


---

### Post by PmDematagoda on 2008-07-13
It is mainly used to copy files/directories from one place to another.

---

### Post by bumanie on 2008-07-13
You use cp command to rename files also.

---

### Post by PmDematagoda on 2008-07-13
> **bumanie said:**
> You use cp command to rename files also.

Isn't that mv?

Edit:- Whoops, you can do that as well, sorry.

---

### Post by bumanie on 2008-07-13
Hmm, I think you're right now you mention it. Funny I used it only yesterday, it is move. Ignore my above confused post. Sorry. Infact PmDematagoda as you are an admin. - remove it if you like. Brief lapse of memory.

---

### Post by PmDematagoda on 2008-07-13
> **bumanie said:**
> Hmm, I think you're right now you mention it. Funny I used it only yesterday, it is move. Ignore my above confused post. Sorry. Infact PmDematagoda as you are an admin. - remove it if you like. Brief lapse of memory.

No, actually you can do that in a way, for example:-
```
cp -R name-of-source-dir name-of-dest-dir
```
essentially renames the directory(although it also copies the directory, which may be an unwanted after-effect;)).

---

### Post by pmlxuser on 2008-07-13
Another best way f finding what a command does is

$ command --help

OR

$ man command

---

### Post by bumanie on 2008-07-13
Maybe my memory is not so bad after all. I really can't remember which I used, but I did rename a file - I thought I used cp, rather than mv, but now I'm not 100% sure. Either way, you've cleared up any confusion with the above example.

---

### Post by ghost_ryder35 on 2008-07-13
> **pmlxuser said:**
> Another best way f finding what a command does is
$ man command
I do this constantly

---

