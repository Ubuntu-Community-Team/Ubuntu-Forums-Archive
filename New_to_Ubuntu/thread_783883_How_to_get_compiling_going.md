---
title: "How to get compiling going?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Hammondman on 2008-05-06
Hi guys,

Here's a very newbie question for you... I am trying to follow some steps I was given to install the ALSA sound drivers.  Seems I'm running into problems when I try to compile  

This is what my terminal gives me:

sudo ./configure --with-cards=hda-intel
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

Can anyone help me out?

Thanks!

---

### Post by Joeb454 on 2008-05-06
Did you install the build-essential package?

```
sudo aptitude install build-essential
```

---

### Post by shadowtroopers on 2008-05-06
Do you have "build-essential"?. I think this is the most important thing we should have in order to compile any programme.

---

### Post by tacutu on 2008-05-06
not a direct answer to your question, but why do you need to compile alsa yourself? Can't you install it from the repositories?

---

