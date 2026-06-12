---
title: "USB reading in c++"
date: 2008-09-10
forum: Programming Talk
---

### Post by kaspar_silas on 2008-09-10
I was hoping to use a serial to USB lead to make a simple data acquisition system. 

I am looking to sample a 0-3v signal at say 4hz writing to an ascii file.

Has anyone any idea how to in c++ actually sample a signal from a USB. 

Any help is greatly appreciated

---

### Post by Zugzwang on 2008-09-10
Note that those converters will only function properly if the input to them follows the protocol. And "0-3v" doesn't seem to be of that type. You will almost surely need additional electronics on the hardware side (like an OP-amp for amplifying data and a some device sending TxD signals at 4hz). And this will only capture digital data. You can however buy off-the-shelf hardware for analog sampling.

Apart from that you can just install the usb-serial driver correctly and read from that port like from a file. See here: [http://www.linux-usb.org/USB-guide/x356.html]("http://www.linux-usb.org/USB-guide/x356.html")

---

### Post by kaspar_silas on 2008-09-10
I did think I would have to condition the signal somehow but I wasn't expecting quite that much. 

Op-amps, ADCs and so on will probably cost me more than a cheap USB DAQ box. 

O well thanks anyway

---

