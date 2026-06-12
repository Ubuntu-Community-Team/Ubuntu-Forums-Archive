---
title: "Help with installation on samsung chrome book"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by tony42 on 2014-04-25
HI all newbie here so no tech speak please.

I have followed instruction on how to get ubuntu on my samsung 3 chrome book, however its all goes south when I do the terminal commands of 
sudo sh -e ~Downloads/crouton -t xfce

however its is stating that crosh can't open ~Downloads/crouton 

but it is on my computer

any suggestions please. I've tried several times

---

### Post by Danger_Monkey on 2014-04-25
Well, the tilde '~' means your home directory, usually /home/your_username.  "sh -e" means to run a shell, and exit on the first error it comes to.  So, I would think the line needs to be:
```

sudo sh -e ~/Downloads/crouton -t xfce
-or
sudo sh -e /home/your_username/Downloads/crouton -t xfce

```

I don't know what the crouton options mean.

---

### Post by tony42 on 2014-05-03
got it running thanks, now just trying to get it working. no software centre, typical

---

