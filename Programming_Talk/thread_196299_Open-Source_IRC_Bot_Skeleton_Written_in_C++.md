---
title: "Open-Source IRC Bot Skeleton Written in C++"
date: 2006-06-14
forum: Programming Talk
---

### Post by QMario on 2006-06-14
Does anyone know where I can download open-source IRC Bot skeletons written in C++?

---

### Post by newteh on 2010-01-09
Bump!

I've recently decided to write a c++ irc client, and struggled to find a nice little skeleton anywhere (I've written a lot of bots in python before). Since this thread is one of the first hits with google, thought I'd post a ""working"" example I've just made (using a few sites on sockets that I'll link to at relevant points). Also, these examples are for unix only (gcc compiler).

First off, a one-file program (just compile with "g++ irc_client.cpp -o irc_client" or whatever). It is largely based on [beej's networking tutorial]("http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html#simpleclient")

```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <string.h>
#include <netdb.h>
#include <sys/types.h>
#include <netinet/in.h>
#include <sys/socket.h>

#include <arpa/inet.h>

#define PORT "6667"

#define MAXDATASIZE 256 // max number of bytes we can get at once 

// get sockaddr, IPv4 or IPv6:
void *get_in_addr(struct sockaddr *sa)
{
    if (sa->sa_family == AF_INET) {
        return &(((struct sockaddr_in*)sa)->sin_addr);
    }

    return &(((struct sockaddr_in6*)sa)->sin6_addr);
}

int main()
{
    int sockfd, numbytes;  
    char buf[MAXDATASIZE];
    struct addrinfo hints, *servinfo, *p;
    int rv;
    char s[INET6_ADDRSTRLEN];

    memset(&hints, 0, sizeof hints);
    hints.ai_family = AF_INET;
    hints.ai_socktype = SOCK_STREAM;

    if ((rv = getaddrinfo("irc.netgamers.org", PORT, &hints, &servinfo)) != 0) {
        fprintf(stderr, "getaddrinfo: %s\n", gai_strerror(rv));
        return 1;
    }

    // loop through all the results and connect to the first we can
    for(p = servinfo; p != NULL; p = p->ai_next) {
        if ((sockfd = socket(p->ai_family, p->ai_socktype, p->ai_protocol)) == -1) {
            perror("client: socket");
            continue;
        }

        if (connect(sockfd, p->ai_addr, p->ai_addrlen) == -1) {
            close(sockfd);
            perror("client: connect");
            continue;
        }

        break;
    }

    if (p == NULL) {
        fprintf(stderr, "client: failed to connect\n");
        return 2;
    }

    inet_ntop(p->ai_family, get_in_addr((struct sockaddr *)p->ai_addr), s, sizeof s);
    printf("client: connecting to %s\n", s);

    freeaddrinfo(servinfo);
    int stay = 1;
    while (stay == 1) {

    if ((numbytes = recv(sockfd, buf, MAXDATASIZE-1, 0)) == -1) {
        perror("recv");
        exit(1);
    }

    buf[numbytes] = '\0';

    printf("%s\n",buf);

}
    close(sockfd);

    return 0;
}

```All this does is simply connect - haven't added the user registration/ping/stuff.

This above code is quite messy, so I decided to split it into a few files - using [this]("http://tldp.org/LDP/LG/issue74/tougher.html") as my motivation. The result is 3 files:

```

/* irc_client.cpp */

#include "Socket.h"
#include "SocketException.h"
#include <iostream>
#include <string>

using namespace std;

const string server = "irc.netgamers.org";
const string port = "6667";

int main ()
{
  try
  {
    Socket sock(server,port);
    if ( !sock.get_address() ) throw SocketException ( "Could not find irc server." );
    if ( !sock.connect() ) throw SocketException ( "Could not connect to irc server." );

    string reply;

    sock >> reply;
    sock >> reply;
    sock << "USER testing11 d d seth000\r\n";
    sock << "NICK testing11\r\n";
    sock >> reply;

    string::size_type loc = reply.find( "PING :", 0 );
    if( loc != string::npos ){
      string pong = "PONG :" + reply.substr(6,-1);
      sock << pong;
      }

    while (true){
      sock >> reply;
    }    
  }
  catch ( SocketException& e )
  {
    cout << "Exception was caught:" << e.description() << "\n";
  }
  return 0;
}

``````

/* Socket.h */

#ifndef Socket_class
#define Socket_class

#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h>
#include <unistd.h>
#include <string>
#include <arpa/inet.h>

const int MAXHOSTNAME = 200;
const int MAXCONNECTIONS = 5;
const int MAXRECV = 500;

class Socket
{
 public:
  Socket(const std::string server,const std::string port);
  ~Socket();

  bool get_address();
  bool connect();
  bool is_valid() const { return m_sock != -1; }
  const Socket& operator >> (std::string&) const;
  const Socket& operator << (const std::string&) const;
 
 private:
  const std::string server;
  const std::string port;

  int m_sock;
  struct addrinfo hints, *servinfo;

};
#endif

``````

/* Socket.cpp */

#include "Socket.h"
#include "string.h"
#include <string.h>
#include <errno.h>
#include <fcntl.h>
#include <iostream>

Socket::Socket(const std::string s, const std::string p) : m_sock(-1), server(s), port(p)
{
  memset ( &hints, 0, sizeof ( hints ) );
  hints.ai_family = AF_INET;
  hints.ai_socktype = SOCK_STREAM;
}

Socket::~Socket()
{
  if ( is_valid() ) ::close ( m_sock );
}


bool Socket::get_address()
{
  int rv = 1;
  rv = getaddrinfo(server.c_str(), port.c_str(), &hints, &servinfo);
// for debugging:  fprintf(stderr, "getaddrinfo: %i\n", rv);
  if (rv != 0) return false;
  return true;
}

void *get_in_addr(struct sockaddr *sa)
{
    if (sa->sa_family == AF_INET) {
        return &(((struct sockaddr_in*)sa)->sin_addr);
    }

    return &(((struct sockaddr_in6*)sa)->sin6_addr);
}

bool Socket::connect ()
{
  struct addrinfo *p;
  int rv, connected;
  char s[INET6_ADDRSTRLEN];

  for(p = servinfo; p != NULL; p = p->ai_next) {
    m_sock = socket(p->ai_family, p->ai_socktype, p->ai_protocol);
    if (m_sock == -1) continue;
    int connected = ::connect(m_sock, p->ai_addr, p->ai_addrlen);
    if (connected == -1){
      close(m_sock);
      continue;}
    break;
  }

  if (connected == -1) return false;

  inet_ntop(p->ai_family, get_in_addr((struct sockaddr *)p->ai_addr), s, sizeof s);
  return true;
}

const Socket& Socket::operator >> (std::string& s) const
{
  char buf [ MAXRECV + 1 ];
  s = "";
  memset ( buf, 0, MAXRECV + 1 );
  ::recv ( m_sock, buf, MAXRECV, 0 );
  s = buf;
  std::cout << ">> " + s << "\n";
  return *this;
}

const Socket& Socket::operator << (const std::string& s) const
{
  ::send ( m_sock, s.c_str(), s.size(), 0 );
  std::cout << "<< " + s << "\n";
}

``````

/* SocketError.h */

#ifndef SocketException_class
#define SocketException_class
#include <string>

class SocketException
{
 public:
  SocketException ( std::string s ) : m_s ( s ) {};
  ~SocketException (){};

  std::string description() { return m_s; }
 private:
  std::string m_s;
};
#endif

```These 4 files can be compiled using a command such as:

```

g++ irc_client.cpp Socket.cpp Socket.h SocketError.h -o irc_client

```Producing an application that can be run with:

```

./irc_client

```Just to repeat - none of this is really my own code - just editted already existing code to work specifically for IRC. I've only just done it and checked that it works, no doubt there's lots of areas where it can be improved upon (well, I know there are - thats the rest of my day taken care of!!).

Cheers

PS. gentoo ftw guys!

---

### Post by newteh on 2010-01-09
While I'm at it, might as well give an example of how to add threading to the irc bot - since this is probably needed to make an irc client: A thread to read from the socket, while your main program (or another thread) allows the user to send input.

Since I am a complete noob with c++ threads, this will undoubtedly be cr*p - but it works! So far.

irc_client.cpp now looks like:

```

#include "Socket.h"
#include "SocketException.h"
#include <iostream>
#include <string>
#include <pthread.h>

using namespace std;

const string server = "irc.netgamers.org";
const string port = "6667";

int main ()
{
  try
  {
    Socket sock(server,port);
    if ( !sock.get_address() ) throw SocketException ( "Could not find irc server." );
    if ( !sock.connect() ) throw SocketException ( "Could not connect to irc server." );

    string reply;

    sock >> reply;
    sock >> reply;
    sock << "USER testing11 d d seth000\r\n";
    sock << "NICK testing11\r\n";
    sock >> reply;

    string::size_type loc = reply.find( "PING :", 0 );
    if( loc != string::npos ){
      string pong = "PONG :" + reply.substr(6,-1) + "\r\n";
      sock << pong;
      }

    pthread_t thread;
    pthread_create(&thread, NULL, &Socket::thread_read, &sock);

    string line;
    char input[512];
    while (true){
      cin.getline(input,512);
      line = input;
      line += "\r\n";
      sock << line;
      if (input == "quit") break;
    }
  }
  catch ( SocketException& e )
  {
    cout << "Exception was caught:" << e.description() << "\n";
  }
  return 0;
}

```I've added a public static function to the Socket class in Socket.h:

```

static void* thread_read (void* arg);

```And in Socket.cpp I've added the following:

```

void* Socket::thread_read (void* arg)
{
Socket* s = (Socket*)arg;

std::string r;
while (true){
  (*s) >> r;
}
return 0;
}

```

---

### Post by dribeas on 2010-01-09
Actually you do not need threads, you can use 'select' to listen for input simultaneously from more than one descriptor. We had to do that at college at one point, but that was long ago, so I don't think I can find the code anymore.

---

### Post by miniCruzer on 2010-10-19
Wow, thanks - this is a big help.

I'm recently interested in starting a project with a C++ IRC Bot, but I couldn't find a good starting place. This seems to be it.

I've tried manipulating this code to fit an actual project. It seems to compile until it reaches the SocketExceptions.

**irc_client.cpp** -> **main.cpp**

```

src/main.cpp: In function ‘int main()’:
src/main.cpp:18: error: no matching function for call to ‘SocketException::SocketException(const char [28], std::string&, std::string&)’
./include/SocketException.h:10: note: candidates are: SocketException::SocketException(std::string)
./include/SocketException.h:8: note:                 SocketException::SocketException(const SocketException&)
src/main.cpp:19: error: no matching function for call to ‘SocketException::SocketException(const char [28], std::string&, std::string&)’
./include/SocketException.h:10: note: candidates are: SocketException::SocketException(std::string)
./include/SocketException.h:8: note:                 SocketException::SocketException(const SocketException&)

```I'm fairly certain everything compiles correctly. These errors are referring to this (irc_client.cpp/main.cpp):

```

      Socket sock(irc.address, irc.port);
      if (!sock.get_address()) throw SocketException ("Could not connect to %s:%s.", irc.address, irc.port);
      if (!sock.connect()) throw SocketException ("Could not connect to %s:%s.", irc.address, irc.port);

```Commenting the above lines clears the errors, but breaks the code and does not connect to the Socket, simply returning an endless loop of ">>" being printed to the console.
```

>> 
>> 
>> 
>>
...

```This appears to be a result of (socket.cpp):
```

const Socket& Socket::operator >> (std::string& s) const
{
  char buf [ MAXRECV + 1 ];
  s = "";
  memset ( buf, 0, MAXRECV + 1 );
  ::recv ( m_sock, buf, MAXRECV, 0 );
  s = buf;
  std::cout << ">> " + s << "\n"; // THIS
  return *this;
}

```

---

### Post by Xaifas on 2011-03-25
Since this thread is on top of google search, here is the most simple structure of an ircbot made in c++

```
#include <iostream>
#include <string>
#include <sys/socket.h>
#include <sys/types.h>
#include <cstring>
#include <netdb.h>
 
using namespace std;
 
int main() {
        int connected = 0; // Used to loop the program
 
        string server = "irc.freenode.net"; // network address
        int port = 6667; // server port
        string nick = "NICK Somebot"; // NICK raw
        string user = "USER Somebot randomtext israndom :My first c++ bot"; // USER raw
 

        /** Structs that hold the socket information **/

        struct sockaddr_in addr;
        struct hostent *host; 

        /** Get an ip address from the network to connect to **/
        host = gethostbyname(server.c_str());

        /** Fill the members of the socket structs required to connect **/
 
        addr.sin_addr.s_addr = *(unsigned long*)host->h_addr;
        addr.sin_family = AF_INET;
        addr.sin_port = htons((unsigned short)port);
        int sockd = socket(AF_INET, SOCK_STREAM, 0);

        /** Connect to address **/
        connect(sockd, (struct sockaddr *)&addr, sizeof(addr));
 
        cout << "Connecting to: " << server << endl;
        send(sockd, nick.c_str(), nick.size(), 0); // Converts nick string to c-array and sends it to server
        cout << "Sent: " << nick << " to server" << endl;
        send(sockd, user.c_str(), user.size(), 0); // Converts user string to c-array and sends it to server
        cout << "sent: " << user << " to server" << endl;
       
        char sockbuff[4096]; // array to hold the incoming socket data
        while (connected < 1) { 
                memset(&sockbuff, '\0', sizeof(sockbuff)); // make sure sockbuff[] is empty
                recv(sockd, sockbuff, 4096, 0); // Recieve all the data from server to sockbuff[]
                cout << sockbuff << endl;;
        }
 
 
        return 0;
}
```

 Enjoy!

---

### Post by dwhitney67 on 2011-03-25
> **Xaifas said:**
> Enjoy!
That won't happen.  The code is lacking the most basic error checking, and appears more like a hack between C and C++.

You'd be better off approaching the solution using neteh's approach.

---

### Post by Xaifas on 2011-03-25
> **dwhitney67 said:**
> That won't happen.  The code is lacking the most basic error checking, and appears more like a hack between C and C++.

You'd be better off approaching the solution using neteh's approach.

It's just a skeleton. It connects and thats it, and its very easy to understand.

newteh's code is harder to understand for beginners.

Anyway, I just gave them another option.

---

