---
title: "UDP java"
date: 2009-02-09
forum: Programming Talk
---

### Post by MurphyP on 2009-02-09
Hi guys, first time poster here, long time Ubuntu user

I am having problems transferring objects via UDP from one thread to another. I keep getting NullPointerException's on my send() call.

I am transferring a "Box" object that implements Serializable, it has two values one is another object that implements Serializable

Here is what my send looks like:
```

Box box = new Box(valueA,valueB);
InetAddress ip = InetAddress.getByName("localhost");

ByteArrayOutputStream b_out = new ByteArrayOutputStream();
ObjectOutputStream o_out     = new ObjectOutputStream(b_out);
o_out.writeObject(box);
byte[] sStream = byteOut.toByteArray();

DatagramPacket sPacket = new DatagramPacket(sStream, sStream.length, ip, toPortNum);
socket.send(sPacket);
```

Here is what the receive looks like:
```

byte[] r_data;
DatagramSocket socket;
DatagramPacket r_packet;	
ByteArrayInputStream b_in;
Box obj;

r_data = new byte[10000];
b_in = new ByteArrayInputStream(r_data);
r_packet = new DatagramPacket(r_data, r_data.length);

try {
	socket.receive(r_packet);
	ObjectInputStream o_in = new ObjectInputStream(b_in);
	obj = (Box) o_in.readObject();
} catch (Exception e) {e.printStackTrace();}
```


the toPortNum is the same number as the receiving threads socket. I have printed the box object before I send it, so it isnt null. The receiving thread waits at .receive(r_packet) and Iget the NullPointerExcption at the sending thread .send(sPacket). I am very new to socket programming so it could be something trivial... 

Any ideas?
Thanks!
Murph

---

### Post by michael_1234 on 2009-02-09
This is probably too simple (this may simply be in code not shown), but the receiver is missing the creation of the Socket, eg, 
    socket = new DatagramSocket(toPortNum);The server shouldn't even start without that (you should get a null pointer exception).  

And, that doesn't necessarily explain why the client (sender) is throwing an exception.  What is the full stack trace of the exception?  Also, you say Box is serializable, but is all the objects it contains also serializable (value A & B)?

Also, you may already be using this as a reference, but you could start with this sample program here & customize: [http://java.sun.com/docs/books/tutorial/networking/datagrams/clientServer.html](http://java.sun.com/docs/books/tutorial/networking/datagrams/clientServer.html)

Cheers,
-m

---

### Post by MurphyP on 2009-02-09
Hi Michael.

The socket creation is actually taken care of in the constructor of the receiving thread. Sorry I didn't mention that before.

Yes the values are also implementing Serializable.

Here is the entire stack trace. run() calls putIn() and putIn() runs the sender code above. After the exception it just bails and runs again. 

java.lang.NullPointerException
	at A2.Client.putIn(Client.java:65)
	at A2.Client.run(Client.java:173)

Edit: I've actually looked at that tutorial and several others, unfortunately I cannot seem to find anything that sends objects through UDP sockets except for [http://www.javaspecialists.co.za/archive/Issue028.html](http://www.javaspecialists.co.za/archive/Issue028.html) at point 4 which I used as a reference

Regards,
Murph

---

### Post by michael_1234 on 2009-02-10
> **MurphyP said:**
> 
Here is the entire stack trace. run() calls putIn() and putIn() runs the sender code above. After the exception it just bails and runs again. 

java.lang.NullPointerException
    at A2.Client.putIn(Client.java:65)
    at A2.Client.run(Client.java:173)


The key line is Client.java:65, there's a reference that has not been assigned. Fire up your IDE (eg, Netbeans or Eclipse if you prefer), set a break point on line 65, and see which reference is NULL.... then, find out why it's null...  Just repeat that process about a billion times, stir in some gray hair and add a generous heaping of very late nights -- and welcome to my life.

-m

---

### Post by MurphyP on 2009-02-10
Thanks Michael - you were actually 99% right in the begginning. I got someone to help me use the debugging feature with a breakpoint at 65 in Client in Eclipse and it turns out my sending thread's(Client) socket hadn't been created. 

Cheers again for your help. 
Now I just need to learn to mark my forum threads as solved :).
Murph

---

