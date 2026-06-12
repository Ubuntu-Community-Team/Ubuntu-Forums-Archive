---
title: "Serial Port Programming Issue with 10.04"
date: 2010-07-08
forum: Programming Talk
---

### Post by SandmanMS on 2010-07-08
I have written a program to connect to the serial port (via an RS-232 to USB convertor) and read encoder position data that is being provided on a continuous basis by an Animatics Smart Motor. The program runs for a while but then after a random amount of time the program stops receiving data. The program is still running just the read() call is throwing the EAGAIN error. Even after letting it sit for a while no data ever shows up again on the line. If I Ctrl-C the program and start it again there is a flow of data until the error happens again. Anyone have any ideas?

This is the code I am using to open the port

```
    
    fd=open("/dev/ttyUSB0", (O_RDWR | O_NOCTTY | O_NDELAY));
    tcgetattr(fd,&newtio);
    cfmakeraw(&newtio);
    cfsetospeed(&newtio,B38400);
    cfsetispeed(&newtio,B38400);

    newtio.c_cflag |= (CLOCAL | CREAD);
    tcsetattr(fd,TCSANOW,&newtio);
    fcntl(fd, F_SETFL, FNDELAY);

```

Thanks for any insight.

M.Sands
VADER Laboratory
Lehigh University

---

### Post by dwhitney67 on 2010-07-08
In this statement, what is FNDELAY?  Also explain the purpose of the statement.  I'm curious because you have already opened the USB device and indicated that you wanted it to be non-blocking.
```

fcntl(fd, F_SETFL, FNDELAY);

```


P.S.  Typically, when I see fcntl() used, the current flag settings that are associated with the file descriptor are obtained, and then after modifying those, the flags are used to set the descriptor.  In the code above, you are chucking out all of the flags, and merely setting FNDELAY.

Something like:
```

int curflags = fcntl(fd, F_GETFL, 0);

fcntl(fd, F_SETFL, curflags | O_NONBLOCK);

```

---

### Post by SandmanMS on 2010-07-08
That line essentially sets it so that read will not block. Removing that line of code does not change the problem. It still behaves in the same manner. Also, substituting in your method also does not change the behavior. It reads, reads, reads, until at some point it just believes there is no data on the line.

---

### Post by dwhitney67 on 2010-07-08
I have no idea what value is represented by O_NONDELAY (or even FNDELAY), but I came across some old code I have where the flags where set to zero, and some additional code was used to set up the port.

I do not know if this will help, but here's that code:
```

int            fd = open(portName, O_RDWR | O_NOCTTY | O_NDELAY);
struct termios opts;


fcntl(fd, F_SETFL, 0);

// Get the current options for the port...
tcgetattr(fd, &opts);

// Set the baud rates to 9600...
cfsetispeed(&opts, B9600);
cfsetospeed(&opts, B9600);

// Enable the receiver and set local mode...
opts.c_cflag |= (CLOCAL | CREAD);

opts.c_cflag &= ~PARENB;
opts.c_cflag &= ~CSTOPB;
opts.c_cflag &= ~CSIZE;
opts.c_cflag |= CS8;

// Set the new options for the port...
tcsetattr(fd, TCSANOW, &opts);

...

fcntl(fd, F_SETFL, FNDELAY);

...

```

EDIT:  I just noticed that my code also employs the FNDELAY (see above in the posted code).

---

