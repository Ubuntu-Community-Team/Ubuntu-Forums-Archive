---
title: "dell vostro 7570 and fingerprint reader  ubuntu 18.04"
date: 2018-06-21
forum: New to Ubuntu
---

### Post by Dominik_Hartwich on 2018-06-21
hello,
after ```
lsusb
``` i received as follows:

```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 27c6:5301  
Bus 001 Device 002: ID 8087:0a2a Intel Corp. 
Bus 001 Device 004: ID 0c45:6a08 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

installed fingerprint-gui and there is no hardware found ("no devices found").

somebody help?

regards, d

---

### Post by #&amp;thj^% on 2018-06-21
> **Dominik_Hartwich said:**
> hello,
after ```
lsusb
``` i received as follows:

```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 27c6:5301  
Bus 001 Device 002: ID 8087:0a2a Intel Corp. 
Bus 001 Device 004: ID 0c45:6a08 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

installed fingerprint-gui and there is no hardware found ("no devices found").

somebody help?

regards, d

I'm sorry I find no evidence this has a fingerprint scan device.
As not found here: [https://www.dell.com/en-nz/work/shop/business-laptop-notebook-computers/vostro-7570/spd/vostro-15-7570-laptop](https://www.dell.com/en-nz/work/shop/business-laptop-notebook-computers/vostro-7570/spd/vostro-15-7570-laptop)

And here also: [http://laptopmedia.com/laptop-specs/dell-inspiron-7570/](http://laptopmedia.com/laptop-specs/dell-inspiron-7570/)
EDIT: I stand corrected but:
> Security made easy: The optional fingerprint reader with Windows Hello allows you to log in securely with one touch &#8211; no passwords necessary.
 
No mention of the chipset used, so this will be a possible windows only device.
I sounds to me that it is either in the touchpad or the power button.

---

### Post by Holger_Gehrke on 2018-06-21
@1fallen: the link to dell you've given does mention an optional fingerprint sensor under the heading 'Reliable security to back your business', about 3/4 down the page.

@Dominik_Hartwich: a web search for the unnamed USB-Device (search term 'USB 27c6:5301') makes me believe this is a Goodix GF3208 Fingerprint Reader. Sadly, it also makes me think you're out of luck getting this to work.

Holger

---

### Post by Dominik_Hartwich on 2018-06-22
Guys, in fact it is a power button-integrated fingerprint sensor.
@1Fallen, @Holger - thx for explanation. 
regards, D

---

