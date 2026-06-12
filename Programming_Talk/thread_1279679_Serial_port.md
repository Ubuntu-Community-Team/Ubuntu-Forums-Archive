---
title: "Serial port"
date: 2009-10-01
forum: Programming Talk
---

### Post by Wipster on 2009-10-01
SOLVED

Hey all,

The task here is to interface to a device over serial, the only way to get it to turn on and respond is to play with the RTS and DTR pins the right way on connect.

After much confusion and rearanging I got the chirp from the device, and it matched. The key to not getting a wierd first bit was to set the attributes after I toggled the pins.

Here is the code. I'm sorry I havn't programmed in a long time so the code is probably nasty, hints on improvements are greatly appreciated.

[PHP]#include <stdio.h>
#include <string.h>
#include <unistd.h>
#include <fcntl.h>
#include <termios.h>
#include <errno.h>
#include <sys/ioctl.h>

int open_port(void) {
	int fd;

	fd = open("/dev/ttyS0", O_RDWR | O_NOCTTY | O_NDELAY);
	if (fd == -1) {
		fprintf(stderr, "Unable to open /dev/ttyS0 - %s\n", strerror(errno));
	}
	else {
		fcntl(fd, F_SETFL, 0);
	}

	return (fd);
}

int main (void) {

	int fd, res, status = 0;
	struct termios options;
	char buf[3];

	printf("Attempting to open port\n");
	fd = open_port();
	if (fd != -1) {
		
		printf("Port opened\n");
		
		tcgetattr(fd, &options);
		// Get attributes

		cfsetispeed(&options, B9600);
		cfsetospeed(&options, B9600);		

		options.c_cflag |= (CLOCAL | CREAD);
		options.c_cflag &= ~PARENB;
		options.c_cflag &= ~CSTOPB;
		options.c_cflag &= ~CSIZE;
		options.c_cflag |= CS8;
		options.c_cflag &= ~CRTSCTS;

		options.c_lflag &= ~(ICANON | ECHO | ISIG);

		options.c_iflag = 0;
		options.c_oflag = 0;

		options.c_cc[VTIME] = 0;
		options.c_cc[VMIN] = 3;
		// Generated Attributes

		ioctl(fd, TIOCMGET, &status);
		// Get Status

		status &= ~TIOCM_RTS;
		status &= ~TIOCM_DTR;
		ioctl(fd, TIOCMSET, &status);
		// Set RTS and DTR low		
		
		sleep(1);
		
		status |= TIOCM_RTS;
		status &= ~TIOCM_DTR;
		ioctl(fd, TIOCMSET, &status);
		// Set RTS high and DTR low

		tcflush(fd, TCIFLUSH);
		tcsetattr(fd, TCSANOW, &options);
		// Flush things and set the attribs
	
		while (1) {
			res = read(fd,&buf,sizeof(buf));
			printf("Read 3 bytes\n");
			
			printf("Got %02X:%02X:%02X::%d\n", buf[0], buf[1], buf[2], res);
			
			usleep(20000);
		}
		close(fd);
		printf("Port closed\n");
	}
	return 1;
}
[/PHP]

I hope this helps someone down the line.

---

