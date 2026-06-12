---
title: "sending multiple packets via TCP port"
date: 2009-03-02
forum: Programming Talk
---

### Post by tneva82 on 2009-03-02
Alright. Working on my server I decided to start working on client logging systems. I got to point where I can send in join message with username and password and check from file that they match. Groovy! Then I changed already existing message check(shutdown) so that it would check that the user that sent is a) logged in b) is of admin type and changed my quick&easy shutdown program(designed just to give me ability to shutdown program WITHOUT CTRL+C combination ;-) Also how finished product is going to be shutdown anyway. Via logging in as admin and telling server to shutdown).

Then I ran into problem. First message comes up just fine. Second came as garbage.

Okay no problem I thought. I delete buffer to message(char *) and create it new before adding next string. Oops! Didn't work. Finally opted to try to put it to wait. That solved it! sleep(1) before sending second message and it works...BUT it only works if I put 1 or more SECONDS sleep.

That just ain't good enough! I need to send data several times per second! 1 time per second and...Well framerate would be 1FPS which is NOT user friendly ;-)

So...What am I doing wrong? I assume there's got to be a way to send more packets than 1 via TCP port but how? Am I supposed to clear the port after sending message? If so how does one do that in SDL_Net?

Thanks.

---

### Post by dwhitney67 on 2009-03-02
If you are using the SDL_net library, then the documentation ought to describe, or at least provide examples, of how to setup and use a TCP port.  If it doesn't, then perhaps you should consider using a different library.

If all you are doing is sending short messages from a client to a server, you probably should have chosen UDP in lieu of TCP.

With TCP, you need to be aware that packets may not necessarily arrive intact, that you may need to buffer the packets until your s/w has determined that a full message has arrived.  It is common practice when using TCP to mark the packets, either with some special header or with a terminating marker (e.g. a newline).

Without seeing your code, I have to assume that you have not considered these issues.

If you want to peruse a easy-to-use TCP and UDP socket library, developed to support either C or C++ applications, click on this [link]("http://softhouseproductions.com/SocketLibrary-1.0.9.tgz").

Here's an excerpt from the TCP server example C++ code, which handles data being received from the client:
```

void manageClient(socketpp::TCPSocket* client)
{
  using namespace socketpp;

  const int sd = client->GetSocketDesc();

  MsgExtractor               msgExtractor;
  io::IOBuffer<MsgExtractor> ioBuf(*client, &msgExtractor, &MsgExtractor::getMsg);
  fd_set                     savefds;
  bool                       connected = true;

  FD_ZERO(&savefds);
  FD_SET(sd, &savefds);

  while (connected)
  {
    // wait for activity from the client
    while (true)
    {
      fd_set readfds = savefds;
      int    sel = select(sd+1, &readfds, 0, 0, 0);

      if (sel > 0) break;
    }

    // activity detected; attempt to read data
    while (true)
    {
      char buf[1024] = {0};
      int  status    = 0;

      if ((status = ioBuf.getNextMsg(buf, sizeof(buf))) > 0)
      {
        std::cout << "Received from Client " << strlen(buf) << " bytes: " << buf;

        std::ostringstream response;
        response << "Server received: " << buf;

        client->Send(response.str().c_str(), response.str().size());
      }
      else if (status == io::NO_MSG)
      {
        break;
      }
      else if (status == io::LOST_CONNECTION)
      {
        std::cout << "The client disconnected!" << std::endl;
        connected = false;
        break;
      }
    }
  }
}

```
Maybe you can adapt something similar for your code.

---

### Post by tneva82 on 2009-03-02
> **dwhitney67 said:**
> If you are using the SDL_net library, then the documentation ought to describe, or at least provide examples, of how to setup and use a TCP port.  If it doesn't, then perhaps you should consider using a different library.

Well there is this: [http://gpwiki.org/index.php/SDL:Tutorial:Using_SDL_net](http://gpwiki.org/index.php/SDL:Tutorial:Using_SDL_net) but since it's sending data user has written I'm not sure wether it works where you would be sending ~40+ times per second messages. Atleast I seem to be doing essentially same thing but not working(unless I put that triple darned sleep(1) in there.

Edit: Tested and example is working allright. Why on earth mine requires sleep(1)?

> If all you are doing is sending short messages from a client to a server, you probably should have chosen UDP in lieu of TCP.

Probably will switch to it later(TCP speed is probably killing this anyway) but TCP was easier to work for now since I don't want to start figuring out how to make damned sure critical messages really DO get sent out. There's certain data that's absolutly *essential* that comes.

I'll worry about speed later once I get server/client internal operations working.

> Without seeing your code, I have to assume that you have not considered these issues.

Good point but a) messages are so short(first one is 1 xxxxxxx xxxxxxx and second is just 999) it shouldn't be problem and b) why the shorter one would be coming split(and why split 999 anyway?). And c) why it works just fine if I put 1 second sleep but not say 0.5 second sleep? Surely first message doesn't take almost 1 second to come?

Anyway so how does one ensure whole packet has been received then?

As for the link...How cross-platform that is? Ie how easy it's to use same thing for windows version?

---

### Post by dwhitney67 on 2009-03-02
> **tneva82 said:**
> ...

Anyway so how does one ensure whole packet has been received then?

Like I stated earlier, the easiest thing to do is place a marker of some sort in your messages.  This can be the length of the message (usually this would go before the message content) or you can use a newline character at the end of the message.

I rely on the Socket Library I mentioned earlier for my development needs.  However, if I had to throw something together on the fly, where I expected my messages to be newline terminated, something like this could be used (and please note, I have not compiled the code):
```

// assumption is made that 'sd' is the socket descriptor returned
// by the accept() function.

bool clientConnected = true;

while (clientConnected)
{
  fd_set savefds;
  FD_ZERO(&savefds);
  FD_SET(sd, &savefds);

  // loop around until the client sends a message or disconnects
  while (true)
  {
    fd_set readfds = savefds;
    if (select(sd+1, &readfds, 0, 0, 0) > 0) break;
  }

  // activity from the client was detected
  char msg[1024] = {0};    // always setup a fresh msg buffer
  int  bytesRcvd = 0;

  while (!strchr(msg, '\n') || bytesRcvd < sizeof(msg) - 1)
  {
    int rtn = recv(sd, msg + bytesRcvd, sizeof(msg) - bytesRcvd - 1, 0);

    if (rtn <= 0)
    {
      if (rtn == 0) clientConnected = false;
      break;
    }

    bytesRcvd += rtn;
  }

  if (strchr(msg, '\n'))
  {
    // full message received
  }
}

```

> **tneva82 said:**
> 
As for the link...How cross-platform that is? Ie how easy it's to use same thing for windows version?
That Socket Library I pointed out is not supported for Windows, but only for Linux.

P.S. I have intimate knowledge of the aforementioned Socket Library... after all, I developed it!  :-)

---

### Post by tneva82 on 2009-03-02
> **dwhitney67 said:**
> That Socket Library I pointed out is not supported for Windows, but only for Linux.

Well that pretty much rules that out since if I want ever to get some testers for my project(more than myself) I'm pretty much forced to do windows port(which is why I'm using crossplatform libraries like openGL, SDL and SDL_net. Platform specific=no go. I don't want to do more of changing things between versions than needed!).

Edit: Dammit. Just can't figure out. Adding bytesRcvd checks from above just started to cause segmentation errors at worst or at best still same issue. Goddamit!

---

### Post by tneva82 on 2009-03-02
Okay I finally managed to figure out a way to solve this. However anybody could explain WHY it works? Code below:

```
int server::listen() {
  char *buf=new char[MAX_PACKET_SIZE];
  vector<char*> messages;
  myServer->checkForConnections();
  if(myServer->hasActivity()) {
    for (int i=0;i<myServer->getNumberOfClients(); i++) {
      if(myServer->checkAndReceiveData(buf, i, MAX_PACKET_SIZE)>0);
	messages.clear();
	buf=strtok(buf, "*");
	while(buf!=NULL) {
	  messages.push_back(buf);
	  buf=strtok(NULL, "*");
	}

	for(int j=0;j<messages.size();j++) {
	  resolvePlayerMessages(messages[j], i); 
	}
      
    }
  }
  delete buf;
 
  return 0;
}
```

And sending done(as said just simple program to get the program shut down!) like this:

```
  char *buf=new char[60];
  char *parameters=new char[70];
  sprintf(parameters, "username/password");
  sprintf(buf, "%i %s*", GJOIN, parameters);
  printf("Sending: %s", buf);
  count=client->sendData(buf);

  //sleep(1);
  delete buf;
  buf=new char[60];
  sprintf(buf, "%i*", GMSHUTDOWN);
  printf("Sending: %s", buf);
  count=client->sendData(buf);
```

What did the trick was adding * after each command and in the first block of code splitting the buffer by it(happy thing I was planning something like this later anyway to reduce number of packets I'll send. Rather than send every message invidually I instead send packet every 10ms or so with multiple commands combined together and separated by specific letter) before dealing with it.

So why this works?

---

### Post by dwhitney67 on 2009-03-02
Well, it appears that you went with a delimiter between messages.  That helps a lot.

One thing that looks questionable about your code is the heavy mixing of C and C++.  Try to utilize the std::string wherever possible, thus reducing the number of allocations you must make.  I wonder right now if your app has a memory leak, since after all you thrashed around buf with the strtok() call.

It is understandable to see char arrays, but you really should never have to allocate memory unless absolutely necessary.  In your case it is not.  Use the std::string, and in the case of your input buffer, just declare one on the stack.

I wrote a "Chat" application (a pretty lame one IMO) a while back, and the particular thread to handle client messages looks like the following:
```

void
ClientReceiver::operator()()
{
  while (!m_quit)
  {
    struct timeval timeout = {1,0};

    std::vector<TCPSocket *> clients = m_clientTable.CheckClientActivity(timeout);

    // Check if timeout occurred
    if (clients.size() == 0)
    {
      //std::cout << "ClientReceiver is idling..." << std::endl;
      continue;
    }

    for (std::vector<TCPSocket*>::iterator it = clients.begin(); it != clients.end(); ++it)
    {
      TCPSocket* client    = *it;
      char       buf[1024] = {0};
      int        bytesRead = 0;
      bool       connected = true;

      do
      {
        int status = client->Recv(buf + bytesRead, sizeof(buf) - bytesRead);

        if (status <= 0)
        {
          //std::cout << "ClientReceiver: client disconnected." << std::endl;
          m_clientTable.RemoveClient(client);
          connected = false;
        }

        bytesRead += status;
      }
      while (connected && !strchr(buf, '\n'));

      if (connected)
      {
        m_msgQueue.insert(new Msg(client, buf));
      }
    }
  }
}

```
In this code, messages are delimited by a newline, and once a full-message is received, it is packaged into a Msg object and place on a queue where another thread will actually read/process the message.

---

### Post by tneva82 on 2009-03-02
> **dwhitney67 said:**
> I wonder right now if your app has a memory leak, since after all you thrashed around buf with the strtok() call.

How could there if there's delete call for every new call? I try to make damned sure I put delete right after adding new.

---

### Post by tneva82 on 2009-03-03
Crap. Still not working. Maybe I should just scrap the idea since I can't seem to figure this one out.

Now problem is: 4 send commands. First is number and 2 strings. Then comes just number. Then 2 very long(but still within buffer) strings just to test it. 

Now what I get?

I get one very long string which has all 4 sendings in it. And I get this twice.

What the heck.

I hate network coding. Wonder why nobody has created simple layer for those. SDL_Net seemed promising but obviously not as easy to use as I thought. Crap.

---

### Post by tneva82 on 2009-03-03
Okay now I'm getting somewhere. Still odd problem in that piece of text not in client(though seems to be part of server's memory allright) appears. Here's the receiver function:

```
int serverNetwork::checkAndReceiveData(char *answer, int portId, int maxLength) {
  int result;
  int  bytesRcvd = 0;
  
  if(SDLNet_SocketReady(clients[portId])!=0) {
   while(!strchr(answer, '\n') || bytesRcvd < sizeof(answer)) {
      
      result=SDLNet_TCP_Recv(clients[portId], answer+bytesRcvd, 1);
      
      if(result==0) {
	SDLNet_TCP_DelSocket(set,clients[portId]);
	SDLNet_TCP_Close(clients[portId]);
	clients.erase(clients.begin()+portId);
	clientsConnected--;
      }
      bytesRcvd+=result;
    }
    //printf("Answer is: %s\n", answer);
  }
  
  return result;
}
```

And here's the function that calls above function:
```

int server::listen() {
  char *buf; //=new char[MAX_PACKET_SIZE];
  vector<char*> messages;
  myServer->checkForConnections();
  if(myServer->hasActivity()) {
    for (int i=0;i<myServer->getNumberOfClients(); i++) {
      buf=new char[MAX_PACKET_SIZE];
      if(myServer->checkAndReceiveData(buf, i, MAX_PACKET_SIZE)>0);
	printf("%s", buf);
	messages.clear();
	buf=strtok(buf, "*");
	while(buf!=NULL) {
	  messages.push_back(buf);
	  buf=strtok(NULL, "*");
	}

	for(int j=0;j<messages.size();j++) {
	  resolvePlayerMessages(messages[j], i); 
	}
      delete buf;
      
    }
  }
  //delete buf;
  return 0;
}
```

And the code that sends data(nevermind wether text there makes sense. I just wanted some random yet identifiable long text so with Patrick Stewards Hamlet-style performance in kid's show started to type something :D). Put it twice since I didn't want to type in second long message which I wanted to test with.

```
char *buf=new char[60];
  char *parameters=new char[70];
  sprintf(parameters, "username/password");
  sprintf(buf, "%i %s*\n", GJOIN, parameters);
  printf("Sending: %s\n", buf);
  count=client->sendData(buf);

  delete buf;
  buf=new char[900];
  sprintf(buf, "Is this going to work or not, now that is the question that I am wondering. Now why should I worry, if not for the fact that I have had lots of errors before as well. Maybe this is going to work or maybe it will not. However this should give me some rought idea wether it's going to work or not.*\n");
  printf("Sending: %s\n", buf);
  count=client->sendData(buf);

  /*waitTime=SDL_GetTicks()+1;

  while(SDL_GetTicks()<waitTime) {
  }*/

  delete buf;
  buf=new char[900];
  sprintf(buf, "Is this going to work or not, now that is the question that I am wondering. Now why should I worry, if not for the fact that I have had lots of errors before as well. Maybe this is going to work or maybe it will not. However this should give me some rought idea wether it's going to work or not.*\n");
  printf("Sending: %s\n", buf);
  count=client->sendData(buf);
  
  /*waitTime=SDL_GetTicks()+1;

  while(SDL_GetTicks()<waitTime) {
  }*/

  delete buf;
  buf=new char[5];
  sprintf(buf, "%i*\n", GMSHUTDOWN);
  printf("Sending: %s\n", buf);
  count=client->sendData(buf);

```

And here's what I receive:

```
1 username/password*
**tures.sav**Is this going to work or not, now that is the question that I am wondering. Now why should I worry, if not for the fact that I have had lots of [I]error
&#631;s before as well.[/I] Maybe this is going to work or maybe it will not. However this should give me some rought idea wether it's going to work ornot.*
Is this going to work or not, now that is the question that I am wondering. Now why should I worry, if not for the fact that I have had lots of errors before as well. Maybe this is going to work or maybe it will not. However this should give me some rought idea wether it's going to work or not.*
999*
```

Bolded the odd one. Also just noticed there's slight hickup in the area that is in italics. 

Now seems those errors aren't constant and there's also randomly trash in the end as well. What's causing these problems?

---

### Post by eye208 on 2009-03-03
> **tneva82 said:**
> Bolded the odd one.
Buffer overflow?

I agree with dwhitney67, your mix of C and C++ doesn't exactly look trustworthy.

---

### Post by dwhitney67 on 2009-03-03
> **tneva82 said:**
> How could there if there's delete call for every new call? I try to make damned sure I put delete right after adding new.

You do indeed have a 'delete' after each 'new' statement, however the address referenced by pointer you are passing to 'delete' is NOT the same as the address returned by the 'new'.

Here's a simple program that does things correctly; you can verify with valgrind.
```

#include <cstring>
#include <iostream>
#include <string>

int main()
{
  char* buf = new char[1024];

  std::cout << "Enter a string w/ multiple words separated by semi-colons (no spaces!):\n";
  std::cin  >> buf;
  std::cout << "buf = " << buf  << std::endl;

  char* tmp = buf;
  tmp = strtok(tmp, ";");

  int i = 0;
  while (tmp && ++i)
  {
    std::cout << "\tword " << i << " = " << tmp << std::endl;

    tmp = strtok(0, ";");
  }

  delete [] buf;
}

```
Now, to make this code like yours, remote the declaration for 'tmp', and in every place you see 'tmp', replace it with 'buf'.  Then compile the program again and run it with valgrind.

---

### Post by dwhitney67 on 2009-03-03
@ tneva82

Here's a problem:
```

int serverNetwork::checkAndReceiveData(char *answer, int portId, int maxLength) {
  int result;
  int  bytesRcvd = 0;
  
  if(SDLNet_SocketReady(clients[portId])!=0) {
   while(!strchr(answer, '\n') || bytesRcvd < sizeof(answer)) {
...

```
The sizeof(answer) will yield a value of 4, which is the correct size of a pointer (4 bytes).  Replace the sizeof() statement with maxLength - 1.  The "minus one" is so that you leave a space for the null character in your buffer.

Also, it would not kill you to modularize your code a little bit more.  For instance, define a class that manages your client list.  Your server should use this list, and the interface ought to be simple.  There should be a method to add a client, remove a client, and to query if one or more clients have activity.

Next, separate the code that performs the connection accepting from the code that actually handles the client.  I do not have a clear understanding of how listen() is being used, but it appears to be linear... you accept a connection from a client, then you handle data traffic from that client.  In the meantime of course, you are not handling any other clients that may wish to connect.  Maybe you aren't expecting any other clients?

Try to reduce your server code to something simple like this:
```

SetupServerSocket()

Forever
{
  clientSocket = Accept()

  HandleClient( clientSocket )

  DestroyClient( clientSocket )
}

```

For HandleClient():
```

clientConnected = true;

EnableNonBlocking( clientSocket );

Do
{
  Wait until ActivityDetected( clientSocket )

  bytesRcvd = 0

  Do Forever
  {
    status = RecvMessage( clientSocket, buffer + bytesRcvd, sizeof(buffer) - bytesRcvd - 1 )

    If (status > 0)
    {
      bytesRcvd += status;

      If ( (msgLen = GotMessage( buffer, bytesRcvd )) > 0 )
      {
        // do something with message in buffer using the number of msgLen

        // adjust buffer
        memcpy(buffer, buffer + msgLen, bytesRcvd - msgLen)
        buffer[bytesRcvd - msgLen] = '\0'
        bytesRcvd -= msgLen
      }
    }
    Else If (status < 0 && errno == EWOULDBLOCK)
    {
      break from Forever
    }
    Else
    {
      clientConnected = false
      break from Forever
    }
  }
} while (clientConnected == true)

```

For GotMessage():
```

msgLen = 0

if ( (pos = strchr(buffer, ';')) )
{
  msgLen = pos - buffer
}

return msgLen;

```

---

### Post by tneva82 on 2009-03-03
> **eye208 said:**
> Buffer overflow?

I agree with dwhitney67, your mix of C and C++ doesn't exactly look trustworthy.

Buffers are overallocated as it is for safe measure.

And I'll use string the second C functions I need accept them as parameters. Before that I won't beg headaches altering between string and char arrays as needed. Much simpler to keep it unified.

---

### Post by tneva82 on 2009-03-03
> **dwhitney67 said:**
> Also, it would not kill you to modularize your code a little bit more.  For instance, define a class that manages your client list.  Your server should use this list, and the interface ought to be simple.  There should be a method to add a client, remove a client, and to query if one or more clients have activity.

Hmm. I have class server which uses class servernetwork. You mean I should have class within class within class? And why the servernetwork class can't handle clients?

> Next, separate the code that performs the connection accepting from the code that actually handles the client.  I do not have a clear understanding of how listen() is being used, but it appears to be linear... you accept a connection from a client, then you handle data traffic from that client.

No. I check for connections and then listen for **all** clients I have(if any). I simply accept before checking wether client ports has activity as I figured it makes more sense to handle any message new client has rightaway rather than next loop.

> 
 In the meantime of course, you are not handling any other clients that may wish to connect.  Maybe you aren't expecting any other clients?

```
myServer->checkForConnections();
```

This accepts new connections(though come to think about it I could alter that to accept connections 'till there's no connections to be accepted. Why didn't I think about that before. Albeit I don't really expect get 2+ connection attempts within 1 loop but what the heck. Might just as well do it since there's no harm in there).

```
if(myServer->hasActivity()) {
```

Is there any activity in ANY of the client sockets I have?

```
for (int i=0;i<myServer->getNumberOfClients(); i++) {
      buf=new char[MAX_PACKET_SIZE];
      memset(buf, ' ', strlen(buf));
      if(myServer->checkAndReceiveData(buf, i, MAX_PACKET_SIZE)>0);
```

Go through ports and if there's activity in said port(done in checkAndReceiveData function) read it. Don't know how to make it more simultaneous without using threads and since that requires locks for tons of different variables to prevent 2 threads accessing same stuff at same time I figured I worry about that part later. Enough source for errors as it is.

> 
For HandleClient():
[code]
clientConnected = true;

EnableNonBlocking( clientSocket );

Do
{
  Wait until ActivityDetected( clientSocket )

Wouldn't this precicely cause program to wait in client #1 for activity before moving on? This isn't using threads! I need function to stop right there if there's no activity. NOT wait for activity. If there's no activity then forget that client and move on. There's too few computer cycles as it is. No need to waste them waiting for activity that might happen in next 10 milliseconds or next 10 minutes...(yeah there could be theoretically situation where client won't send anything for n+1 unless I put some sort of ping system there but that would be initiated from server side so again can't afford to wait for activity here).

---

### Post by tneva82 on 2009-03-03
> **dwhitney67 said:**
> The sizeof(answer) will yield a value of 4, which is the correct size of a pointer (4 bytes).  Replace the sizeof() statement with maxLength - 1.  

Won't work. I get segmentation errors instead. I'll accept some random trash(which doesn't seem to interfere with the program's running either) at the end of program any day over segmentation error.

---

### Post by dwhitney67 on 2009-03-03
If you want to service more than one client, you can do so with a single thread, although a new client may have to wait before getting connected because you may be servicing another client.

All things that you are trying to accomplish have been solved by other developers, including myself.  I look at your code, and all I can do is shake my head in amazement on how complex you have made it.

You could simplify you code immensely if you would redesign portions of it.  But since you are unable to get even the comm between one client and the server working, I question your need to support multiple clients at this time.

I've seen another forum member who was using SDL_net for his app, and once again, the code was complex.  SDL_net, IMPO (P == Professional) is a POC.  The API is horrible, and is very C-like... not very useful in C++ applications.

I am advising you to take a step back, rewrite your server without the SDL nonsense, to handle ONE client.  Try to get it done within an hour or two.  It's a piece of cake.  I'm almost tempted to do it for you, but since you insist on it being M$ compatible, it may take me 20 years to put it together.  If all you want is Linux compatible, then shoot, I will have it ready in about an hour.  Just refresh my memory on what the message protocol is between the client/server.

---

### Post by tneva82 on 2009-03-03
> **dwhitney67 said:**
> All things that you are trying to accomplish have been solved by other developers, including myself.  I look at your code, and all I can do is shake my head in amazement on how complex you have made it.

I'm sure they have been but I figure they have either been lot smarter people able to figure these things by themselves or have had better help available than I have. I'm going by SDL_Net's API and that's it. Oh sure I could have socket API but that's even worse since there's bunch of more variables and functions I need to figure out what to do with them.

So precicely what's so overcomplicated I have done?

ATM I accept connections, put them in vector, check wether there's any activity and if there are loop through them to see wether that's active. If it is read it.

ATM actually it's working pretty well apart from that unimportant trash(if it doesn't interfere with program as it doesn't I don't particulary care about it) and trying to figure out how to read whole line from file WITHOUT new line in the end.


> I've seen another forum member who was using SDL_net for his app, and once again, the code was complex.  SDL_net, IMPO (P == Professional) is a POC.  The API is horrible, and is very C-like... not very useful in C++ applications.

Still by far easiest solution I have found. I looked at using sockets without any additional API but that seemed even harder as I would have to...Well basicly reimplemet everything in SDL_Net myself. Not fun.

>  but since you insist on it being M$ compatible

Not something I have control over. Not much of a good doing software if you can't then even test wether it works or not. Afterall how can I then see wether it works if I can't TEST it? Sure I can SAY it works but for all I know it works only with one client and second causes it go BOOM! Or some other weirdness. Not to mention I can't get half-decent idea how well it handles multiple clients in pure efficiency terms(ie does multiple clients cause it to lag too much. This thing is supposed to operate atleast 30+ times per second for the client).

Frankly starting to feel like I should just say screw it to both project and programming alltogether since I'm obviously too stupid to code anything more complicated than "hello world!".

---

### Post by dwhitney67 on 2009-03-03
Here's some server code that you can play with.  It is single-threaded, yet uses fork to handle one or more clients.  If you expect high-rates of message traffic between your server and clients, then I suggest you create a multi-threaded application so that client messages can be received and processed in separate threads.

```

#include <string>
#include <iostream>
#include <stdexcept>
#include <cstdlib>
#include <cerrno>
#include <cstring>
#include <csignal>

// You can take these headers and the function prototype that follow, and
// replace with the equivalent SDLnet functions.
//
#include <sys/socket.h>
#include <sys/types.h>
#include <netdb.h>
#include <fcntl.h>


void Bind(int sd, const std::string address, const unsigned short port);
void FillAddress(int domain, const std::string& address, const unsigned short port,
                 struct sockaddr_in& addr);
void Listen(int sd, int backlog);
int  Accept(int sd);
void SetNonBlocking(int sd);
int  Recv(int sd, char* buf, const size_t bufSize);
//
//  End of non-SDLnet code


void HandleClient(int sd);
size_t GetMessage(const char* buf, const size_t bufLen);

bool done = false;

void sigHandler(int signum)
{
  done = true;
}

int main(int argc, char** argv)
{
  signal(SIGINT, sigHandler);

  try
  {
    const std::string    serverAddr = (argc > 1 ? argv[1] : "localhost");
    const unsigned short serverPort = (argc > 2 ? atoi(argv[2]) : 50000);

    std::cout << "Server is using serverAddr = " << serverAddr
              << " and serverPort = " << serverPort
              << std::endl;

    int serverSock = socket(AF_INET, SOCK_STREAM, 0);

    Bind(serverSock, serverAddr, serverPort);
    Listen(serverSock, 5);
    SetNonBlocking(serverSock);

    while (!done)
    {
      int clientSock = 0;

      if ((clientSock = Accept(serverSock)) > 0)
      {
        if (fork() == 0)
        {
          HandleClient(clientSock);

          close(clientSock);
        }
      }
    }

    close(serverSock);
  }
  catch (std::exception& e)
  {
    std::cerr << "Exception: " << e.what() << std::endl;
    return 1;
  }
}


void HandleClient(int sd)
{
  SetNonBlocking(sd);

  bool connected = true;

  fd_set savefds;
  FD_ZERO(&savefds);
  FD_SET(sd, &savefds);

  while (connected)
  {
    while (true)
    {
      struct timeval timeout = {1,0};
      fd_set readfds = savefds;
      if (select(sd+1, &readfds, 0, 0, &timeout) > 0) break;
    }

    // activity detected
    char buf[1024] = {0};
    int  bytesRcvd = 0;

    while (true)
    {
      int status = Recv(sd, buf, sizeof(buf));

      if (status > 0)
      {
        int msgLen = 0;

        bytesRcvd += status;

        while ((msgLen = GetMessage(buf, bytesRcvd)) > 0)
        {
          std::string msg = std::string(buf).substr(0, msgLen);
          std::cout << "Msg of " << msgLen << " byte(s) received: " << msg << std::endl;

          memcpy(buf, buf + msgLen + 1, bytesRcvd - msgLen);
          buf[bytesRcvd - msgLen] = '\0';
          bytesRcvd -= (msgLen +1);
        }
      }
      else if (status < 0 && errno == EWOULDBLOCK)
      {
        break;
      }
      else
      {
        connected = false;
        break;
      }
    }
  }
}


size_t GetMessage(const char* buf, const size_t bufLen)
{
  if (bufLen < 1) return 0;

  const char* pos     = strchr(buf, ';');
  size_t      msgSize = (pos ? pos - buf : 0);

  return msgSize;
}


void Bind(int sd, const std::string address, const unsigned short port)
{
  struct sockaddr_in addr;

  FillAddress(AF_INET, address, port, addr);

  if (bind(sd, (struct sockaddr*) &addr, sizeof(struct sockaddr_in)) != 0)
  {
    throw std::runtime_error("Could not bind socket.");
  }
}


void FillAddress(int domain, const std::string& address, const unsigned short port,
                 struct sockaddr_in& addr)
{
  if (address == "")
  {
    memset(&addr, 0, sizeof(struct sockaddr_in));

    addr.sin_family      = domain;
    addr.sin_addr.s_addr = htonl(INADDR_ANY);
    addr.sin_port        = htons(port);
  }
  else
  {
    struct addrinfo* host_info = 0;

    if (getaddrinfo(address.c_str(), 0, 0, &host_info) != 0  ||
        !host_info || !host_info->ai_addr || host_info->ai_family != domain)
    {
      if (host_info) freeaddrinfo(host_info);
      throw std::runtime_error("Error getting address information.");
    }

    memcpy(&addr, host_info->ai_addr, sizeof(struct sockaddr_in));
    addr.sin_port = htons(port);

    freeaddrinfo(host_info);
  }
}


void Listen(int sd, int backlog)
{
  if (listen(sd, backlog) != 0)
  {
    throw std::runtime_error("Error listening on socket.");
  }
}


int Accept(int sd)
{
  return accept(sd, 0, 0);
}


void SetNonBlocking(int sd)
{
  int flags = fcntl(sd, F_GETFL, 0);

  if (fcntl(sd, F_SETFL, flags | O_NONBLOCK) < 0)
  {
    throw std::runtime_error("Cannot change socket to non-blocking.");
  }
}


int Recv(int sd, char* buf, const size_t bufSize)
{
  int rcvdBytes = 0;

  if ((rcvdBytes = recv(sd, buf, bufSize, 0)) < 0 && errno != EAGAIN)
  {
    throw std::runtime_error("Recv failed.");
  }

  return rcvdBytes;
}

```

---

### Post by tneva82 on 2009-03-03
Your code is precicely the reason why I use SDL_Net. I understand maybe 20% of the socket code there. Not much of a help there since I have no idea how that code works.

Bleh. I just accept that random trash at the end. Since it doesn't interfere with the program I'll live with it rather than try to create multi-platform raw socket library myself. Assuming I won't just quit whole programming to begin with.

One would think SOMEBODY would have made something like that which isn't crap but guess not if SDL_Net is crap.

---

### Post by dwhitney67 on 2009-03-03
> **tneva82 said:**
> Your code is precicely the reason why I use SDL_Net. I understand maybe 20% of the socket code there. Not much of a help there since I have no idea how that code works.

Bleh. I just accept that random trash at the end. Since it doesn't interfere with the program I'll live with it rather than try to create multi-platform raw socket library myself. Assuming I won't just quit whole programming to begin with.

One would think SOMEBODY would have made something like that which isn't crap but guess not if SDL_Net is crap.

One can run a Server under Linux and test it with a Client running under another Linux system, a Windoze system, or even a Mac.  Your testers can be on any platform they wish.

As for the translation from Linux-specific functions to SDLnet functions, it shouldn't be that difficult.  A server must always perform the following:

1.  create a socket
2.  bind to the socket
3.  listen on the socket
4.  accept connection(s)

Optionally the server can configure their socket to be non-blocking, but it is not required.  I only did it in the sample code above because I wanted to cleanup properly when I interrupted the program using a ctrl-c.

---

### Post by tneva82 on 2009-03-03
> **dwhitney67 said:**
> One can run a Server under Linux and test it with a Client running under another Linux system, a Windoze system, or even a Mac.  Your testers can be on any platform they wish.

So I should do the server with linux specific system and then create client for both linux AND windows...Ummmm...Why not use multi-platform solution for the network as well? What's the benefit for using platform dependant solution for server(nevermind that in theory if this would be complete product server should be crossplatform product as well though I doubt I'll ever get this that far anyway) and then while creating client switch to platform independent solution?

Dunno. Getting it working right in one system is hard enough I don't want to do it for two systems.

Or did you think client is some ready made software and I'm just coding server? Oh no. I need to do BOTH programs. If I don't program client then I have server looping pretty useless. Sure it can do some of stuff but with no clients not that much.

> 1.  create a socket
2.  bind to the socket
3.  listen on the socket
4.  accept connection(s)

1) Check
2) Bind? Only bind functions in SDL_Net is for UDP. No Bind function for TCP.
3) Check
4) Check(though done before listening).

I already do those.

> Optionally the server can configure their socket to be non-blocking, but it is not required.  I only did it in the sample code above because I wanted to cleanup properly when I interrupted the program using a ctrl-c.

Blocking is program killer for this. I can't have it blocked waiting for the one client who happens to be on lunchbreak and ergo won't send any activity for half an hour. Would freeze other clients as well.

---

### Post by dwhitney67 on 2009-03-03
> **tneva82 said:**
> ...

1) Check
2) Bind? Only bind functions in SDL_Net is for UDP. No Bind function for TCP.
3) Check
4) Check(though done before listening).

I already do those.

The SDL_Net probably does the Bind step automatically (maybe when the socket is created?).  You can bind a socket to a port, or to a port at a specific address (e.g. "localhost" or IP address), or too a socket-file.

> **tneva82 said:**
> 
Blocking is program killer for this. I can't have it blocked waiting for the one client who happens to be on lunchbreak and ergo won't send any activity for half an hour. Would freeze other clients as well.
I think you are confused wrt the server socket descriptor and the client socket descriptor.  The latter should be setup as non-blocking; the former does not need to be.

Btw, I get the impression that you are frustrated with my help/advice, so I am going to go on my way.

---

### Post by tneva82 on 2009-03-03
> **dwhitney67 said:**
> Btw, I get the impression that you are frustrated with my help/advice, so I am going to go on my way.

Not with your help no. Frustrated with my lack of progress yes. Sorry if I'm sounding rude. Just getting major headaches from this.

However on more positive note I THINK it's working now. Not sure but this is output I'm getting ATM:

Connection established! // good. Connection received
1 username/passwd //excelent. First command succesfully through
8 Rufus Valkoparta* // managed to read the file. This is string that's going to be sent back to client

Is this going to work or not, now that is the question that I am wondering. Now why should I worry, if not for the fact that I have had lots of errors before as well. Maybe this is going to work or maybe it will not. However this should give me some rought idea wether it's going to work or not. // first long string through. No problems
Is this going to work or not, now that is the question that I am wondering. Now why should I worry, if not for the fact that I have had lots of errors before as well. Maybe this is going to work or maybe it will not. However this should give me some rought idea wether it's going to work or not. // second through. STILL no problems
999 // good. Shutdown received
GMSHUTDOWN RECEIVED! // groovy. No trash between 999 and this which was last issue.

So as far as I can tell I have somehow got this working though since I have little idea what SDL_Net does or how it's supposed to be used it still might have some issues that only pops up under heavy message input but since I don't have client done(nor windows port of the program which is required. Unless I want to buy multiple new computers and program AI for the client so that it can do the testing without human input. Yea right. No money for new computers and programming AI seems harder than porting to windows) can't test that one.

So I'll proceed with the assumption this works as it's meant, hope any changes I might have to do can be done within xxxnetwork class(and ergo not interfere with logic of program) and start working on server-client communication to the point I can start work on the client. Not much else I can do ATM.

Oh and how can any socket be blocking if it's absolutly **crucial** program doesn't wait for activity _anywhere_ but keeps looping through functions as fast as the computer's calculation power allows it? The faster the better. I thought blocking means precicely that. Blocks program from continuing until something happens that unblocks it.

---

### Post by dwhitney67 on 2009-03-03
Try to keep your server application "simple".

The server should setup a socket and await for a connection from a client.  If it gets a connection, spawn a new process or thread to handle that client, and then return back to waiting for another client.

Assuming the server's socket is setup, here's the gist of what I'm saying:
```

...
  // accept connections
  while (true)
  {
    socketpp::TCPSocket* client = server.Accept();

    if (client)
    {
      if (fork() == 0)
      {
        manageClient(client);
        delete client;
      }
    }
  }

```

See how simple!  The server blocks on Accept().  When a client connects, I create a new process to manage the communications with that client.  The existing process wraps around the while-loop and sits there listening for any new connections.  The client on the other hand (mind you, in a separate process) is busy being serviced. 

Here's how manageClient() could be implemented:
```

void manageClient(socketpp::TCPSocket* client)
{
  using namespace socketpp;

  MsgExtractor               msgExtractor;
  io::IOBuffer<MsgExtractor> ioBuf(*client, &msgExtractor, &MsgExtractor::getMsg);
  bool                       connected = true;

  while (connected)
  {
    if (client->ActivityDetected())
    {
      // activity detected; attempt to read data
      while (true)
      {
        char buf[1024] = {0};
        int  msgLen    = 0;

        if ((msgLen = ioBuf.getNextMsg(buf, sizeof(buf))) > 0)
        {
          // Ok, got a message.  It is in buf, and it is null terminated.
          // The message length is msgLen.
          // Now do something with the message!
        }
        else if (msgLen == io::NO_MSG)
        {
          break;
        }
        else if (msgLen == io::LOST_CONNECTION)
        {
          std::cout << "The client disconnected!" << std::endl;
          connected = false;
          break;
        }
      }
    }
  }
}

```
Ok, the code above looks complicated, but it is really easy.  The IOBuffer object is used to receive data from the client.  The data is received each time getNextMsg() is called... in other words, whenever client activity has been detected.

getNextMsg() parses the data received by the client to determine if indeed there is a complete message present.  If there is a complete message, do something with it.  If there is no message, then wait for more activity from the client.  If activity from the client is detected, and the receive returns a 0, that indicates the client has disconnected.

Once again, bear in mind that when all this stuff is happening with the client, the main server process is still cheerfully, and independently of the client, accepting other client connections.

P.S.  The IOBuffer object sets up the client's socket to be Non-Blocking.

P.S.S.  getNextMsg() calls the getMsg() function of MsgExtractor to determine if there is a message.  Think of IOBuffer as merely a reader.  It is up to MsgExtractor to tell IOBuffer if there is a valid message in the IOBuffer's internal buffer.

If you want to see the code for IOBuffer and MsgExtractor, _let me know_.  The IOBuffer code calls recv() and fcntl().  There are M$ equivalents for these functions... or just find/use the appropriate SDL_Net equivalent.

---

### Post by dwhitney67 on 2009-03-03
Try this:
```

#include <SDL_net.h>
#include <string>
#include <cstdlib>
#include <csignal>

bool done = false;

void sigHandler(int signum)
{
  done = true;
}


int main(int argc, char** argv)
{
  signal(SIGINT, sigHandler);


  const std::string    serverAddr = (argc > 1 ? argv[1] : "localhost");
  const unsigned short serverPort = (argc > 2 ? atoi(argv[2]) : 50000);
  IPaddress            ip;

  SDLNet_Init();
  SDLNet_ResolveHost(&ip, serverAddr.c_str(), serverPort);

  TCPsocket sd = SDLNet_TCP_Open(&ip);

  while (!done)
  {
    TCPsocket csd = SDLNet_TCP_Accept(sd);

    if (csd)
    {
      if (fork() == 0)
      {
        manageClient(csd);
        SDLNet_TCP_Close(csd);
      } 
    } 
  }

  SDLNet_TCP_Close(sd);
  SDLNet_Quit();
} 


void manageClient(TCPsocket& csd)
{
  bool connected = true;

  while (connected)
  {
    if (SDLNet_SocketReady(csd)) // ????
    {
      char buf[1024] = {0};
     
      if (SDLNet_TCP_Recv(csd, buf, sizeof(buf) - 1) > 0)
      {
        // message received.
      }
      else
      {
        connected = false;
      }
    }
  }
}

```

---

### Post by tneva82 on 2009-03-03
> **dwhitney67 said:**
> Try to keep your server application "simple".

The server should setup a socket and await for a connection from a client.  If it gets a connection, spawn a new process or thread to handle that client, and then return back to waiting for another client.

I think I'll settle for single thread program and loop through ports for now. Much safer this way than to start worrying about 2+ threads accessing same data at the same time(by the nature of program I can quarantee there's going to be a lot of those 30+ times a second(assuming program works as fast as it needs to work). I don't want to add THAT complication to things as well! I have quite enough to worry about already thank you very much ;-) I don't want to start debugging multi-threaded programs before I get it working in single thread first.

Hard enough to get it working in single thread. About everything I have read on programs with multiple threads warns it's not going to be easy and my program has tons of data multiple clients could be altering/reading and repeatedly. Sounds perfect recipe for disaster in my book.

And since my program seems to be working(can't be sure but that's only reason enough to get working on internal logic of the server and not worry about network for now and then get rudimentary client so I could actually start to do some REAL testing that simulates what happens when client joins. Don't think I can be sure at all wether it works or not before I can get the client up and running so I can test wether it's going to break it) I most DEFINETLY don't want to start messing around with it for now. Making it multithreaded is all very good and probably where I head eventually anyway(since this program is so speed dependant why not use advantage of multiple processors if available? Assuming of course using those happens by creating additional threads to run) but for now...I'll start working on the REAL meat of the project and leave the network code for now since it seems to be working(atleast I haven't seen a glitch for a while from the test client use I have though it's seriously limited. But then again neither does server do all that much...Which is why that's area I should work for now).

---

### Post by dwhitney67 on 2009-03-03
If it's any consolation, I once worked on an application which required the receiving of up to 2300 TCP messages per second, and "concurrently", up to 100 UDP messages per second.

The application was multi-threaded and ran on a dual-processor SunSparc system.

With the Boost thread library, setting up a thread is cake, and preventing concurrent access to shared objects can be managed with Boost thread library's mutex and scoped_mutex.

---

### Post by eye208 on 2009-03-04
> **tneva82 said:**
> Buffers are overallocated as it is for safe measure.
There is no safety in over-allocation, only waste of resources. If you don't do boundary checks, the person providing the username and password can break your code and make it do funny things. This has happened thousands of times before, and each time the programmer thought he was safe because of over-allocation.

> And I'll use string the second C functions I need accept them as parameters. Before that I won't beg headaches altering between string and char arrays as needed. Much simpler to keep it unified.
C++ has classes not only for strings but also for TCP streams and threads. Reading/writing a TCP stream is as easy as reading/writing a file.

There is no reason to mix C and C++ the way you do. dwhitney67 is right: The proper way to implement a multi-client TCP server is with threads and blocking calls. Blocking is not a problem because you can define a timeout after which the read call will throw an exception so you can drop the connection and terminate the thread for that client. Using mutex objects you can serialize the client/server communication. Your code will be more robust and easier to maintain. I remember you calling me ["blindsided"](http://ubuntuforums.org/showthread.php?p=6732559#post6732559) for pointing out the obvious, but that's the way to do things in C++ unless you are willing to settle for subpar solutions.

---

### Post by tneva82 on 2009-03-04
> **eye208 said:**
> There is no safety in over-allocation, only waste of resources. If you don't do boundary checks

Oh client WILL check for boundaries. Just meant that there's no way they could go over here as I have made damned sure the client tester sends out messages that are more than short enough for the buffer.

> C++ has classes not only for strings but also for TCP streams and threads. Reading/writing a TCP stream is as easy as reading/writing a file.

And how easy it is to apply those strings to C functions I need?-) Plenty of those I can find use for.

> The proper way to implement a multi-client TCP server is with threads and blocking calls. Blocking is not a problem because you can define a timeout after which the read call will throw an exception so you can drop the connection and terminate the thread for that client.

Timeout? Gee that just ain't good enough. If I waste even 5ms waiting each loop for activity...Well let's see. 5 clients(and in theory this should be able to handle dozens of clients). Let's say I put 40FPS as goal(and I know people who would baulk at such low FPS). So 40 loops. Each loop therefore wastes 5x5ms=25ms or for one second 1000ms wasted...

...Wait a second...Isn't 1000ms precicely one second? So in program which handles "merely" 5 clients I would need to do rest of the stuff(heavy mathematics) instantly.

Somehow I'm not convinced.

Also multithreaded is recipe for disaster. If I can't get this working(though as I have said several times already CODE WORKS already!!! Why I should go for multithreaded now to "fix" it when it already works?) why you think I wouldn't get gazillion segmentation faults and funny errors by exponentially more complicated multi-threaded program?

I don't need to worry about how to ensure efficient and safe multithreaded program. Safe isn't good enough. Since each client needs other clients data I would need multithreaded solution that doesn't kill performance when one client waits for other to release access to his own resources. So the speed gain I would gain from multi-threaded program might be negated(or go even negative) from inefficient multi-threaded solution.

And then there's of course "simple" problem of ensuring program doesn't just crash thanks to some data slipping unprotected and getting modified by 2+ threads at the same time.

Sorry but haven't seen yet one good reason told why I should change working single-thread solution to multi-threaded nightmare which I might or might not be able to produce. Speed would be handy enough but now I would like to get internal logic working so I could start to figure out how much of a more speed I need before worrying about speed and how to get multithreaded program working to begin with.

Sorry but troll saying I should change working solution to highly lot harder solution isn't all that convincing. I worry about getting program to run faster when it's time there's actually need for faster program. And still not convinced spending seconds in merely to wait inactive clients to timeout doesn't sound good idea when program depends on speed. Blocks=bad. Very bad. Fine for non-speed critical programs. Killers for speed critical programs.

---

### Post by dwhitney67 on 2009-03-04
@ tneva82

You comments appear to be derived from inexperience.  If I were to design your application, I would have one dedicated thread to handle client connections.  When a client connects, I would add that client's connection information to a ClientTable.

If I am expecting between 1-10 clients, then I would have another thread to handle the receiving of client messages.  Anymore clients than 10 would probably dictate that separate threads be used; either one thread per client or one thread for every 5-10 clients.

As this point, you can decide whether you want these client-message-receiving threads to process client messages, or just simply place these messages onto a queue where another thread (or threads) can be used to process the messages (and if necessary, send back a response to the client).

You make it sound like your application is unique, and that it's a monumental challenge, similar to like putting a man on the moon.  But all kidding aside, it is only difficult if 1) you think it is, and/or 2) you make it that way.

And from my experience, taking an application similar to yours to its full completion, and then later trying to convert it to a multi-threaded application is not fun.  You need to make design decisions early in the process, not late or after the project is "complete".  If you will go with the multi-threaded approach, do it now.

Anyhow, good luck with your endeavour.   From what you've stated, it appears that you got the TCP side of your project working, which is fantastic.

---

### Post by tneva82 on 2009-03-04
> **dwhitney67 said:**
> 
You make it sound like your application is unique, and that it's a monumental challenge, similar to like putting a man on the moon.  But all kidding aside, it is only difficult if 1) you think it is, and/or 2) you make it that way.

No. What I'm saying is that ATM it's not worth the effort to make it multi-threaded applications whose complexity is expontentially bigger than single threaded. Look. 99% testing will be done by myself. That's ONE thread. Remaining 1% will be done with 2, maybe 3 clients at the same time. Single threaded program might not be most efficient but I seriously doubt biggest bottleneck of the program will be network code with 2 or 3 clients.

For program to seriously need the speed for more clients I would need to get the program to be good enough that lots of people would want to use it. And THAT would require a) need to do bloody lot bigger program than I'm planning to anyway(this is more of a can I do framework of program rather than full program. I figure it would take good part of a decade for me to code up FULL program myself. There's a reason why companies doing this have multiple programmers!) b) hire up more people to make up non-coding part like 3d models, 2d art, music and whatnot c) buy myself dedicated server machine d) buy myself static IP address and domain name for the program e) begin massive advertisement campaign to actually get people to _use_ the client rather than commercially available higher quality products.

Now how much of the above sounds likely?-) I just don't see myself being able to hire(that means PAY) people to do stuff I have absolutly no skills in(my ability in graphic department can be summed as drawing boxes and if I would compose music people would throw their speakers out of the room if that's only way to not listen to it!). Nor do I see myself having much of a interest to buy efficient computer just to run this server. Nor pay out for static address for said computer so that clients can connect to it without problems of IP address changing. And frankly how could I compete with existing solutions? There's even **free** high quality solutions. Kinda hard to compete with that.

So why worry about speed for now when other aspects are lot more critical than ability to handle multiple clients in multi-threaded enviroment.

Frankly if I get to point where the 5 points above would be feasible I would have programmed on this long enough that it would be more efficient to program the server from scratch and optimise whole thing from the core while adding multi-threaded ability and utilising experience gained while programming the single thread version. As it is I expect biggest speed bottlenecks not to come from network connection(when biggest amount of simultaneous clients I expect to run is 3. MAYBE 4 if I'm lucky) but from the internal workings which have very little to do with network code. Network provides input and output. Bottleneck is likely going to be between those two.

I have more than enough stuff to study already without adding complex multi-threaded program logic into the mix. If I ever get to point where I actually might have serious need for multi-threaded programs I'll seriously look into reworking whole thing from scratch ANYWAY and keeping only elements of design I like(mainly what I want to accomplish) and start up company for it(since I would need to start to look at the project from viewpoint of how to make money with it to allow me to hire additional people it would need if I ever want it to be used in bigger enviroment than me and my friends testing just for fun of it).

I might be mad but I'm not mad enough to think this will ever be bigger program than personal curiosity and wish to program SOMETHING. Programming stuff I don't need has never been inspiring enough and there's nothing I really need which is suitably small I could get high quality product done in reasonable time. Therefore I code rather framework of bigger program out of sheer curiosity to see parts of how it's done to satisfy own curiosity.

Edit: Oh and one more reason to scrap current program and redesign from scratch if I need to handle dozens of clients at same time. TCP. Slow=bad. I would need to figure out a way to get reliable enough system with UDP since there's data that absolutly **has** to reach client/server. After figuring out some sort of a system for that one figured to scrap that one and settle for TCP for now since it's hopefully able to provide sufficient speed to test main workings in limited enviroment I'll be testing anyway.

---

### Post by eye208 on 2009-03-04
> **tneva82 said:**
> And how easy it is to apply those strings to C functions I need?-) Plenty of those I can find use for.
Don't call C APIs directly. Use wrapper classes. Your current implementation is a mess. It's hard to maintain and not exception-safe.

> Timeout? Gee that just ain't good enough. If I waste even 5ms waiting each loop for activity...Well let's see. 5 clients(and in theory this should be able to handle dozens of clients). Let's say I put 40FPS as goal(and I know people who would baulk at such low FPS). So 40 loops. Each loop therefore wastes 5x5ms=25ms or for one second 1000ms wasted...
On the contrary, your current implementation wastes CPU cycles by polling a list of sockets for input even when there is none. A multi-threaded solution with blocking read calls would perform much better, because a thread waiting for input requires no CPU cycles at all. The system will wake it up either when there is input available or when a timeout has expired. A timeout means that the connection is dead because the client hasn't sent any keep-alive packets for an extended period of time.

> I have said several times already CODE WORKS already!!! Why I should go for multithreaded now to "fix" it when it already works?
It doesn't work. Your server totally ignores the condition of a client going offline without closing its connection.

<snip>

---

