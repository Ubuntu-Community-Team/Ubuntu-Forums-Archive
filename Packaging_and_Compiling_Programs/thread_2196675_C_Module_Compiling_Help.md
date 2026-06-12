---
title: "C Module Compiling Help"
date: 2013-12-30
forum: Packaging and Compiling Programs
---

### Post by G4dget on 2013-12-30
I have a pinnacle moviebox usb_b used to plug analog equipment into and then run usb to the computer and have been unable to get it working with Ubuntu. There is no native pre-compiled driver and the only working driver that I know of is for windows xp. Sourceforge has a [driver]("http://sourceforge.net/projects/pinnaclembusb/") that appears to be written in C and ready for compiling into a kernal module but I have no idea how to do that. I know I need header files (which I have) and I think I need to edit the makefile that is included to use the right usb kernal headers. Any help on the best way to go about this would be most appreciated. I am familiar with process of compiling applications from source but not a kernal module.

I am running Ubuntu 10.04 with kernal 3.00-23

[edit]
So I have tried to run what I believe is a generic kernal module makefile to make the .ko. Here is the code in my Makefile
```
obj-m = pmbplay.o
KVERSION = $(shell uname -r)
all:
        make -C /lib/modules/$(KVERSION)/build M=$(PWD) modules
clean:
        make -C /lib/modules/$(KVERSION)/build M=$(PWD) clean
```

The drivers MakeFile consists of 
```
all: pmbplay pmbpipe

pmbplay: pmbplay.o libpmb.o
	gcc -lusb -o pmbplay pmbplay.o libpmb.o

pmbpipe: pmbpipe.o libpmb.o
	gcc -lusb -o pmbpipe pmbpipe.o libpmb.o

pmbplay.o: pmbplay.c
	gcc -c -o pmbplay.o pmbplay.c

pmbpipe.o: pmbpipe.c
	gcc -c -o pmbpipe.o pmbpipe.c

libpmb.o: libpmb.c
	gcc -c -o libpmb.o libpmb.c

clean:
	rm -f *.o pmbplay

```

When I run make it just returns with "nothing to do for all"

I am running these from the directory containing all of the c files from sourceforge in my downloads directory. Do I need to move them for it to work or do I need to make some changes to either of the Makefiles?

Thanks
G4dget

---

