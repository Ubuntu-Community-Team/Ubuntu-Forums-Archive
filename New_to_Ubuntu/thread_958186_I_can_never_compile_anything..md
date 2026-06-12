---
title: "I can never compile anything."
date: 2008-10-25
forum: New to Ubuntu
---

### Post by Rovdjur on 2008-10-25
Compiling for me never seems to work, I always get some type of error and it is annoying :-/

Yes, I have the build-essentials and everything else installed!

I have a Lenovo X300 and the sound does not work so I need to compile a more recent version of the ALSA drivers.

The ./configure seems to work fine, but once I try to compile the drivers, I get this:

> copying file alsa-kernel/pci/emu10k1/emu10k1_main.c
patching file emu10k1_main.c
Hunk #4 succeeded at 1408 with fuzz 2 (offset 3 lines).
Hunk #5 FAILED at 1441.
Hunk #6 succeeded at 1761 (offset 15 lines).
1 out of 6 hunks FAILED -- saving rejects to file emu10k1_main.c.rej
make[3]: *** [emu10k1_main.c] Error 1
make[3]: Leaving directory `/home/rovdjur/alsa-driver/pci/emu10k1'
make[2]: *** [prepare] Error 1
make[2]: Leaving directory `/home/rovdjur/alsa-driver/pci'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/rovdjur/alsa-driver'
make: *** [include/sndversions.h] Error 2
rovdjur@rovdjur-laptop:~/alsa-driver$ 


For some reason I get a similiar error no matter what I try to compile on both my laptops (the X300 and the T60p)

Can anyone tilt me in the right direction?

Thanks.

---

### Post by WRDN on 2008-10-25
The first thing you should do is ensure you have the build-essential package(s) installed:

```
sudo apt-get install build-essential
```

EDIT: Sorry, I missed the comment that you had it installed.

---

### Post by philinux on 2008-10-25
> **WRDN said:**
> The first thing you should do is ensure you have the build-essential package(s) installed:

```
sudo apt-get install build-essential
```


He already has it installed.

---

### Post by mister_pink on 2008-10-25
The first issue there is that a patch is failing to apply. This is most likely because its not meant to be applied against that version. 

The second thing seems to be missing dependencies. Have you checked to make sure you have them all? Often you need the -dev package too. You could try
sudo apt-get build-dep alsa

---

