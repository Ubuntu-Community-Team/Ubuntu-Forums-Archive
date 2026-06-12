---
title: "[C++] Some socket problems"
date: 2009-07-10
forum: Programming Talk
---

### Post by psld on 2009-07-10
Hi!
I've tried and tried beginning with socket programming but right now it just feels bad so I'd like some help with this.
It seems like the server never gets any data at all..
If someone could help me I would be really thankful.
**psld@jabber.org**

[http://gunnesgard.se/per/client_server_problem.zip](http://gunnesgard.se/per/client_server_problem.zip)

---

### Post by dwhitney67 on 2009-07-10
You did not describe what problem you were having, nor which protocol (TCP or UDP) you are using.

Here's the basics of a server and a client that use UDP.

Server.cpp:
```

#include <Socket/UDPSocket.hpp>
#include <string>
#include <stdexcept>
#include <iostream>

int main()
{
   using namespace socketpp;
   using namespace std;

   const unsigned int port = 9000;

   try {
      UDPSocket sock;
      string    msg;

      sock.bind(port);

      if (sock.activityDetected()) {
         sock >> msg;
         cout << "Message received: " << msg << endl;
      }
   }
   catch (exception& e) {
      cerr << e.what() << endl;
      return 1;
   }   
}

```

Client.cpp:
```

#include <Socket/UDPSocket.hpp>
#include <string>

int main()
{
   using namespace socketpp;
   using namespace std;

   const string         serverAddr = "127.0.0.1";
   const unsigned short serverPort = 9000;
   const string         msg        = "Hello Server.";

   UDPSocket sock;
   sock.connect(serverAddr, serverPort);

   sock << msg;
}

```

Click [here]("http://softhouseproductions.com/SocketLibrary.tgz") to download the Socket Library demonstrated above.

---

### Post by Mirge on 2009-07-10
> **psld said:**
> Hi!
I've tried and tried beginning with socket programming but right now it just feels bad so I'd like some help with this.
It seems like the server never gets any data at all..
If someone could help me I would be really thankful.
**psld@jabber.org**

**[http://gunnesgard.se/per/client_server_problem.zip](http://gunnesgard.se/per/client_server_problem.zip)**

The browser could not find the host server for the provided address.

---

### Post by psld on 2009-07-11
> **Mirge said:**
> The browser could not find the host server for the provided address.

It works for me but I have uploaded it on the forums now.

I am using TCP, the problem is that when I use the function write(); the server dont get the data.

Thanks for the answers!

---

### Post by dwhitney67 on 2009-07-11
I took a quick peek at your client.cpp; it looks as if you are trying to send the address of the variable 'i'.  Perhaps you wanted to send its value (10)??

Also, consider using send() in lieu of write(), not that it makes much difference, but it is merely the accepted practice.

On your server side, you are reading from the listen socket, not the client socket, which is returned from the accept() call.  That's the problem.

---

### Post by psld on 2009-07-11
> **dwhitney67 said:**
> I took a quick peek at your client.cpp; it looks as if you are trying to send the address of the variable 'i'.  Perhaps you wanted to send its value (10)??

Also, consider using send() in lieu of write(), not that it makes much difference, but it is merely the accepted practice.

On your server side, you are reading from the listen socket, not the client socket, which is returned from the accept() call.  That's the problem.

Thanks! ):P

---

