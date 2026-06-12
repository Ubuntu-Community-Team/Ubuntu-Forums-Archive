---
title: "hibernate problems"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by gameryoshi600 on 2008-05-08
hi
i am using a compaq presario v6000 with hardy heron installed. when i hibernate there is a black screen. then i click a key. it does not resume. help appreciated

---

### Post by glennric on 2008-05-08
After attempting to hibernate can you post the output of 
```
cat /var/log/pm-suspend.log
```

---

### Post by gameryoshi600 on 2008-05-08
Heres the output:
```
Thu May  8 18:44:36 EDT 2008: running hibernate hooks.
===== Thu May  8 18:44:36 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Thu May  8 18:44:36 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Thu May  8 18:44:36 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Thu May  8 18:44:36 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
===== Thu May  8 18:44:36 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Thu May  8 18:44:36 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Thu May  8 18:44:36 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Thu May  8 18:44:37 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Thu May  8 18:44:37 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Thu May  8 18:44:37 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Thu May  8 18:44:37 EDT 2008: done running hibernate hooks.

```

---

### Post by glennric on 2008-05-08
Hmm, not a lot of help there.  I was hoping there would be an error in there.

---

### Post by gameryoshi600 on 2008-05-08
oh.. i am going to attempt a hibernate.

---

### Post by glennric on 2008-05-08
So when you hibernate the computer does it power off, or does it just stop at a black screen and never power off after waiting for a while?  Or does the black screen occur when you power it back on.

---

### Post by gameryoshi600 on 2008-05-08
hmm this time i did it it actually worked but there was some little white bar on top of my panels and such.. it works now apparently.. so its solved

---

### Post by glennric on 2008-05-08
Wait!  Answer the question I asked before about when the black screen appears.  This may be related to the white bar you saw.  Also, is there some flickering and such after resuming?

Also, what video card does that computer have?

---

