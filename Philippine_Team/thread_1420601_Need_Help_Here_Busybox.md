---
title: "Need Help Here: Busybox?"
date: 2010-03-03
forum: Philippine Team
---

### Post by killer_d76 on 2010-03-03
i was just watching Youtube when all of a sudden i can't seem to open open office and text editor...  i restarted our lappie and choose recovery option on boot manager and here is what i got! (see attached picture) .. please help! this laptop is used by my wife on here work that she bring here at home ;)

thanks in advance!

---

### Post by killer_d76 on 2010-03-03
need help here.. anyone?..  hate to re-install everything :(

---

### Post by loell on 2010-03-03
it's kinda difficult. ;)

time stamp counter, has something to do with the processors clock speed.

probably try the ```
 clocksource=hpet 
``` parameter in the kernel?


[http://kerneltrap.org/node/8306]("http://kerneltrap.org/node/8306")

---

### Post by killer_d76 on 2010-03-04
nothing happened loell..

---

### Post by loell on 2010-03-04
awww,  
the processor is acting up, not really sure what else to suggest. :(

---

### Post by Script Warlock on 2010-03-04
reinstall?:-k

---

### Post by killer_d76 on 2010-03-04
> **Script Warlock said:**
> reinstall?:-k

hehehe.. yup! that fixed the issue! ;)

---

### Post by killer_d76 on 2010-03-05
okey I have solved the issue by re-installing ubuntu... now the question is how can I prevent this to happen again?.. was this cause by the new kernel update to 2.6.28-18?

---

### Post by jepong on 2010-03-08
upgrade ka na kasi sa karmic... im using the same dongle on kubuntu and ok naman. :-D

---

### Post by jepong on 2010-03-08
> **jepong said:**
> upgrade ka na kasi sa karmic... im using the same dongle on kubuntu and ok naman. :-D

wtf? paano 'to napunta d2? sorry guys wrong thread...

---

### Post by Script Warlock on 2010-03-08
baka nilipat ng mods :lolflag:

---

### Post by Ravskie on 2010-03-09
> **killer_d76 said:**
> okey I have solved the issue by re-installing ubuntu... now the question is how can I prevent this to happen again?.. was this cause by the new kernel update to 2.6.28-18?


Sir over clocking ba CPU i mean altered ba ang speed nya o kernel lang talaga upgrade mo ...?

---

### Post by badrra on 2010-03-17
Sakin nangyari na din yan on a wubi installation. The ubuntu boot files got corrupted dahil sa pag manual turn off ng PC lalo na pag seemingly nag hang ubuntu at di makapaghintay, ayun pindutin ng matagal ang switch ng PC hangang mamatay kusa. 

One suggestion is to repair that portion of the disk by doing chkdsk /r on the ubuntu directory only. The other is of course reinstalling ubuntu which sucks hehehehe. 

Solution ko dito? Make it light and simple. Para hindi nag hahang hehehhe.

---

