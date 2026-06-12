---
title: "How to send SMS using micromax 352g"
date: 2012-07-21
forum: New to Ubuntu
---

### Post by apurbapaul0 on 2012-07-21
Hi
I am using micromax 352g usb modem to connect internet. I want to send and receive SMS using the same. Also I want to be able to dial some no like *121# to know the balance and validity. Since without knowing this I browse net for a long time, I may run out of data usage and lots of money will be deducted from my balance.
Please tell me if there is any software to do this job?

Thanks in advance
Apurba

---

### Post by chandra2730 on 2012-09-23
Open terminal
type the following codes
"sudo gedit /etc/modules"

and then at the end of the line
type this

"usbserial
option"




and then restart your computer and connect the modem
then you'll see your modem
now create a new mobile broadband profile clicking on the edit connections and add new on mobile broadband tab
you must put RIGHT APN for your carrier


for
Indian carriers


TATA DOCOMO=tata.docomo.internet
AIRTEL=airtelgprs.com
AIRCEL=aircelweb
BSNL=bsnlnet
VODAFONE=www
VIRGIN MOBILE=vinternet.in





---------THIS WORKS FOR MY MICROMAX 352G MODEM WITH UBUNTU 12.04.

---

