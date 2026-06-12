---
title: "MTP device makes everything, well, MTP, crash"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by shatteredmindofbob on 2008-10-11
I recently picked up a Phillips GoGear which as I understand uses the MTP protocol. I had it working perfectly with Gnomad2 then after transferring a bunch of songs and disconnecting, I can not longer reconnect it without any program that accessing MTP crashing. 

Gnomad2 will load for a second then immediately shut down (segfault, according to the terminal display) Same with Banshee and Amarok will also crash if I try to access the GoGear...um, anyone have any idea what's going on? 

As I said, it worked perfectly and now anything that tries to access it crashes. Does anyone have any idea what happened?

---

### Post by shatteredmindofbob on 2008-10-12
Here's the full terminal message from Gnomad2 crashing if it helps:

PTP: Opening session
PTP_ERROR_IO: Trying again after re-initializing USB interface
Clearing stall on IN endpoint
Clearing stall on OUT endpoint
PTP: Opening session
Segmentation fault

---

