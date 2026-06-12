---
title: "[LUCID] Can't buld v4l-dvb"
date: 2010-05-10
forum: Packaging and Compiling Programs
---

### Post by deadland on 2010-05-10
Hi ubuntu-friends,

when I try to compile the lates v4l-dvb-tree I get the following error-message:

```
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/tama/src/v4l-dvb/v4l/ir-raw-event.o
/home/tama/src/v4l-dvb/v4l/ir-raw-event.c: In function 'ir_raw_event_register':
/home/tama/src/v4l-dvb/v4l/ir-raw-event.c:80: warning: passing argument 1 of 'kfifo_alloc' makes integer from pointer without a cast
include/linux/kfifo.h:37: note: expected 'unsigned int' but argument is of type 'struct kfifo *'
/home/tama/src/v4l-dvb/v4l/ir-raw-event.c:80: warning: passing argument 3 of 'kfifo_alloc' makes pointer from integer without a cast
include/linux/kfifo.h:37: note: expected 'struct spinlock_t *' but argument is of type 'unsigned int'
/home/tama/src/v4l-dvb/v4l/ir-raw-event.c:80: warning: assignment makes integer from pointer without a cast
/home/tama/src/v4l-dvb/v4l/ir-raw-event.c: In function 'ir_raw_event_store':
/home/tama/src/v4l-dvb/v4l/ir-raw-event.c:145: error: implicit declaration of function 'kfifo_in'
/home/tama/src/v4l-dvb/v4l/ir-raw-event.c: In function 'ir_raw_event_handle':
/home/tama/src/v4l-dvb/v4l/ir-raw-event.c:168: error: implicit declaration of function 'kfifo_out'
make[3]: *** [/home/tama/src/v4l-dvb/v4l/ir-raw-event.o] Error 1
make[2]: *** [_module_/home/tama/src/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make[1]: *** [default] Fehler 2
make[1]: Verlasse Verzeichnis '/home/tama/src/v4l-dvb/v4l'
make: *** [all] Fehler 2
```

Any ideas?

---

### Post by deadland on 2010-05-10
Well, well....

I found the solution on my own:

> replace "kfifo_in" with "kfifo_get" and "kfifo_out" with "kfifo_put".

---

### Post by E_lexy on 2010-05-12
Thanks, could have cost me some time to find in my own!:guitar:

---

### Post by mr297 on 2010-05-12
Thanks! I would never have solved this problem otherwise!

---

### Post by deadland on 2010-05-12
You wellcome :)

---

### Post by joebu23 on 2010-05-12
> **deadland said:**
> Well, well....

I found the solution on my own:

replace "kfifo_in" with "kfifo_get" and "kfifo_out" with "kfifo_put". 


I've run into the same problem.  How exactly do you do this?  Currently running into this problem getting the driver to make in mythbuntu.

---

### Post by Professor Ducky on 2010-05-13
Thanks for solving this, what has caused the change in the kfifo_in/out to kfifo_get/put?

To answer your question joebu23, open the file ir-raw-event.c with your favourite text editor and do a find and replace on kfifo_in and replace with kfifo_get and the same with kfifo_out and kfifo_put.

Hope this helps.

---

### Post by joebu23 on 2010-05-13
> **Professor Ducky said:**
> Thanks for solving this, what has caused the change in the kfifo_in/out to kfifo_get/put?

To answer your question joebu23, open the file ir-raw-event.c with your favourite text editor and do a find and replace on kfifo_in and replace with kfifo_get and the same with kfifo_out and kfifo_put.

Hope this helps.

Thanks so much.  I'll give it a try and see what happens.

---

### Post by matt06 on 2010-05-13
Thanks guys.  Still got a few compile warnings, but it works now.

---

### Post by joebu23 on 2010-05-13
I tried this, but it didn't work.  Ended up deleting the v4l-dvb directory and starting from fresh using this:

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

Seems to be working now - I'm not getting the artifacting in the video and odd pops in the audio on HD channels that I was getting with the pre-packaged cx18 driver that came with Mythbuntu 10.04

---

### Post by quequotion on 2010-05-17
> **deadland said:**
> Well, well....

I found the solution on my own:

Did you find that [here](http://ubuntuforums.org/showthread.php?t=1475857)?

---

### Post by deadland on 2010-05-18
Yes

---

