---
title: "Serial communication, sending esc char"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by PermNoob on 2012-02-26
so I have a serial device interfaceing with my laptop on ttyUSB0.  the device has an onboard serial to usb adapter, so it is recognized as a serial device.  I have sucesfully used minicom and cutecom to listen to the device and see the expected output in the terminal.  However to change the settings on hte device i must send the esc key followed by the command.  an example of what I want to do is send 

<ESC> R 1 <space>

how do i get that esc command passed along? can I do it with either of these programs?  I am a complete newb so please make no assumptions and feel free to talk to me like I am an idiot, but seeing as how i was able to configure both of those programs at least I am capable of learning.

Thank you so much for any help folks!

---

### Post by PermNoob on 2012-02-28
bumping this back up, is this the right forum?  I am an absolute beginner, but this is kind of a specialized question i guess.

---

### Post by HermanAB on 2012-02-28
You can use Cutecom in Hex mode and then send Esc as 1B.

---

