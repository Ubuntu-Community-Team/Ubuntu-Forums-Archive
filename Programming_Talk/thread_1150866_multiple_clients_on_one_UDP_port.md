---
title: "multiple clients on one UDP port"
date: 2009-05-06
forum: Programming Talk
---

### Post by bwm71 on 2009-05-06
I am trying to solve a UDP client/server problem where I don't think I can fork() as per the usual method of writing a server.  Here is the setup.  I have an RS-232 base unit that communicates with various hand held units using a technology similar to Bluetooth.  The way it communicates isn't important other than to note that in the payload of each message that a remote unit sends to the base is its "address".  This is how the base knows to which unit to send return messages.

The base connects to a device server that converts serial to TCP/IP.  The remote and local UDP port can then be defined for that serial port.

The problem is how do I handle multiple hand held units talking to this UDP server since they will all appear to come from the same client which is the device server?  It doesn't seem that a fork() in the server will buy me anything since to the server I only have one client.  If I have a single threaded server and keep track of what data belongs to which hand held unit based on its "address" which is sent in the payload, will I run into trouble if the server is trying to reply with data intended for one hand held unit while data from another is coming in.

Hope this makes sense?  Any help is appreciated.

Brandon

---

### Post by dwhitney67 on 2009-05-06
I'm not sure I quite understand your question/dilemma.  Multiple clients can send messages to a server that is managing a single UDP socket.

When the server receives from the socket, using recvfrom(), it is provided the address/port of the client that sent the message.  The server would presumably use this information when replying to the client, via a sendto() call.

---

### Post by bwm71 on 2009-05-06
The problem is that all messages sent to the server will appear to come from the same client since the real devices are connecting to the server via a serial to ethernet device server.  So, all messages will appear to come from a single IP address.

The crux of the problem is in the fact that a single RS-232 base station connected to aforementioned device server talks to multiple hand held units.  The UDP header information knows nothing about these individual units.  Only in the payload of the packet is the "address" of these hand held units.  Furthermore, multiple hand held units could be trying to communicate with the server simultaneously.

Hope that clears it up.

---

### Post by dwhitney67 on 2009-05-06
It would appear that it is the client is nothing more than a middle-man, or proxy, for these (bluetooth) devices.

It should be the responsibility of this client to keep track of the devices (i.e. when they connect, disconnect, and send messages), and should forward device messages to the UDP server, and then handle the replies from the server by forwarding them to the appropriate device.

Sending the device "address" (or identifier) as part of the message data in the UDP datagram from the client to the server is what you need to do; you just need to make sure that this same address is returned by the server when it replies.  Note that I'm not implying that this address be part of either the IP or UDP headers; I'm implying that it should be part of the message data.

Perhaps what you need to do is develop an ICD that your client and server will adhere to when communicating.  A field in the message(s) will be the device address.

---

### Post by bwm71 on 2009-05-06
Exactly right.  The "address" of the devices is in the payload of the UDP message.  Keeping track of this and sending it as part of the reply from the server is no problem.  My question really boils down to whether or not I should still fork() in the UDP server and if not, will a single threaded server choke if it's trying to reply to one device while another device is trying to send a packet to the server or will the UDP packets simply wait in line until they are processed by the server?

In other words, is UDP a free-for-all enough protocol in that messages can be slung back and forth without worrying about the client and server trying to write (or read) at the same time.

---

### Post by The Cog on 2009-05-06
Provided that the UDP packet contains a way to identify which handheld unit it came from, you can have a single controller listening on a socket that instantiates a class or structure / state machine to encapsulate the state of its relationship with each unit. That controlled can process each message itself, consulting the appropriate state machine.

---

### Post by bwm71 on 2009-05-06
This sounds interesting.  I have a server for one hand held unit currently working which is written in Perl.  Can you provide some more details on what you mean by a state machine?  Would the server still be single threaded and you are simply referring to keeping the data for each unit stored appropriately in a data structure?  Basically, I currently have

```

while ($SERVER->recv($data,$length) {
  # Do stuff with data
  $server->send($reply);
  # Where $reply contains as first four characters address of unit
  # That is decoded by base unit and rest of message is sent to
  # appropriate hand held unit
}

```

---

### Post by dwhitney67 on 2009-05-06
Think of UDP (and TCP) sockets as being two-lane highways; they have two internal buffers, one for receiving and one for sending data.  These buffers are independent, and in fact can be configured by the application to be a certain depth.

One thing you can define with the client/server messages is a field that contains a Message-ID.  Use this unique identifier to store the received message (in a hash-table?) if a reply cannot immediately be sent back.

I can assure you that using fork() or writing a multi-threaded application is doable, and probably wise.  Your server should have an independent "Receiver" and "Sender", especially if you foresee the need to handle hundreds of messages per second, or if there will be any type of delay in responding to the client.

Similarly, the client could be setup like the server, with a "Sender" and "Receiver".

---

### Post by bwm71 on 2009-05-07
OK.  The two lane highway analogy helps.  Sorry to be so obtuse about this, but I think I'm just about there.  Using the highway analogy, will UDP packets wait in line until they can clear the toll booth?  Also, since the IP/port of the client is fixed I can manually create a handle to send the client in my code, but how would I go about creating a different sender and receiver without hardcoding the IP/port address of the client and did something like

> 
while ($SERVER->recv()) {
  $SERVER->send()
}


In this example, it seems I don't have a different sender and receiver.

---

### Post by dwhitney67 on 2009-05-07
UDP packets are indeed queued as they are sent.  Use this feature to your advantage when planning your design.

Without detailed timing requirements for your project, it is quite possible that you do not need to fork() or develop threads; this was merely a suggestion.

Here's a scenario where forking is not done:
```

// assume socket already setup

timeout = 0.1;   // one-tenth of a second

// block until either ready to receive, or timeout expires.
if (readyToReceive(socketDescriptor, timeout) is true)
{
   Message msg

   receiveMsg(socketDescriptor, msg)

   storeMessage(msg)
}
else
{
   while (haveMessagesToProcess() is true)
   {
     Message msg      = getNextMessage()
     Message response = prepareResponse(msg)

     sendMsg(socketDescriptor, response)
  }
}

```

---

### Post by bwm71 on 2009-05-07
Thank you very much.  What you have shown is essentially what I have working now for the one hand held unit that sits behind the client.  I'll just need to fix up the data structure to account for multiple units.

I really appreciate the help and sticking with me on the discussion.

Brandon

---

### Post by The Cog on 2009-05-07
Yes, incoming UDP packets will get queued up while you are processing the previous one.

Dumb analogy: Imagine a lawyer involved in property conveyancing. He waits by the letterbox for a letter to arrive. When a letter arrives, he gets out the relevant file, deals with the letter by doing filing, writing more letters and posting them. Then returns to waiting by the letterbox. Multiple conveyances for multiple clients in progress, but only one lawyer doing any work.

---

