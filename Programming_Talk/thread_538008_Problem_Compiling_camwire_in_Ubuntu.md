---
title: "Problem Compiling camwire in Ubuntu"
date: 2007-08-29
forum: Programming Talk
---

### Post by jrojfer on 2007-08-29
Hi all,
I am trying to compile desperately camwire to try to acquire images from a camera based on firewire (I have already used Coriander but I have some problems) and I would like to compile this API which comes with a cammonitor to display the images in real time...

Well, ieee1394 ohci1394 video1394 and raw1394 modules are loaded... Devices are created and I have installed (I think) libdc1394,... 

```
javier@javier-ubuntu:~/FIREWIRE/camwire-0.8.0$ lsmod |grep 1394
dv1394                 20696  0 
video1394              19672  0 
raw1394                30328  0 
ohci1394               36528  2 dv1394,video1394
ieee1394              299448  5 dv1394,sbp2,video1394,raw1394,ohci1394

javier@javier-ubuntu:~/FIREWIRE/camwire-0.8.0$ ls -l /dev/raw1394
crw-rw-rw- 1 root disk 171, 0 2007-08-29 11:47 /dev/raw1394

javier@javier-ubuntu:~/FIREWIRE/camwire-0.8.0$ ls -l /dev/video1394/*
crw-rw-rw- 1 root video 171, 16 2007-08-29 11:47 /dev/video1394/0
crw-rw-rw- 1 root video 171, 17 2007-08-29 11:47 /dev/video1394/1

```

I get this error when I type make...

```
javier@javier-ubuntu:~/FIREWIRE/camwire-0.8.0$ make
make -C src
make[1]: se ingresa al directorio `/home/javier/FIREWIRE/camwire-0.8.0/src'
make[1]: No se hace nada para `library'.
make[1]: se sale del directorio `/home/javier/FIREWIRE/camwire-0.8.0/src'
make -C tools
make[1]: se ingresa al directorio `/home/javier/FIREWIRE/camwire-0.8.0/tools'
gcc -c -D CAMWIRE_DEBUG -O2 -Wall -W -I../src  -I/usr/include -I/usr/src/linux-headers-2.6.20-16-generic/include/config/ unlisten_1394.c -o unlisten_1394.o
unlisten_1394.c: En la función ‘main’:
unlisten_1394.c:64: error: ‘VIDEO1394_IOC_UNLISTEN_CHANNEL’ no se declaró aquí (primer uso en esta función)
unlisten_1394.c:64: error: (Cada identificador no declarado solamente se reporta una vez
unlisten_1394.c:64: error: ara cada funcion en la que aparece.)
make[1]: *** [unlisten_1394.o] Error 1
make[1]: se sale del directorio `/home/javier/FIREWIRE/camwire-0.8.0/tools'
make: *** [tools] Error 2

```
Question is, VIDEO1394_IOC_UNLISTEN_CHANNEL shoud be defined in video1394.h that is located in /usr/src/linux-headers-2.6.20-16-generic/include/config/ieee1394
but I could check some files there are empty:

```
javier@javier-ubuntu:~/FIREWIRE/camwire-0.8.0$ ls -l /usr/src/linux-headers-2.6.20-16-generic/include/config/ieee1394
total 12
drwxr-xr-x 3 root root 4096 2007-08-20 15:01 config
-rw-r--r-- 1 root root    0 2007-06-07 19:47 dv1394.h
-rw-r--r-- 1 root root    0 2007-06-07 19:47 eth1394.h
drwxr-xr-x 3 root root 4096 2007-08-20 15:01 extra
-rw-r--r-- 1 root root    0 2007-06-07 19:47 ohci1394.h
drwxr-xr-x 2 root root 4096 2007-08-20 15:01 oui
-rw-r--r-- 1 root root    0 2007-06-07 19:47 pcilynx.h
-rw-r--r-- 1 root root    0 2007-06-07 19:47 rawio.h
-rw-r--r-- 1 root root    0 2007-06-07 19:47 sbp2.h
-rw-r--r-- 1 root root    0 2007-06-07 19:47 video1394.h
javier@javier-ubuntu:~/FIREWIRE/camwire-0.8.0$ 
```

Anybody knows why are they empty? Any clue how could I fix it? I don't know what to do...

Thanks to everybody just for reading till here, and if you are thinking a bit of it thanks again and if you are going to reply me THANKS!

JRF

---

### Post by daniel.hauagge on 2007-10-25
Hi,

I'm having the exact same problem here trying to compile camwire on ubuntu. 

Have you tried OpenCV? It has a simple interface for capturing images from webcam.

---

### Post by stuporglue on 2007-10-26
> make[1]: se sale del directorio `/home/javier/FIREWIRE/camwire-0.8.0/src'
make -C tools

I came across this as I was trying to get some other stuff to work...camwire didn't work for me either, but I got it to compile. 

1) Edit Makefile.common like the readme says. 
 I changed line 30 to point to /usr/src/linux, which is where I linked my header files
 # Location of ieee1394/video1394.h:
INCS += -I/usr/src/linux/include/config/

2) The compile is failing on the camwire tools, which I don't think you need to just use the program, it probably depends what you want to do. Since I didn't need them, I removed the TOOLS line of the install section of the Makefile (not Makefile.common). 

I had to create the /usr/local/share/linux directory structure, but then "sudo make install" worked for me. 

Don't forget that /usr/local/linux/bin isn't going to be in your path, so you won't be able to say "cammonitor" after installing

If you need the tools, I'm not sure what to say. 

Hope that helps

---

