---
title: "Remote Debug using Serial Port resulting in error"
date: 2014-07-13
forum: Programming Talk
---

### Post by Alok_Potrapalli on 2014-07-13
Hi All,


I am using ubuntu 14.04 and trying to remote debug a program on a target board using serial port(/dev/ttyS0), on the target board i started the gdbserver as follows:


Target:
sudo gdbserver /dev/ttyS0 myprog


On the host side i am using the following command under gdb :


Host:
(gdb) target remote /dev/ttyS0


I get the following error on the host side:


(gdb) target remote /dev/ttyS0
get_tty_state failed: Input/output error
set_tty_state failed: Input/output error
Remote debugging using /dev/ttyS0
Remote communication error.  Target disconnected.: Input/output error.
(gdb)


Can someone tell me , what I am doing wrong here.

---

### Post by tgalati4 on 2014-07-14
What are your serial port settings?

Install *setserial*:

```
sudo apt-get install setserial
man setserial
sudo setserial -vG /dev/ttyS0
```

It might look like:

tgalati4@Mint14-Extensa ~ $ sudo setserial -vG /dev/ttyS0
/dev/ttyS0 uart unknown port 0x03f8 irq 4 baud_base 115200 spd_normal skip_test

Your serial device might use a slower speed like 38400 or even 9600 baud.

---

### Post by SeijiSensei on 2014-07-14
I bet it has to do with permissions.  
```
crw-rw---- 1 root dialout 4, 64 Jul 12 17:36 /dev/ttyS0
```
Only root and members of group dialout can communicate with the device.  As someone suggested in a similar posting this morning, the solution is to add yourself to the "dialout" group.

---

### Post by Alok_Potrapalli on 2014-07-14
Hi Guys,

Thank you for the reply, I installed setserial and this is the output that i got after executing the command ([COLOR=#000000]sudo setserial -vG /dev/ttyS0)[/COLOR]

/dev/ttyS0 uart unknown port 0x03f8 irq 4 baud_base 115200 spd_normal skip_test.


so my serial device is set to the max baud rate.

Also , I added myself to the dialout group and I can see on both target and host side

This is my output on the target side:

ubuntu@arm:~$ ls -al /dev/ttyS*
crw-rw---- 1 root dialout 4, 64 Jun  5 23:34 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 Jun  5 23:34 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 Jun  5 23:34 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 Jun  5 23:34 /dev/ttyS3
ubuntu@arm:~$ 

This is my output on host side:

 $ ls -al /dev/ttyS*
crw-rw---- 1 root dialout 4, 64 Jul 13 11:02 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 Jul 13 11:02 /dev/ttyS1
crw-rw---- 1 root dialout 4, 74 Jul 13 11:02 /dev/ttyS10
crw-rw---- 1 root dialout 4, 75 Jul 13 11:02 /dev/ttyS11
crw-rw---- 1 root dialout 4, 76 Jul 13 11:02 /dev/ttyS12
crw-rw---- 1 root dialout 4, 77 Jul 13 11:02 /dev/ttyS13
crw-rw---- 1 root dialout 4, 78 Jul 13 11:02 /dev/ttyS14
crw-rw---- 1 root dialout 4, 79 Jul 13 11:02 /dev/ttyS15
crw-rw---- 1 root dialout 4, 80 Jul 13 11:02 /dev/ttyS16
crw-rw---- 1 root dialout 4, 81 Jul 13 11:02 /dev/ttyS17
crw-rw---- 1 root dialout 4, 82 Jul 13 11:02 /dev/ttyS18
crw-rw---- 1 root dialout 4, 83 Jul 13 11:02 /dev/ttyS19
crw-rw---- 1 root dialout 4, 66 Jul 13 11:02 /dev/ttyS2
crw-rw---- 1 root dialout 4, 84 Jul 13 11:02 /dev/ttyS20
crw-rw---- 1 root dialout 4, 85 Jul 13 11:02 /dev/ttyS21
crw-rw---- 1 root dialout 4, 86 Jul 13 11:02 /dev/ttyS22
crw-rw---- 1 root dialout 4, 87 Jul 13 11:02 /dev/ttyS23
crw-rw---- 1 root dialout 4, 88 Jul 13 11:02 /dev/ttyS24
crw-rw---- 1 root dialout 4, 89 Jul 13 11:02 /dev/ttyS25
crw-rw---- 1 root dialout 4, 90 Jul 13 11:02 /dev/ttyS26
crw-rw---- 1 root dialout 4, 91 Jul 13 11:02 /dev/ttyS27
crw-rw---- 1 root dialout 4, 92 Jul 13 11:02 /dev/ttyS28
crw-rw---- 1 root dialout 4, 93 Jul 13 11:02 /dev/ttyS29
crw-rw---- 1 root dialout 4, 67 Jul 13 11:02 /dev/ttyS3
crw-rw---- 1 root dialout 4, 94 Jul 13 11:02 /dev/ttyS30
crw-rw---- 1 root dialout 4, 95 Jul 13 11:02 /dev/ttyS31
crw-rw---- 1 root dialout 4, 68 Jul 13 11:02 /dev/ttyS4
crw-rw---- 1 root dialout 4, 69 Jul 13 11:02 /dev/ttyS5
crw-rw---- 1 root dialout 4, 70 Jul 13 11:02 /dev/ttyS6
crw-rw---- 1 root dialout 4, 71 Jul 13 11:02 /dev/ttyS7
crw-rw---- 1 root dialout 4, 72 Jul 13 11:02 /dev/ttyS8
crw-rw---- 1 root dialout 4, 73 Jul 13 11:02 /dev/ttyS9


After googling for a while i found out that my beagleboard target has only one serial port enabled.

followed the link [http://beaglebone.cameon.net/home/serial-ports-uart](http://beaglebone.cameon.net/home/serial-ports-uart)  to enable other ports. I still get the same error.

any ideas. :(

---

### Post by tgalati4 on 2014-07-14
The documentation shows the serial ports as ttyO0 not ttyS0, I don't know if the docs are wrong or if it makes a difference.  Check the serial port speed on the beagleboard and make sure it is the same as the host PC.

---

### Post by Alok_Potrapalli on 2014-07-15
Yes, I agree the documentation shows the serial ports as ttyO[012345]. My host side has no serial ports starting with /dev/ttyO* , how can i find out which is my corresponding serial port on the host side. I checked the baud rate on the beagle board and it is set to max baud rate similar to host side.

Thanks for the help.

---

### Post by steeldriver on 2014-07-15
I've never used the serial debugger, but there's a suggestion in the documentation that gdb on the host side needs to be invoked with an explicit --baud or -b value

```

*On the GDB host machine,*  you need an unstripped copy of your program, since GDB needs symbols and debugging information.  Start up GDB as usual, using
 the name of the local copy of your program as the first argument. (**You may also need the `--baud' option if the serial line is running at anything other than 9600bps.**) 
After that, use target remote to establish communications with gdbserver.

```

e.g.

```

gdb --baud 115200 yourprog

(gdb) target remote /dev/ttyS0

```

or 
```

gdb -b 115200 yourprog

(gdb) target remote /dev/ttyS0

```

---

### Post by Alok_Potrapalli on 2014-07-15
Thanks for the reply, 

After googling for a while and reading through this link([https://cygwin.com/ml/gdb/2007-11/msg00005.html](https://cygwin.com/ml/gdb/2007-11/msg00005.html)), I finally figured out.

This is what I requested from the Target Side:

ubuntu@arm:~/Projects$ sudo gdbserver /dev/ttyGS0 BBB
[sudo] password for ubuntu: 
Process BBB created; pid = 1779
Remote debugging using /dev/ttyGS0 


This is on the Host Side:
$ sudo gdb BBB
GNU gdb (Ubuntu 7.7-0ubuntu3.1) 7.7
Copyright (C) 2014 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
<http://www.gnu.org/software/gdb/documentation/>.
For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from BBB...done.
(gdb) target remote /dev/ttyACM0
Remote debugging using /dev/ttyACM0
warning: Architecture rejected target-supplied description
Remote 'g' packet reply is too long: 00000000bdf9ffbe0000000000000000000000000000000000000000000000000000000000000000000000000000000000000000d0f8ffbe00000000c0fbfdb6300000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000
(gdb) b 1
Breakpoint 1 at 0x86e8: file ../src/BBB.cpp, line 1.
(gdb) 

as it can be seen now I am able to remote debug, The executable was Cross-Compiled for Beagle Board which ARM based and the host PC which is X86, hence the warning message at the start of the debugging session.

Since, I use USB cable from host to the board I used these ports ,which is also how telnet communicates between these two sides.

Thanks for all the help.

---

