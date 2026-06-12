---
title: "Python Server and Java client communication issue"
date: 2015-11-21
forum: Programming Talk
---

### Post by Blackbug on 2015-11-21
I am trying to connect a simple java client to a simple python test server, but for some reason i am unable to do so. My java client is an android app on my phone which is on same network as my laptop on which i am running python test server. The codes of both are as below:

python server

```
   import socket               # Import socket module
    soc = socket.socket()         # Create a socket object
    host = "localhost" # Get local machine name
    port = 2001                # Reserve a port for your service.
    soc.bind((host, port))       # Bind to the port
    soc.listen(5)                 # Now wait for client connection.
    while True:
         conn, addr = soc.accept()     # Establish connection with client.
         print ("Got connection from",addr)
         msg = conn.recv(1024)
         print (msg)
         if ( msg == "Hello" ):
             print("Msg received from test client")
         else: 
             print("No connections received")
```

android client:
using this line to connect to socket and then various methods of socket class to play with data
```

s = new Socket(IP address of my laptop, 2001);
```

I checked the tcpdump on port 2001(on my laptop where server is running) while I am triggering the connection from the app, and it does show messages the moment I trigger the connection, however, nothing on the server. I dont understand the tcpdump output nor the situation. I have openssh-sever installed, and able to even ssh from my android phone( using an android-terminal app) to my laptop.

```

> sudo tcpdump -i any port 2001
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on any, link-type LINUX_SLL (Linux cooked), capture size 262144 bytes
02:06:51.741482 IP 10.42.0.43.33328 > 10.42.0.1.2001: Flags [S], seq 1067828140, win 14600, options [mss 1460,sackOK,TS val 818858 ecr 0,nop,wscale 6], length 0
02:06:51.741609 IP 10.42.0.1.2001 > 10.42.0.43.33328: Flags [R.], seq 0, ack 1067828141, win 0, length 0
02:06:56.529649 IP 10.42.0.43.40191 > 10.42.0.1.2001: Flags [S], seq 4259599449, win 14600, options [mss 1460,sackOK,TS val 819814 ecr 0,nop,wscale 6], length 0




```
Any ideas? Thanks.

---

### Post by ian-weisser on 2015-11-22
Here's how I troubleshoot such problems:

Open a terminal window and create the simplest listening socket possible:
```
nc -l 45678
```

Open *another* terminal window and connect to the socket using the simplest client possible: 
```
nc localhost 45678
```

Type some gibberish and pass it back and forth between the windows using the open socket. You KNOW that socket works - you just tested it.

Now you know how to create test servers and test clients that you know work (and how to test them).

Check your client with the test server.
Check your server with the test client.

I think your tcpdump indicates an issue with your server, since it's picking up the client TCP traffic. While your socket server is running, check 'netstat -tulpn' to see if it's really listening on a socket.

Here's how I did it in Python3:
```

>>> import socket
>>> tempsocket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
>>> tempsocket.bind(("127.0.0.1", 45678))   ## Tuple: (IP Addr, Port)
>>> tempsocket.listen(1)
>>> conn, addr = tempsocket.accept()        ## Listener blocks here awaiting sender's connect()
>>> conn.recv(1024).decode('UTF-8')         ## Listener blocks here awaiting send()
'Hello, World'                              ## Try it a few times to catch each send()
>>> tempsocket.close()
```

---

### Post by Blackbug on 2015-11-22
Thanks your command line approach was really helpful. Indeed, my android client was able to communicate with the basic server. However, I just realised I need a websocket server to handle request from webclient and route to my android client.

Thanks anyways. It was helpful.

---

