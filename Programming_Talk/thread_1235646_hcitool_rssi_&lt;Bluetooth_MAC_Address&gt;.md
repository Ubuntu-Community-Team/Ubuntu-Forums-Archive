---
title: "hcitool rssi &lt;Bluetooth MAC Address&gt;"
date: 2009-08-09
forum: Programming Talk
---

### Post by eng_akyq on 2009-08-09
:confused:I wonder what is the unit of RSSI here and actually what is RSSI in Bluetooth technology.
I only know that it's Received Signal Strength Indicator.
I could not find any documentation about hcitool in details.
Please help me to find one:(

---

### Post by eng_akyq on 2009-08-09
I only found the source code of hcitool from [www.bluez.org](www.bluez.org) with just some comments without any detailed explanations.

---

### Post by eng_akyq on 2009-08-12
Don't worry guys, as I used from this forum.
I only get help from the web search and little bit hard work searching.
hcitool uses HCI , I think so, so hcitool rssi uses HCI_Read_RSSI and it's related to the Golden Receive Range.
If you want to find more check this book: Bluetooth: Operation and Use by Robert Morrow.
You can read this book for free from Google Books

---

