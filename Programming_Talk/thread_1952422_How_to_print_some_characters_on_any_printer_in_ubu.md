---
title: "How to print some characters on any printer in ubuntu?"
date: 2012-04-04
forum: Programming Talk
---

### Post by Gurmeet Singh on 2012-04-04
Hello,

I am working on to develope a printer driver on ubuntu for 24-pin DMP using CUPS.
I have to print some characters or junk characters if xxx printer is not attached and attached printer is from other vendor (**Non - xxx. xxx is printer for which i am developing driver**).

Is it possible? if yes then please help me to move in right directly. I have to implement it for three interfaces (usb/serial/parallel):confused:

Thanks in advance.

---

### Post by CynicRus on 2012-04-04
Maybe cups notification interface may help you.

See: [http://linux.die.net/man/7/notifier]("http://linux.die.net/man/7/notifier")

But im not sure.

---

