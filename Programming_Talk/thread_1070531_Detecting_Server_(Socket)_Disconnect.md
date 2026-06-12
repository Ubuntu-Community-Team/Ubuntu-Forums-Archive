---
title: "Detecting Server (Socket) Disconnect?"
date: 2009-02-15
forum: Programming Talk
---

### Post by gvanto on 2009-02-15
After following the great tutorial on here: <a href="http://tldp.org/LDP/LG/issue74/tougher.html">http://tldp.org/LDP/LG/issue74/tougher.html</a>[<a href="http://tldp.org/LDP/LG/issue74/tougher.html" target="_blank" title="New Window">^</a>]

sources in folder here: <a href="http://www.sharedigest.com/SocketClientServer.zip">http://www.sharedigest.com/SocketClientServer.zip</a>[<a href="http://www.sharedigest.com/SocketClientServer.zip" target="_blank" title="New Window">^</a>]

I've managed to get the client and server talking to each other.

This is for an setup whereby data will be transmitted to my client via telnet from a remote server, and, according to them, I need to configure the client in such a way that it checks if the server dies and automatically attempts to reconnect after some (pre-specified) time period.

Currently, when I kill the server, I get ALOT of '' received by the client, continuously ... (output shown below, main routine shown below output)

I was wondering if there's a way to detect that the connection from the server's been lost, and consequently attempt to reconnect and keep listening for incoming messages?

Help much appreciated!
gvanto
socket newbie

<code>
Server:
pacific@mainbox:~/workspace/SocketClientServer/Debug$ ./SocketClientServer 0
starting server ...
Hello server from client.
Please enter string to send: hello back to client
Please enter string to send: another message
Please enter string to send: one more
Please enter string to send:     //here i kill the server using ctrl+c


Client:
pacific@mainbox:~/workspace/SocketClientServer/Debug$ ./SocketClientServer 1
starting client ...
Sending hello server msg ...
Listening ...
We received this response from the server:
"hello back to client"
Listening ...
We received this response from the server:
"another message"
Listening ...
We received this response from the server:
"one more"
Listening ...
We received this response from the server:  //AFter server killed, FLOOD of incoming BLANK messages received by client
""
Listening ...
We received this response from the server:
""
Listening ...
We received this response from the server:
""
Listening ...
We received this response from the server:
""
Listening ...
We received this response from the server:
""
Listening ...
We received this response from the server:
""
Listening ...
We received this response from the server:
""
Listening ...
We received this response from the server:
""
Listening ...
We received this response from the server:
""
Listening ...
We received this response from the server:
""
Listening ...
We received this response from the server:
""
Listening ...
We received this response from the server:
""
Listening ...
We received this response from the server:
""
Listening ...
We received this response from the server:
""
Listening ...
We received this response from the server:

</code>


MAIN ROUTINE:
<code>

/*
 * main.cpp
 *
 *  Created on: 15/02/2009
 *      Author: pacific
 *
 *      [http://tldp.org/LDP/LG/issue74/tougher.html](http://tldp.org/LDP/LG/issue74/tougher.html)
 */


#include <iostream>
#include <cstdlib>
#include <stdio.h>
#include <string>
#include <stdlib.h>

#include "ServerSocket.h"
#include "ClientSocket.h"
#include "SocketException.h"

#define DO_MAIN 1

using namespace std;


#ifdef DO_MAIN
int main(int argc, char *argv[]) {

	if(argc > 1) {
		/*****************************************************
		 * *********** SERVER *******************************/
		if(atoi( argv[1] ) == 0) { //server mode
			cout << "starting server ... " << endl;

			try {
				//Create the server socket
				ServerSocket *server = new ServerSocket(30000); //set up socket and listen on local port

				while(true) { //wait for incoming connections

					/**
					 * Contains all of our socket information, used to exchange data with the client.
					 */
					ServerSocket new_sock;
					server->accept(new_sock); //accept new incoming socket connection

					try {
						while(true) {
							string data;
							new_sock >> data; //read data from new_sock into 'data'
							cout << data << endl;
							//new_sock << data; //sends data in 'data' back throught the socket to the client (echo server)

							string sendstr;
							while(1) {
								cout << "Please enter string to send: ";
								getline (cin, sendstr);
								new_sock << sendstr; //send it!
							}

						}
					}
					catch(SocketException&) {}
				}

			}
			catch(SocketException &e) {
				 std::cout << "Exception was caught:" << e.description() << "\nExiting.\n";
			}

		}


		/*****************************************************
		 * *********** CLIENT *******************************/
		if(atoi(argv[1]) == 1 ) { //client mode
			cout << "starting client ... " << endl;

			try {
				//Create the server socket
				ClientSocket client("localhost", 30000); //set up socket and listen on local port
				string reply;

				try {
					cout << "Sending hello server msg ... " << endl;
					client << "Hello server from client. "; //send
				}
				catch(SocketException &) {}

				while(true) { //keep listening

					try {
						cout << "Listening ... " << endl;
						//client << "Test message. "; //send
						client >> reply; //receive
					}
					catch(SocketException &) {}

					std::cout << "We received this response from the server:\n\"" << reply << "\"\n";;
				}
			}
			catch(SocketException &e) {
				std::cout << "Exception was caught:" << e.description() << "\nExiting.\n";
			}

		}

	}
	else {
		cout << "usage: ./SocketClientServer 0|1 (0 == server, 1 == client)" << endl;
	}

	return 0;
}



#endif

























</code>

---

### Post by dwhitney67 on 2009-02-15
I like what you have done with the overloading of the operator>>() and operator<<() for receiving and sending messages.  I may do something similar for my Socket class library.

One thing I could not gather from your code, is whether the "receive" overloaded operator method is performing a select(), and if the method is returning an error (via a flag or other means) if activity is detected but no data is received.  If the method is setting an error flag, then you need to examine it before assuming you have received data.

If you decide not to use a select(), and just want to read whenever instructed to do so (by the >> operator), then recv() should return a value of zero when the peer has (properly) shutdown.  You may also want to consider looking at other possibilities (i.e. return value is -1), if the stream is setup as non-blocking.

My instincts however, are to recommend that you employ the use of select() to determine when there is activity on the socket descriptor.

P.S.  I would recommend that you consider refactoring your code; when the server accepts a connection, the socket object that is return should not be a ServerSocket object; it should be something similar, but without the capabilities to perform server duties (e.g. accept()).

P.S.S.  I looked over your code again; one thing that seems odd is that your client is printing the server response outside of the try-catch blocks; maybe you should consider moving the cout statement inside the try-block.

---

### Post by gvanto on 2009-02-16
thanks alot dwhitney,
i've put in some error checking and i think it now works! will see when it goes into production though ... :-)

many thanks again for your help!

onto threads now ... best way to do this in C++ :-)

---

### Post by captwiggum on 2009-04-28
```
"""
tcp_disconnect.py
Echo network data test program in python. This program easily translates to C & Java.

By TCP rules, the only way for a server program to know if a client has disconnected,
is to try to read from the socket. Specifically, if select() says there is data, but
recv() returns 0 bytes of data, then this implies the client has disconnected.

But a server program might want to confirm that a tcp client is still connected without
reading data. For example, before it performs some task or sends data to the client.
This program will demonstrate how to detect a TCP client disconnect without reading data.

The method to do this:
1) select on socket as poll (no wait)
2) if no recv data waiting, then client still connected
3) if recv data waiting, the read one char using PEEK flag 
4) if PEEK data len=0, then client has disconnected, otherwise its connected.
Note, the peek flag will read data without removing it from tcp queue.

To see it in action: 0) run this program on one computer 1) from another computer, 
connect via telnet port 12345, 2) type a line of data 3) wait to see it echo, 
4) type another line, 5) disconnect quickly, 6) watch the program will detect the 
disconnect and exit.

I hope this is helpful to someone. John Masinter, 17-Dec-2008.
"""

import socket
import time
import select

HOST = ''       # all local interfaces
PORT = 12345    # port to listen

# listen for new TCP connections
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
s.bind((HOST, PORT))
s.listen(1)
# accept new conneciton
conn, addr = s.accept()
print 'Connected by', addr
# loop reading/echoing, until client disconnects
try:
    conn.send("Send me data, and I will echo it back after a short delay.\n")
    while 1:
        data = conn.recv(1024)                          # recv all data queued
        if not data: break                              # client disconnected
        time.sleep(3)                                   # simulate time consuming work
        # below will detect if client disconnects during sleep
        r, w, e = select.select([conn], [], [], 0)      # more data waiting?
        print "select: r=%s w=%s e=%s" % (r,w,e)        # debug output to command line
        if r:                                           # yes, data avail to read.
            t = conn.recv(1024, socket.MSG_PEEK)        # read without remove from queue
            print "peek: len=%d, data=%s" % (len(t),t)  # debug output
            if len(t)==0:                               # length of data peeked 0?
                print "Client disconnected."            # client disconnected
                break                                   # quit program
        conn.send("-->"+data)                           # echo only if still connected
finally:
    conn.close()

```

---

