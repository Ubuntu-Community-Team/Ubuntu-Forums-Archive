---
title: "Serial port capture"
date: 2005-02-02
forum: Programming Talk
---

### Post by firstbishop on 2005-02-02
Hi

I'm new to Linux so this may be a very simple question!

Our switchboard outputs phone call data to the serial port of a PC (COM1 on the existing windows machine). At present I use a windows utility to write that data to a text file, which is then queried by a database.

Is there an equivalent utility for Ubuntu? From a discussion I had with a friend, he feels it should be possible to write a script, which automatically captures any text coming in to the serial port on the Ubuntu box.

I'd be really grateful for any pointers. Thanks

Mike

---

### Post by Uuggerr on 2007-03-15
I am also looking for the exact same thing.  Our phone system is a NEC I-Series.

I believe the com port that the data is coming in on is /dev/ttyS1 but have yet to beable to capture this data.

Thanks

---

### Post by tomchuk on 2007-03-15
Here's a very brain dead simple C program that will capture from the defined port at the defined baud rate and write to stdout, from there, you can redirect to a logfile. Put the code in a file called serialcap.c, and specify the serial port and speed in the defines. Compile with gcc -o serialcap serialcap.c It seems to work just fine with my router connected with a null modem cable. This is assuming 8N1.

```

#include <fcntl.h>
#include <stdio.h>
#include <termios.h>
#include <stdlib.h>
#include <strings.h>

/* Change to the baud rate of the port B2400, B9600, B19200, etc */
#define SPEED B9600

/* Change to the serial port you want to use /dev/ttyUSB0, /dev/ttyS0, etc. */
#define PORT "/dev/ttyS1"

int main( ){
    int fd = open( PORT, O_RDONLY | O_NOCTTY );
    if (fd <0) {perror(PORT); exit(-1); }
    struct termios options;

    bzero(&options, sizeof(options));
    options.c_cflag = SPEED | CS8 | CLOCAL | CREAD | IGNPAR;
    tcflush(fd, TCIFLUSH);
    tcsetattr(fd, TCSANOW, &options);

    int r;
    char buf[255];
    while( 1 ){
        r = read( fd, buf, 255 );
        buf[r]=0;
        printf( "%s", buf );
    }
}

```

---

### Post by supirman on 2007-03-15
I've used interceptty to capture data coming in/going out over a serial line.  

[http://www.suspectclass.com/~sgifford/interceptty/](http://www.suspectclass.com/~sgifford/interceptty/)

---

### Post by dwblas on 2007-03-16
What language are you using?  In Python it's something like (most languages have something similiar)
```
S = serial.Serial(com_port)
if S.getCTS():
         #do something
```

---

### Post by dpm on 2007-03-16
> **dwblas said:**
> What language are you using?  In Python it's something like (most languages have something similiar)
```
S = serial.Serial(com_port)
if S.getCTS():
         #do something
```

Where is the serial class defined? Which library needs to be imported to make use of it?

---

### Post by dwblas on 2007-03-16
Try USPP first.  If you don't like that, other can be found via Google.
[http://ibarona.googlepages.com/uspp](http://ibarona.googlepages.com/uspp)

---

### Post by woooee on 2007-03-16
> Where is the serial class defined? Which library needs to be imported to make use of it?Pyserial will also do this.  It's on Sourceforge [http://pyserial.sourceforge.net](http://pyserial.sourceforge.net)

---

### Post by dpm on 2007-03-17
> **dwblas said:**
> Try USPP first.  If you don't like that, other can be found via Google.
[http://ibarona.googlepages.com/uspp](http://ibarona.googlepages.com/uspp)

> **woooee said:**
> Pyserial will also do this.  It's on Sourceforge [http://pyserial.sourceforge.net](http://pyserial.sourceforge.net)

I know this is slightly off-topic, but I believe the original question has already been answered anyway, so here's my question to people who've been using pyserial and ussp in python?
[LIST]
[*]Which one of them would you reccommend?[/LIST]I've been playing around with pyserial and it seems easy and complete enough for me, but I still haven't had the chance to try uusp. A couple of personal observations:

_Pyserial:_
[LIST]
[*]Packaged for debian and ubuntu (i.e. available from the universe repos) as '*pyton-serial*'
[*]It seems to be the one most people use, although it does not seem to be maintained anymore (last version as of 2002-02-13, according to the project's page at sourceforge)
[*]It works for me (TM)[/LIST]_USSP_:
[LIST]
[*]No packages available.
[*]It seems to be relatively current (February 2006)
[*]I haven't had the chance to test it yet.[/LIST]Thanks.

---

### Post by dwblas on 2007-03-17
I have never tried pyserial so can't comment.  As far as last version = 02/13/2002, I think that may be the future of all serial port apps.  They aren't being maintained because communication through the serial port is diminishing rapidly.  If the program does whatever it is that you are looking for, then the 2002 doesn't matter as I doubt that any new serial port features have been added to computers recently.  I would suggest looking at the code and determining which you understand better because __you__ may just be maintaining it for your own use in the future. I just want to capture data from a portable data terminal so either would probably work for me.

---

