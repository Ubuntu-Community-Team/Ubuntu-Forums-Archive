---
title: "Software installation problems - permission denied"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by nyflyguy on 2008-04-28
I am using Ubuntu 8.04 (duel-boot with Vista) and I'm trying to install some software that will allow me to tether my blackberry pearl with Linux so I can have access to the internet since I can't seem to get my broadcom wireless card to work :mad:

So far I have tried installing Open Motif 2.3 and Xlt, both of which I receive errors after typing "make" in the terminal. "./configure" seemed to work fine, so I don't have any idea what the problem could be. I also tried "make install" after "make" and it says permission denied :confused:

Any suggestions? I'm very new to Linux so sorry if the solution turns out to be really simple.

---

### Post by fenian on 2008-04-28
Try it like this...

> ./configure
make
sudo make install

---

### Post by Michael.Godawski on 2008-04-28
Sudo before the command should do the trick. But first make sure your applications cannot be installed via Synaptic.

---

### Post by nyflyguy on 2008-04-28
Thanks for the quick reply guys. I just tried what was suggested but it didn't work. It no longer says permission denied but I still get errors. Here are the last few lines I get when I type "make"

> 
makestrs.c:736: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
make[2]: *** [makestrs.o] Error 1
make[2]: Leaving directory `/home/jeremy/Blackberry/openmotif-2.3.0/config/util'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jeremy/Blackberry/openmotif-2.3.0/config'
make: *** [all-recursive] Error 1

I also get something very similar when I try "sudo make install"

Any ideas?

---

### Post by nyflyguy on 2008-04-28
Thanks for the quick reply guys. I just tried what was suggested but it didn't work. It no longer says permission denied but I still get errors. Here are the last few lines I get when I type "make"

> 
makestrs.c:736: warning: incompatible implicit declaration of built-in function ‘strlen’
make[2]: *** [makestrs.o] Error 1
make[2]: Leaving directory `/home/jeremy/Blackberry/openmotif-2.3.0/config/util'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jeremy/Blackberry/openmotif-2.3.0/config'
make: *** [all-recursive] Error 1

I also get something very similar when I try "sudo make install"

Any ideas?

---

