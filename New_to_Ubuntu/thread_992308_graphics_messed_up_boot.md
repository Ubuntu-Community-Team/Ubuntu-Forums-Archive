---
title: "graphics messed up boot"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Magnus¤4 on 2008-11-24
Recently installed ubuntu 8.10 from a live cd, everything went alright until I downloaded some video drivers (xorg-driver-fglrx) for my ATI Mobility Radeon 9200, since I thought the movie resolution wasnt that good. Then internet stopped working so I restarted. Then, when booting, it said: kinit:no resume image, doing normal boot or something like that, and asked for my Login and password, which didnt work. It just says incorrect password. After some tries It drops down to prompt. Because I read some threads I have tried waiting, repairing broken packages, fix xserver, but nothing works. The thing is that this happened once before when I upgraded from 8.04 to 8.10, and then simply rescued my stored stuff by using the live cd and then reinstalled everything. Does this has to do with the graphics drivers or ? What can I do? Thanx for advice!

---

### Post by alienexplorers on 2008-11-24
How did you load fglrx.  Did you use Envyng or did you do it manually.  I had the same card and I could not get fglrx to work with it.  To fix your problem try booting into recovery mode and when you get to a menu select fix x and the select continue boot.  If it boots up fine then try restarting.  If not, hit ctrl+alt+F1 and login.  Shutdown gdm using sudo /etc/init.d/gdm stop.  Run if loaded sudo envyng -t.  Use this to remove the driver.  If envyng is not loaded the load sudo apt-get install envyng-core and run the last section.  This should get you back to vesa.

BTW- I ended up using the alternate drivers.

---

### Post by Magnus¤4 on 2008-11-25
thanks for the help. Actually I don´t know what envyng means.., I just downloaded it with the help of synaptics package manager, and did nothing more. 

I did the things you wrote. sudo apt-get install envyng-core worked almost alright, some "archives" missing. Didn´t work to do
sudo envyng -t then.

maybe some help??:

when I type startx:
Backtrace:
0: /usr/bin/x11/X(xf86Sighandler+0x79) [0x80c3009]
1: [0xb8000400]
2: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7a80b07]
3: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7a4e55a]
4: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7a514fc]
5: /usr/bin/x11/X(InitOutput+0x96f) [0x80aac9f]
6: /usr/bin/x11/X(main+0x279) [0x8071b19]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c07685]
8: /usr/bin/x11/X [0x8071101]
Saw signal 11. Server aborting.
giving up.
xinit: Connection refused (errno 111):  unable to connect to X server
xinit: No such process (errno 3):  Server error.


What do you mean by alternate drivers? The ones that comes with the distribution. Can you get good quality with those.

thanx!

---

