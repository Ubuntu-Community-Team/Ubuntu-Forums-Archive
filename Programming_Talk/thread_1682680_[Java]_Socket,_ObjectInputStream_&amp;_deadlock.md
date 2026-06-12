---
title: "[Java] Socket, ObjectInputStream &amp; deadlock?"
date: 2011-02-06
forum: Programming Talk
---

### Post by SpinningAround on 2011-02-06
In the following code do I wish to create communication between a server and a client, problem is that everything stop when ObjectInputStream are being created. First out.println are printed but not the second. 
[PHP]
class ConnectedThread extends Thread{
	private ObjectInputStream in = null;
	private ObjectOutputStream out = null;

	ConnectedThread(Socket socket) throws IOException{
		System.out.println("CT 1"); // printed
		in = new ObjectInputStream(socket.getInputStream());
		System.out.println("CT 2"); // never printed
		out = new ObjectOutputStream(socket.getOutputStream());
		System.out.println("CT 3");
	}
[/PHP]

If I stop either the server or the client do I get this exception
[PHP]
java.io.EOFException
	at java.io.ObjectInputStream$PeekInputStream.readFully(ObjectInputStream.java:2297)
	at java.io.ObjectInputStream$BlockDataInputStream.readShort(ObjectInputStream.java:2766)
	at java.io.ObjectInputStream.readStreamHeader(ObjectInputStream.java:797)
	at java.io.ObjectInputStream.<init>(ObjectInputStream.java:297)
	at network.ConnectedThread.<init>(ConnectedThread.java:15)
	at network.Client.<init>(Client.java:30)
	at network.HandleConnections.run(Server.java:94)
[/PHP]

EDIT:
Solved it, change place between input and output.

---

### Post by PaulM1985 on 2011-02-07
Is it definately not throwing the IOException in the constructor?  Can you provide some of the surrounding code, like when the socket is created.

From looking at the EOFException, I am assuming this is client code.  Are you writing something to the client socket before the client manages to get set up fully?

Paul

---

### Post by Some Penguin on 2011-02-08
Perhaps you're not flushing the data, in which case the consumer may well be waiting for data which is sitting in the producer's buffers.

---

### Post by PaulM1985 on 2011-02-17
I have recently had the same problem and I thought I would post what happened to me, incase anyone else has the same issue.

I was connecting at the server end using:
createSomeStream(getInputStream());
createSomeStream(getOutputStream());

and at the client end
createSomeStream(getInputStream());
createSomeStream(getOutputStream());

It seems that because they are both getting an input stream, they both need to wait for the other to get an output stream, causing a deadlock.  Something to always remember is that these should be done in opposite orders at the client and server end, so the server could do:
createSomeStream(getInputStream());
createSomeStream(getOutputStream());

and the client:
createSomeStream(getOutputStream());
createSomeStream(getInputStream());

I hope this helps someone out in the future.

Paul

---

