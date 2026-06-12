---
title: "[SOLVED] C++ Sockets - send() problem !"
date: 2008-06-30
forum: Programming Talk
---

### Post by tornado89 on 2008-06-30
I' Running A Server And Client Exchanging  Commands...
I Have A Strange Problem In The Server

Server
======
I'm select()ing Between The Normal Input ( stdin ) and The Listening Socket
And Then recv() Data From The Socket If Ready


Client
======
When I Write Multiple ( Send() ) Commands... The Server Receive Them As
One Packet

If I Sent "Test" followed By Another send() command Containing "Test2"
They Arrive As One Package With Size of 9 !!!!!!!
The Server Command recv() Is Invoked Only Once !!!!!

---

### Post by slavik on 2008-06-30
turn off buffering

---

### Post by tornado89 on 2008-06-30
Do U Mean Specifying The FLAG TCP_NODELAY for the Socket...
or What's The Best Way To Do It ??

---

### Post by slavik on 2008-06-30
probably

---

### Post by tornado89 on 2008-06-30
It Didn't Work For Me....
It Works As Supposed When I Force The Client To Wait ( sleep(1) )
Between Each Call to send()...

But That's The Dirty Way:D... Is There Another Way ???!

---

### Post by escapee on 2008-06-30
I believe recv() pulls in as a stream, so until it reaches it's max amount or reaches something to stop the read, it'll keep pulling in more information.  
Did you create a method of some sort to denote that the message is complete?

---

### Post by tornado89 on 2008-06-30
Nope.. I'll Try It Out Now...
Then I'll Repost...
:)
Thx..

---

### Post by public_void on 2008-06-30
I wouldn't use TCP packets to act as a delimiter of commands. Each command is having to be wrapped and sent, even then big commands will have to span two or more packets. You may want to define a simple protocol for you commands. For example you could send:

[size][command][terminator]

This allows you send variable length commands, however this has the problem of possibly partial sends and buffering the data as its received to detect incomplete commands. This is because as TCP may split the command over two or more packets.

---

### Post by tornado89 on 2008-06-30
Hey public_void, i know what you're talking about....
i have no problem in packet division.. 
i can create a send loop to make sure that data are all sent

about the approach of 

[PHP]
[size][command][terminator]
[/PHP]

When i send the size followed by the command
they're sent in one packet....[ size+command ]

---

### Post by escapee on 2008-06-30
> **public_void said:**
> I wouldn't use TCP packets to act as a delimiter of commands. Each command is having to be wrapped and sent, even then big commands will have to span two or more packets. You may want to define a simple protocol for you commands. For example you could send:

[size][command][terminator]

This allows you send variable length commands, however this has the problem of possibly partial sends and buffering the data as its received to detect incomplete commands. This is because as TCP may split the command over two or more packets.

I'm sorry, "terminator" was the term I was intending, but only delimiter came to mind.  Good catch, thanks for that.

---

### Post by johnl on 2008-07-01
TCP guarantees that the data you transmit will be 1) received reliably 2) in the order it was sent.  It does not guarantee anything about how much of it will arrive at once -- it's a stream protocol, not a packet-based protocol.

What you need to do is what was suggested above -- create your own application-level protocol that can handle packets.  Usually you will see something like this:

```

uint8_t  magic_byte;  // this is some arbitary byte.. 0xff, 0x3a, whatever.
uint8_t  packet_id;   // this is how you identify which packet this is
uint16_t packet_size; // the number of data bytes in this packet, plus
                      // the four bytes for this header
void*    packet_data; // packet-specific data.

```

Basically, what you can do then is this -- whenever you read data from the socket, add it to the end of your buffer.  Then, check the first four bytes of the buffer, which will correspond to the packet header.  You can read the size of the packet from that.  If the size is less than the number of bytes in your buffer, you can pull that out and process it as a packet!  Continue, until the length found in the header is larger than the number of bytes you have left.

Here's an example I just whipped up -- not tested :)
Obviously this is C, in C++ you could do a lot of this with stl containers or classes.
```

#define MAX_BUFFER_SIZE 2048
#define MY_MAGIC_CONSTANT 0xFF

uint8_t buffer[MAX_BUFFER_SIZE];
size_t buffer_size = 0;


while(true) {
   len = recv(socket, buffer + buffer_size, MAX_BUFFER_SIZE - buffer_size, 0);
   /* check here that len > 0 (ie, connection still alive) */
   buffer_size += len;

   /* while we have a packet header */
   while(buffer_size >= 4) {
       uint8_t magic = buffer[0];
       uint8_t id = buffer[1];   
       uint16_t packet_size = *(uint16_t*)(buffer + 2);

       /* check that this packet starts with our magic byte */
       if (magic != MY_MAGIC_CONSTANT) {
           printf("expected 0x%02x, got 0x02%x\n",
                  MY_MAGIC_CONSTANT,
                  magic);
           /* handle this somehow.  or just die. */
           exit(1);
       }
       
       if (packet_size <= buffer_size) {
           /* supposing we have a function
            * handle_packet(int packet_id,
            *               void* packet_data,
            *               int packet_data_size);
            */
           handle_packet(id, buffer + 4, packet_size - 4);

           /* now shift the data down so we can check the next packet. */
           memmove(buffer, buffer + packet_size, buffer_size - packet_size);
           buffer_size -= packet_size;
       } else {
           /* we need to receive more data before we can
            * process this packet. */
           break;
       }    

   }
}

```

Hope this helps!

---

