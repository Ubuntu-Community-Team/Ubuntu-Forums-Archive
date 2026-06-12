---
title: "Developing C++ Multi-platform Socket Class -- Any Need?"
date: 2009-06-07
forum: Programming Talk
---

### Post by qhimq on 2009-06-07
I've looked at a couple of libraries that have socket functionality, but they didn't look like what I wanted.  Is there any libraries that have the following functions implemented for cross platform?

Either way, I'm pretty much done creating the class.  I'm in the testing stages for a variety of operating systems.  I was wondering if there is enough interest for me to release it using the apache license. I have to go through a decent amount of effort to release it outside of my work, so I want to check if its worth it.  I am not very familiar to open source communities because I have never contributed before.

Here are implemented functions so far:
accept
bind
close
connect
listen

//returns actual amount recv'ed
int recv(void *buffer, unsigned int maxToRecv)

// uses the above function for the special purpose of recv'ing data that we know can be interrupted into a C++ string
string RecvString(unsigned int maxToRecv)

// blocks until we have completely recv'ed the desired_len
void recvBlock(void *buffer, unsigned int desired_len)

string recvBlockString(unsigned int desired_len)

// blocks until we have filled buffer w/buflen data or we have filled the buffer with the endData from the socket.
int RecvBlock(void *buffer, unsigned int buflen, void *endData)

string RecvBlockString( unsigned int upperBound, string& endStr)

int Send(void *buffer, unsigned int buflen)

int SendString(string &str)

bool Select(unsigned int millisec)

set<Socket*> getSocketsWaitingToBeRead()

What other forums should I post on, to check interest?

---

### Post by kknd on 2009-06-07
Hi. I've created a small class to do this too, but I only used it once, and may have bugs. The code is in [http://svn.tuxfamily.org/viewvc.cgi/oproj_oprojsvn/socket/trunk/](http://svn.tuxfamily.org/viewvc.cgi/oproj_oprojsvn/socket/trunk/) .

I think that it would be good to have a C++ class that is easy to use and doesn't have much dependencies, so it would be nice if you release your work under a LGPL ou more permissive license.

---

### Post by leblancmeneses on 2009-06-07
This is a common attempt by most programmers.

first really think about the api.  don't just wrap linux api and call it a different name because you become tied to linux operating system.  Example: RecvBlockString

copy from the pros:
[http://www.qtsoftware.com/products/library/modular-class-library#info_networking](http://www.qtsoftware.com/products/library/modular-class-library#info_networking)

[http://msdn.microsoft.com/en-us/library/system.net.sockets.tcpclient.aspx](http://msdn.microsoft.com/en-us/library/system.net.sockets.tcpclient.aspx)

Summary:
if you really want to continue use:
TcpClient
UdpClient
TcpServer
UdpServer


I would really consider just copying microsofts api as they're documentation is easy to get to.

---

### Post by leblancmeneses on 2009-06-07
by the way why not release under MIT license?

example: my open source project.
npeg.codeplex.com

others:
mono project

---

### Post by soltanis on 2009-06-07
Many a general purpose sockets library has been developed. I have found that typically, the low-level implementation works almost perfectly, and out of the original C TCP library I once wrote, I use exactly two functions: nwlisten(int port) - create a socket, bind to a port, and listen for connections, and nwconnect(char *ip, int port) - connect to a remote host.

Notice that these are (not coincidentally) the two most common multi-line tasks for TCP sockets.

If you would like the code, I can public domain it for you.

---

### Post by dwhitney67 on 2009-06-07
Lots of people/organizations already have their own socket library.

Even I have [one]("http://softhouseproductions.com/SocketLibrary-1.1.5.tgz").  Works only with Linux.  Those who wish to write portable s/w apps could consider using SDL_net.

---

### Post by qhimq on 2009-06-08
kknd :: thanks.

leblancmeneses:: I'm not wrapping a linux system call.  I have #ifdef MINGW lines defining where windows dependent lines are.  Your recommended links show .NET dependent and QT dependent code which are very bulky for what I want to do.  They are so bulky I don't even see those functions that I want in those libraries.
mm, I'll worry about the licensing later. But I want it to be open for change and input into proprietary software which MIT and apache licenses offer.

soltanis:: I'm doing much string handling through this class that I *need* to have those above functions I wrote.  I already have those functions you specify.

dwhitney67:: I also do not see any of the blocking functions I need in that SDL_net library.


I have yet to see a socket library that has the functionality I need and that is open for proprietary software.

---

### Post by dwhitney67 on 2009-06-08
> **qhimq said:**
> ...
dwhitney67:: I also do not see any of the blocking functions I need in that SDL_net library.


A socket can be configured to be non-blocking; by default it is set to block on a recv() or recvfrom().

When dealing with TCP, a sent message may be delivered as smaller messages; it is up to the developer to develop s/w to handle this case.  It would be impractical to develop this feature in a library, other than perhaps in a library that is project-specific.

In essence, it is not practical to have an application to block indefinitely while waiting for N bytes of data to arrive.  The reason is because N bytes may not necessarily arrive.  Thus, your recvBlock() method, IMO, is missing a parameter... it should also include a timeout period.  But then, what is the point of that when one can use select()?

The best way to receive data is to use the select() so that the application is notified that data is ready to be received, and then in a loop, use recv() until there is no more data to receive.  Then repeat if necessary.

Something like:
```

unsigned char buffer[1024] = {0};
unsigned int  bytesRcvd = 0;
for (;;)
{
  int sel = select(...);

  if (sel == 0)
  {
    // timeout
    // reset readfds
    continue;
  }
  else if (sel < 0)
  {
    // error
    break;   // or continue?... up 2 u
  }

  // receive data
  while (bytesRcvd < sizeof(buffer))
  {
    int rtn = recv(sd, buffer + bytesRcvd, sizeof(buffer) - bytesRcvd, 0);

    if (rtn <= 0) break;

    bytesRcvd += rtn;
  }

  // check data
  if (expectedDataReceived(buffer, bytesRcvd) == true)
  {
    // process data here?  or elsewhere?
    break;
  }
}

```

---

### Post by qhimq on 2009-06-08
I agree, I would like to have a timeout arg for some applications and this class if it is to be a library.  But I would also want indefinitely blocking functions also.

I think though it would be practical in some cases to assume your data will come...eventually.  My block functions aren't busy waiting and using the select function.  In multi-threaded applications of today I think that assumption isn't extremely dangerous.

---

### Post by dwhitney67 on 2009-06-08
> **qhimq said:**
> ...
I think though it would be practical in some cases to assume your data will come...eventually.  My block functions aren't busy waiting and using the select function.  In multi-threaded applications of today I think that assumption isn't extremely dangerous.

You contradict yourself with the statement above.

Don't assume the data will come eventually; it may not.  And if you want to block indefinitely, then recv(), or recvfrom(), will happily oblige with that.  That's the whole point for using select() --- so that the application does not block with a recv() when no data available for reading.

If you setup your socket to be non-blocking, then a recv() will return immediately, either indicating data has been received or not.  In the case of using a TCP socket, you also be able to determine if the socket has been closed (by the peer).

And as for multi-threaded applications, whether a thread blocks indefinitely, or not, waiting for data is outside the scope of this issue.  That's an application design issue, not a socket issue.  There are cases where a thread's job is to do nothing other than receive data, so it does not matter if it blocks.

I'm no expert in the matter of sockets and threads, but I do consider myself semi-competent in the area since I practically work with this stuff day-in/day-out at my job, and have been doing so for the last 10 years.  I think it was the boredom/chore of having to remember each and every header file needed for each of the flavors of socket library calls that pushed me to develop my own library.

Anyhow, good luck with your library or whatever avenue you take.  Just remember not to confuse the "tools" with the actual "job".

---

