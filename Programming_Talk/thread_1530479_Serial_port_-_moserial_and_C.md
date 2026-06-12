---
title: "Serial port - moserial and C"
date: 2010-07-13
forum: Programming Talk
---

### Post by adhika on 2010-07-13
Hi,

I am writing a C code to decode GPS Binary Message.
The GPS is hooked to my serial port recognized as /dev/ttyS0. 
Every time I fired up my program, my program does not work because the message does not pass the checksum. 

However, after firing up apps like moserial or cutecom available in the repository then turning it off, my own program is able to decode the message correctly. This continues to succeed until I restart the computer

Could I be enlightened on what is going on with my code? My best reckon is that I have some problem with the serial port initialization. When moserial or cutecom was fired up, they set the attribute correctly and it remains until I restart the computer. 

The setting should be: no handshaking, 8N1, with Baud rate 38400.

I attached the code used to open and initialize the port.

Thank you so much! Your help is greatly appreciated.

```
int open_port(void)
{
  int fd; /* File descriptor for serial port */
  struct termios options; /* structure with termios options */

  fd = open("/dev/ttyS0", O_RDWR | O_NOCTTY | O_NDELAY);
  if (fd == -1)
  {
    /* Could not open the port */
    perror("open_port: Unable to open /dev/ttyS0 - ");
  }
  else
    //fcntl(fd, F_SETFL, FNDELAY); /* Read function to return 0 if no data */

  /* Serial port settings */

  /* Get current options for port */
  tcgetattr(fd, &options);

  /* Set the baud rate */
  cfsetispeed(&options, B38400);
  cfsetospeed(&options, B38400);

  /* Set character size: No parity (8N1) */
  options.c_cflag &= ~PARENB; 
  options.c_cflag &= ~CSTOPB;
  options.c_cflag &= ~CSIZE;
  options.c_cflag |= CS8;

  options.c_cc[VMIN]=0;
  options.c_cc[VTIME]=1;

  /* Enable receiver and set local mode */
  options.c_cflag |= (CLOCAL | CREAD);


  /* Set new options for port */
  if(tcsetattr(fd, TCSANOW, &options)!=0) {
	fprintf(stderr,"Cannot set attribute\n");
  };

  return fd;
}

int main(void) {
 int SPort;

 SPort = open_port();
 
 ...

 return 0;
}

```

---

### Post by xb12x on 2010-07-13
I suspect it has something to do with the port not being in raw mode. 

The serial-port can be set to use the high bit of each byte to distinguish control characters, characters that control the serial port itself (cntrl-s, etc). These characters are NOT part of the actual data, but ADDED to the data when necessary, to slow down or temporarily stop data flow, etc. The actual data then uses seven bits, such as 7-bit ASCII.

I suspect your GPS data uses all 8 bits so the port should be set to "raw" mode so it will ignore the toggling of the high bit.

---

### Post by adhika on 2010-07-13
xb12x,

Thanks for the reply. However, with 
```
 
  options.c_lflag &= ~(ICANON | ECHO | ECHOE | ISIG);
  options.c_oflag &= ~OPOST;

```

it still doesn't give the desired result... AFAIK, if ~ICANON is set, the reading is raw.

---

### Post by xb12x on 2010-07-13
Well, you've probably already thought of this but I'll suggest it just the same:

Write some code that returns the settings of the port and driver. Run it before and after the port works.

---

### Post by khalidyousafzai on 2010-07-15
hi, i am not a programming guy as such but am facing a similar problem. i am using a usb to rs232 cable and unable to communicate with my microcontroller board. i have traced it to a wierd thing. if i send say "a" and watch the data coming out of the rs232 cable using an oscilloscope i find 3-bytes being sent out. i donot know why it is that way. 
if i get to thwe bottom of it i'll let you know

khalid

---

### Post by dwhitney67 on 2010-07-15
> **adhika said:**
> xb12x,

Thanks for the reply. However, with 
```
 
  options.c_lflag &= ~(ICANON | ECHO | ECHOE | ISIG);
  options.c_oflag &= ~OPOST;

```

it still doesn't give the desired result... AFAIK, if ~ICANON is set, the reading is raw.

You can use cfmakeraw() to ensure that the termios values are properly configured to setup the port to accept raw input.

Usage is something like:
```

struct termios tios;

...

cfmakeraw(&tios);

...

tcsetattr(fd, TCASNOW, &tios);

```
There a manpage description for cfmakeraw(); I'd suggest you reference it if you have additional questions.

---

### Post by adhika on 2010-07-15
> **dwhitney67 said:**
> You can use cfmakeraw() to ensure that the termios values are properly configured to setup the port to accept raw input.


This works great! 

I am not sure why but my code works well in other computer, but not my own computer. However cfmakeraw() has solved my problem. Thank you so much!

@khalid:
> if i send say "a" and watch the data coming out of the rs232 cable using an oscilloscope i find 3-bytes being sent out. i donot know why it is that way.

Are the last two bytes CR and LF?

---

