---
title: "Write to serial modem from the command line"
date: 2009-07-19
forum: Programming Talk
---

### Post by RocketRanger on 2009-07-19
Hi

I'm doing various programming experiments using an Atmel STK500 kit and it would be helpful if there is a simple way of writing to the usb serial port from the command line, similar to how it's possible to pipe its output into cat.

I have tried to do this:
$ sudo echo a | /dev/ttyUSB2

but it tells that I don't have write permission to that port, even though ls -l gives me
crw-rw---- 1 root dialout 188, 2 2009-07-19 18:12 /dev/ttyUSB2

Any ideas?

---

### Post by unutbu on 2009-07-19
Maybe this?
```
echo a | sudo tee /dev/ttyUSB2
```

---

### Post by ahmatti on 2009-07-19
/dev/ttyUSB2 is a file so you don't pipe the output. Instead of | use > .

ie.
```

 echo a > /dev/ttyUSB2

```
 
Also have a look at: [http://www.mm.helsinki.fi/~mpastell/serial.pdf](http://www.mm.helsinki.fi/~mpastell/serial.pdf)

HTH

---

### Post by RocketRanger on 2009-07-19
Thanks. Both work beautifully and thanks for the serial guide. I wasn't able to find that on google!

---

