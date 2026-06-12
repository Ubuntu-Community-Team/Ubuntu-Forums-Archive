---
title: "Problems with rs232 and tcp/ip thread"
date: 2010-05-25
forum: Programming Talk
---

### Post by ritchie-w on 2010-05-25
Hi,

I have a problem with a serial connection and a tcp/ip connection in a running thread as a server.

If I do not have a connection to the TCIP/IP server, the rs232 program thread is running correct.

That means, if not connection to the rs232 is existing, the read command exists after the defined timeout.

If the TCP/IP server has a active connection, I guess the termios setting is suddenly different, because the read command does not finished, as long at least one char is received.

Does somebody knows where the problem is existing ?

Best regards

R.

---

### Post by dwhitney67 on 2010-05-25
You will need to post some code; the problem could lie anywhere.  Perhaps you are corrupting the stack?

It seems unlikely that two descriptors (one a file, and another a socket) are interfering with each other.

Consider, at least for the RS-232 port, of setting it up as non-blocking.  Avoid reading any port or socket unless there is data waiting to be read.  Use select() to determine this.

---

### Post by ritchie-w on 2010-05-26
The rs232 stuff is running in a seperate class, but i am using QT class to do the TCP/IP stuff. So i do not know how to check problems with the file descriptor.

I also will take a look into the select() function, but my problem is also, that the communication can break during during a running communication, and the program must be able to handle this as well.

I am using kubuntu 9,10 / qt 4.5 lib.

Thanks for help up to now..

---

### Post by dwhitney67 on 2010-05-26
If memory serves me right...
```

#include <sys/select.h>
...

fd_set save_fds;
FD_ZERO(&save_fds);
FD_SET(fd, &save_fds);

while (true)
{
   fd_set  read_fds = save_fds;
   timeval timeout  = { 1, 0 };   // one second

   int sel = select(fd + 1, &read_fds, 0, 0, &timeout);

   if (sel > 0)
   {
      // data is ready to receive
   }
   else if (sel == 0)
   {
      // timeout before data was ever received
   }
   else
   {
      // error (unlikely to occur)
   }
}

```
select() can monitor more than one file descriptor (which btw is synonymous with a socket descriptor).  All you have to do is add each descriptor to the fd_set.  You can use FD_ISSET() and the read_fds to determine which descriptor is ready for reading when select() reports that data is available.

Undoubtedly Qt has wrapped the select() function into their own little beast.  Do the research with the Qt API to find out what it is called.

---

### Post by ritchie-w on 2010-05-26
Hi,

here is just a code snippet of the init function of the port

```

	if ((fd = open(p, O_RDWR | O_NOCTTY | O_SYNC )) == -1)
		{
		ErrorText=tr("initPort: Can't open device %1").arg(comPortString);
		ErrorStatus=true;
		return;
		}
	/* configurare RS232 */
	if (tcgetattr(fd, &term_attr) != 0)
		{
		ErrorText=tr("initPort: get first tcgetattr() failed (%1).").arg(comPortString);
		ErrorStatus=true;
		return;
		}

	if (tcgetattr(fd, &oldTerm_attr) != 0)
		{
		ErrorText=tr("initPort: backup tcgetattr() failed (%1).").arg(comPortString);
		ErrorStatus=true;
		return;
		}
	
	cfsetispeed(&term_attr, TERM_SPEED);
	cfsetospeed(&term_attr, TERM_SPEED);
	cfmakeraw(&term_attr);
	term_attr.c_cc[VMIN] = 0; 				/* finished after one bye */
	term_attr.c_cc[VTIME] = 10; 			/* or 1000ms */

	term_attr.c_iflag &= ~(BRKINT | ICRNL | INPCK | ISTRIP | IXON | IUCLC | INLCR| IXANY );

	/* output modes - clear giving: no post processing such as NL to CR+NL */
	term_attr.c_oflag &= ~(OPOST|OLCUC|ONLCR|OCRNL|ONLRET|OFDEL);

	/* control modes - set 8 bit even partiy 1 stop bit*/
	term_attr.c_cflag |= (CS8 | PARENB);

    /* local modes - clear giving: echoing off, canonical off (no erase with 
	backspace, ^U,...),  no extended functions, no signal chars (^Z,^C) */
	term_attr.c_lflag &= ~(ECHO | ECHOE | ICANON | IEXTEN | ISIG);

	term_attr.c_cflag |= CRTSCTS;					/* using flow control via CTS/RTS */
																
	if (tcsetattr(fd, TCSAFLUSH, &term_attr) != 0)
		{
		ErrorText=tr("initPort: tcsetattr() failed (%1).").arg(comPortString);
		ErrorStatus=true;
		return;
		}

	/* change standard input */
	if (tcgetattr(fd, &term_attr) != 0)
		{
		ErrorText=tr("initPort: changed tcgetattr() failed (%1).").arg(comPortString);
		ErrorStatus=true;
		return;
		}

	if (tcsetattr(fd, TCSAFLUSH, &term_attr) != 0)
		ErrorText=tr("initPort: tcsetattr() failed (%1).").arg(comPortString);

	FD_SET(fd, &input_fdset); 						 /* Select the first channel 1 */
	ErrorStatus=false;

```

For QT it ist just a new class of the object QTCPSERVER() in example.

like
```

		m_IOServer[(int)i] = new TCPServer(this,AccessPoint);

```

see also as an example here the threaded TCPSERVER

[http://doc.trolltech.com/4.5/network-threadedfortuneserver.html](http://doc.trolltech.com/4.5/network-threadedfortuneserver.html)

File handling is handled internally. I have to find how .

I start to read the docs of QT ...
I will return with a result later.

---

### Post by ritchie-w on 2010-05-27
Hello,

i am still running blind.
> 
int			S5_3964::tty_read(unsigned	char	*buffer,	int maxdatasize)
{
	int	state=1;																				// Number of chars read
	int	receivedbyte=0;																// total number of chars
	int	timeoutcounter=10;														// count the waiting for data

	while( 	timeoutcounter > 0 && 										// as long time is running
				  receivedbyte < maxdatasize)								// as long chars reached
	{
		state =read(filedesc,&buffer[receivedbyte],1);		// Read and store

		if( state > 0 )																			// byte reached
		{
			timeoutcounter=10;														// reset counter
			receivedbyte++;																// count bytecounter
		}
		else
		{
			usleep(1000);																	// Wait a max. of 1 msec. for data 
			timeoutcounter--;																// decrease counter*/
		}
	}
	return	receivedbyte;																// Number of chars read back
}



if a TCP/IP Connections in another thread of the program is active, the code "read()" will not return, even, if it setup as seen before. 

The file handle of both functions TCP/IP socket and serial connection is different.

I also try to work with "select" and "ioctl(filedesc ,TIOCOUTQ, &bytesToSend)" to get the information, if bytes available before starting to read,  
> 
Buffer count and flushing

FIONREAD int *argp
    Get the number of bytes in the input buffer. 
TIOCINQ int *argp
    Same as FIONREAD. 


but the communication did not work proper with this functions.

Any hints ?

Does a QTCPSERVER-Object change the terminal settings ?

Can I have a problem with different libs ?
  read() from different packages ?

R.

---

### Post by dwhitney67 on 2010-05-27
I presume you are using recv() to read from your TCP socket.  This is a **blocking** call!  If you specify that you want to receive 256 bytes, and yet only 10 have been sent to your socket, well then the recv() is going to wait until more data has been received.

Obviously this is not desirable; if you set up the socket to be **non-blocking**, this will mitigate the blocking issues.  Of course, with this setup, you want to avoid reading from the socket unless you have received notification that there is data to be read.  This is where the usage of select() comes into use.

I would suggest that you take a step back from your application, and temporarily try developing smaller applications that perform the basic operations that you seek.  You should be able to easily setup a server and a client that send data to each other.  The input data can come from the keyboard.


P.S.  Look into using fcntl() for setting up the socket to be non-blocking.  Something like:
```

#include <fcntl.h>
#include <sys/socket.h>

...

int sd = socket(...);
fcntl(sd, F_SETFL, O_NONBLOCK);

...

```

---

### Post by ritchie-w on 2010-05-30
Thanks dwhitney67 

for you help.

I found the main reason for this, which sounds really silly.

The real program works, fine. It tested the program the whole time
in the developement environment (kdevelop).

But when I use the I/O server as the real program (not in debug mode),
the client handling and the failure handling works correct.

Thanks

---

