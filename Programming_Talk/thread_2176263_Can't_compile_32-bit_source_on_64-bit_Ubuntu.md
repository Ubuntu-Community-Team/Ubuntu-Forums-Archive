---
title: "Can't compile 32-bit source on 64-bit Ubuntu"
date: 2013-09-23
forum: Programming Talk
---

### Post by sumigamer on 2013-09-23
Hey guys, I have a really peculiar problem. I am trying to install some drivers (for my Xilinx board on Ubuntu 12.10, usb-driver-HEAD.tar.gz), but it just throws an error on my 64-bit system. Since its a 32 bit source package, it asks me to use 'make lib32', which I promptly do, after which I get the following lines of errors:
```

make LIBVER=32 clean all
make[1]: Entering directory `/home/sumit/Documents/usb-driver-HEAD-2d19c7c'
rm -f libusb-driver.so libusb-driver-DEBUG.so
cc -Wall -fPIC -DUSB_DRIVER_VERSION="\"2011-12-12 10:47:45\""  -m32 -DJTAGKEY usb-driver.c xpcu.c parport.c config.c jtagmon.c jtagkey.c -o libusb-driver.so -ldl -lusb -lpthread -L/usr/lib/x86_64-linux-gnu -lftdi -lusb -shared
parport.c: In function ‘parport_transfer’:
parport.c:21:23: warning: variable ‘last_pp_write’ set but not used [-Wunused-but-set-variable]
/usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/libdl.so when searching for -ldl
/usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/libdl.a when searching for -ldl
/usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/libusb.so when searching for -lusb
/usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/libusb.a when searching for -lusb
/usr/bin/ld: cannot find -lusb
/usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/libpthread.so when searching for -lpthread
/usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/libpthread.a when searching for -lpthread
collect2: error: ld returned 1 exit status
make[1]: *** [libusb-driver.so] Error 1
make[1]: Leaving directory `/home/sumit/Documents/usb-driver-HEAD-2d19c7c'
make: *** [lib32] Error 2

```

I have already installed the dev files of all the libraries in the errors thrown and have confirmed their presence and type (32-bit, by using objdump) in /usr/lib32. But its always the same error. My makefile is:
```

CFLAGS=-Wall -fPIC -DUSB_DRIVER_VERSION="\"$(shell stat -c '%y' usb-driver.c |cut -d\. -f1)\"" #-DFORCE_PC3_IDENT -DNO_USB_RESET

LIBS=-ldl -lusb -lpthread

SRC=usb-driver.c xpcu.c parport.c config.c jtagmon.c
HEADER=usb-driver.h xpcu.h parport.h jtagkey.h config.h jtagmon.h

ifeq ($(LIBVER),32)
CFLAGS += -m32
CXXFLAGS += -m32
LDFLAGS += -m32 -L/usr/lib32/
endif

FTDI := $(shell libftdi-config --libs 2>/dev/null)
ifneq ($(FTDI),)
SRC += jtagkey.c
CFLAGS += -DJTAGKEY
LIBS += $(FTDI)
endif

SOBJECTS=libusb-driver.so libusb-driver-DEBUG.so

all: $(SOBJECTS)
	@file libusb-driver.so | grep x86-64 >/dev/null && echo Built library is 64 bit. Run \`make lib32\' to build a 32 bit version || true

libusb-driver.so: $(SRC) $(HEADER) Makefile
	$(CC) $(CFLAGS) $(SRC) -o $@ $(LIBS) -shared

libusb-driver-DEBUG.so: $(SRC) $(HEADER) Makefile
	$(CC) -DDEBUG $(CFLAGS) $(SRC) -o $@ $(LIBS) -shared

lib32:
	$(MAKE) LIBVER=32 clean all

```

In the makefile I added LDFLAGS only after I tried everything else and couldn't think of anything else. Like I said, all the libraries are installed in the /usr/lib32 directory and using -m32 should search for the files automatically. I have tried compiling these drivers on my Ubuntu 12.10, 13.04, both inside and outside VMs, but always get the same result. Please, help me out in case I am doing something wrong.

Thanks in advance!

---

