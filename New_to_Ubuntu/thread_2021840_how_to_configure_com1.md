---
title: "how to configure com1"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by barrykgerdes on 2012-07-09
I have a com1 on my computer or a prolific USB-Serial converter.
How do I config them to 9600baud No parity 8bits 1stop

stty -F /dev/tty0 -a shows the speed as 38400
stty -F /dev/ttyUSB0 -a shows speed as 115200

Barry

---

### Post by UrFriendlyVirus on 2012-07-10
Hello Barry,

First, are you sure this is Absolutely Beginners Talk? I think it was placed in the wrong forum. Anyway I found a link (You may have already seen it) that might help you out.

**[Check and use Serial Ports]("http://www.cyberciti.biz/faq/find-out-linux-serial-ports-with-setserial/")**

All the Best,
UrFriendlyVirus

---

