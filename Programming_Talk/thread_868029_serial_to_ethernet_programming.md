---
title: "serial to ethernet programming"
date: 2008-07-23
forum: Programming Talk
---

### Post by Adntu on 2008-07-23
I have a RS232 (ANSI) device connected to the PC using Serial to Ethernet converter.
I have to write a program (c/c++) to connect and write/read data to the device.
please some directions or references.
thanks

---

### Post by cacycleworks on 2008-07-23
That will depend on your development environment and how you utilize it.

The core of it is that you'll need access to hardware addresses, which windblows prevents (and thus the M$ Visual C IDE). Visual C has windows APIs built in, which give you access.

In linux land, you open the port /dev/tty0 (or whatever the rs232 port is) and then open another port on /dev/eth0 and feed the two to each other. If you're in windblows land and doing this for school, root around in msvc for "com port" and "com1" and winsock (or whatever it's called now). You could also try to find the memory map and write an embedded assembly function which handles the IRQ from serial and feeds it to the winsock. IOW, "write a virus". ;)

:) Chris

---

### Post by Adntu on 2008-07-23
my environment is Ubuntu (of course!)
I am not sure that I understand this "feed" trick, you mean I should write a program handling a RS232 port then  redirect the  output of this one to a socket to access the NIC ?!
thanks for your help (thanks also for the Virus :))

---

### Post by cacycleworks on 2008-07-23
Yes, the feeding would be something akin to a "file copy". In php, you open file  / resource descriptors for each and then a stream type of command can connect them. 

One of our computers has a php script that opens a com port to connect a digital scale to the webserver. Unfortunately, that machine is in storage, or I would paste in the code.

In ubuntu, to write to the NIC will be "opening a socket" or "establishing a port". You can use php to monitor the port for incoming calls. php is amazing... we're using it for all kinds of unintended uses. :)

---

### Post by mssever on 2008-07-23
> **cacycleworks said:**
> In ubuntu, to write to the NIC will be "opening a socket" or "establishing a port". You can use php to monitor the port for incoming calls. php is amazing... we're using it for all kinds of unintended uses. :)
You'll probably also need to be root to write to eth0.

---

