---
title: "Console over serial port"
date: 2006-06-01
forum: Programming Talk
---

### Post by Peepsalot on 2006-06-01
I have a project in mind to create a device that acts like a sort thin client or dumb terminal (don't know the exact terminology), using a PS/2 keyboard, LCD character display, and PIC microchip to interface these with a serial port on my ubuntu box.

I'm fairly new to microchip programming but I think I can handle this.  I'm just a little confused on the nature of the data will be sent/received over this port.  I haven't ever done anything involving the serial port in linux.

My question is how would I link the output and input of a console (tty1 for example) to a serial port.  I would like to do this(if possible) in a way that I could still switch to this terminal and use my normal monitor and keyboard at the same console.

Also what is the protocol like for character output?

---

### Post by IYY on 2006-06-01
You could try using Kermit (sudo apt-get install kermit). I use it to connect to another machine through the serial port as a client, but I think it can also act as a server (I know it can be used to send files over the serial port, I've done this as well).

---

