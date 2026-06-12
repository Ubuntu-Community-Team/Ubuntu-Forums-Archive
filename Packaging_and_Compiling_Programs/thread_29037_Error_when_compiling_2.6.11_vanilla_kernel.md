---
title: "Error when compiling 2.6.11 vanilla kernel"
date: 2005-04-22
forum: Packaging and Compiling Programs
---

### Post by krrh on 2005-04-22
make-dpkg halts on the following error:

 CC [M]  drivers/media/video/saa7134/saa7134-dvb.o
drivers/media/video/saa7134/saa7134-dvb.c: In function `dvb_init':
drivers/media/video/saa7134/saa7134-dvb.c:56: error: too few arguments to function `videobuf_dvb_register'
make[5]: *** [drivers/media/video/saa7134/saa7134-dvb.o] Error 1
make[4]: *** [drivers/media/video/saa7134] Error 2
make[3]: *** [drivers/media/video] Error 2
make[2]: *** [drivers/media] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.11.7'
make: *** [stamp-build] Error 2

I've applied the swsusp2 patch, but otherwise this is clean kernel source. Has anyone else run across this problem? I found a bug report on the Debian lists detailing the exact same error, but not fix was offered. 

Thanks.

---

### Post by xenoxaos on 2005-05-19
I had that problem, and seeing as how i dont know what saa7134 and i dont think i need it, i edited .config in gedit and searched for saa7134 and kept them from compiling (i did both of them) just change the =m to an =n  and then make away

---

### Post by wbeck85 on 2005-05-22
[QUOTE=krrh]make-dpkg halts on the following error:

 CC [M]  drivers/media/video/saa7134/saa7134-dvb.o
drivers/media/video/saa7134/saa7134-dvb.c: In function `dvb_init':
drivers/media/video/saa7134/saa7134-dvb.c:56: error: too few arguments to function `videobuf_dvb_register'
make[5]: *** [drivers/media/video/saa7134/saa7134-dvb.o] Error 1
make[4]: *** [drivers/media/video/saa7134] Error 2
make[3]: *** [drivers/media/video] Error 2
make[2]: *** [drivers/media] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.11.7'
make: *** [stamp-build] Error 2

I've applied the swsusp2 patch, but otherwise this is clean kernel source. Has anyone else run across this problem? I found a bug report on the Debian lists detailing the exact same error, but not fix was offered. 

Thanks.[/QUOTE]
 I just ran into the same problem! I wonder if this is an error on the Ubuntu/Debian distros end or some sort of compiler error or a Vanilla Kernel problem. Anyway, Glad to see I'm not the only one with the error. I'm trying to compile the 2.6.11.10 vanilla kernel. xenoxaos, thanks for the tip. Seems simple enough! Yeah, I just hope that saa7134 isn't important....

---

### Post by jerome bettis on 2005-05-22
i got that error a long time ago.  just get rid of all that stuff in the video for linux section when you do the menu config.

---

### Post by jerome bettis on 2005-05-22
[QUOTE=wbeck85], I just hope that saa7134 isn't important....[/QUOTE]

A LOT of stuff in the device drivers section is not for a newer machine.  but it's better to have a working kernel than a small one.  i spent a few weeks removing more stuff each time and i've ended up with an incredibly small and fast kernel and everything still works.

---

