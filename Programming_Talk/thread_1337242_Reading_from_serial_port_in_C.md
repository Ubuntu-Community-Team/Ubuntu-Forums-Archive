---
title: "Reading from serial port in C"
date: 2009-11-25
forum: Programming Talk
---

### Post by exutable on 2009-11-25
Hello,

I am currently working with a microcontroller that is connected to /dev/ttyUSB0.  I can read from it in GtkTerm, bash script, python and every other thing available for reading serial ports.

When I try in C, I get -1 on the read but can easily write to it..

What is wrong?

Here is the bash script that works fine!
```
#/bin/bash
while true
do
  read LINE < /dev/ttyUSB0
  echo $LINE
done
```


Here is the C, I know I have a lot of includes(desperation):
```
#include <stdio.h>
#include <termios.h>
#include <sys/stat.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/fcntl.h>
#include <string.h>
#include <errno.h>

static int fd = 0;
char psResponse[10];
int iIn = 0;
int iOut = 0;

int main(void) {
fd = open("/dev/ttyUSB0", O_RDWR | O_NOCTTY | O_NONBLOCK);
	//iOut = write(fd, "o", 1);
	iIn = read(fd, psResponse, 1);
	printf("%d\n", iIn);
}
```

It simply returns -1, meaning that read couldn't get anything from it.


Thanks

---

### Post by Arndt on 2009-11-25
> **exutable said:**
> Hello,

I am currently working with a microcontroller that is connected to /dev/ttyUSB0.  I can read from it in GtkTerm, bash script, python and every other thing available for reading serial ports.

When I try in C, I get -1 on the read but can easily write to it..

What is wrong?

Here is the bash script that works fine!
```
#/bin/bash
while true
do
  read LINE < /dev/ttyUSB0
  echo $LINE
done
```


Here is the C, I know I have a lot of includes(desperation):
```
#include <stdio.h>
#include <termios.h>
#include <sys/stat.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/fcntl.h>
#include <string.h>
#include <errno.h>

static int fd = 0;
char psResponse[10];
int iIn = 0;
int iOut = 0;

int main(void) {
fd = open("/dev/ttyUSB0", O_RDWR | O_NOCTTY | O_NONBLOCK);
	//iOut = write(fd, "o", 1);
	iIn = read(fd, psResponse, 1);
	printf("%d\n", iIn);
}
```

It simply returns -1, meaning that read couldn't get anything from it.


Thanks

What is errno set to? Since you open it non-blocking, maybe it's just saying that there is nothing there yet.

---

### Post by exutable on 2009-11-25
Not sure what you mean??  The chip writes 888888888 back constantly.

---

### Post by Arndt on 2009-11-25
> **exutable said:**
> Not sure what you mean??  The chip writes 888888888 back constantly.

The value of errno, what is it.

---

### Post by Zugzwang on 2009-11-25
> **exutable said:**
> Not sure what you mean??  The chip writes 888888888 back constantly.

But not with infinite speed. Therefore, it is possible that between opening the file and reading from it, no data has arrived yet.

---

### Post by dwhitney67 on 2009-11-25
```

...

#include <errno.h>
#include <string.h>

...

int main(void) {
   int fd = open("/dev/ttyUSB0", O_RDWR | O_NOCTTY | O_NONBLOCK);
   //int iOut = write(fd, "o", 1);
   int iIn = read(fd, psResponse, 1);

   printf("%d, %s (%d)\n", iIn, strerror(errno), errno);

   return 0;
}

```
If you have an EAGAIN errno (resource unavailable), then you have your answer.  I suspect that Arndt is correct.

From the read() manpage:
```

...
If O_NONBLOCK is set, read() shall return -1 and set errno to [EAGAIN].

```

---

### Post by exutable on 2009-11-26
Ah yes it seems he was correct.  This is the exact code:

```
#include <stdio.h>
#include <sys/fcntl.h>
#include <math.h>

int fd = 0;
char psResponse[2];
double n;

int main(void) {
fd = open("/dev/ttyUSB1", O_RDWR | O_NOCTTY);
while(1)
{
	write(fd, "o", 1);
	read(fd, psResponse, 2);
	n = atoi(psResponse)*0.322265625;
	printf("%.1f\n", n);
}
close(fd);
}
```

O_NONBLOCK was the problem.  I'm having another weird issue though.  My program can only read if I have another program reading from the port.  For example if I have gtkterm open, then my program starts reading.  The second I close it, my program stops reading.

Any ideas?

---

### Post by Zugzwang on 2009-11-26
> **exutable said:**
> Any ideas?

Yes: Extend your program by proper error-handling, i.e., after each "open" or "read" operator, check for errors and make your program inform the user about the error occured. For this, read out the value of the "errno" variable. This should give you first hints.

---

### Post by dwhitney67 on 2009-11-26
> **exutable said:**
> Ah yes it seems he was correct.  This is the exact code:

```
#include <stdio.h>
#include <sys/fcntl.h>
#include <math.h>

int fd = 0;
char psResponse[2];
double n;

int main(void) {
fd = open("/dev/ttyUSB1", O_RDWR | O_NOCTTY);
while(1)
{
	write(fd, "o", 1);
	read(fd, psResponse, 2);
	n = atoi(psResponse)*0.322265625;
	printf("%.1f\n", n);
}
close(fd);
}
```

O_NONBLOCK was the problem.  I'm having another weird issue though.  My program can only read if I have another program reading from the port.  For example if I have gtkterm open, then my program starts reading.  The second I close it, my program stops reading.

Any ideas?

Perhaps you launched your 'reader' application from the gtkterm?

Btw, you have a hidden bug in your code (above)... you declare 'psResponse' to be 2-chars wide, and you use read() to read two chars.  That's great up until the point where you use atoi().  The atoi() function expects a null-terminated string, which you may not have.

If your intent is to read only one-char from the USB port, then modify your read() function.  Otherwise, augment the size of the 'psResponse' array by one byte.

Finally, in your small application, and pretty much most applications, there is no need to declare global variables.  Those that you have chosen to declare as global can easily be placed into the main() function.

P.S.  If you are indeed launching your reader app from the gtkterm, you can prevent its termination by using the 'nohup' statement:
```

$ nohup reader

```

---

### Post by exutable on 2009-11-26
yeah but it's weird... It's as if the terminal doesn't have permission to open the serial port.  I have tried it on 3 different computers, the 1 can use it fine but the other ones hav the same problem.

If i run gtkterm in my terminal, connect to the port and then close gtkterm from the terminal then I have permission.(doesn't work if I close gtkterm using gtk close button)

If I try to run a simple print with a read command on that port.  The printf doesn't even print out, the program just sits and waits.

Anybody know what the hell to do?


@dwhitney  It returns "80" every 10 seconds so shouldn't it receive it correctly if I specified that it should receive 2 bytes?

---

### Post by dwhitney67 on 2009-11-26
> **exutable said:**
> 
@dwhitney  It returns "80" every 10 seconds so shouldn't it receive it correctly if I specified that it should receive 2 bytes?

Well, tell it to receive 2 bytes; however you need to augment 'psResponse' to be 3 bytes in size.
```

...
char psResponse[3] = {0};   // initialize to nulls
...
read(fd, psResponse, 2);
double n = atoi(psResponse)*0.322265625;
...

```

---

### Post by exutable on 2009-11-26
Here is what I get:

```
dshea@dshea-laptop:~/Documents/Programming/C/Learning$ gcc test1.c -o test
dshea@dshea-laptop:~/Documents/Programming/C/Learning$ ./test

```
(just sits)

with this code:
```
#include <stdio.h>
#include <sys/fcntl.h>
#include <math.h>
int fd = 0;
char psResponse[3] = {0};
double n;
int main(void) {
fd = open("/dev/ttyUSB0", O_RDWR | O_NOCTTY);
read(fd, psResponse, 2);
n = atoi(psResponse);
printf("%.1f\n",n);
close(fd);
}
```


yet if I run gtkterm from terminal and exit with Ctrl+C:
```
Control signals read: Input/output error
Control signals read: Input/output error
Control signals read: Input/output error
Control signals read: Input/output error
Control signals read: Input/output error
Control signals read: Input/output error
^C
dshea@dshea-laptop:~/Documents/Programming/C/Learning$ ./test
80.0
dshea@dshea-laptop:~/Documents/Programming/C/Learning$ 

```


Screenshot of gtkterm attached.

---

### Post by exutable on 2009-12-01
bumpety bumpety

---

### Post by Zugzwang on 2009-12-01
> **exutable said:**
> bumpety bumpety

You still do not check for errors in your program. Fix it!

---

### Post by dwhitney67 on 2009-12-01
@ the OP:

```

#include <stdio.h>
#include <fcntl.h>
#include <sys/types.h>
#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>

int main()
{
   int fd = open("/dev/ttyUSB0", O_RDWR | O_NOCTTY);

   if (fd != -1)
   {
      char psResponse[3] = {0};
      int bytes = read(fd, psResponse, 2);

      if (bytes == 2)
      {
         double n = atoi(psResponse) * 0.322265625;
         printf("n = %.1f\n", n);
      }
      else if (bytes == 0)
      {
         printf("EOF detected!\n");
      }
      else if (bytes == -1)
      {
         printf("Error: %s (%d)\n", strerror(errno), errno);
      }

      close(fd);
   }
   else
   {
      printf("Error: Cannot open USB device; Reason: %s (%d)\n",
             strerror(errno), errno);
      return -1;
   }

   return 0;
}

```

---

### Post by dandanfeng160 on 2012-09-03
Hi&#65292;
    Mybe you have to configure your serial port after you have opened it.
Such as baud rate&#65292;flow control and so on.
    You can type "man termios" in the terminal to see the Manual page.

    Here are the code I copy from stackoverflow.com:url: [http://stackoverflow.com/questions/10710083/serial-programming-on-linux-in-c](http://stackoverflow.com/questions/10710083/serial-programming-on-linux-in-c)

int configure_port(int fd)      // configure the port
{
struct termios port_settings;      // structure to store the port settings in

cfsetispeed(&port_settings, B19200);    // set baud rates
cfsetospeed(&port_settings, B19200);

port_settings.c_cflag &= ~PARENB;    // set no parity, stop bits, data bits
port_settings.c_cflag &= ~CSTOPB;
port_settings.c_cflag &= ~CSIZE;
port_settings.c_cflag |= CS8;

cfmakeraw(&port_settings);
tcsetattr(fd, TCSANOW, &port_settings);    // apply the settings to the port
return(fd);

}

---

### Post by conradin on 2012-09-10
try cutecom, a program in the repos. It makes figuring out whats going on with the serial port a bit easier. it wont write your program, but it can help trouble shoot communication issues. 
A page Ive referred to alot in the past is:
[http://tldp.org/HOWTO/Serial-Programming-HOWTO/x115.html](http://tldp.org/HOWTO/Serial-Programming-HOWTO/x115.html)

Ill dig in later for my serial port programing stuff. What micro controler is it?

---

### Post by dwhitney67 on 2012-09-11
Damn!  This thread is nearly 3 years old.  No doubt the OP has moved on.

---

### Post by RichardUK on 2012-09-11
> **dwhitney67 said:**
> Damn!  This thread is nearly 3 years old.  No doubt the OP has moved on.

Stupid thing is, I bet all he needed to do was check he's permissions. Probable just needed to join the dialout group. ;)

---

