---
title: "USB programming -How can I read &quot;pulses&quot; from it, and how to send pulses by hardware?"
date: 2010-08-12
forum: Programming Talk
---

### Post by Repgahroll on 2010-08-12
Hello there.

I want to read "pulses" via USB, so I have some basic questions:>

1-How do I send a pulse to an USB?
 I know it may be as simple as connecting DATA+ and DATA-, but can I monitor the 5v & Ground connection?; or even connect some external electric wire to the DATA pin in order to be able to use higher resistance wires?

2-How can I read such pulses?
 I need to be able to read these pulses at high frequency (>60Hz) so I can develop a program to register them.

Thanks in advance and sorry my english.

---

### Post by interval1066 on 2010-08-12
Not too sure what you mean by "pulse." If you want to write a pulse generator, you need to solder up some simple hardware, which is outside the scope of this forum. If you want to read to or write from the usbfs you either need a usb client program, or if you are trying to write a driver, you need to create a kernel module. Google "usb_skeleton.c" to a copy of the standard kernel mod framework.

---

### Post by Repgahroll on 2010-08-12
Thanks for your answer.

It's possible to generate it by short circuiting the DATA- and the 5v pins. It's possible to "sniff" the pulse and it looks alright.

However, i have no idea on how to properly track it. usbmon seems a nice module to do this, but it'll be necessary to recompile the kernel to use it :(.

Thanks.

---

### Post by StephenF on 2010-08-12
A USB serial port adapter would be easier to work with. They are cheap, well documented and have control lines in abundance. Well, six on a nine pin interface. Google RS232 for more.

Real USB communications generally go to a microcontroller and then on to whatever peripheral hardware is attached to that.

[http://www.ladyada.net/learn/arduino/index.html](http://www.ladyada.net/learn/arduino/index.html)

---

