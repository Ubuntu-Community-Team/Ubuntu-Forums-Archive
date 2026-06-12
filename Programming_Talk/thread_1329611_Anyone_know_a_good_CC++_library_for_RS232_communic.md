---
title: "Anyone know a good C/C++ library for RS232 communication?"
date: 2009-11-17
forum: Programming Talk
---

### Post by Mark20 on 2009-11-17
Hi all,

I'm working on an embedded system, and I'm trying to find a serial library which I can use to communicate with a target by writing C/C++ code.  Almost every single library I've found does NOT compile, and gives random error messages.  I am wondering if anybody knows of any simple to use C or C++ libraries which can help with serial communication?

Thanks,
Mark

---

### Post by MindSz on 2009-11-17
Have you tried termios?

The Library:
```
#include <termios.h>
```

To open the port (as if it were a file) located at /dev/ttyTS0:
```
	myFD = open("/dev/ttyTS0", O_RDWR | O_NOCTTY | O_NONBLOCK);

	if (myFD<0){return 1;} 

   	bzero(&TermIO, sizeof(TermIO));
	TermIO.c_cflag = BAUDRATE | CS8 | CLOCAL | CREAD;
	TermIO.c_lflag = ICANON;
	TermIO.c_iflag = IGNPAR | IGNCR | IGNBRK;
	TermIO.c_oflag = 0;
	TermIO.c_cc[VINTR]    = 0;     
	TermIO.c_cc[VQUIT]    = 0;     
	TermIO.c_cc[VERASE]   = 0;    
	TermIO.c_cc[VKILL]    = 0;     
	TermIO.c_cc[VEOF]     = 0;
	TermIO.c_cc[VTIME]    = 0;     
	TermIO.c_cc[VMIN]     = 1;     
	TermIO.c_cc[VSWTC]    = 0;     
	TermIO.c_cc[VSTART]   = 0;    
	TermIO.c_cc[VSTOP]    = 0;     
	TermIO.c_cc[VSUSP]    = 0;     
	TermIO.c_cc[VEOL]     = 0;    
	TermIO.c_cc[VREPRINT] = 0;    
	TermIO.c_cc[VDISCARD] = 0;    
	TermIO.c_cc[VWERASE]  = 0;    
	TermIO.c_cc[VLNEXT]   = 0;     
	TermIO.c_cc[VEOL2]    = 0;   
	tcflush(FDGPS, TCIFLUSH);
	tcsetattr(FDGPS,TCSANOW,&TermIO);
```

To receive data:
```
LenRead = read(myFD,Buf,LenBuf) ;
```

To send data:
```
write(myFD,outBuf,outLen);
```

---

### Post by dribeas on 2009-11-18
ASIO (or boost::asio) have multiplatform support for serial communications. I have not really used it, so I cannot tell you much about the serial port support, but we do use TCP/UDP support in boost ASIO extensively.

ACE does also have support for serial port communications and is also cross platform, but to me the ASIO lib feels more natural to program (softer learning curve)

---

### Post by Mark20 on 2009-11-22
Hi all, 

Thanks for the input, I ended up using termios to put together my serial communication code.  I'll post the code online I just want to clean it up a bit fist.

@dribeas
I would definitely consider using Boost, but I'm still not sure if I want to use C or C++ for this project.  Since my system is pretty small I'm leaning more towards C, so I won't be able to use Boost.

Cheers,
Mark

---

### Post by sergio santos on 2010-01-22
Im interested on your feedback

> **Mark20 said:**
> Hi all, 

Thanks for the input, I ended up using termios to put together my serial communication code.  I'll post the code online I just want to clean it up a bit fist.

@dribeas
I would definitely consider using Boost, but I'm still not sure if I want to use C or C++ for this project.  Since my system is pretty small I'm leaning more towards C, so I won't be able to use Boost.

Cheers,
Mark

---

### Post by Mark20 on 2010-09-25
Hi all,

I've hacked together an example of how you could use termios.  Written in under 30 minutes so please don't expect high quality code :p

```

#include <termios.h>
#include <fcntl.h>
#include <stdio.h>
#include <string.h>
/* baudrate settings are defined in <asm/termbits.h>, which is included by <termios.h> */
#define BAUDRATE B9600            
/* change this definition for the correct port */
#define MODEMDEVICE "/dev/ttyS0"
#define _POSIX_SOURCE 1 /* POSIX compliant source */
#define FALSE 0
#define TRUE 1


int main(int argc, char *argv[])
{
	volatile int STOP=FALSE;
       
	int res,fd;
	struct termios oldtio,newtio;
	char buf[255];
    char *msg="hello world\n";
	fd = open(MODEMDEVICE, O_RDWR | O_NOCTTY ); 
	if (fd <0) {perror(MODEMDEVICE); return(-1); }
        
	tcgetattr(fd,&oldtio); /* save current port settings */
        
	bzero(&newtio, sizeof(newtio));
	newtio.c_cflag = BAUDRATE | CRTSCTS | CS8 | CLOCAL | CREAD;
	newtio.c_iflag = IGNPAR;
	newtio.c_oflag = 0;
        
	/* set input mode */
	newtio.c_lflag = 0;
         
	newtio.c_cc[VTIME]    = 0;   /* inter-character timer unused */
	newtio.c_cc[VMIN]     = 1;   /* blocking read until 1 char received */
        
	tcflush(fd, TCIFLUSH);
	tcsetattr(fd,TCSANOW,&newtio);
		
	char tmptmp[20];
    int tmpInt;    
	while (STOP==FALSE) 
	{       /* loop for input */
		res = read(fd,tmptmp,20);   // returns after up to 20 chars has been received 
		printf("received: %s",tmptmp);	
	}
	/* you can write using write system call like so: write(fd, dataToWrite, length) */
	tcsetattr(fd,TCSANOW,&oldtio);
}

```

---

