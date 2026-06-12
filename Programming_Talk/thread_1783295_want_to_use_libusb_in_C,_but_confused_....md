---
title: "want to use libusb in C, but confused ..."
date: 2011-06-15
forum: Programming Talk
---

### Post by cjh19460 on 2011-06-15
I'm running ubuntu, have  done web search, but find conflicting/confusing information regarding the use of libusb -

first, I have done the following:

apt-get install libusb-dev
apt-get install libusb-1.0-0-dev

I have not been able to find a description of what the difference is between these, of why I need both, or what they really are - can someone illuminate?

second, looking at online examples, I see different function name prefixes some "usb_" some "libusb_", for example:

usb_get_device_list()
libusb_get_device_list()

is one deprecated?  or are they for different libraries?

third, when I search my computer I find /usr/include/usb.h but no libusb.h.  Again, I hve seen online examples with:

#include <libusb.h>

but is that really for real?  Is it maybe deprecated?

fourth, when I build with gcc what library option to I use?  -lusb? -llibusb?

Ultimately my goal is to use the libusb functions to extract the manufacturer, product and serial number strings.

Thanks in advance -
Carl

---

### Post by ian dobson on 2011-06-15
Hi,

I think you just need usb.h

Have a look here [http://www.linuxquestions.org/linux/answers/Programming/Developing_Linux_Device_Drivers_using_Libusb_API](http://www.linuxquestions.org/linux/answers/Programming/Developing_Linux_Device_Drivers_using_Libusb_API)

Regards
Ian Dobson

---

