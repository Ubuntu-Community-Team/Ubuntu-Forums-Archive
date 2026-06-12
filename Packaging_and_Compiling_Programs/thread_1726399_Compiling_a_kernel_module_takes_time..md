---
title: "Compiling a kernel module takes time."
date: 2011-04-11
forum: Packaging and Compiling Programs
---

### Post by moma on 2011-04-11
Hello,
I want to compile a kernel module for my old laptop. The module's source code is here.
[http://www.amilo-forum.com/topic,929,105,-linux-on-amilo-li-1718.html](http://www.amilo-forum.com/topic,929,105,-linux-on-amilo-li-1718.html)

I repeat the instructions here:
```
wget http://homepage.ntlworld.com/roadrash/lucid/fsam7400-0.5.2.tbz

tar -xvf fsam7400-0.5.2.tbz 

cd fsam7400*

make
```

The compilation seems to stop indefinetly. 

I have also created my own Makefile2. It's this
```
obj-m += fsam7400.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

$ [COLOR="DarkGreen"]make -f Makefile2 [/COLOR]
make -C /lib/modules/2.6.35-28-generic/build M=/home/moma/fsam7400-0.5.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'

Then it stops. I can't see it do anything at all.

I have installed 
$ [COLOR="DarkGreen"]sudo apt-get install build-essential linux-headers-$(uname -r)[/COLOR]

This happens on both Ubuntu 10.10 and Ubuntu 11.04 beta. 
Any tips?

---

### Post by SevenMachines on 2011-04-12
hmm, are you getting any sort of errors? on 11.04 amd64, replacing the Makefile with Makefile2 above i get no problems. try 'makefile -d'

---

### Post by moma on 2011-04-12
Hello,
Thanks for your reply.

As you suggest, it works if I replace the original Makefile content with Makefile2 (see above). Then simply:
$ [COLOR="DarkGreen"]make[/COLOR]

I thought the -f option would do the same thing, 
$ [COLOR="DarkGreen"]make -f Makefile2[/COLOR]
But no success. 

Anyway, I got the module compiled right.
And it actually works (it lit the wireless LED) in Fujitsu Siemens AMILO li 1718.

Installation of fsam7400.ko:
$ [COLOR="DarkGreen"]sudo mkdir /lib/modules/$(uname -r)/extra[/COLOR]
$ [COLOR="DarkGreen"]sudo cp fsam7400.ko /lib/modules/$(uname -r)/extra[/COLOR]
$ [COLOR="DarkGreen"]sudo depmod -a[/COLOR]

Manually loading the module (watch the wifi lamp)
$ [COLOR="DarkGreen"]sudo modprobe fsam7400[/COLOR]

Read also [this posting...]("http://ubuntuforums.org/showthread.php?p=10613592") related to Fujitsu Siemens AMILO Li 1718.

---

### Post by SevenMachines on 2011-04-12
[COLOR=Black]```
$ make -f Makefile2 
```[/COLOR][COLOR=DarkGreen][COLOR=Black]
works normally but i think due to the different way kernel modules build it uses Makefile too, i dont know why, though i would be interested if someone knows or has the time to look :)[/COLOR]
[/COLOR]

---

