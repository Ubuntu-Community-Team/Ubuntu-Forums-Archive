---
title: "Driving me to serial murder..."
date: 2005-11-21
forum: Programming Talk
---

### Post by Todd_Z on 2005-11-21
yes, even programming dorks can make english puns. :p 

Anywho. back to the problem:

```

#include <iostream>
#include <stdio.h>
#include <string.h>
#include <unistd.h>
#include <fcntl.h>
#include <errno.h>
#include <termios.h>

using namespace std;

void setBaud(int fd);
int openPort();
void readBuffer(int fd);

int main(int argc, char *argv[]) {
	int port;
	system("clear");
	cout << "\n\n\nWelcome to the Linux Serial Keys program." << endl;
	port = openPort();
	setBaud(port);
	readBuffer(port);
	close(port);
	return 0;
}

void setBaud ( int fd ) {
	struct termios options;
	tcgetattr( fd, &options );
	cfsetispeed( &options, B9600 );
	cfsetospeed( &options, B9600 );
	options.c_cflag |= (CLOCAL | CREAD); // CS8??
	tcflush( fd, TCIFLUSH );
	tcsetattr( fd, TCSANOW, &options );
}

int openPort ( ) {
	int fd;
	fd = open( "/dev/ttyS0", O_RDWR | O_NOCTTY );
	if ( fd == -1 )
		perror( "open port: Unable to open /dev/ttyS0 - " );
	else
		fcntl( fd, F_SETFL, 0 );
	return(fd);
}

void readBuffer ( int fd ) {
	int res;
	char buf[255] = "";
	while ( res = read(fd,buf,1) != -1 ) {
		buf[res] = 0;
		printf( ":%s:%d\n", buf, res );
		if ( buf[0] == '1' )
			return;
	}	
}

```

Now heres the problem.  I have a basic stamp: which theoretically is supposed to echo back anything i send to it.  I know that the serial connection is working, but i just cant figure out whether or not the computer is recognizing the basic stamp.  I get nothing for output, its just the default ::1 over and over and over.  Any ideas would be MUCH appreciated.

---

### Post by toojays on 2005-11-22
How do you know that the serial connection is working? Have you tried using a program like minicom or something? I wouldn't expect this program to get anything back as output, because you never send anything for the basic stamp to echo back! What you are seeing is the call to read() timing out.

---

### Post by Todd_Z on 2005-11-22
um.... How do you think I should test to see if the connection is working?  What is stumping me about this problem is that there are SO many steps in the process that it could be - I don't know how to debug it.

---

### Post by toojays on 2005-11-22
Here's some things to consider:

1) You want to be sure that the cable between the PC and stamp is connected correctly, and that your program is using the correct port. One way to check this is to use minicom in local terminal mode. [This page]("http://nms.lcs.mit.edu/projects/cricket/v2man-html/node6.html") describes how to do that for university students wanting to talk to a cricket. This is very similar to talking to a basic stamp, except since the stamp has its own echo, you don't need to turn on minicom's echo.

2) The program you posted previously works correctly as far as I can see. All the times it prints "::0", are just timeouts. It times out because the stamp isn't sending anything. The stamp isn't sending anything because you aren't sending anything to *it*. Make a writebuffer function to put before readbuffer.

I've been in your shoes, and it is hard to figure out what's going wrong when it doesn't work. If you don't need the implementation to be in C, you might find it a helluva lot easier to use [pySerial]("http://pyserial.sourceforge.net/") (the Ubuntu package is called python-serial).

---

### Post by Todd_Z on 2005-11-22
```

::1
::1
::1
::1
::1

```

is the output when i run the prog.  It's not that I *need* it to be in C, but i'd rather write the script myself so that I can really learn whats going on in the process.  Wrapper classes take away all the fun!

ARGH.  Now that i screwed something up in minicom, i cant even get *that* output from the program.  It just hangs on the "open" command.
```

	fd = open( "/dev/ttyS0", O_RDWR | O_NOCTTY );

```
I think its because I "exitted and reset" in minicom.  Not sure though.

---

### Post by toojays on 2005-11-22
It sounds like minicom still has the port open, so your program can't open it. I suspect that in that case, if you added the O_NONBLOCK flag to your open(), it would return -1.

Did you understand what I wrote about the stamp not echoing back?

Here's some code I have used to successfully open a serial port in the past; maybe something in there will help you:```

  fd = open(port_path, O_RDWR | O_NOCTTY | O_NDELAY);
  if (fd == -1)
    return;
  else
    fcntl(fd, F_SETFL, 0);      // set port to operate in blocking-mode

  // read current options
  tcgetattr(fd, &options);

  // set for 8-bit bytes, no parity, one stop bit
  options.c_cflag &= ~PARENB;
  options.c_cflag &= ~CSTOPB;
  options.c_cflag &= ~CSIZE;
  options.c_cflag |= CS8;

  // clear all input mode flags
  options.c_iflag = 0;

  // set for raw input, 1 second timeout
  options.c_cflag |= (CLOCAL | CREAD);
  options.c_lflag &= ~(ICANON | ECHO | ECHOE | ISIG);
  options.c_oflag &= ~OPOST;
  options.c_cc[VMIN] = 0;
  options.c_cc[VTIME] = 10;

  // write back options
  tcsetattr(fd, TCSANOW, &options);
```

---

### Post by Todd_Z on 2005-11-22
I'm getting an odd response:  Any ideas?

I wish I knew if the signal was actually being sent... I'm dual booting with windoze, and the basic stamp software works, so I know its not a problem with the connection or anything.

```

Basic Stamp Testing Program:
BWriting to Buffer...

```

```

#include <iostream>
#include <stdio.h>
#include <string.h>
#include <unistd.h>
#include <fcntl.h>
#include <errno.h>
#include <termios.h>

using namespace std;

int openPort();
string readBuffer(int fd);
void writeBuffer(int fd,string str);

int main ( int argc, char *argv[] ) {

	int port;
	string chr;
	system("clear");
	
	printf ( "\n\nBasic Stamp Testing Program:\n\n" );
	port = openPort();
	
	printf ( "\nWriting to Buffer..." );
	writeBuffer(port, "B");
	
	printf ( "\nReading Buffer..." );
	chr = readBuffer(port);
	
	printf ( "\nReading Buffer..." );
	chr = readBuffer(port);
	
	printf ( "\n\tCharacter read: %s", chr.c_str() );
	
	if ( chr != "B" )
		return -1;
	
	printf ( "\nWriting to Buffer..." );
	writeBuffer(port, "S");
	
	printf ( "\nReading Buffer..." );
	chr = readBuffer(port);
	
	printf ( "\n\tCharacter read: %s", chr.c_str() );
		
	if ( chr != "S" )
		return -1;
	
	printf ( "\nWriting to Buffer..." );
	writeBuffer(port, "0");
	
	printf ( "\nReading Buffer..." );
	chr = readBuffer(port);
	
	printf ( "\nReading Buffer..." );
	chr = readBuffer(port);
		
	printf ( "\n\tCharacter read: %s", chr.c_str() );
		
	if ( chr != "0" )
		return -1;
		
	printf ( "\nReading Buffer..." );
	chr = readBuffer(port);
		
	printf ( "\n\tCharacter read: %s", chr.c_str() );
		
	printf ( "\nProper Process." );
	
	close(port);
	printf( "\n\n" );
	return 0;
}

int openPort ( ) {

	int fd;
	struct termios options;
	
	fd = open("/dev/ttyS0", O_RDWR | O_NOCTTY | O_NDELAY );
	if (fd == -1)
		return -1;
	else
		fcntl(fd, F_SETFL, 0);
	
	tcgetattr(fd, &options);
	
	options.c_cflag &= ~PARENB;
	options.c_cflag &= ~CSTOPB;
	options.c_cflag &= ~CSIZE;
	options.c_cflag |= CS8;
	
	options.c_iflag = 0;
	
	options.c_cflag |= (CLOCAL | CREAD);
	options.c_lflag &= ~(ICANON | ECHO | ECHOE | ISIG);
	options.c_oflag &= ~OPOST;
	options.c_cc[VMIN] = 0;
	options.c_cc[VTIME] = 10;
	
	tcsetattr(fd, TCSANOW, &options);
	
}

string readBuffer ( int fd ) {
	int res;
	char buf[255] = "";
	while ( res = read(fd,buf,1) != -1 ) {
		buf[res] = 0;
		printf( ":%s:%d\n", buf, res );
		return string( buf );
	}
}

void writeBuffer ( int fd, string str ) {
	if ( write( fd, str.c_str(), str.length() ) < 0 )
		printf( "\nwrite(%s) failed.\n", str.c_str() );
}

```

---

### Post by toojays on 2005-11-22
I don't understand that at all. Where is that 'B' coming from?

A couple of other things to try:

1) The port code I gave you doesn't set the baud rate, you may need to do that.

2) Run your program using strace and see if the pattern of read, writes and printfs gives you any clues.

---

### Post by Todd_Z on 2005-11-23
Thats the end section: if you think seeing more would be helpful, let me know.  I have to ctrl+c it because it just hangs on the read.

```

open("/dev/ttyS0", O_RDWR|O_NONBLOCK|O_NOCTTY) = 3
fcntl64(3, F_SETFL, O_RDONLY)           = 0
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B9600 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B9600 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_START or TCSETS, {B9600 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B9600 -opost -isig -icanon -echo ...}) = 0
brk(0)                                  = 0x804b000
brk(0x806c000)                          = 0x806c000
write(0, "B", 1B)                        = 1
read(0,  <unfinished ...>

```

Btw, I changed the main function to be a lot more simple:

```

int main ( int argc, char *argv[] ) {
	int port;
	string chr;
	system("clear");
	
	printf ( "\n\nBasic Stamp Testing Program:\n\n" );
	port = openPort();
	
	writeBuffer( port, "B" );
	
	chr = readBuffer( port );
	
	printf ( "\nReceived Character: %s", chr.c_str() );
	
	close(port);
	printf( "\n\n" );
	return 0;
}

```

---

### Post by toojays on 2005-11-23
I'm stumped. Are you sure /dev/ttyS0 is the correct port? COM1 on Windows?

---

### Post by Todd_Z on 2005-11-23
Yes.

---

