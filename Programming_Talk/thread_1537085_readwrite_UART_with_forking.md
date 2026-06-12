---
title: "read/write UART with forking"
date: 2010-07-23
forum: Programming Talk
---

### Post by supernewbbie on 2010-07-23
Hi all,
I developed 2 separate sw in C++ in order to send out over serial port and read back (with appropriate hw bridge on serial port).
First program start to read in stand-by, and then starting the second program to write I can see that the the bytes written on /dev/ttyS0 are correctly read from the first program (that was in read....).

Now, I need to put those 2 sw togheter in order to set a baudrate on uart, write and then read.
To do this I put above 2 separate programs in one method, forking it to start read before write. 
Unfortunaly it seems that nothing is working: read starts, write correctly sendout bytes, but the 2 seem to be on different worlds.
Note that if I start a separate write program, the read catch it correctly.
Can anyone support me to understand what is wrong? Below is trhe code:

/*---------------------------------------------------------------------------------------*/
/*                                INCLUDES                                               */
/*---------------------------------------------------------------------------------------*/
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <fcntl.h>
#include <unistd.h>	
#include <termios.h>

int readfromuart(int baudrate_in);
int write2uart(int baudrate_out);
int writeread(int baudrate_out, int baudrate_in);

int main()
{


	int baudrates[] = { B2400, B4800, B9600, B19200, B38400, B57600, B115200 };


	pid_t  pid;
	pid = fork();
	if (pid == 0) 
	{          
		sleep(2);
		write2uart(baudrates[0]); //Childprocess
		sleep(3);
		exit(1);
		
	}
	else
	{
		readfromuart(baudrates[0]);//Parentprocess
		wait();
	}       


}


int write2uart(int baudrate_out)
{
	//WRITE TO UART
	struct termios termAttr;
	char pattern[10] = {'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'l'};
	int fd;

	printf("\n\n***************\n");
	printf("\nSending.....\n");
	fd = open("/dev/ttyS0", O_RDWR | O_NOCTTY );

	if(fd<0)	
	{
		// Could not open the port.
		perror("Sending section - ");
		perror("open_port: Unable to open /dev/ttyS0 - ");
		exit(-1);
	}

	printf("\nfile handle with /dev/ttyS0 opened\n");

	cfsetospeed(&termAttr, baudrate_out);

	// Clear the line 
	tcflush(fd,TCOFLUSH);
		
	if(tcsetattr(fd,TCSANOW,&termAttr)<0)
	{
		// Could not set  attributes inpu/output baud rate speed for UART.
		perror("tcsetattr: Unable to set attributes ispeed/ospeed for /dev/ttyS0 - ");
		exit(-1);
	}

	printf("\nUART: attributes ispeed/ospeed successfully set\n");

	int num_data_written = write(fd, pattern, sizeof(pattern));
	if (num_data_written<0)
	{
		// Could not write data to UART.
		perror("Write: Unable to write to /dev/ttyS0 - ");
		exit(-1);
	}
	printf("\n%d bytes successfully written to UART\n", num_data_written);
		
	close(fd);


}

int readfromuart(int baudrate_in)
{
	//READ FROM UART
	struct termios termAttr;
	char pattern[10] = {'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'l'};
	char buf_read_temp[10] = {0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00};	
	int fi;

	printf("\n\n***************\n");
	printf("\nReceiving.....\n");

	fi = open("/dev/ttyS0", O_RDWR | O_NOCTTY );

	if(fi<0)
	{
		// Could not open the port.
		perror("Receiving section - ");
		perror("open_port: Unable to open /dev/ttyS0 - ");
		exit(-1);
	}

	printf("\nfile handle with /dev/ttyS0 opened\n");

	cfsetispeed(&termAttr, baudrate_in);
	termAttr.c_cc[VMIN]     = 10;   /* blocking read until 10 chars received */
	tcsetattr(fi,TCSANOW,&termAttr);

	int num_data_received = read(fi, buf_read_temp, sizeof(pattern));

	if (num_data_received<0)
	{
		//Could not receive data from UART.
		perror("Read: Unable to read from /dev/ttyS0 - ");
		exit(-1);
	}

	printf("\n%d bytes successfully received from UART:\n", num_data_received);
	printf("\n\n");
	for (int j=0; j<sizeof(pattern);j++)
	{
		printf(" %x ", buf_read_temp[j]);
	}	
	printf("\n\n");

	close(fi);

}

---

