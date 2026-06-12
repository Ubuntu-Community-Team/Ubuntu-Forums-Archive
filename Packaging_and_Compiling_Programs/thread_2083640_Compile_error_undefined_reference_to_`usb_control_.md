---
title: "Compile error: undefined reference to `usb_control_msg'"
date: 2012-11-13
forum: Packaging and Compiling Programs
---

### Post by eldite on 2012-11-13
Hi
 
My first post.  I'm pretty much a complete noob with Linux.   I'm trying to compile and program which I've found.  I'm a professional .Net developer, so have a good development understanding.
 
I'm compiling this program here:
[http://www.gniibe.org/oitoite/ac-power-control-by-USB-hub/hub-ctrl.c](http://www.gniibe.org/oitoite/ac-power-control-by-USB-hub/hub-ctrl.c)
 
This is my makefile:
>  
# build hub-ctrl executable when user executes "make"
hub-ctrl: hub-ctrl.o
 $(CC) $(LDFLAGS) hub-ctrl.o -o hub-ctrl
hub-ctrl.o: hub-ctrl.c
 $(CC) $(CFLAGS) -c hub-ctrl.c
# remove object files and executable when user executes "make clean"
clean:
 rm *.o hub-ctrl


And this is the compiler output
[EMAIL="user@ubuntu:~/usb/src$"]>  
[/EMAIL][EMAIL="user@ubuntu:~/usb/src$"]user@ubuntu:~/usb/src$[/EMAIL][EMAIL="user@ubuntu:~/usb/src$"] make
cc  -c hub-ctrl.c
cc  hub-ctrl.o -o hub-ctrl
hub-ctrl.o: In function `hub_port_status':
hub-ctrl.c:(.text+0xb4): undefined reference to `usb_control_msg'
hub-ctrl.o: In function `usb_find_hubs':
hub-ctrl.c:(.text+0x390): undefined reference to `usb_get_busses'
hub-ctrl.c:(.text+0x455): undefined reference to `usb_open'
hub-ctrl.c:(.text+0x4bc): undefined reference to `usb_control_msg'
hub-ctrl.c:(.text+0x666): undefined reference to `usb_close'
hub-ctrl.c:(.text+0x76d): undefined reference to `usb_close'
hub-ctrl.o: In function `main':
hub-ctrl.c:(.text+0xb11): undefined reference to `usb_init'
hub-ctrl.c:(.text+0xb16): undefined reference to `usb_find_busses'
hub-ctrl.c:(.text+0xb1b): undefined reference to `usb_find_devices'
hub-ctrl.c:(.text+0xbe1): undefined reference to `usb_open'
hub-ctrl.c:(.text+0xcf2): undefined reference to `usb_control_msg'
hub-ctrl.c:(.text+0xd43): undefined reference to `usb_close'
collect2: ld returned 1 exit status
make: *** [hub-ctrl] Error 1
[/EMAIL][EMAIL="user@ubuntu:~/usb/src$"]user@ubuntu:~/usb/src$[/EMAIL][EMAIL="user@ubuntu:~/usb/src$"] 

[/EMAIL]

Note that I have installed the libusb-dev package to get the usb.h include from the program.
 
I'm sure I'm just doing something stupid.  Would really appreciate your assistance.
 
Cheers,
Henry

---

### Post by ercherramon on 2012-11-13
have installed the build-essential package, libc6-dev and gcc?

after installing these packages and run these commands:

```
wget http://www.gniibe.org/oitoite/ac-power-control-by-USB-hub/hub-ctrl.c

sudo gcc hub-ctrl.c
```

anyway check if the package in C is compatible with your ubuntu distribution.

---

### Post by eldite on 2012-11-13
Thank you, but still an almost identical error message.    I have installed those packages, and ran the commands suggested. 
 
I checked the usb.h file, and I can see those method signatures are there - so can't understand why it is saying 'undefined reference' for them?
 
How can I check the C program is compatible with Ubuntu?
 
Thanks,
Henry

---

### Post by steeldriver on 2012-11-13
I haven't looked at the website, but **undefined reference** is a message from the link phase telling you that it cannot find the actual code module - as well as #including the .h file you usually need to link the corresponding library (unless your LDFLAGS variable does that already?), something like

```
hub-ctrl: hub-ctrl.o
 $(CC) $(LDFLAGS) -o hub-ctrl hub-ctrl.o **-lusb**

```(you will need to check the actual library name). The header file only declares things.

---

### Post by eldite on 2012-11-13
You little honey, that worked a treat.   Any good place I can read up on how all this stuff hangs together?

---

