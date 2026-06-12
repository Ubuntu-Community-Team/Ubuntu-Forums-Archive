---
title: "help with terminal dpkg configure"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by anarchy88 on 2008-05-27
Any time i run a sudo apt-get install i get this error
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
I was wondering what i needed to do to fix the problem.  I have just installed moblock and had to add 2 lines to /etc/apt/sources.list in order to get it installed.  I do not believe i screwed anything up while installing anything.  Thanks for any help.

---

### Post by Paqman on 2008-05-27
Have you tried running

```

sudo dpkg --configure -a

```

like it suggests?

---

### Post by anarchy88 on 2008-05-28
wow i wasnt adding the word sudo at the front when i was trying it

---

