---
title: "Problem with sound"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by chezerian on 2008-07-24
Hi 

I compiled kernel 2.6.25.10 using the instructions from the master kernel thread and now I've got no sound. I think it's because when setting up the config file I forgot to tick ALSA and Intel HD under PCI devices. 
With subsequent kernel compilations I've ticked both and sound works so how would I go about fixing it?

---

### Post by tzulberti on 2008-07-26
You may check the following things:
alsamixer: to see if the sound card was detected
asoundconf list: to see list of sound cards you have configurated.

---

