---
title: "SMS via USB Dongle"
date: 2012-02-06
forum: Philippine Team
---

### Post by nirvblakr on 2012-02-06
I am presently using a Globe Prepaid Tattoo Sim in an unlocked Huawei E353 and a Huawei E1550.  Since it is a prepaid SIM, sometimes I need to send a text message to Globe to enroll lets say Unlimited Internet for a day or just to check my balance.  The software included in Globe is only Windows based.  I tried downloading the Mobile Partner software for Linux and it doesn't detect any of the 2 USB modems.  Is there any way that I can send and receive text messages via my USB dongle.  BTW, I am using Ubuntu 10.10 (32bit).  Thanks in advance!

---

### Post by loell on 2012-02-06
have you tried using gammu?

[http://tensixtyone.com/perma/howto-send-sms-using-a-huawei-e160g-and-debian](http://tensixtyone.com/perma/howto-send-sms-using-a-huawei-e160g-and-debian)

---

### Post by tech-hero on 2012-02-07
you may also want to try WAMMU. :)

---

### Post by nirvblakr on 2012-02-07
> **loell said:**
> have you tried using gammu?

[http://tensixtyone.com/perma/howto-send-sms-using-a-huawei-e160g-and-debian](http://tensixtyone.com/perma/howto-send-sms-using-a-huawei-e160g-and-debian)

I tried GAMMU.  This is what I got when tried to detect modem:

> nirvblakr@Acer-Ferrari:~$ dmesg|grep tty
[    0.000000] console [tty0] enabled
[    0.936385] tty ptmx: hash matches
[   21.153680] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[   21.153831] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[   21.153963] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2
[   21.174625] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB3
[   21.174806] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB4
[  267.213864] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  267.214105] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  267.214276] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[  267.214473] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  267.215964] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  307.548897] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[  307.549399] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[  307.549826] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB2


When I tried to getallsms, this is what I got:

> nirvblakr@Acer-Ferrari:~$ gammu getallsms
Error opening device, it doesn't exist.


---

### Post by kiminaiseah on 2012-02-14
aralin mu muna basic AT Commands 

para ma intindhan mo ang errors ng wammu at gammu

well i think baka pag na intindihan mo ang AT Commands 

baka mag kannel kana

---

### Post by leeyopanda on 2012-08-26
pa-butt-in ako, medyo out of topic, hindi ko kasi magrasp kung paano ginagamit ang kannel, gammu, at wammu.

can you please enlighten me? thank you. :)

---

