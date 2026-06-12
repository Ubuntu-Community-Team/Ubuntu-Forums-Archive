---
title: "Compiling errors on usb reset script"
date: 2014-05-29
forum: Packaging and Compiling Programs
---

### Post by jakke1975 on 2014-05-29
Hi, 

I'm heaving difficulties with my wireless networking. I have a usb-wifi for a better range than my internal wifi card. The problem is that when I reboot, the usb-wifi doesn't pick up any network unless I unplug it and plug it back in. I'm doing this on Ubuntu 14.04 x32.
For this, I found a script that I could launch automatically at logon: [http://superuser.com/questions/141908/how-do-i-reset-an-usb-device-without-unplugging-it-in-linux](http://superuser.com/questions/141908/how-do-i-reset-an-usb-device-without-unplugging-it-in-linux)
I need to compile the script, but it's spitting out errors. I'm not a programmer and I'm kinda lost as to what to do.
These are the errors:

jan@callisto:~/bin$ gcc -lusb usbreset.c -o usbreset
/tmp/ccgZIXxB.o: In function `main':
usbreset.c: (.text+0x1c): undefined reference to `usb_init'
usbreset.c: (.text+0x21): undefined reference to `usb_find_busses'
usbreset.c: (.text+0x26): undefined reference to `usb_find_devices'
usbreset.c: (.text+0x2b): undefined reference to `usb_get_busses'
usbreset.c: (.text+0x5b): undefined reference to `usb_open'
usbreset.c: (.text+0x83): undefined reference to `usb_get_string_simple'
usbreset.c: (.text+0xb4): undefined reference to `usb_reset'
usbreset.c: (.text+0xe8): undefined reference to `usb_close'
collect2: error: ld returned 1 exit status


and the script is:
#include <stdio.h>
#include <usb.h>

int main(void)
{
      struct usb_bus *busses;
      usb_init();
      usb_find_busses();
      usb_find_devices();
      busses = usb_get_busses();
      struct usb_bus *bus;
      int c, i, a;
      /* ... */
      for (bus = busses; bus; bus = bus->next) {
        struct usb_device *dev;
        int val;
        usb_dev_handle *junk;
        for (dev = bus->devices; dev; dev = dev->next) {
          char buf[1024];
          junk = usb_open ( dev );
          usb_get_string_simple(junk,2,buf,1023);
          if ( junk == NULL ){
            printf("Can't open %p (%s)\n", dev, buf );
          } else {
            val = usb_reset(junk);
            printf( "reset %p %d (%s)\n", dev, val, buf );
          }
          usb_close(junk);
        }
      }
}

To compile the package, I tried installing libusb-dev, libusb-1.0.0-dev, otherwise it's giving errors on line 2.
Another solution to reset my usb devices at logon would be very helpful as well :)

Thanks in advance

---

### Post by steeldriver on 2014-05-29
Try placing the library AFTER the source code file on the gcc command line (link order matters)

```

gcc **usbreset.c -lusb** -o usbreset 

```

---

### Post by jakke1975 on 2014-05-29
gosh, I had no idea the answer was so simple :-s
thanks a lot, it compiled flawlessly!

---

