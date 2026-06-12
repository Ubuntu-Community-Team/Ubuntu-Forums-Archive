---
title: "Peng Modification Compilation Problem"
date: 2006-01-08
forum: Programming Talk
---

### Post by fusionex on 2006-01-08
Hi All,

I'm using g++ 4.0.2 and I'm trying to compile and install the dialer for AOL in linux called peng. Unfortunately, there have been compilation problems using the command ./recompile. I've had to modify the code to replace deprecated headers such as <iostream.h> with <iostream> and <stdlib.h> with <cstdlib>.

This allowed me to reduce some errors that get saved to the make.log file. Unfortunately, there are some errors that just make no sense to me.
Here's the output of the log file:

kernel30.h:226: error: ISO C++ forbids declaration of ‘CAolCmd30’ with no type
kernel30.h:226: error: expected ‘;’ before ‘*’ token
make[2]: *** [threadELV3.o] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all-recursive-am] Error 2
/peng/peng'
make[1]: Leaving directory `/home/fusionex/peng'

The code in kernel30.h does not seem problematic and neither do the header file or implementation file for CAolCmd30 namely caolcmd30.h and caolcmd30.cpp. However, there is something wrong. I think that the 4.0.2 version of g++ doesn't like the way peng is coded.

Here is the file that causes the error above:

line 226 corresponds to the line that says "CAolCmd30 * m_cCmd;":
I'm also attaching a tarred and gzipped copy of the kernel30.h that I've modified.
Thanks to anyone who can help.

/************************************************** *************************

kernel30.h - description

-------------------

begin : Fri Jun 1 2001

copyright : (C) 2001 by stephane (birdy57)

email : [email]birdy57@multimania.com[/email]

************************************************** *************************/



/************************************************** *************************

* *

* This program is free software; you can redistribute it and/or modify *

* it under the terms of the GNU General Public License as published by *

* the Free Software Foundation; either version 2 of the License, or *

* (at your option) any later version. *

* *

************************************************** *************************/



#ifndef KERNEL30_H

#define KERNEL30_H



#ifdef WIN32

#include <winsock>

#else /*
*/
#include <unistd.h>

#include <cstdlib>

#include <cstdio>

#include <termios.h>

#include <sys/fcntl.h>

#include <sys/ioctl.h>

#include <sys/types.h>

#include <sys/socket.h>

#include <sys/un.h>

#include <sys/time.h>

#include <netinet/in.h>

#include <netdb.h>

#include <arpa/inet.h>

#define SOCKET int

#define closesocket close

#endif /*
*/


#include "nulldriver.h"

#include "ckernel.h"

#include "caolheader30.h"

#include "cvjcompress.h"

#include "caoltoclient30.h"

#include "caolcmd30.h"

#include "cclienttoaol30.h"




#define MRUIn 1550

#define MRUOut 1550



/**noyau de simulation 3.0

*@author stephane (birdy57)

*/


class Kernel30ublic CKernel
{

public:
Kernel30();

~Kernel30();

friend class CAolToClient30;

friend class CClientToAol30;

friend class CAolCmd30;


/** ecrit une sequence Raw en y ajoutant le header AOL */

void WriteRawIn(char *buffer, int nLon);


/** recherche l'adresse IP */

bool FindIp(char *sBuffer, int nLon);


/** Demmare le noyau */

void Start();


/** Connection */

bool Connect(char *Login, char *Pass);


/** donne l'adresse IP */

void GetIp(char *sBuffer);


/** donne le nom de domaine */

void GetDomainName(char *sBuffer);


/** Donne le Dns */

void GetDns(char *sBuffer);


/** arrete le noyau */

void Stop();


protected:

class m_CData {

public:
const char *dat1;

const char *dat2;

const char *dat3;

const char *dat4;

const char *dat5;

const char *dat6;

const char *dat7;

const char *dat8;

const char *dat9;

const char *dat10;

const char *dat11;

const char *dat12;

const char *dat13;

const char *dat14;

const char *dat15;

const char *dat16;

const char *dat17;

const char *dat18;

const char *dat19;

const char *dat20;

};


class m_CIp {

public:
unsigned char Ip1;

unsigned char Ip2;

unsigned char Ip3;

unsigned char Ip4;

unsigned char Dns1;

unsigned char Dns2;

unsigned char Dns3;

unsigned char Dns4;

char *DomainName;

void GetIpStr(char *buffer) {
sprintf(buffer, "%d.%d.%d.%d", Ip1, Ip2, Ip3, Ip4);
};

void GetDnsStr(char *buffer) {
sprintf(buffer, "%d.%d.%d.%d", Dns1, Dns2, Dns3, Dns4);
};

};



/** donnee */

m_CData * CData;


/** Header aol version 3.0 et cable */

CAolHeader30 * AolHeaderIn;


protected: // Protected methods

/** Lecture d'un trame AOL , la longueur est retoune */

int ReadAolTrame(char *buffer, int MaxBuffer);


/** recharge la trame nAck,nSeq */

int ReadAolTrameSeqAck(char *buffer, int nBufferSize, int nSeq,
int nAck);


/** negociation de la connection */

bool Negociate(char *Login, char *PassWord);


/** Classe Ip */

m_CIp * m_Ip;


/** compresseur */

CVjcompress * VjcompressOut;


// Variables commune au 3 classe du noyau


bool bStopTunneling;

bool bNeedAck;

bool bIDLE;

unsigned short m_nNeedAck;

unsigned short m_nNeedSeq;

bool m_bAckTrame;

unsigned short m_nLastAolAck;

unsigned short m_nLastAolSeq;

unsigned short m_nLastAolInet;

unsigned short m_nFirstAolSeq;


/** Classe Cmd */

CAolCmd30 * m_cCmd;


/** classe client->Aol */

CClientToAol30 * m_cClientToAol;


/** classe Aol->client */

CAolToClient30 * m_cAolToClient;


/** ecriture */

bool m_bWriting;

};



#endif /*
*/

---

### Post by SEWi on 2006-03-28
im haveing the same problem.i also got justa bout as far.im going to compair your modifid file and my modifid file and mabie the both of them will fix eachothers problem.if you got a fix allredy please share.
     thanks

---

