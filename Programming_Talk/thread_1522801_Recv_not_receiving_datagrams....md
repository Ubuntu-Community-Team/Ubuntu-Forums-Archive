---
title: "Recv not receiving datagrams..."
date: 2010-07-02
forum: Programming Talk
---

### Post by xefix on 2010-07-02
I am very new to socket programming, so please bear with me if I don't make any sense. I have a system set up where I create a socket, bind to it, then use recv to read incoming datagrams. These datagrams come in first to a radio that I have connected to my PC, then should technically get routed to the PC itself. However, for some reason, when I start my application, recv blocks, waiting for packets, and never receives anything. I thought the issue was occurring because no packets were being sent to the radio, but I used netsniff-ng to listen to the traffic coming in to my radio when I was expecting them, and here's the output:


50 Byte, Timestamp (1278117888.570803 s) 
 [ MAC (0a:00:3e:12:52:5f => 0a:00:3e:c8:05:34), Proto (0x0800) ] 
 [ IPv4 Addr (12.0.0.1 => 192.168.91.2), Proto (17), TTL (64), TOS (0), Ver (4), IHL (1280), Tlen (36), ID (0), 
Res: 0 NoFrag: 0 MoreFrag: 0 offset (0), Chsum (0x531e) is ok ] 
 [ UDP Port (4005 => 4005), Len (16), Chsum (0xc780) ] 
 [ Payload hex  (00 06 f0 20 01 31 00 00 ) ]
 [ Payload char (. . .   . 1 . . ) ]

42 Byte, Timestamp (1278117888.571815 s) 
 [ MAC (0a:00:3e:c8:05:34 => ff:ff:ff:ff:ff:ff), Proto (0x0806) ] 
 [ ARP Format HA (1), Format Proto (2048), HA Len (1536), Proto Len (1024), Opcode (1 => ARP request) ] 
 [ Payload hex  (0a 00 3e c8 05 34 c0 a8 5b 02 00 00 00 00 00 
   00 c0 a8 5b 01 ) ]
 [ Payload char (. . > . . 4 . . [ . . . . . . . . . [ . ) ]

42 Byte, Timestamp (1278117888.573740 s) 
 [ MAC (0a:00:3e:12:52:5f => 0a:00:3e:c8:05:34), Proto (0x0806) ] 
 [ ARP Format HA (1), Format Proto (2048), HA Len (1536), Proto Len (1024), Opcode (2 => ARP reply) ] 
 [ Payload hex  (0a 00 3e 12 52 5f c0 a8 5b 01 0a 00 3e c8 05 
   34 c0 a8 5b 02 ) ]
 [ Payload char (. . > . R _ . . [ . . . > . . 4 . . [ . ) ]

78 Byte, Timestamp (1278117888.573755 s) 
 [ MAC (0a:00:3e:c8:05:34 => 0a:00:3e:12:52:5f), Proto (0x0800) ] 
 [ IPv4 Addr (192.168.91.2 => 12.0.0.1), Proto (1), TTL (64), TOS (192), Ver (4), IHL (1280), Tlen (64), ID (41586), 
Res: 0 NoFrag: 0 MoreFrag: 0 offset (0), Chsum (0xafdf) is ok ] 
 [ Payload hex  (03 0a 24 c3 00 00 00 00 45 00 00 24 00 00 00 
   00 40 11 53 1e 0c 00 00 01 c0 a8 5b 02 0f a5 0f a5 00 10 
   c7 80 00 06 f0 20 01 31 00 00 ) ]
 [ Payload char (. . $ . . . . . E . . $ . . . . @ . S . . . 
   . . . . [ . . . . . . . . . . . .   . 1 . . ) ]



192.168.91.2 is the IP assigned by the radio to my PC, and 12.0.0.1 is the data's source IP. When I was binding to a socket, I tried to bind to port 4005 with the IP 192.168.91.2
Is this incorrect? 


Also, I should say that port 4005 is predetermined by the radio's settings for this type of data (registration information). For simple string messages, for instance, the port number is different, and I was able to get that working fine, but no luck with registration messages. Can anyone point me in the right direction or tell me what I'm missing?

---

### Post by dwhitney67 on 2010-07-02
> **xefix said:**
> ... tell me what I'm missing?
More information!

What is this "radio"?  Is it a s/w application?  Is it running concurrently with your application, and if so, is it possible that it bound port 4005 to 192.168.91.2 before your application?

It also would be helpful if you posted your code, namely where you are attempting to bind() the port and also where you are performing the recv().

---

### Post by xefix on 2010-07-02
No, the radio is a piece of hardware connected to my PC via a USB cable. The PC seems to think that it's a wireless device of some sort (the radio has an IP address and appears as wlan0). Of course, it has its own embedded software, but it should not be binding to any ports. 

Here are the relevant parts of the code (createConnection and ReceiveThread). I've only posted a portion of ReceiveThread because it never gets past recv, and the rest of it is various formatting that I do to display the received data anyway, so it probably isn't relevant. I run the function as a thread along with SendThread, but SendThread is not created until I attempt to send something, which I haven't been doing, so I don't think it would be interfering. Let me know if you need to see more code.

```


int createConnection(char *destIP, char *destPort, char *localIP, char *localPort, int delay){

  printf("Create a socket connection\n");

  // Create a listening socket
  ConnectSocket = socket( AF_INET, SOCK_DGRAM, 0 );
  if (ConnectSocket < 0) {
    printf("ConnectSocket Error at socket()\n");
    return 0;
  }

  //---------------------------------------
  // Declare and init variables
  u_short dest_port, source_port;
  char hostName[256];
  char servInfo[256];
  int retVal;
  dest_port = atoi(destPort);
  source_port = atoi(localPort);
  //-----------------------------------------
  // Set up sockaddr_in structure which is passed
  // to the getnameinfo function
  dest.sin_family = AF_INET;
  dest.sin_addr.s_addr = inet_addr(destIP);
  dest.sin_port = htons(dest_port);

  source.sin_family = AF_INET;
  source.sin_addr.s_addr = inet_addr(localIP);
  source.sin_port = htons(source_port);
  //-----------------------------------------


  // Connect to IP Port
  if(!connected){
    if ( bind( ConnectSocket, (struct sockaddr*) &source, sizeof(source) ) < 0) {
      printf( "Socket Failed to bind.\nSource IP address and Source port combination may already be in use!\nRun 'route print' to verify your routing is up to date!\n" );
      printf("Error #: %d\n", errno);
      return 0;
    }else{
      printf("Source Socket connected to %s %s \n\n", localIP, localPort);
      connected = 1;  
    }
  }


  // while((runsend) && !failure){};
  // printf("end\n");
  return 0;
}



void* ReceiveThread( void *args ) 
{ 
  int sendOnce = 0;
  int bytesRecv = 0;
  int bytesSent = 0;
  int i = 1;
  int pass = 0;
  int messageStart = 0;
  int k = 0;
 
  unsigned char *confirmReceipt;
  int bytesTransferred;
  confirmReceipt = malloc(5);
  confirmReceipt[0] = 0x0;
  confirmReceipt[1] = 0x3;
  confirmReceipt[2] = 0xBF;
  confirmReceipt[3] = 0x0;
  confirmReceipt[4] = 0x0;
  

  while( 1 ) {
    unsigned char *recvbuf;
    unsigned char *formatted;
    recvbuf = malloc(512);
    if(recvbuf == NULL){
      errNotify("Out of memory. Please, close a few background applications and try again.");
    }
    printf("listening\n");
    bytesRecv = recv( ConnectSocket, (char*)recvbuf, 512, 0 );


```

---

### Post by dwhitney67 on 2010-07-02
I haven't a clue.  It would be helpful if I had a similar radio, but I do not.  Are you 100% sure that the radio is receiving (RF?) data and then forwarding this data to 192.168.91.2/4005?

Your sniffer app seems to imply that data is being sent to 192.168.91.2/4005, but there is no evidence that this data is available to other apps other than your radio.  Anyhow, I could be confused; like I said, it would be helpful if I had a similar radio or something that I could use to emulate it.

P.S.  Test your application with a client application that sends data to 192.168.91.2/4005.  See if your primary app is able to receive data.  Make sure to try this w/o the radio plugged in.

---

### Post by pbrane on 2010-07-02
It seems to me that you're program is a 'server' type application. I don't see where you are calling *listen()* or *accept()*. Then again you haven't posted all your code.

Maybe your radio just sends UDP data to the USB once it's powered on. You still need to *select()* I think. 

It also might help to use something like wireshark to see the network traffic in a more organized fashion. I'm not sure looking at the netsniff output what's going where. 192.168.91.2 and 12.0.0.1 are two different networks. Why is the radio assigning the computer an address? I mean other than it has a DHCP server, is it a router too? Maybe you could post the make and model of that radio. I'm sure someone here can help.

It's also possible that since the computer sees your radio as *wlan0* that it is messing you up here. *wlan0* would be treated as a network device by the OS.

Doing what dwhitney67 says makes sense. Test your app without the radio.

---

### Post by soltanis on 2010-07-02
With UDP datagrams you neither use **listen(2)** nor **accept(2)**. Attempting to do so on a properly allocated datagram socket will give you an "operation not supported" error. You should also use **recvfrom(2)** rather than straight **recv(2)** with those sockets as well. That might be part of your problem.

Oh, and finally, no one packs struct sockaddr manually anymore; it's bad practice because it's both a hassle and not IPv6 compatible. It's also making your life more difficult when it doesn't need to be; look at the syntax for **getaddrinfo(3)**, which will do all the work of packing these structures for you.

Check out the Beej guide -- it's got much better explanations of all of this: [http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html#getaddrinfo](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html#getaddrinfo)

---

### Post by pbrane on 2010-07-03
> **soltanis said:**
> With UDP datagrams you neither use **listen(2)** nor **accept(2)**. ...

#-o   You are absolutely correct!

I'm sorry for the bad advise. I should know better, I use **recvfrom** in one of my own apps. And **getaddrinfo** as well.

---

### Post by xefix on 2010-07-07
Thanks to everyone who helped me! Per your suggestions, I have changed the code to use recvfrom and getaddrinfo. While this wasn't the issue, I am glad that you helped me clean up my code :D

The issue was actually the firewall. For some reason, the packets were being discarded by the system, which I found out when I ran tcpdump. I fixed this by adding port 4005 to my firewall's "allow" list. I don't really understand why 4005, but not 4007 (used for simple text messages, which I got to work without a problem), was being blocked, but at least the problem is now resolved. Again, thank you all!

---

