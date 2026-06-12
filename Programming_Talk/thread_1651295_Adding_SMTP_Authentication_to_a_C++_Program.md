---
title: "Adding SMTP Authentication to a C++ Program"
date: 2010-12-22
forum: Programming Talk
---

### Post by nova47 on 2010-12-22
I've been teaching myself some Visual C++ over the holiday break and have gotten a bit hung up on getting a program to successfully send e-mails from itself. I pulled this code from another forum and I was wondering how one goes about adding SMTP authentication to this code.

[PHP]

#define WIN32_LEAN_AND_MEAN

#include <stdio.h>
#include <stdlib.h>
#include <fstream.h>
#include <iostream.h>
#include <windows.h>
#include <winsock2.h>

#pragma comment(lib, "ws2_32.lib")

// Insist on at least Winsock v1.1
const VERSION_MAJOR = 1;
const VERSION_MINOR = 1;

#define CRLF "\r\n"                 // carriage-return/line feed pair

void ShowUsage(void)
{
  cout << "Usage: SENDMAIL mailserv to_addr from_addr messagefile" << endl
       << "Example: SENDMAIL smtp.myisp.com rcvr@elsewhere.com my_id@mydomain.com message.txt" << endl;

  exit(1);
}

// Basic error checking for send() and recv() functions
void Check(int iStatus, char *szFunction)
{
  if((iStatus != SOCKET_ERROR) && (iStatus))
    return;
 
  cerr << "Error during call to " << szFunction << ": " << iStatus << " - " << GetLastError() << endl;
}

int main(int argc, char *argv[])
{
  int         iProtocolPort        = 0;
  char        szSmtpServerName[64] = "";
  char        szToAddr[64]         = "";
  char        szFromAddr[64]       = "";
  char        szBuffer[4096]       = "";
  char        szLine[255]          = "";
  char        szMsgLine[255]       = "";
  SOCKET      hServer;
  WSADATA     WSData;
  LPHOSTENT   lpHostEntry;
  LPSERVENT   lpServEntry;
  SOCKADDR_IN SockAddr;

  // Check for four command-line args
  if(argc != 5)
    ShowUsage();

  // Load command-line args
  lstrcpy(szSmtpServerName, argv[1]);
  lstrcpy(szToAddr, argv[2]);
  lstrcpy(szFromAddr, argv[3]);

  // Create input stream for reading email message file
  ifstream MsgFile(argv[4]);

  // Attempt to intialize WinSock (1.1 or later)
  if(WSAStartup(MAKEWORD(VERSION_MAJOR, VERSION_MINOR), &WSData))
  {
    cout << "Cannot find Winsock v" << VERSION_MAJOR << "." << VERSION_MINOR << " or later!" << endl;

    return 1;
  }

  // Lookup email server's IP address.
  lpHostEntry = gethostbyname(szSmtpServerName);
  if(!lpHostEntry)
  {
    cout << "Cannot find SMTP mail server " << szSmtpServerName << endl;

    return 1;
  }

  // Create a TCP/IP socket, no specific protocol
  hServer = socket(PF_INET, SOCK_STREAM, 0);
  if(hServer == INVALID_SOCKET)
  {
    cout << "Cannot open mail server socket" << endl;
  
    return 1;
  }

  // Get the mail service port
  lpServEntry = getservbyname("mail", 0);

  // Use the SMTP default port if no other port is specified
  if(!lpServEntry)
    iProtocolPort = htons(IPPORT_SMTP);
  else
    iProtocolPort = lpServEntry->s_port;

  // Setup a Socket Address structure
  SockAddr.sin_family = AF_INET;
  SockAddr.sin_port   = iProtocolPort;
  SockAddr.sin_addr   = *((LPIN_ADDR)*lpHostEntry->h_addr_list);

  // Connect the Socket
  if(connect(hServer, (PSOCKADDR) &SockAddr, sizeof(SockAddr)))
  {
    cout << "Error connecting to Server socket" << endl;

    return 1;
  }

  // Receive initial response from SMTP server
  Check(recv(hServer, szBuffer, sizeof(szBuffer), 0), "recv() Reply");

  // Send HELO server.com
  sprintf(szMsgLine, "HELO %s%s", szSmtpServerName, CRLF);
  Check(send(hServer, szMsgLine, strlen(szMsgLine), 0), "send() HELO");
  Check(recv(hServer, szBuffer, sizeof(szBuffer), 0), "recv() HELO");

  // Send MAIL FROM: <sender@mydomain.com>
  sprintf(szMsgLine, "MAIL FROM:<%s>%s", szFromAddr, CRLF);
  Check(send(hServer, szMsgLine, strlen(szMsgLine), 0), "send() MAIL FROM");
  Check(recv(hServer, szBuffer, sizeof(szBuffer), 0), "recv() MAIL FROM");

  // Send RCPT TO: <receiver@domain.com>
  sprintf(szMsgLine, "RCPT TO:<%s>%s", szToAddr, CRLF);
  Check(send(hServer, szMsgLine, strlen(szMsgLine), 0), "send() RCPT TO");
  Check(recv(hServer, szBuffer, sizeof(szBuffer), 0), "recv() RCPT TO");

  // Send DATA
  sprintf(szMsgLine, "DATA%s", CRLF);
  Check(send(hServer, szMsgLine, strlen(szMsgLine), 0), "send() DATA");
  Check(recv(hServer, szBuffer, sizeof(szBuffer), 0), "recv() DATA");

  // Send all lines of message body (using supplied text file)
  MsgFile.getline(szLine, sizeof(szLine));             // Get first line

  do         // for each line of message text...
  {
    sprintf(szMsgLine, "%s%s", szLine, CRLF);
    Check(send(hServer, szMsgLine, strlen(szMsgLine), 0), "send() message-line");
    MsgFile.getline(szLine, sizeof(szLine)); // get next line.
  } while(MsgFile.good());

  // Send blank line and a period
  sprintf(szMsgLine, "%s.%s", CRLF, CRLF);
  Check(send(hServer, szMsgLine, strlen(szMsgLine), 0), "send() end-message");
  Check(recv(hServer, szBuffer, sizeof(szBuffer), 0), "recv() end-message");

  // Send QUIT
  sprintf(szMsgLine, "QUIT%s", CRLF);
  Check(send(hServer, szMsgLine, strlen(szMsgLine), 0), "send() QUIT");
  Check(recv(hServer, szBuffer, sizeof(szBuffer), 0), "recv() QUIT");

  // Report message has been sent
  cout << "Sent " << argv[4] << " as email message to " << szToAddr << endl;

  // Close server socket and prepare to exit.
  closesocket(hServer);

  WSACleanup();

  return 0;
}

[/PHP]

I've read through it all and understand all of the code but just can't seem to figure out how to get it to authenticate with an SMTP server. In my case I'm trying to send an e-mail to myself from myself via the gmail SMTP server (smtp.gmail.com).

---

### Post by nova47 on 2010-12-24
Actually it doesn't really even need to be for that code. Does anyone have any code that allows someone to enter their e-mail username and password (specifically for gmail) and send e-mails via a C++ program?

---

### Post by odyniec on 2010-12-25
The code that you posted talks to the mail server directly using the SMTP protocol -- this is somewhat an overkill if you just want to send messages from your program. Look for a library which takes care of all the protocol-related stuff and lets you send messages using simple function calls. For instance, the POCO SMTPClientSession class looks promising: [http://pocoproject.org/docs/Poco.Net.SMTPClientSession.html](http://pocoproject.org/docs/Poco.Net.SMTPClientSession.html) (it supports authentication).

---

### Post by nova47 on 2010-12-25
I browsed that briefly while I was cruising around. To be honest at the end of the day I just got lazy, chucked the whole C++ idea and just did it in Ruby. Took about 5 seconds lol. C++ is good for a lot of things; ease of use and simplicity are not on the list :-p

---

