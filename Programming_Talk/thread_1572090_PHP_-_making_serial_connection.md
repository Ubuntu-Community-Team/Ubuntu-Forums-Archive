---
title: "PHP - making serial connection"
date: 2010-09-10
forum: Programming Talk
---

### Post by MN Noob on 2010-09-10
I know I can use fopen, but the problem is you have to know which tty to use. (i.e. it may be ttyUSB0 or ttyUSB1) I may not always have this information, nor do I feel like making sure I always have the right one. In addition, I am planning on using this software at a few places, and so I need it to be as smart as possible.

I saw there is a serial class [here]("http://phpclasses.elib.com/package/3679-PHP-Communicate-with-a-serial-port.html"), but it is for PHP4. Does anyone know of a new php class for accessing a usb device.

Here is what it would need to do, determine if any USB devices are connected (I can extend the class to determine if it is my hardware), read data, and write data. Not sure, besides PHP, what would make a difference, but it would need to work with PHP 5.3, Apache 2.0, and Ubuntu 10.04.

Or will the class I mentioned be able to do that? (has anyone used it before?)

---

