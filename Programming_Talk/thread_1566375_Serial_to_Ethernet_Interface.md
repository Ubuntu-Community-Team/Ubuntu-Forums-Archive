---
title: "Serial to Ethernet Interface?"
date: 2010-09-02
forum: Programming Talk
---

### Post by Krupski on 2010-09-02
Hi all,

I'm working on a project that uses a microcontroller to acquire temperature data from an air temperature sensor (ultimately to record temperature change patterns and be able to predict upcoming THERMALS to launch model airplanes into).

The microcontroller has an RS-232 port on it and I communicate with it via a plain text console terminal emulator.

What I WANT to do is instead access the board with a web browser.

I would write code for the microcontroller to generate HTML for simple stuff like drop-down menus, file transfers, etc...

What I need is a way to get the serial port to talk to a web browser?

Any help will be greatly appreciated!

-- Roger

---

### Post by Zugzwang on 2010-09-02
I do see two possibilities:

[LIST=1]
[*]You can run a specialized web server program on the computer that connects to the serial port. That would "mediate" between the browser and the device.
[*]You could use another more sophisticated microcontroller that comes with an ethernet and serial interface and use it as "hardware" mediator, i.e., you plug it between the microcontroller you already have and the ethernet port. Programming it can however be quite some task.
[/LIST]

---

### Post by dwhitney67 on 2010-09-02
Or you can just develop a TCP app that funnels data between the web browser and the serial port.

---

### Post by soltanis on 2010-09-02
Ethernet and TCP/IP are implemented in a stack-like fashion. Writing it all yourself is not only complicated, but likely will not fit on a simple field-programmable microcontroller. Instead, I suggest you write an application on the computer connected to the sensor via a serial port to serve data over its network connection, since this is much easier.

---

