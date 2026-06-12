---
title: "Udev Rules for multiple USB GSM Modem"
date: 2010-10-20
forum: Philippine Team
---

### Post by denzky on 2010-10-20
Hi sir,

Pa help naman related sa UDEV rules.
May project kasi ako sms gateway using multiple GSM Modem. Ang gamit ko ay Huawei Modem. Ang gusto ko sana mangyari everytime na tanggalin at ikabit ulit ang gsm modem sa ubuntu ma-detect ng ubuntu yung modem at mount nya sa fixed ttyUSB port

e.g.
huawei 1 -> ttyUSB1
huawei 2 -> ttyUSB2

Ang problem ko ay para ma implement ito dapat may unique value ang huawei modem sa isat isa (e.g. vendorID, productID or serial) Ang nakikita ko lang na unique value ng huawei modem ay ang IMEI value nila.

I hope someone can give me some light. Thanks

---

### Post by loell on 2010-10-20
try using **lsusb** on your script, as it gives the vendor ID & product ID, you basically had to parse the output, either on regular expression or simple string match algorithm.

---

### Post by denzky on 2010-10-21
nag nakikita lang ng lsub ay product, vendor and serial.

pareho pareho kasi kaya ang nakikita ko lang na pinagkaiba ay IMEI ID. Paanu ko po kaya pwede gawin na gamitin si minicom para makita yung IMEI tapos yung result ibigay kay udev. thanks

---

