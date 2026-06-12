---
title: "[SOLVED] c++ &amp;amp; sockets hang after 3 reads using read() or recv()"
date: 2008-03-22
forum: Programming Talk
---

### Post by ZeroHimself on 2008-03-22
i wrote a client tcp socket program to interface with a SMTP server....
if hanges after 3 reads using either read() or recv().......
using gcc or gpp......

also worth noting, is that *ANY* socket demo code i download from the net does the same thing.......?

i send "user username\n"
followed by "pass password\n"
followed by "list\n" or "stat\n" and it hangs....

any ideas?

---

### Post by PaulFr on 2008-03-22
1. I assume you know this, but I think you mean the POP3 protocol (port 110, RFC 1939), not the SMTP protocol (port 25, RFC 821 or 2821), right ? *Or is it the IMAP protocol ?*

2. To test ASCII protocols, it may be better to first understand the protocol with > telnet <hostname> <port_number> and then you type out the commands and verify they work.

Hope this helps.

---

### Post by ruy_lopez on 2008-03-22
Have you tested read/recv for errors, using strerror(errno)?

---

### Post by Roptaty on 2008-03-22
You have to terminate all commands with a carriagereturn linefeed pair (CRLF)... (\r\n, and not only \n). :)

---

### Post by ruy_lopez on 2008-03-22
> **Roptaty said:**
> You have to terminate all commands with a carriagereturn linefeed pair (CRLF)... (\r\n, and not only \n). :)

I never did that before, and everything worked fine. Mind you, I was only running these:

EHLO hostname
ETRN hostname
QUIT

---

### Post by ZeroHimself on 2008-03-22
opps, i did mean pop3, sorry

ok, i terminate all strings with "\r\n"...

i can telnet, and telnet works just fine

and strerror(errno)  just returns "Success".........

---

### Post by lnostdal on 2008-03-22
flush the output

---

### Post by POW R TOC H on 2008-03-22
Use netcat to simulate a mail server on your machine with pop3 port :
```

sudo nc -l -p 110 -vv

```
You must run it with sudo (or root tights)

Then, see what kind of output your program makes. Also, try using gdb, that might be useful. If these solutions fail, post your source code, if it's not a secret, maybe someone will find the error...

Good luck!

---

### Post by ZeroHimself on 2008-03-22
weird stuff

the netcat test works fine

.......
it doesn't seem to be a flushing problem...

it seems to hang on any protocol....
it only works when i write my own program to reply......

it hangs on the 2nd-4th read() or recv() calls.....(i debuged too)

it would appear that my read/recv calls are waiting for remote data to be sent...
but when i verify the io with telnet, it does send data on my last commands...


anyhow, heres some code
```

#include <netdb.h>
#include <netinet/in.h>
#include <unistd.h>
#include <iostream>

#define MAX_LINE 2048
#define LINE_ARRAY_SIZE (MAX_LINE+1)

using namespace std;

int main()
{
  int socketDescriptor;
  unsigned short int serverPort;
  struct sockaddr_in serverAddress;
  struct hostent *hostInfo;
  char buf[LINE_ARRAY_SIZE], c;

  cout << "Enter server host name or IP address: ";
  cin.get(buf, MAX_LINE, '\n');

  // gethostbyname() takes a host name or ip address in "numbers and
  // dots" notation, and returns a pointer to a hostent structure,
  // which we'll need later.  It's not important for us what this
  // structure is actually composed of.
  hostInfo = gethostbyname(buf);
  if (hostInfo == NULL) {
    cout << "problem interpreting host: " << buf << "\n";
    exit(1);
  }

  cout << "Enter server port number: ";
  cin >> serverPort;
  cin.get(c); // dispose of the newline

  // Create a socket.  "AF_INET" means it will use the IPv4 protocol.
  // "SOCK_STREAM" means it will be a reliable connection (i.e., TCP;
  // for UDP use SOCK_DGRAM), and I'm not sure what the 0 for the last
  // parameter means, but it seems to work.
  socketDescriptor = socket(AF_INET, SOCK_STREAM, 0);
  if (socketDescriptor < 0) {
    cerr << "cannot create socket\n";
    exit(1);
  }

  // Connect to server.  First we have to set some fields in the
  // serverAddress structure.  The system will assign me an arbitrary
  // local port that is not in use.
  serverAddress.sin_family = hostInfo->h_addrtype;
  memcpy((char *) &serverAddress.sin_addr.s_addr,
         hostInfo->h_addr_list[0], hostInfo->h_length);
  serverAddress.sin_port = htons(serverPort);
				
  if (connect(socketDescriptor,
              (struct sockaddr *) &serverAddress,
              sizeof(serverAddress)) < 0) {
    cerr << "cannot connect\n";
    exit(1);
  }

  cout << "\nEnter some lines, and the server will modify them and\n";
  cout << "send them back.  When you are done, enter a line with\n";
  cout << "just a dot, and nothing else.\n";
  cout << "If a line is more than " << MAX_LINE << " characters, then\n";
  cout << "only the first " << MAX_LINE << " characters will be used.\n\n";


  // Zero out the buffer.
  memset(buf, 0x0, LINE_ARRAY_SIZE);

  // Read the modified line back from the server.
  int n;
  //if (recv(socketDescriptor, buf, MAX_LINE, 0) < 0) {
  n=read(socketDescriptor, buf, MAX_LINE);
  if (n <=0) {
    cerr << "didn't get response from server?";
    close(socketDescriptor);
    exit(1);
  }

    cout << "Sever: " << buf << "\n";

  // Prompt the user for input, then read in the input, up to MAX_LINE
  // charactars, and then dispose of the rest of the line, including
  // the newline character.
  cout << "Input: ";
  cin.get(buf, MAX_LINE, '\n');
  while (cin.get(c) && c != '\n')
    ;
  strcat(buf, "\r\n");
  // Stop when the user inputs a line with just a dot.
  while (strcmp(buf, ".")) {
    // Send the line to the server.
    if (send(socketDescriptor, buf, strlen(buf) + 1, 0) < 0) {
      cerr << "cannot send data ";
      close(socketDescriptor);
      exit(1);
    }

//    READ FROM SERVER .... crashes on 2nd-4th try.......

    // Zero out the buffer.
    
    memset(buf, 0x0, LINE_ARRAY_SIZE);
    //if (recv(socketDescriptor, buf, MAX_LINE, 0) < 0) {
    n=read(socketDescriptor, buf, MAX_LINE) ;
    if(n<= 0) {
      cerr << "didn't get response from server?";
      close(socketDescriptor);
      exit(1);
    }

    cout << "Sever: " << buf << "\n";

    // Prompt the user for input, then read in the input, up to MAX_LINE
    // charactars, and then dispose of the rest of the line, including
    // the newline character.  As above.
    cout << "Input: ";
    cin.get(buf, MAX_LINE, '\n');
    while (cin.get(c) && c != '\n')
      ;
  }

  close(socketDescriptor);
  return 0;
}

```

---

### Post by ruy_lopez on 2008-03-22
Do a capture with wireshark/tcpdump, to make sure the data is being transmitted/received properly.

I know next to nothing about C++. I recognise the sockets code, but the rest is alien.

---

### Post by ZeroHimself on 2008-03-22
SOLVED IT!!!!!!!!!!!!:guitar:


The POP3 protocol uses a "\r\n" to terminate commands...., i missed a \r\n, therefor the server got my command, but never executed it.....

then i did a recv() or read(), and it just waited for the data(that wasn't coming because the server was still waiting for my input).......

sometimes i am totally retarted:lolflag:

---

