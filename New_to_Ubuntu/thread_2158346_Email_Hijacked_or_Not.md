---
title: "Email Hijacked or Not?"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by skaxer on 2013-06-28
Apologies for the thumbs up next to the title

Really old machine built from scrap and Sky boxes
 I have just ran Rkhunter and have come across some Text that i am unsure of and are quite worried about
i may have no reason to however i thought a s being new to Ubuntu best to be safe than sorry.
I have looked around the forums and Google but Laymans terms evade me here goes

1:  [19:35:08] Warning: User 'postfix' has been added to the passwd file.

 2: [19:35:08]   Checking for group file changes                 [ Warning ]     [19:35:08] Warning: Group 'postfix' has been added to the group file.
     [19:35:08] Warning: Group 'postdrop' has been added to the group file.

3:[19:35:08] Warning: Hidden directory found: /dev/.udev


4: [19:35:08] Warning: Hidden file found: /dev/.initramfs: symbolic link to `/run/initramfs'
    [19:35:26]


 Now i do not remember ever loading either PostDrop nor postfix I am just a run of the mill End user from a home P.C
If some one could advise on how i can find out if i did load these two mail programs when i installed 12.04 last week
or if indeed you can do this (load at install) , I would be very grateful. I will try to CD around in the terminal until hopefully i get a reply
to see if i can find any dates of install (postdrop)+(postfix). Thanks for reading and or replying as it is a concern for all novice or pro's
alike as i don't really want stuff going on that i do not know about through my Email accounts..:confused:..

---

### Post by Bucky Ball on 2013-06-28
Welcome to the forums. A concern it is, and might move this to a more suitable sub-category shortly, but for now I advise you to give you thread a more descriptive title ASAP. This will greatly improve your chances of help. Also, try and give a bit more detail; I have no real idea what is going on exactly. Try and explain step by step and include software/relevant hardware info. Good luck.

---

### Post by Frogs Hair on 2013-06-28
See these in the terminal .
 
```
man postfix 
``````
man postdrop
```

---

### Post by deadflowr on 2013-06-28
When you installed rkhunter, did you also install other security type programs, like logwatch?
If so, that would be a start to look at where postfix came from.

---

