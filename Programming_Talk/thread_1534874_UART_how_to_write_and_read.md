---
title: "UART: how to write and read"
date: 2010-07-20
forum: Programming Talk
---

### Post by supernewbbie on 2010-07-20
Hi All,
I'm very very new to Ubuntu and linux in general, but I need to write a sw in C++ in order to set an UART baud rate for input/output, write a byte array and then read it in order to check if UART is communicating correctly. Final system will be embedded but currently I'm testing it on my virtualbox with ubuntu on my PC.

Last thing: i'm using a serialport inverter in order to have output pin on input pin.

My question is the following: how can I test from Console if UART is working fine? 
Some days ago i did something like this:
1) from one console
cat /dev/ttyS0 (it stated in waiting .....)

2) from another console:
echo "something" > /dev/ttyS0 (it wrote out string and Console at  point 1 captured and displayed it correctly)

Unfortunately today it seems above points are not working could someone help me?

---

### Post by StephenF on 2010-07-20
The setserial command is a good place to start looking. Really I can't see any point in going through the source code as it's already a complete solution other than for educational purposes of course.

---

