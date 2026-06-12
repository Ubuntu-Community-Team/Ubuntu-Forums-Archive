---
title: "Threading/Public Object Help"
date: 2007-09-09
forum: Programming Talk
---

### Post by t3hi3x on 2007-09-09
I am trying to create a program that uses the pthread library. the problem I am having is that i am creating a socket to connect in one thread and then i want to send later. the deal with that is that it saying that the socket being created is not defined. I couldnt find anything online on how to make it when i create the object in one subroutine that it makes it accessible in any other subroutine.

can someone help me?

ex.

```


connect ()

{
ClientSocket new_sock;

//wait

}

main

{
connect ();

new_sock >> "out";


```

compiler throws

> ...new_sock not defined...

i know this is pretty simple, just cant figure it out :(

---

### Post by dwhitney67 on 2007-09-09
It appears that you are writing code in C++, and that you have an object (class) called ClientSocket.  Is this correct?

The code you provided in your post is not complete.  Can you provide all of the code you are trying to compile, including the command you are using to compile your code.

Thank you.

---

### Post by DavidBell on 2007-09-09
new_sock is declared in connect() scope, and not available to main().

You either have to declare it at file level, or get connect() to return a pointer or something like that.

DB

---

### Post by dwhitney67 on 2007-09-09
> **DavidBell said:**
> new_sock is declared in connect() scope, and not available to main().

You either have to declare it at file level, or get connect() to return a pointer or something like that.

DB

Good eyes.  Your right!  Let's see if the OP understands you.

I would rewrite the the main function (based on the limited knowledge I have of the existing code) as:

[PHP]int main( int argc, char** argv )
{
  ClientSocket new_sock;

  new_sock >> "out";
}[/PHP]

---

### Post by aks44 on 2007-09-09
@OP: I really don't mean to be rude or anything, but I'd advise you to forget about multithreading for a moment, until you have a better mastery of the C++ language itself.


Multithreading & concurrency is one of the hardest things to get right in programming.

(Herb Sutter: "*The vast majority of programmers today don&#8217;t grok concurrency, just as the vast majority of programmers 15 years ago didn&#8217;t yet grok objects*" and also "*locks are hard for **expert** programmers to get right*", emphasis mine)

If you don't grasp yet such a simple concept as scoping, you'd really be better off not even trying to do multithreading, unless you want to have to deal with random deadlocks / memory corruptions / core dumps which are nearly impossible to debug but by chance. FWIW even full teams of highly skilled people struggle with such problems more than often.

However if you're only half as stubborn as I can be myself :p you may want to start anyway with message-based concurrency (which works quite smoothly), and *stick with it* for quite some time.

But anyway I don't recommend it for now.

---

### Post by t3hi3x on 2007-09-09
> **dwhitney67 said:**
> 
[PHP]int main( int argc, char** argv )
{
  ClientSocket new_sock;

  new_sock >> "out";
}[/PHP]

the problem with that is that when the subroutine is ended the socket disconnects (deletes the socket) from the server. 

i know i dont know a lot bout c++, but am learning it as i go. could you expand on what a pointer is?

thanks,
alex

---

### Post by tripokey on 2007-09-09
... It would be to lengthy to explain in the forums i belive... 

So choose a book and look it up:

[http://freeprogrammingresources.com/cppbooks.html](http://freeprogrammingresources.com/cppbooks.html)

---

### Post by dwhitney67 on 2007-09-09
> **t3hi3x said:**
> the problem with that is that when the subroutine is ended the socket disconnects (deletes the socket) from the server. 

i know i dont know a lot bout c++, but am learning it as i go. could you expand on what a pointer is?

thanks,
alex

The example I coded was just that, an example.

If you are developing a server application, then you are correct, the socket should remain available.  Hence the server should not terminate (unless told to do so).

Here's a pseudocode example:

```
OpenSocket();

while forever
{
  ListenForConnection();
  HandleConnection();
}
```

---

### Post by t3hi3x on 2007-09-09
```
OpenSocket();

while forever
{
  ListenForConnection();
  HandleConnection();
}

```

The problem with this code is the handle connection can't access the socket object created (new sock)

The way the class works is that it makes the socket by the command ```
ClientSocket new_sock( server, port)
``` (new_sock can be what ever i want). then (if it's within the same subroutine) i can send a plain text string (or array of chars) to the server using ```
new_sock >> string;
``` and then receive a plain text string from the server using ```
new_sock << reply;
```. it doesn't work when i use the ```
ClientSocket new_sock
``` in a connect function.

the reason i cannot use it in a single threaded environment is because i have to connect to the server and stay connected and still wait for a song from the server, while playing a song via a streaming server.

i've got MOST of the basics down for C++ and it's coming quickly, but books and online tutorials don't seem to help with specific problems like this one.

would using ```
OpenSocket();

while forever
{
  ListenForConnection();
  HandleConnection();
}
``` work for this type of deal? i guess i could rewrite it to follow this form, but i dont see how it work as i need to communicate both ways with server and stay connected all at the same time (the need for threading) and execute other commands. and i would like these to (and i think they have to be) in separate functions.

heres a run down on how the code is set up

```


#include "ClientSocket.h"
#include "SocketException.h"
#include <iostream>
#include <string>
#include <pthread.h>

int establishconnection (std::string server, int port)

{
	int quit;

	//CREATE THE SOCKET
	ClientSocket new_sock ( server, port );

	//WAIT FOR SIGNAL TO QUIT
	
	do
	{
	sleep(1);
	}
	while ( quit != 0);

return 0;
}

bool AuthReciever(std::string server, int port)

{

	
 try
 {
	std::string macaddress;
	std::string reply;

	try
	{
		
	std::cout << "What is your MAC Address (it is located on the sticker on your Hypercast Reciever)\n";
	std::cin >> macaddress;
	
	std::cout << "Sending " << "CONNECT|" << macaddress << " to " << server << ":" << port << " \n";
	
		
	new_sock << macaddress;
	new_sock >> reply;
	
	}

    catch ( SocketException& ) {}

    std::cout << "We received this response from the server:\n\"" << reply << "\"\n";
	
 
	if (reply == "JOIN")
	{
	std::cout << "This reciever has been aloud to join the server.\n";
	return true;
	}

    if (reply == "REFUSE")
	{	
	std::cout << "This reciever has been rejected by the server.\n";
	return false;
	}
}
  catch ( SocketException& e )
    {
      std::cout << "Error: " << e.description() << "\n";
    }
}

int songwait (std::string songserver, int songport)

{
	bool gotsong = false;
	int songnumber = 0;
	std::string incomingdata;
	std::string streamfile;

	std::cout << "Waiting for song from Apollo Server...\n";
	
//wait for song
	do
		{

			//ClientSocket& song_sock();
			//std::cout << s;
			gotsong = true;
		}
	while (gotsong == 1);	

return 0;
}

int main ()
{

//Declarations
	std::string reply;
	pthread_t connectthread;
	std::string connectServer;
	int connectPort;	


//Initial Connection
	std::cout << "What is the IP Address of the Apollo Server?\n";
	std::cin >> connectServer;

	std::cout << "What port is it located on? \n";
	std::cin >> connectPort;

	pthread_create( &connectthread, NULL, &establishconnection, NULL);
	
	if (AuthReciever(connectServer, connectPort) == true)
	{
	std::cout << "Connected";

//LISTEN

//songwait(connectServer, connectPort);

	
	}
return 0;
}






```

---

### Post by dwhitney67 on 2007-09-09
I was only providing that previous code snippet as an example, not an actual implementation.  Here's the (partial) listing of a working implementation for a simple server:


[PHP]    TCPServerSocket serverSock;

    serverSock.SetNonBlocking();
    serverSock.SetSendBufferSize(128*1024);             // optional
    serverSock.SetRecvBufferSize(128*1024);             // optional
    serverSock.EnableReuseAddress();
    serverSock.Enable(port);
    serverSock.SetConnectBacklog(0);                    // optional

    // Indefinetely accept connections from clients
    //
    for (;;)
    {
      TCPSocket* clientSock = serverSock.Accept();

      if (clientSock)
      {
        // Handle the client after the connection has been accepted.
        // Note this would be better if there would be a fork right here,
        // thus allowing this thread to accept even more connections.
        //
        HandleTCPClient(clientSock);
        delete clientSock;
      }
      else
      {
        sleep(1);
      }
    }[/PHP]

---

### Post by t3hi3x on 2007-09-09
Did I not mention it was client program? Sorry :(

nevertheless i think this will help. i didn't think about pushing the object through functions like that. good idea. 

i'll give it a try. i think that would work.

thanks for the help.

---

