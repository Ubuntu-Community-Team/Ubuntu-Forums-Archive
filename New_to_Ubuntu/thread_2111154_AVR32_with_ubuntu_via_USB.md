---
title: "AVR32 with ubuntu via USB"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by kazukazu on 2013-02-01
hello all,

it is my first posting here,
I would like to ask if anybody have experienced connecting avr32 to Ubuntu via USB,

I tried to send data to avr32 trough the usb,
the board itself is not custom,

the reference said the ubuntu will recognize the usb as cdc_acm, but there is no ttyACM created when I plugged the usb connection,

I find in some forum, it will be possible that I have to enable the ttyACM manually,
so I am trying to find which USB address is my board connected to,

by trying to unplug and plug the usb connection and check in kernel message with dmesg.

but seems when I check it
(comparing the log file before and after plug )there nothing different or nothing change in kernel message,

is this mean there is something broken in usb connection, I am not sure about this, whether the usb on the go on chip in avr is not fully configure or there is some broken connection on the board?

any answer will be appreciated for me to start my investigation

thank you in advance

regards
kazu

---

