---
title: "Serial programming woes"
date: 2005-11-09
forum: Programming Talk
---

### Post by raublekick on 2005-11-09
I'm working on a project that involves reading data through the serial port (ttyS0). We're following the Serial Programming Guide for POSIX Operating Systems as a source, which is fairly in depth up until the section on reading. 

The basic outline is:
open(ttyS0);
set baud rate and other stuff
read(ttyS0) within a loop
close(ttyS0);
exit

The problem is that for many of us, the reading has worked. It will display one character at a time. However, all of us who have gotten it working have also gotten it to not work anymore. Yesterday, after several people both succesfully got it to work and successful had it not work afterwards, I successfully got mine to work. Then another person tested theirs out, and it didn't work. Then I tried mine, without any changes in the code or recompilation, and it didn't work anymore! 

What could be causing this to not behave consistently?

<edit> I should mention that we are making sure the baud is set the same on each end.

---

### Post by LordHunter317 on 2005-11-09
Posting the code could be helpful.

---

### Post by raublekick on 2005-11-09
```
// serialkeys.cc
// Author: John Raub
// Date: November 2005
// Class: CS380 Operating Systems

/* The purpose of this program is to read input 
   from the serial bus using standard POSIX 
   programming. */

#include <iostream>
#include <stdio.h>
#include <string.h>
#include <unistd.h>
#include <fcntl.h>
#include <errno.h>
#include <termios.h>

using namespace std;

//!! Function Prototypes !!//
void welcome(string baud);
void setBaud(int fd, string baud);
int openPort();
void readBuffer(int fd);

int main(int argc, char *argv[]) {
	
	int port;
	string baud = "0";

	if(argc == 0 || argc == 1) {
		baud = "0";
	}
	else {
		baud = argv[1];
	}
		
	welcome(baud);

	port = openPort();
	setBaud(port, baud);

	readBuffer(port);

	close(port);

	return 0;
}

//!! Functions !!//

// welcome(), displays a simple welcome message
void welcome(string baud) {
	system("clear");
	cout << "\n\n\nWelcome to the Linux Serial Keys program. "
	     << "The purpose is to recieve input from another computer through the serial bus. " << endl;
	if(baud == "0") {
		/*cout << "You did not enter a baud setting! Please enter one now 			(options are 300, 1200, 9600, 57600*default): ";
		cin >> baud;*/
		cout << "You entered a baud setting of 0, baud will default to 57600. " << endl;
	}
	else {
		cout << "You entered a baud setting of: " << baud << 
endl;
	}
}

// setBaud(int fd, string baud), sets the baud and port settings
void setBaud(int fd, string baud) {
	struct termios options;

	// get current options for the port
	tcgetattr(fd, &options);

	// set baud rates to user defined values
	if (baud == "300") {
		cfsetispeed(&options, B300);
		cfsetospeed(&options, B300);
	}
	else if (baud == "1200") {
		cfsetispeed(&options, B1200);
		cfsetospeed(&options, B1200);
	}
	else if (baud == "9600") {
		cfsetispeed(&options, B9600);
		cfsetospeed(&options, B9600);
	}
	else if (baud == "57600") {
		cfsetispeed(&options, B57600);
		cfsetospeed(&options, B57600);
	}
	else {
		cfsetispeed(&options, B57600);
		cfsetospeed(&options, B57600);
	}

	// enable the reciever and set local mode
	options.c_cflag |= (CLOCAL | CREAD); // CS8??

	// flush line
	tcflush(fd, TCIFLUSH);
	//set new options for the port
	tcsetattr(fd, TCSANOW, &options);
}

// openPort(), opens the port for use
int openPort() {
	int fd; // File descriptor for the port

	fd = open("/dev/ttyS0", O_RDWR | O_NOCTTY); //| O_NDELAY);
	if(fd == -1) {
		perror("open port: Unable to open /dev/ttyS0 - ");
	}
	else {
		fcntl(fd, F_SETFL, 0);
	}

	return(fd);
}

// readBuffer(int fd), reads input from port
void readBuffer(int fd) {
	//string input = "";
	int res;
	char buf[255] = "";
	
	while(res = read(fd,buf,1) != -1) {
		buf[res] = 0;
		printf(":%s:%d\n", buf, res);
		//cout << buf;
		//cout << strerror(errno);
		if (buf[0]=='1')
			return;
	}	
}

```

---

### Post by raublekick on 2005-11-10
bump-o-rama

still no success

---

