---
title: "Beginner programming challenge #5"
date: 2009-06-02
forum: Programming Talk
---

### Post by snova on 2009-06-02
[CENTER][SIZE="4"]**Beginners Programming Challenge #5**[/SIZE][/CENTER]

It took me a little while to come up with a good idea. The first few I had were either boring or too hard.

This one might teach you something new if you aren't already familiar- networking. You are going to write a server.

**Rules**

The server must accept client connections, and echo lines from each connection to every other connection. That is, if clients A, B, and C are connected and A send "Hello, world", this string should show up in B and C's windows.

In a way, this is a simple kind of chat server.

**Extra features**

The more features you can give it, the better. Some suggestions:

[LIST]
[*] A "login" sequence. Require clients to give themselves a name, and send this name along with messages that they send. Then you can tell who said what.
[*] Following the first suggestion, send notifications to other clients when someone connects or disconnects.
[*] Authentication- let names (or only some) require a password. Maybe even let that password be changed.
[/LIST]

Going above and beyond this list is encouraged- anything you can think of.

**Hints**

You have to be able to listen to every client connection you have at once. Polling is rather unoptimal in this situation. Threads are one possibility, but this does not scale well to more than a few clients. Also, it requires locking, which makes it more complicated. The best way to multiplex connections is to be asyncronous in the first place.

For that, the common solution is to use select(), which waits for one of a set of sockets to have available data.

For Python programmers, I direct you to the [socket]("http://docs.python.org/library/socket.html") and [select]("http://docs.python.org/library/select.html") modules in the standard library. The examples in the documentation should help you along.

An alternative option for Python is to use the [Twisted]("http://twistedmatrix.com/") networking framework- if you can take the time to learn how to use it (it's not that complicated, it may be simpler than the first option of rolling your own socket code), it will serve you well in many ways.

---

### Post by Coldhearth on 2009-06-02
Sounds interesting, so we need to write a client program and a server program as well that can talk with more than 1 client program at a time? :)

---

### Post by snova on 2009-06-02
> **Coldhearth said:**
> Sounds interesting, so we need to write a client program and a server program as well ...

Just the server. For a client, all you really need is netcat (a socket utility) to send data directly to the socket. But if your server had enough features, a specialized client wouldn't be too bad of an idea.

Oh, and by the way, some clients will send "\n" to mark the end of the line, and others will send "\r\n"... the latter is more typical on the internet, but why be specific?

(Or you could just assume the former, it's easier.)

> ... that can talk with more than 1 client program at a time? :)

They all have to.

---

### Post by Coldhearth on 2009-06-02
Hmm interesting, although I wouldn't know where to start... 
Can you maybe point me in the right direction? (I have never done networking before) :)

---

### Post by simeon87 on 2009-06-02
> **Coldhearth said:**
> Hmm interesting, although I wouldn't know where to start... 
Can you maybe point me in the right direction? (I have never done networking before) :)

I must say I felt it to be complicated for a beginners challenge. After all, you need to know about localhost, ports, sockets and let's forget threads :)

---

### Post by snova on 2009-06-02
> **Coldhearth said:**
> Hmm interesting, although I wouldn't know where to start... 
Can you maybe point me in the right direction? (I have never done networking before) :)

Assuming Python: The documentation for the socket module should show you how to set up a server socket and listen for connections.

After that, it becomes a problem of polling your clients for data to read.

> I must say I felt it to be complicated for a beginners challenge. After all, you need to know about localhost, ports, sockets and let's forget threads :)

I tried not to let it get too complicated, but you don't need threads.

I'm hoping somebody uses Twisted, because it's wonderful for Python networking.

[[COLOR="RoyalBlue"]How to write servers in Twisted[/COLOR]]("http://twistedmatrix.com/projects/core/documentation/howto/servers.html") (should show you how the API in general works)
[[COLOR="#4169e1"]Twisted tutorial[/COLOR]]("http://twistedmatrix.com/projects/core/documentation/howto/tutorial/index.html")

---

### Post by Simian Man on 2009-06-02
> **simeon87 said:**
> I must say I felt it to be complicated for a beginners challenge. After all, you need to know about localhost, ports, sockets and let's forget threads :)

Even in C, you can do this in a few hundred lines of code (less if you want to skip some features).  And you don't need threads if you have the select function like C and, apparently, Python.

---

### Post by jimi_hendrix on 2009-06-02
points off for using POE or twisted? (i am curious even though i am using erlang)

---

### Post by snova on 2009-06-02
> **jimi_hendrix said:**
> points off for using POE or twisted? (i am curious even though i am using erlang)

No.

---

### Post by bgs100 on 2009-06-02
Do I get points for being the first answer? ;)
The Server:
[PHP]#!/usr/bin/env python
import socket, select

HOST = 'localhost'
PORT = 9001
server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server.bind((HOST, PORT))
server.listen(3)
connections = [server]

def send(connection, message):
    connection.send(message + '\r\n')

while True:
    ready_connections = select.select(connections, [], [])[0]
    for connection in ready_connections:
        if connection is server:
            connect, address = server.accept()
            connections.append(connect)
            print 'Connected: ' + address[0]
            for con in connections:
                if con is not server and con is not connect:
                    send(con, address[0] + ' JOIN')
        else:
            message = connection.recv(512)
            if message:
                address = connection.getsockname()[0]
                print 'Recieved From ' + connection.getsockname()[0] + ' :' + message
                for con in connections:
                    if con is not server and con is not connection:
                        send(con, address + ' MSG :' + message)
            else:
                address = connection.getsockname()[0]
                print 'Disconnected: ' + address
                connection.close()
                connections.remove(connection)
                for con in connections:
                    if con is not server and con is not connection:
                        send(con, address + ' QUIT')[/PHP]

And The Client:
[PHP]#!/usr/bin/env python
import socket, threading

HOST = 'localhost'
PORT = 9001
client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client.connect((HOST, PORT))

def listen():
    while True:
        data = client.recv(512)[:-2].split()
        who = data[0]
        command = data[1]
        args = data[2:]
        if command == 'MSG':
            print who + ': ' + ' '.join(args)[1:]
        if command == 'JOIN':
            print '--> ' + who + ' has joined'
        if command == 'QUIT':
            print '<-- ' + who + ' has quit'

def send():
    while True:
        try:
            message = raw_input('')
        except KeyboardInterrupt:
            message = 'quit'
            print
        if message.lower() == 'quit':
            client.close()
            exit()
        client.send(message + '\r\n')

thread1 = threading.Thread(target = listen)
thread2 = threading.Thread(target = send)
thread1.start()
thread2.run()[/PHP]
EDIT: Ooops, forgot something. It'll work, but...

---

### Post by jimi_hendrix on 2009-06-02
> **snova said:**
> No.
no fair...they are easy :)

---

### Post by s.fox on 2009-06-03
Hi,

Okay,  It looks like a basic chat room.  I should have something together as soon as I can.  Most likely be Ajax and PHP powered.  I'll see what I can do. :D

-Ash R

---

### Post by soltanis on 2009-06-03
I actually wrote one of these a while ago in Java. Real fancy stuff. Blew it away though. Sad.

---

### Post by Bodsda on 2009-06-04
Hmmm, I have a huge pot of coffee, shed loads of cigarettes and a whole day to myself. Lets get to work :)
[SIZE="6"][COLOR="Red"]**_Announcement_**[/COLOR][/SIZE]

The Ubuntu Beginners team (formerly Ubuntu forums beginners team) are now sponsoring these challenges!!

 The team have a focus group dedicated to programming and development and have agreed to be the front line for beginners needing help with these challenges. You can find us in ##beginners-dev on irc.freenode.net (Ubuntu network) or in our parent channel #ubuntu-beginners (formerly #ubuntuforums-beginners). We hope to see people come along and introduce themselves, even if you just want to chat thats fine. Soon we hope to have challenge information in the channel topic, I'm just waiting to get hold of a channel op for this.

Many of the participants of these challenges are directly involved with the beginners team, such as myself, Snova and Ash_R as well as others. There are no stupid questions in ##beginners-dev, we dont mind if your asking how to automated tedious tasks or if your unsure how to write a hello world program. If we can help, we will. 

Hope to see you soon.

Kind Regards,

Bodsda

---

### Post by stevescripts on 2009-06-04
Bodsda -

A very worthy (IMHO) undertaking.  I may even be tempted to find an IRC client that I like that works when I am on windoze (which, I mostly am, unfortunately ...) and drop in to visit sometime soon.

Everybody needs help getting started.

Steve

---

### Post by Bodsda on 2009-06-04
> **stevescripts said:**
> Bodsda -

A very worthy (IMHO) undertaking.  I may even be tempted to find an IRC client that I like that works when I am on windoze (which, I mostly am, unfortunately ...) and drop in to visit sometime soon.

Everybody needs help getting started.

Steve

Steve, that would be great, were on freenode in ##beginners-dev -- most irc clients have a windows version:

[Xchat]("http://www.silverex.org/download/")
[irssi]("http://irssi.org/download")
[BitchX]("http://www.bitchx.com/download.php")
[mIRC]("http://www.mirc.com/get.html")

Regards,

Bodsda

---

### Post by stevescripts on 2009-06-04
After finding a few minutes to have (and enjoy) a brief chat with Bodsda,
I promised to hack up a simple tcl/tk example, that someone could build upon if they so desired...

Lacking the time right now - here is a link to a simple client server example written in tcl - [http://www.tcl.tk/about/netserver.html](http://www.tcl.tk/about/netserver.html)

Someone with a little time and energy could easily build on this to enter the challenge ...

I hope that some will at least find it interesting/informative.

Steve

---

### Post by ibuclaw on 2009-06-04
This is the general gist of things in C:

Doesn't really meet the criteria of the challenge, but shows a simple one way client->server connection.

**server.c**
[PHP]
#include <stdio.h>
#include <unistd.h>
#include <netdb.h>

#define INVALID_SOCKET -1
#define SOCKET_ERROR   -1
#define PORT            1989

int main()
{
    struct sockaddr_in address;
    int sockfd, inputfd;
    unsigned int addrlen, retlen;
    char buffer[1024];
    /* Create Socket */
    sockfd = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);
    if(sockfd == INVALID_SOCKET)
        goto end_conn;
    /* Bind Socket to a port */
    address.sin_family = AF_INET;
    address.sin_addr.s_addr = INADDR_ANY;
    address.sin_port = htons(PORT);
    bind(sockfd, (struct sockaddr*)&address, sizeof(address));
    /* Start listening */
    listen(sockfd, 3);
    /* Wait for 1 client to connect */
    addrlen = sizeof(address);
    inputfd = accept(sockfd, (struct sockaddr*)&address, &addrlen);
    /* Message Loop */
    printf("JOIN: socket %d\n", inputfd);
    while(1)
    {
        retlen = recv(inputfd, buffer, 1023, 0);
        if(retlen == SOCKET_ERROR || !retlen)
            break;
        buffer[retlen] = '\0';
        printf("MSG: %s", buffer);
    }
    printf("QUIT: socket %d\n", inputfd);
end_conn:
    return close(sockfd);
}
[/PHP]
**client.c**
[PHP]
#include <netdb.h>
#include <unistd.h>
#include <readline/readline.h>

#define INVALID_SOCKET -1
#define SOCKET_ERROR   -1
#define PORT            1989
#define SERVER         "localhost"

int main()
{
    struct sockaddr_in address;
    struct hostent *resolv;
    int sockfd;
    FILE *dataout;
    char *message;
    /* Create Socket */
    sockfd = socket(AF_INET, SOCK_STREAM, IPPROTO_TCP);
    if(sockfd == INVALID_SOCKET)
        goto end_conn;
    /* Get server address */
    resolv = gethostbyname(SERVER);
    if(!resolv)
        goto end_conn;
    memcpy(&address.sin_addr, resolv->h_addr, resolv->h_length);
    address.sin_family = AF_INET;
    address.sin_port = htons(PORT);
    /* Connect to Server */
    if((connect(sockfd, (struct sockaddr*)&address, sizeof(address))) == -1)
        goto end_conn;
    /* Open a data stream */
    dataout = fdopen(sockfd, "w");
    /* Message Loop */
    printf("Connected to server\n");
    while ((message = readline("server:> ")) != NULL)
    {
        fprintf(dataout, "%s\r\n", message);
        fflush(dataout);
    }
    printf("\nConnection closed\n");
end_conn:
    return close(sockfd);
}
[/PHP]
**compile**
```
gcc -Wall server.c -o server
gcc -Wall client.c -o client -lreadline

```

Then in one terminal:
```
./server
```
and in another:
```
./client
```
To kill the connection, press "Ctrl+D" on the client-side.
Regards
Iain

---

### Post by GF_Sobriquet on 2009-06-04
Is there a deadline for this challenge? I have a working version in Python, but I want to know how much time I have to add fun features.

---

### Post by s.fox on 2009-06-04
> **GF_Sobriquet said:**
> Is there a deadline for this challenge? I have a working version in Python, but I want to know how much time I have to add fun features.

I believe Snova said 2 weeks to me earlier this week in the IRC channel.   That would make the deadline next Saturday.  :)

-Ash R

---

### Post by snova on 2009-06-04
> **GF_Sobriquet said:**
> Is there a deadline for this challenge? I have a working version in Python, but I want to know how much time I have to add fun features.

I'm going to say the 13th, or thereabouts.

---

### Post by GF_Sobriquet on 2009-06-05
I'm going to be doing some traveling and I'm not sure I'll be able to work on this any more before the deadline. This is just the server code, which you can connect to using netcat. I'd like to add a few more features, maybe make a dedicated client, and figure out a good way to quit the server, but here is my work in progress:
[PHP]import socket, select, sys
class Server:
    """chat server class""" 
    
    def __init__(self,host="",port=3030):
        self.HOST=host
        self.PORT=port
        self.servSocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        self.servSocket.bind((self.HOST,self.PORT))
        self.servSocket.listen(5)
        self.connSocks=[self.servSocket, sys.stdin]
        self.users = dict()
        self.running = False
        
    def run(self):
        """start running the server"""
        self.running = True
        while self.running==True:
            # get lists of clients ready to read or write data
            readReady, writeReady, errors = select.select(self.connSocks,self.connSocks,[])
            for current in readReady:
                if current is self.servSocket:
                    # accept any incoming connections
                    conn, addr = self.servSocket.accept()
                    self.connSocks.append(conn)
                    conn.send("Welcome! Please enter a username:\n")
                    username = conn.recv(1024)
                    username = username[:-1]
                    self.users[conn] = username
                    self.__broadcast(" joined the server\n", conn, writeReady,"")
                elif current is sys.stdin:
                    x = sys.stdin.readline()[:-1]
                    if x=="stop":
                        self.stop();
                    else:
                        continue
                else:
                    # accept any incoming data from the client (or a disconnection)
                    data = current.recv(1024)
                    self.__broadcast(data, current, writeReady)
            
    def stop(self):
        """stop the server, pretty straight forward"""
        self.running = False
        print "shutting down the server\n"
        for sock in self.connSocks:
            if sock is not sys.stdin:
                sock.shutdown(socket.SHUT_RDWR)
                sock.close()
        
    def __broadcast(self,data,current,writeReady,div=": "):
        """broadcast a message to all ready clients except 'current'"""
        if not data: # means the client disconnected
            for w in writeReady:
                if w is not current:
                    w.send(self.users[current] + " disconnected\n")
            del self.users[current]
            self.connSocks.remove(current)
        else: 
            for w in writeReady:
                if w is not current:
                    w.send(self.users[current] + div + data)

if __name__=="__main__":
    serv=Server()
    serv.run()[/PHP]

Edit: Thanks snova! This was challenging and fun to work on.

---

### Post by ibuclaw on 2009-06-06
> **GF_Sobriquet said:**
> I'm going to be doing some traveling and I'm not sure I'll be able to work on this any more before the deadline. This is just the server code, which you can connect to using netcat. I'd like to add a few more features, maybe make a dedicated client, and figure out a good way to quit the server, but here is my work in progress:
[PHP]    
    def __init__(self,host="",port=1337):
[/PHP]


Port 1337 .... :|

You could of at least used a more original port number. (Birth years ftw) ;)

---

### Post by GF_Sobriquet on 2009-06-06
> **tinivole said:**
> Port 1337 .... :|

You could of at least used a more original port number. (Birth years ftw) ;)

Haha, just a habit...more of a joke than anything.

Okay, I updated a few things in the code, including changing the default port. :P

---

### Post by Froodolt on 2009-06-09
Think I am gone skip this one.

Just finished a chapter of my Java course about networking and threads, explained by writing a simple chat server and client in Java. 
:lolflag:

---

### Post by snova on 2009-06-17
I think I may have made this a bit too hard, unfortunately, but we'll let someone else pick a simpler one next time.

I'm going to start testing the entries. We should have a winner within a day or two, though there is still time for last minute entries (Bodsda informed me he has one, at least).

---

### Post by snova on 2009-06-22
Ok, this has gone on long enough (my fault, sorry), and I realize now that it was too hard. I am going to declare **ibuclaw** as the winner.

Going through these entries:

GF_Sobriquet: I probably paid the most attention to yours. I like that it requires no special client (well, none of them do), and also that it was neatly encapsulated. With the stop() function you could even think about how to run the server in the background and have this function be called on a signal to shut down cleanly- basic daemonization.

I'm not particularly fond of adding stdin to the list of sockets though. This requires the server to be running in someone's console 24/7. It's also a source of bugs: __broadcast() throws an exception when I try to connect, because it attempts to call stdin.send() (which doesn't exist).

The thing that concerns me most is the conn.recv() call on line 28, however. When somebody logs in, every client connected to the server must wait for this blocking call to complete. I could lock up your entire server by simply opening a connection and letting it wait for my username for eternity.

Now, bgs100. I know you, so don't kill me. :) This is pretty clean code, with the exception of a few duplicated lines between the second if/else pair. It also slightly bugs me that pressing Enter (blank line) will disconnect me. Also, I think you forgot to strip() the message somewhere, because sending a message sends an extra blank line to every other client.

The client I have other thoughts about. The MSG/JOIN/QUIT commands are more apparent on this side of the connection and make this quite interesting- you have a simple protocol going on here.

The threads, however, are largely unnecessary- you can add sys.stdin to the list of waiting connections and use it as any other socket with select(). Even then, thread2.run() is kinda silly- why not just call send() directly?

Then there is tinivoles. The server, for a program using the basic C socket API, is quite understandable. It doesn't fufill my requirements because it uses the first socket it accepts directly (you can't connect more than one client), but adding a select() loop in here somewhere would probably not be a lot of effort.

The client is also neat- fdopen() is a new call for me. It uses readline, which is a thoughtful little feature.

Anyway, I'm looking forward to another challenge, after this one was delayed for so long. Apologies again.

---

### Post by ibuclaw on 2009-06-22
> **snova said:**
> Ok, this has gone on long enough (my fault, sorry), and I realize now that it was too hard. I am going to declare **ibuclaw** as the winner.

Then there is tinivoles. The server, for a program using the basic C socket API, is quite understandable. It doesn't fufill my requirements because it uses the first socket it accepts directly (you can't connect more than one client), but adding a select() loop in here somewhere would probably not be a lot of effort.

The client is also neat- fdopen() is a new call for me. It uses readline, which is a thoughtful little feature.

Anyway, I'm looking forward to another challenge, after this one was delayed for so long. Apologies again.

So you chose mine because you had the least amount of gripes with it?

Also, your challenge isn't difficult. I just think that there is no motivation to do such a thing.

Anyways, I'll come up with a new challenge, I suppose... :)

---

