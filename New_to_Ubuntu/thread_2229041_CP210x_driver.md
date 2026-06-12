---
title: "CP210x driver"
date: 2014-06-11
forum: New to Ubuntu
---

### Post by schade2 on 2014-06-11
Hi there!

I'm trying to install this driver as per the directions but it doesn't seem to want to work for me. 

The instructions state:

> Ubuntu: 
1. make ( your cp210x driver ) 
2. cp cp210x.ko to /lib/modules/<kernel-version>/kernel/drivers/usb/serial 
3. insmod /lib/modules/<kernel-version/kernel/drivers/usb/serial/usbserial.ko 
4. insmod cp210x.ko 


The contents of the directory:

> cp210x.c               CP210x_VCP_Linux_3.x.x_Release_Notes.txt
cp210x_gpio_example.c  Makefile

Step 1 gives me this:

> 
schade@W500:~/LinuxDriver$ make
make -C /lib/modules/3.13.0-29-generic/build M=/home/schade/LinuxDriver modules
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-29-generic'
  CC [M]  /home/schade/LinuxDriver/cp210x.o
/home/schade/LinuxDriver/cp210x.c:164:12: error: ‘usb_serial_probe’ undeclared here (not in a function)
  .probe  = usb_serial_probe,
            ^
/home/schade/LinuxDriver/cp210x.c:165:16: error: ‘usb_serial_disconnect’ undeclared here (not in a function)
  .disconnect = usb_serial_disconnect,
                ^
/home/schade/LinuxDriver/cp210x.c: In function ‘cp210x_get_config’:
/home/schade/LinuxDriver/cp210x.c:321:3: error: implicit declaration of function ‘dbg’ [-Werror=implicit-function-declaration]
   dbg("%s - Unable to send config request, "
   ^
/home/schade/LinuxDriver/cp210x.c: In function ‘cp210x_open’:
/home/schade/LinuxDriver/cp210x.c:430:36: error: ‘struct usb_serial_port’ has no member named ‘number’
  dbg("%s - port %d", __func__, port->number);
                                    ^
/home/schade/LinuxDriver/cp210x.c: In function ‘cp210x_close’:
/home/schade/LinuxDriver/cp210x.c:451:36: error: ‘struct usb_serial_port’ has no member named ‘number’
  dbg("%s - port %d", __func__, port->number);
                                    ^
/home/schade/LinuxDriver/cp210x.c: In function ‘cp210x_get_termios’:
/home/schade/LinuxDriver/cp210x.c:534:17: error: invalid type argument of ‘->’ (have ‘struct ktermios’)
    &tty->termios->c_cflag, &baud);
                 ^
/home/schade/LinuxDriver/cp210x.c: In function ‘cp210x_get_termios_port’:
/home/schade/LinuxDriver/cp210x.c:556:36: error: ‘struct usb_serial_port’ has no member named ‘number’
  dbg("%s - port %d", __func__, port->number);
                                    ^
/home/schade/LinuxDriver/cp210x.c: In function ‘cp210x_change_speed’:
/home/schade/LinuxDriver/cp210x.c:706:21: error: invalid type argument of ‘->’ (have ‘struct ktermios’)
  baud = tty->termios->c_ospeed;
                     ^
/home/schade/LinuxDriver/cp210x.c: In function ‘cp210x_set_termios’:
/home/schade/LinuxDriver/cp210x.c:735:36: error: ‘struct usb_serial_port’ has no member named ‘number’
  dbg("%s - port %d", __func__, port->number);
                                    ^
/home/schade/LinuxDriver/cp210x.c:740:22: error: invalid type argument of ‘->’ (have ‘struct ktermios’)
  cflag = tty->termios->c_cflag;
                      ^
/home/schade/LinuxDriver/cp210x.c: In function ‘cp210x_tiocmset_port’:
/home/schade/LinuxDriver/cp210x.c:871:36: error: ‘struct usb_serial_port’ has no member named ‘number’
  dbg("%s - port %d", __func__, port->number);
                                    ^
/home/schade/LinuxDriver/cp210x.c: In function ‘cp210x_tiocmget’:
/home/schade/LinuxDriver/cp210x.c:910:36: error: ‘struct usb_serial_port’ has no member named ‘number’
  dbg("%s - port %d", __func__, port->number);
                                    ^
/home/schade/LinuxDriver/cp210x.c: In function ‘cp210x_break_ctl’:
/home/schade/LinuxDriver/cp210x.c:932:36: error: ‘struct usb_serial_port’ has no member named ‘number’
  dbg("%s - port %d", __func__, port->number);
                                    ^
/home/schade/LinuxDriver/cp210x.c: In function ‘cp210x_init’:
/home/schade/LinuxDriver/cp210x.c:989:2: error: implicit declaration of function ‘usb_serial_register’ [-Werror=implicit-function-declaration]
  retval = usb_serial_register(&cp210x_device);
  ^
/home/schade/LinuxDriver/cp210x.c:996:3: error: implicit declaration of function ‘usb_serial_deregister’ [-Werror=implicit-function-declaration]
   usb_serial_deregister(&cp210x_device);
   ^
cc1: some warnings being treated as errors
make[2]: *** [/home/schade/LinuxDriver/cp210x.o] Error 1
make[1]: *** [_module_/home/schade/LinuxDriver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-29-generic'
make: *** [all] Error 2



I can't tell if those are serious errors or not.

Step 2 results in this:

> schade@W500:~/LinuxDriver$ cp cp210xcl.ko to /lib/modules/3.13.0-29-generic/kernel/drivers/usb/serial
cp: cannot stat ‘cp210xcl.ko’: No such file or directory
cp: cannot stat ‘to’: No such file or directory


So I'm not sure whether I didn't wind up creating **cp210xcl.ko **because of those errors perhaps, or is this a typo because the file in the directory is **cp210x.c** which is really similar.

Anywho, I give up for now. 
Any help would be much appreciated. :smile:

---

