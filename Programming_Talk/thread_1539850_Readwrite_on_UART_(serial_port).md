---
title: "Read/write on UART (serial port)"
date: 2010-07-27
forum: Programming Talk
---

### Post by supernewbbie on 2010-07-27
Hi All,
does someone know how to read and write from/to UART with C++?

1) I can start a blocking read on UART process
2) I can start a writing to UARt process
3) UARt is read correcty (what I wrote is read).

BUT when i try to do the same things (1,2 and 3) in the same software (separating read and write with a fork or thread) I cannot write anything (read thread stay on waiting state for reading and write thread complete writing, but the two seems to have not interacttions...).

Thx in advance,
Rgds,
Supernewbbie

---

### Post by supernewbbie on 2010-07-27
Just and additional detail: to have previous 3 points working fine with separate read/write processes, I loopedback PC serial èports via HW (bridging input-output pins).

---

### Post by nebu on 2010-07-28
u can set the baud rate using the stty command... something like...
```
system("stty -F /dev/device <options>");
```
then just use the open, read, write, system calls to read/write data required
you can check [this link]("http://www.cs.uofs.edu/~bi/2003f-html/cs352/syscalls-file.htm") for the system calls

the link is for freebsd but since ubuntu and freebsd both implement the posix standard.... the system calls should be the same...

---

### Post by supernewbbie on 2010-07-29
Hi,
thanks a lot, I'm going t try via system calls.

But really (as stated by my username:)) i'm really newbbie in linux programming, so I would ask You some detail about system call use (what i have not understood from your and other links).

My current C++ code to read is something like this:
int fi = open("/dev/ttyS0", O_RDWR | O_NOCTTY );
int num_data_received = read(fi, buf_read_temp, sizeof(pattern));

Using system calls i have the need to manage file handle fi, buf_read and num_data_received, but i don't understand if this is possible, given that with system call i would have:

int fi = system("open(\"/dev/ttyS0\", O_RDWR | O_NOCTTY )");
int num_data_received = system("read(fi, buf_read_temp, sizeof(pattern))"); 

How can I insert system calls in my code C++?
Something like above for writing.

The strange thing is that read and write code separately compiled and run are working fine, but togheter (separating read and write with a fork or threads and starting write after read with a long delay of 10 seconds) is not working, or better read stay there waiting for bytes and write writes bytes but they seems to not "communicate each other.

---

### Post by Dingo_aus on 2011-11-14
Sample C code for reading the serial port:

[http://www.adventuresinsilicon.net/node/19](http://www.adventuresinsilicon.net/node/19)

---

