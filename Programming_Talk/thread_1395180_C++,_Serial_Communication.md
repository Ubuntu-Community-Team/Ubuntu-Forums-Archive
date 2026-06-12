---
title: "C++, Serial Communication"
date: 2010-01-31
forum: Programming Talk
---

### Post by Sniperchang on 2010-01-31
Hello,

I'm writing a simple program to interface with a serial port (to later communicate with a microcontroller). I've done it in windows and now I'm trying in Ubuntu 9.10. I've been following this [guide]("http://www.easysw.com/%7Emike/serial/serial.html"), as well as a few other similar ones.

Writing to the port is no trouble, the signal is clear and as expected. However, I can't get the thing to read. I've tied the RX TX lines to try and read. It looks like the input buffer never receives any bytes. The protocol is 8 bits one stop byte, no parity, no control lines, no flow control. I believe I have the correct settings, maybe you can spot something?

Thank you, my code:

```
#include <stdio.h>
#include <string.h>
#include <unistd.h> //UNIX Standard function definitions
#include <fcntl.h> //File control
#include <errno.h> //Error number def
#include <termios.h> //POSIX terminal control
#include <termio.h>

int open_port(){ //-1 is a error
  int port = open("/dev/ttyS0", O_RDWR | O_NOCTTY | O_NDELAY);
  /*O_RDWR POSIX read write
  O_NOCTTY: not a "controlling terminal"
  O_NDELAY": Ignore DCD signal state*/

  if(port == -1){
    perror("open_port: Unable to open /dev/ttyS0 - ");
  }else fcntl(port, F_SETFL, 0);
  return (port);
}

int set_port(int port){
  struct termios options;
  tcgetattr(port, &options);

  cfsetispeed(&options, B9600); //Typical way of setting baud rate. Actual baud rate are contained in the c_ispeed and c_ospeed members
  cfsetospeed(&options, B9600);
  options.c_cflag |= (CLOCAL|CREAD);

  options.c_cflag &= ~CSIZE;
  options.c_cflag &= ~CSTOPB;
  options.c_cflag &= ~PARENB;
  options.c_cflag |= CS8;     //No parity, 8bits, 1 stop bit (8N1)
  options.c_cflag &= ~CRTSCTS;//CNEW_RTSCTS; //Turn off flow control

  options.c_lflag &= ~(ICANON | ECHO | ECHOE | ISIG); //Make sure that Canonical input is off (raw input data)

  options.c_iflag &= ~(IXON | IXOFF | IXANY); //Turn off software control flow

  options.c_oflag &= ~OPOST; //Raw output data

  options.c_cc[VMIN] = 0;
  options.c_cc[VTIME] = 10;

  return tcsetattr (port, TCSANOW, &options); //Make changes now without waiting for data to complete.
}

int main(){
  int fd, n;
  unsigned char byte = 0x0F;
  unsigned char buff[255];
  int ready;

  fd = open_port();
  set_port(fd);
  //n = write(fd, &byte, 1);
  n = write(fd, "ATZ", 3);
  if (n < 0) fputs("write() failed!\n", stderr);

  usleep(1000000); //Wait for 1 sec

  ioctl(fd, FIONREAD, &ready);
  printf("Bytes in input buffer: %d\n\n", ready);


  fcntl(fd, F_SETFL, FNDELAY); //Return read immidiatly
  n = read(fd, buff, 255);
  printf("Byte Read: %d\nByte received: %d %d %d\n\n", n, buff[0], buff[1], buff[2]);

  close(fd);
  return 0;
}

```Console Output:

```
Bytes in input buffer: 0

Byte Read: -1
Byte received: 132 4 8

```

Any help is very much appreciated.

---

### Post by lloyd_b on 2010-01-31
It's been a few years since I played with modems, but IIRC you need a <CR> character after the AT command before the modem will actually process it.  So it may be you're getting nothing back because it hasn't actually processed the reset (ATZ) command.

Lloyd B.

---

### Post by dwhitney67 on 2010-01-31
Nice C code... it's not C++.

Consider using select() to determine if there is actually anything to read on your open file (serial port) descriptor.

Also, bear in mind that if there is not anything to read on a *non-blocking* port, that read() will return -1.  Check the status of errno; I bet it is equal to EWOULDBLOCK.

---

### Post by Sniperchang on 2010-01-31
> **lloyd_b said:**
> It's been a few years since I played with modems, but IIRC you need a <CR> character after the AT command before the modem will actually process it. So it may be you're getting nothing back because it hasn't actually processed the reset (ATZ) command.

Lloyd B.

Thanks for the reply, but I'm not communicating with a modem. Just straight up RS-232 Communication. "ATZ" was just to output random bytes.

> **dwhitney67 said:**
> Nice C code... it's not C++.

Consider using select() to determine if there is actually anything to read on your open file (serial port) descriptor.

Also, bear in mind that if there is not anything to read on a *non-blocking* port, that read() will return -1.  Check the status of errno; I bet it is equal to EWOULDBLOCK.

It's not C++ yet ;)

I gave select() a try, and it just times out. So the port is just not getting any input, and you can see from my program's output that there's 0 bytes in the input buffer. It's like the receive line is turned off. There's nothing wrong physically, my windows equivalent code works as expected. I must be missing a setting or something...


EDIT: Ok guys I got it. I checked it again in windows and it really was a physical issue. It seems to be working perfectly now. Thanks for your help.

---

### Post by kaspar_silas on 2010-02-18
Hi when you say a physical issue. What was it exactly. 

I seem to get the same value of -1 returned by read.

---

