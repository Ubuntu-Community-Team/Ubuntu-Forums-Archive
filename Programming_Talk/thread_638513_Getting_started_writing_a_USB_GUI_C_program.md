---
title: "Getting started writing a USB GUI C program"
date: 2007-12-12
forum: Programming Talk
---

### Post by Alf Stockton on 2007-12-12
I have an HSDPA modem connected via a USB port. This modem, of course, comes with Windows software but I want the same facility in Ubuntu 7.10
The modem works well in Ubuntu with commands such as "pppd call gprs" and in minicom "AT+CUSD=1,"*141#",15" which gives remaining airtime.
Now I would like to combine all this into a GUI that I wish to write in C but I have no clue how to address the modem 
I know that when it is plugged into the USB port it is /dev/ttyACM0 but now what?

---

### Post by cmnorton on 2007-12-12
My suggestion is to find yourself a serial programming library. Speaking from only a Windows serial programming background, the modem is a modem, whether it connects via RS232, USB, or is built-in. 

I started Googling for linux serial library, and got many, many hits. Here is one:

[http://www.lafn.org/~dave/linux/Serial-Programming-HOWTO.txt](http://www.lafn.org/~dave/linux/Serial-Programming-HOWTO.txt)

To the best of my knowledge, even though Linux/Unix is very powerful on accessing devices and you could probably access the device directly, I have to believe there is an API out there. When you find it, I'd love to know what it is.

---

### Post by Alf Stockton on 2007-12-12
I understand what you are saying but as the system has already recognised /dev/ttyACM0 I thought that my software could talk directly to that device.

---

### Post by stroyan on 2007-12-13
The /dev/ttyACM0 file will be emulating a serial tty device.
You can open it with open() and read and write to it with
read() and write() calls.  You will probably need to change some
of the default settings for the "termios" terminal attributes.
See the following resources for information on and examples of
manipulating terminal I/O settings.

[http://tldp.org/HOWTO/Serial-Programming-HOWTO/x56.html](http://tldp.org/HOWTO/Serial-Programming-HOWTO/x56.html)
[http://tldp.org/HOWTO/Serial-Programming-HOWTO/x115.html](http://tldp.org/HOWTO/Serial-Programming-HOWTO/x115.html)
[http://tldp.org/HOWTO/Serial-Programming-HOWTO/x165.html](http://tldp.org/HOWTO/Serial-Programming-HOWTO/x165.html)
man termios
and
[http://www.easysw.com/~mike/serial/](http://www.easysw.com/~mike/serial/)

You say that minicom and pppd can work well with the device.
This is linux.  You can look at the source code of those programs
to see how they work with the device.

mkdir minicom_source; cd minicom_source
apt-get source minicom
grep -r tcsetattr .
Explore the source.

It can also be very interesting to use the strace command to see all
the system calls made by a program such as minicom.  That can show
you what a program is doing before trying to find the source
code that makes those calls.

---

### Post by Alf Stockton on 2007-12-13
Thank you, that was exactly the kind of data I was looking for.

---

