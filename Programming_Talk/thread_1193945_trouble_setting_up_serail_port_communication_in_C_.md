---
title: "trouble setting up serail port communication in C (HELP!)"
date: 2009-06-22
forum: Programming Talk
---

### Post by MR.UNOWEN on 2009-06-22
Hello,

I'm having trouble writing a c program that communicates with a led display over the serial port. So far I'm able to send data, but it turns out to be garbage on the other end.

-It's one way communication (computer to device).
-9600 baud rate
-no parity bit
-rising edge triggered (I think....)
-not synchronized with clock (edge triggered)
-reads a byte at a time (8 bits)

What configuration do I set to get the needed settings. Also is write() the proper function call and open() the proper way to access the serial port?

I remember doing this a while ago, but I lost the code to do this.

Please help ASAP

---

### Post by MR.UNOWEN on 2009-06-22
After testing a number of things, I've determined that the bug is due to the fact that it's not writing all 50 bytes. How to do I ensure / force all 50 bytes to be written?

---

### Post by Habbit on 2009-06-22
> **MR.UNOWEN said:**
> How to do I ensure / force all 50 bytes to be written?
Did you remember to [flush your buffers]("http://www.cplusplus.com/reference/clibrary/cstdio/fflush/")?

---

### Post by mdurham on 2009-06-22
MR.UNOWEN, I've attached some code that 'might' be of use. I used it for many years on Windows. I converted it to a class from my old C code so it still looks like C code I guess. As you will I'm no expert at programming but the code seems to work ok.
Cheers, Mike

oops, it seems the attachment didn't work for some reason. So I've pasted the files here.

/***************************************************************************
 *            SerialObj.cc
 *
 *  Fri Nov 18 08:27:33 2005
 *  Copyright  2005  Mike
 *  Email
 ****************************************************************************/

#include <iostream>
#include "SerialObj.h"
#include "TickCounter.h"

CSerialObj::CSerialObj(char *pName, int BaudRate)
{
	ioFd = open(pName, O_RDWR | O_NOCTTY | O_NONBLOCK);
	if(ioFd > 0)
	{
		tcgetattr(ioFd,&Oldtio); // save current port settings

		// set new port settings for canonical input processing
		BAUD = BaudLookup(BaudRate);
		DATABITS = DataBitsLookup(8);
		STOPBITS = StopBitsLookup(1);
		PARITYON = 0;
		PARITY = 0;

		tcgetattr(ioFd, &Newtio); // get current port settings

		Newtio.c_cflag = BAUD | CRTSCTS | DATABITS | STOPBITS | PARITYON | PARITY | CLOCAL | CREAD;
		Newtio.c_iflag = IGNPAR;
		Newtio.c_oflag = 0;
		Newtio.c_lflag = 0;       //ICANON;
		Newtio.c_cc[VMIN]=1;
		Newtio.c_cc[VTIME]=0;
		tcflush(ioFd, TCIFLUSH);
		tcsetattr(ioFd, TCSANOW, &Newtio);

		// Make the file descriptor asynchronous (the manual page says only
		// O_APPEND and O_NONBLOCK, will work with F_SETFL...)
		fcntl(ioFd, F_SETFL, FNDELAY);

		SetDTR();
		SetRTS();
	}
//TRACE(MyCStringf(">>> CSerialObj %s at %d baud == ioFd == %d", pName, BaudRate, ioFd));
}

CSerialObj::~CSerialObj()
{
	if(IsValid())
	{
		tcsetattr(ioFd, TCSANOW, &Oldtio);
		ClearDTR();
		ClearRTS();
		close(ioFd);
	}
}

bool CSerialObj::DataAvailable()
{
	int nAvailable = 0;

	if(IsValid())
		ioctl(ioFd, FIONREAD, &nAvailable);

	return(nAvailable > 0 ? true : false);
}

BYTE CSerialObj::GetByte()
{
	BYTE b = 0;

	if(IsValid())
		read(ioFd, &b, 1);

	return(b);
}

void CSerialObj::WriteString(char *pStr)
{
	while(*pStr)
		WriteByte(*pStr++);
}

void CSerialObj::SetInputRate(int Rate)
{
	cfsetispeed(&Newtio, BaudLookup(Rate));
	tcsetattr(ioFd, TCSANOW, &Newtio);
}


void CSerialObj::SetOutputRate(int Rate)
{
	cfsetospeed(&Newtio, BaudLookup(Rate));
	tcsetattr(ioFd, TCSANOW, &Newtio);
}

void CSerialObj::SetIoctl(UINT Func, UINT SetBits, UINT ClearBits)
{
		int status;

		ioctl(ioFd, TIOCMGET, &status);
		status &= ~ClearBits;
		status |= SetBits;
		ioctl(ioFd, Func, &status);
}

UINT CSerialObj::BaudLookup(int Rate)
{
	UINT BAUD;

	switch(Rate)
	{
		case 460800:
			BAUD = B460800;
			break;
		case 230400:
			BAUD = B230400;
			break;
		case 115200:
			BAUD = B115200;
			break;
		case 57600:
			BAUD = B57600;
			break;
		case 38400:
			BAUD = B38400;
			break;
		case 19200:
			BAUD  = B19200;
			break;
		case 9600:
			BAUD  = B9600;
			break;
		case 4800:
			BAUD  = B4800;
			break;
		case 2400:
			BAUD  = B2400;
			break;
		case 1800:
			BAUD  = B1800;
			break;
		case 1200:
			BAUD  = B1200;
			break;
		case 600:
			BAUD  = B600;
			break;
		case 300:
			BAUD  = B300;
			break;
		case 200:
			BAUD  = B200;
			break;
		case 150:
			BAUD  = B150;
			break;
		case 134:
			BAUD  = B134;
			break;
		case 110:
			BAUD  = B110;
			break;
		case 75:
			BAUD  = B75;
			break;
		case 50:
			BAUD  = B50;
			break;
		default:
			BAUD = B9600;
			break;
	}

	return(BAUD);
}

UINT CSerialObj::DataBitsLookup(int Bits)
{
	UINT DATABITS;

	switch (Bits)
	{
		case 8:
		default:
			DATABITS = CS8;
			break;
		case 7:
			DATABITS = CS7;
			break;
		case 6:
			DATABITS = CS6;
			break;
		case 5:
			DATABITS = CS5;
			break;
	}

	return(DATABITS);
}

UINT CSerialObj::StopBitsLookup(int Bits)
{
	UINT STOPBITS;

	switch(Bits)
	{
		case 1:
		default:
			STOPBITS = 0;
			break;
		case 2:
			STOPBITS = CSTOPB;
		break;
	}

	return(STOPBITS);
}

UINT CSerialObj::ParityLookup()
{
/*	switch (Parity)
      {
         case 0:
         default:                       //none
            PARITYON = 0;
            PARITY = 0;
            break;
         case 1:                        //odd
            PARITYON = PARENB;
            PARITY = PARODD;
            break;
         case 2:                        //even
            PARITYON = PARENB;
            PARITY = 0;
            break;
      }
*/
	return(0);
}

/***************************************************************************
 *            SerialObj.h
 *
 *  Fri Nov 18 08:17:45 2005
 *  Copyright  2005  Mike
 *  Email
 ****************************************************************************/

#ifndef __SERIALOBJ_H__
#define __SERIALOBJ_H__

#include <iostream>
#include <fcntl.h>
#include <sys/ioctl.h>
#include <termios.h>
#include "MyInclude.h"

class CSerialObj
{
public:
	CSerialObj(char *pName, int BaudRate);
	virtual ~CSerialObj();

	bool DataAvailable();
	BYTE GetByte();

	void WriteByte(BYTE b)
	{
		if(IsValid())
			write(ioFd, &b, 1);
	}

	void WriteBlock(BYTE *pBuf, int nBytes)
	{
		if(IsValid())
			write(ioFd, pBuf, nBytes);
	}

	void WriteString(char *pStr);

	void SetInputRate(int Rate);
	void SetOutputRate(int Rate);

	void SetDTR() {SetIoctl(TIOCMSET, TIOCM_DTR, 0);}
	void ClearDTR() {SetIoctl(TIOCMSET, 0, TIOCM_DTR);}
	void SetRTS() {SetIoctl(TIOCMSET, TIOCM_RTS, 0);}
	void ClearRTS() {SetIoctl(TIOCMSET, 0, TIOCM_RTS);}

	bool IsValid() {return(ioFd > 0 ? true : false);}

	int GetWaitingCount()
	{
		int n = 0;
		if(IsValid())
			ioctl(ioFd, FIONREAD, &n);
		return(n);
	}

protected:
	UINT BaudLookup(int Rate);
	UINT DataBitsLookup(int Bits);
	UINT StopBitsLookup(int Bits);
	UINT ParityLookup();
	void SetIoctl(UINT Func, UINT SetBits, UINT ClearBits);

private:
	int ioFd;
	BYTE bData;
	struct termios Oldtio;
	struct termios Newtio;

	// values set in Newtio.c_cflag
	UINT BAUD;
	UINT DATABITS;
	UINT STOPBITS;
	UINT PARITYON;
	UINT PARITY;
	//
};


#endif

---

