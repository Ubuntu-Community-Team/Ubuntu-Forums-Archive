---
title: "Received data from serial port and send it through ethernet"
date: 2013-01-02
forum: Programming Talk
---

### Post by tzeronone on 2013-01-02
Is there any C program that will receive some data from serial port and the data will forwarded through Ethernet port?

---

### Post by mevun on 2013-01-02
There are devices called "terminal servers" which do that.  Presumably, someone has written programs for those devices to do what you want.  From personal experience, it seems those devices might use Linux (or at least provide a Linux-similar shell).

The way they work is that you can connect via SSH or telnet protocol from your computer to the terminal server.  Then you issue a command like "connect 1" which means you want to use serial port 1.  Then if the other end of the serial connection has a human-usable interface, you can type whatever commands are destined for the other end.  For example, the serial port can be connected to a network router.

I believe what a C program does on the terminal server would be something like this:
fd = **open**("/dev/ttys0",. . . ) for the serial port
You might need some **ioctl **call to set baud rate, parity, etc.
socketfd = **socket**(AF_INET, . . .) for the network interface (assuming Internet Protocol)
The rest of the network code depends on whether you are using TCP or UDP and will be the server or client side.
If you really meant Ethernet (i.e. not IP), then you need a raw socket.
Basically, once you have file descriptors for both interfaces, you use the **read** or **write** system calls after that.

---

### Post by tzeronone on 2013-01-03
Any specific program or link that I can download?

---

