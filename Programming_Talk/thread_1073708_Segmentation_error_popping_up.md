---
title: "Segmentation error popping up"
date: 2009-02-18
forum: Programming Talk
---

### Post by tneva82 on 2009-02-18
I'm trying to get some sort of network code working with SDL_Net. Managed to get UDP packet sent(yey!) and received(YEY!) in the server. Once. Second packet causes segmentation error. Groovy!

I'll put code below but in case you don't want to spend time looking over I would be happy enough if you would just give me pointers on precicely what I should be looking for as cause of segmentation error.

Anyway code for client side(just the sending part for now. I don't think opening port or binding is issue since I managed to send it allright).

```
int myNetwork::sendData(char *message) {
  packet=SDLNet_AllocPacket(1024);
  packet->channel=myChannel;
  printf("sending data"); //don't mind these. While debugging I just put these to see where it crashed
  
  packet->maxlen=1024;
  packet->address.host=ipaddress.host;
  packet->address.port=ipaddress.port;

  Uint8 data[strlen(message)+1];

  for(int i=0;i<strlen(message)+1;i++) {
    data[i]=(Uint8)message[i];
  }
  printf("data prepared");
  packet->data=data;
  packet->len=strlen(message)+1;
  int numsent;

  numsent=SDLNet_UDP_Send(udpsock, packet->channel, packet);
  if(!numsent) {
    printf("SDLNet_UDP_Send: %s\n", SDLNet_GetError());
    
  }
  printf("data sent");
  SDLNet_FreePacket(packet);

}
```

Also for the server side. Again trimmed down port opening and binding since I think that works allright. If it turns out it might be there I'll post them as well.

```
UDPpacket *packet;
  packet=SDLNet_AllocPacket(1024);
int numrecv;
  
  while(1) {
    numrecv=SDLNet_UDP_Recv(udpsock, packet);
    if(numrecv) {
      char buf[1024];
      printf("%s\n", packet->data);
    
    }
    numrecv=0;
    
    }
  SDLNet_FreePacket(packet);
```

Anyway any pointers where I have messed up?

---

### Post by dwhitney67 on 2009-02-18
I do not quite understand why you elected to use SDL libraries for UDP message transfers; creating your own is quite simple, and a lot less baggage involved.

Anyhow, I came across this tutorial that maybe you can reference:  [http://gpwiki.org/index.php/SDL:Tutorial:Using_SDL_net](http://gpwiki.org/index.php/SDL:Tutorial:Using_SDL_net)

As for your SegFault, it may be occurring here:
```

  for(int i=0;i<strlen(message)+1;i++) {
    data[i]=(Uint8)message[i];
  }

```
Notice how you are writing to one more slot that you really should.

---

### Post by kavon89 on 2009-02-18
> **dwhitney67 said:**
> Notice how you are writing to one more slot that you really should.

Off by one error gets the best of us.

---

### Post by johnl on 2009-02-18
> **dwhitney67 said:**
> 
As for your SegFault, it may be occurring here:
```

  for(int i=0;i<strlen(message)+1;i++) {
    data[i]=(Uint8)message[i];
  }

```
Notice how you are writing to one more slot that you really should.

It seems to me this code is fine -- it's just including the null terminator in the packet?

I would suggest running your program with gdb.  You can pinpoint from there where the program is crashing and figure out why.

---

### Post by tneva82 on 2009-02-19
> **dwhitney67 said:**
> I do not quite understand why you elected to use SDL libraries for UDP message transfers; creating your own is quite simple, and a lot less baggage involved

Because SDL_Net seemed suitably easy to use ;-) I prefer higher level libraries where possible rather than try to get it working myself from low-level simply due to me not being pro programmer ;-) And I rather like SDL so I figured SDL_Net(once I heard it's existance) would be good idea.

> 
Notice how you are writing to one more slot that you really should.

Not really. Note how data is defined:

  Uint8 data[strlen(message)+1];

So if message length is 11 data is data[12] and I'll loop from 0 to <12 ie 0, 1...11.

Can't see I would see. I added +1 specifically because it crashed before I sent it even once before.

BTW how does one approach creating system where one server speaks(both way) to multiple clients? I figured I would have server listening port X. Clients contact them and say they want to talk to them. As far as I can tell UDP packet contains senders IPaddress in it so would it work if I save that to arrays containing clients and then when I need to talk I can send it back?

Should there be more than one port for server(well probably anyway if there's multiple clients...). Whatabout clients? Should they have one port for listening and one for sending? And send the listening port in the opening message?

Just a bit of theory so I can start working on the server-client code properly once I figure out where the segmentation error happens(this code is mainly to try it out so that I know I can get it working).

Some more ideas for the server side code(I think that's the trickiest one since it has to deal with multiple clients AND do the stuff it's supposed to do). Would it be good idea to split the program to multiple threads? One for handling connections(accepting new ones, managing old ones etc), 1 for parsing messages from clients connected and acting through them, one for doing global stuff affecting _every_ client and maybe one for sending messages back(or maybe this one can be integrated to 2nd thread). Might make it more complicated but atleast it should in theory work faster? Would Linux take use of multiple processors in computer this way(running each thread in own processor) or would there be more work to do?

Seems like would be good practical use to try thread coding(obviously starting with less complicated stuff with aim of incorporating it to this one).

---

### Post by the_unforgiven on 2009-02-19
> **tneva82 said:**
> Because SDL_Net seemed suitably easy to use ;-)



Not really. Note how data is defined:

  Uint8 data[strlen(message)+1];


Are you sure this works?
I always thought you needed a constant for array dimensions while defining the array - the compiler always croaked on that one.

The logical reasoning:
The memory for the array is allocated by the compiler statically on the stack during compile-time. However, strlen(message) is not evaluated until runtime. So, it's impossible for the compiler to know how much to allocate for the array.

I wonder how come the compiler didn't croak at you...
Or, did I miss something?

---

### Post by tneva82 on 2009-02-19
> **the_unforgiven said:**
> Are you sure this works?
I always thought you needed a constant for array dimensions while defining the array - the compiler always croaked on that one.

You might be on to something. Maybe I should swap it for pointer like

Uint8 *data=new Uint8[strlen(message)+1]

Hum hum. Good point and yeah there were no compiler errors. Just couple of warnings but they weren't related to this by long shot. For some reason calling this: LoadGLTextures(char *fileName) function by LoadGLTextures("something.dat") causes warning: deprecated conversion from string constant to ‘char*’ warning. 2 more for similar function which loads the 3d model in similar function call). 

And top of that first message went through just fine(same string I sent got printed on server window). I was sure I had it cracked when I saw that and then BANG it crashed :-/ Premature start of cheering!

---

### Post by hastur on 2009-02-19
hi,

dynamic length array declaration is not ANSI C, but it works with gcc, when the length depends on a parameter of the function where the declaration happens.
the compiler implicitly calls an [c]alloc() function to initialize the variable, then a free() when leaving the function.
example :
```

int function(int a) {

char array[a] = {0,};

}

```
should work fine.
in your case the only doubt is that you're using "strlength(parameter)" instead of just "parameter", but I would say - as long as the compiler doesn't complains at compile time and it works for the first packet sent - it may well works.
however it should be easy to make a few tests with a fixed length buffer to see if this solves the segmentation fault.

also, IMHO, trying to find a segfault from just a short extract of your code may be impossible : what if you corrupted your heap in another (totally unrelated) function and the segfault just happens here and there as a result ?

---

### Post by tneva82 on 2009-02-19
> **hastur said:**
> also, IMHO, trying to find a segfault from just a short extract of your code may be impossible : what if you corrupted your heap in another (totally unrelated) function and the segfault just happens here and there as a result ?

Not a good prospect but luckily got segmentation errors away. Though I'm not quite sure WHY it goes haywire :-/ Basicly I moved the allocation of memory for packet to constructor of network class and deallocating to destructor. So rather than creating new packet and deleting it for every message I just reuse it(well might be good idea anyway for performance). Hey presto steady stream of messages moves between server and client.

Now if I could get some pointers to theory questions I posted I would be on my way toward basic server-client code.

---

### Post by the_unforgiven on 2009-02-19
I must be getting old.. :(
According to the GCC manual:
[http://gcc.gnu.org/onlinedocs/gcc-4.3.3/gcc/Variable-Length.html#Variable-Length](http://gcc.gnu.org/onlinedocs/gcc-4.3.3/gcc/Variable-Length.html#Variable-Length)
tneva82's code is supposed to work without problems.
So, looks like it is segfaulting due to some other reason..

---

### Post by dwhitney67 on 2009-02-19
> **tneva82 said:**
> ...
Not really. Note how data is defined:

  Uint8 data[strlen(message)+1];

So if message length is 11 data is data[12] and I'll loop from 0 to <12 ie 0, 1...11.

Can't see I would see. I added +1 specifically because it crashed before I sent it even once before.

Yeah, I guess the issue is not in the for-loop, but as others have mentioned, in the declaration of 'data'.

> **tneva82 said:**
> 
BTW how does one approach creating system where one server speaks(both way) to multiple clients? I figured I would have server listening port X. Clients contact them and say they want to talk to them. As far as I can tell UDP packet contains senders IPaddress in it so would it work if I save that to arrays containing clients and then when I need to talk I can send it back?

Your server can retain the foreign address and port used by a client to respond at a later time if necessary.

> **tneva82 said:**
> 
Should there be more than one port for server(well probably anyway if there's multiple clients...).

Typically a simple UDP server will only require one port.  Individual clients can communicate using the same port.

> **tneva82 said:**
> 
Whatabout clients? Should they have one port for listening and one for sending? And send the listening port in the opening message?

A client should not have to listen; I believe it is only required by the server, when using a connection-based protocol (i.e. TCP).

> **tneva82 said:**
> 
Some more ideas for the server side code(I think that's the trickiest one since it has to deal with multiple clients AND do the stuff it's supposed to do). Would it be good idea to split the program to multiple threads? One for handling connections(accepting new ones, managing old ones etc), 1 for parsing messages from clients connected and acting through them, one for doing global stuff affecting _every_ client and maybe one for sending messages back(or maybe this one can be integrated to 2nd thread). Might make it more complicated but at least it should in theory work faster? Would Linux take use of multiple processors in computer this way(running each thread in own processor) or would there be more work to do?

For a busy server, using multiple threads can speed up the processing of messages, by using one thread to receive messages, another thread to process the messages, and perhaps yet another thread to respond to the client with a response.

If you plan to use UDP, there are no "connections" by peers.  It is connectionless.

> **tneva82 said:**
> 
Seems like would be good practical use to try thread coding(obviously starting with less complicated stuff with aim of incorporating it to this one).
Get your client/server applications working first before jumping into multi-threaded programming.  Unless you are expecting your application to process hundreds (perhaps thousands) of messages per second, you may not need to make it into a multi-threaded application.

P.S.  Try to see if you can build the example client and server applications posted within the tutorial I posted earlier.  If you design your application "correctly", you should be able to develop your own library that is based on the SDL_Net framework.  Your application should be unaware of what framework is being used.  For instance, your library could have a functions such as:

```

void Send(const char* msg, const size_t msgLen, const std::string& foreignAddress, const unsigned short foreignPort);

int Recv(char* msg, const size_t msgLen, std::string& sourceAddress, unsigned short& sourcePort);

```
The obfuscates the dependency of the SDL_Net framework, including the need to maintain the socket handle.

---

### Post by tneva82 on 2009-02-19
> **dwhitney67 said:**
> A client should not have to listen; I believe it is only required by the server, when using a connection-based protocol (i.e. TCP).

If client isn't listening how client knows server has just sent him information that he needs to act? I would need both sides to send messages to each other and act on them rather than just one way around. That's the thing that tutorial is lacking. It has just one way around posting. How would it work if I want to send data back(even if something as simple as acknowledging that yes I received your message!).

---

### Post by dwhitney67 on 2009-02-19
A server cannot initiate contact with a "true" client.  Typically the first thing a client will do is send a message to a server, then perhaps await a response.  The server cannot send a response (a message) to the client unless it has the client host/port information.

If initially a "client" is waiting for a message from another peer, before it has ever made contact with this peer, then in essence it is a server.  The peer would have to know the host/port that this "client" is using.

Does any of this make sense?  Basically, it boils down to semantics as to what defines a client vs. a server.

P.S.  An Apache web server does not initiate communications with my web browser; my web browser (the client) initiates communications.

---

### Post by tneva82 on 2009-02-19
> **dwhitney67 said:**
> A server cannot initiate contact with a "true" client.  Typically the first thing a client will do is send a message to a server, then perhaps await a response.  The server cannot send a response (a message) to the client unless it has the client host/port information.

Yes. Basicly my idea so far is:

Client sends message to server telling server I wanna join in! In this message(apart from command join) might be parameter to port number client is using for receiving packets(this is what I mean by listening) assuming client has to use different to read packets than to send. Then server assigns id for client for the session(first available) and sends reply to client containing session id. Address would either be received from clients packet it received(I thought I read somewhere it would contain senders address) or alternatively from data message received from client.

Then communication would proceed sending messages according to program's logic with client passing it's clientid to server so that server knows WHICH client sent the message.

I think I wrote poorly before what I meant(never did I think server would be starting up session. Sorry if I caused misunderstanding ;-) ) but above is how I figured this would work. Does above make any sense? And then few clarifications to help making it a reality.

a) where the server would pull needed address. From packet's address field(I could swear I read it is changed on it's way to contain senders address) or should that be part of clients message?
b) does server need to use different port for receiving and sending?
c) same for client. Can it use same port for receiving and sending or different ports?

---

### Post by dwhitney67 on 2009-02-19
The quick answer is yes, the client can use the same port for sending/receiving.  Similar for the server.

On the server side, make sure that you bind() the port being used.  Sometimes it is necessary/prudent to do.

Now I have to run off to work...

---

### Post by tneva82 on 2009-02-19
> **dwhitney67 said:**
> Now I have to run off to work...

Thanks. Much appreciated! I'll start working on simple server/client program to test how this works.

Again big thank you!

---

