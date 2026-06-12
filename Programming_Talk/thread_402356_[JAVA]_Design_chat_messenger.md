---
title: "[JAVA] Design: chat messenger"
date: 2007-04-05
forum: Programming Talk
---

### Post by serlex on 2007-04-05
hi

I want to create a simple java chat program like aMSN(msn) where you people can pick users from  a list and chat to them in a separate window. 

I was thinking of having a server and client, clients connected to the server and server sends that client all the clients connected to the server which he/she can pick from; is this right or any other ways of doing this? 

Thanks

---

### Post by SniperSlap on 2007-04-05
I have some code lying around somewhere which has the basic connectivity all sorted out.  It was part of a half-baked college assignment which didn't have to be fully finished.

If you're looking to keep it as simple as possible, write a client that connects to a server using TCP connections.  Don't worry yourself about UDP just yet.  You'll want to bone up on threads as well.

My program had clients that notified the server they were disconnecting, a server that recognized clients that disconnected intentionally or not and was just about ready to pass messages back & forth.

Your server will likely want to have a heartbeat if you want it to be slightly intelligent, otherwise you're stuck only performing actions when users interact with the system.

Hopefully that gives you a good start.

---

### Post by serlex on 2007-04-06
Thanks for the reply,I just wanna get two clients talking to each other staticly and then move on to multiple clients.

quick clear out: messages from client to client go through the server? or directly from client to the client?

---

### Post by smokey edgy on 2007-04-06
I'd say it depends on your requirements. There's probably more than a few approaches. 

If you want something that will notify friends when a friend has come online, you might want to centralize the logging in to a server of some sort. In this case, the server's role would be to maintain the buddy lists and send the appropriate notifications to let people know when their friends have logged in. The actual chatting could be sent through a TCP socket client to client. But this would mean somehow discovering what your friend's IP is.  This discovery could be pretty easy as you could register and maintain the IPs of all the logged in users on the server. When you plan on sending a message to your friend, you could go off and ask the server for his or her IP and a port. You could then create a connection and send stuff across.

Or you can keep everything centralized in the server which would make your clients a little lightweight. Send messages to the server where they are queued up and sent across to their destination. Essentially, all communication is proxied through the server. A possible downside to this is an overworked server that would need to be clustered somehow.

I'm sure there's other approaches and/or variants of these.

---

### Post by Tomosaur on 2007-04-06
Java is a pretty good language to do this in. The hardest part is setting up the 'middle-man' as it were, as smokey described. You need some method of allowing your users to find and talk to each other. While it's entirely possible to use an IP-based connection method - you will lose the portability of apps like msn (ie - you will need to re-add your buddies if they log in from a different computer).

While it is entirely possible to do a client-client connection, it is much more sensible, and more flexible, to use a client-server-client combo. The two clients register each other through the server and then each can find the other.

You may also want to consider writing your own encryption algorithms to send the data (unless you don't mind sending plain-text, of course - your users may want security). Java has some encryption stuff available already, but it's up to you.

I guess you could also take a look at Java's RMI capabilities. It could allow you to create some interesting new features.

---

### Post by SniperSlap on 2007-04-06
RMI would just complicate things.

Stick to writing TCP connections.  Create your server and have messages passed through it.  This will scale better when it comes time for you to have multiple participants in a single conversation.

Your only other option would be a peer to peer model, and that would then require a bit more complex of a setup for routing messages and status information between indirectly-linked clients.

---

### Post by serlex on 2007-04-06
cheers for the replys, i'm gona stick with simple client-server-client model with TCP. Messages will be plain text going through the server. And when a client connects, server will send all the "connected" clients to the new client and then hopefully have monitoring where server knows who has disconnected.

---

### Post by smokey edgy on 2007-04-06
Cool. I agree with you sniper, the client-server-client model is more scalable and probably the more simpler solution. Serlex, I would start off with what you said (simplest solution first) and then if there's a need to have client to client communication (perhaps for file transfering and the such), build it accordingly.

Good luck!

---

### Post by serlex on 2007-04-20
Right im kind of stuck so im asking for help. at the minute I'm trying to do a chat room which is easier than a messenger. Bit I'm stuck at is the listening for messages. I can write to the server but dont know how to listen for messages in the client.

Here is my code for writing messages which works
```
sendButton.addActionListener(
				new ActionListener()
				{
				public void actionPerformed(ActionEvent event)
				{
				if (send.getText().length() == 0 ) {
				 // don't accept
				} else {
				String text = send.getText();
        		send.setText("");

			 try {
	                         sock = new Socket("127.0.0.1",5333);       // create socket and connect
				 pw   = new PrintWriter(sock.getOutputStream(), true);  // create reader and writer

					 pw.println(text);

					 } catch (Throwable e) {
					receive1.setText("server is no longer available");
					 e.printStackTrace();}}
				  }
			});//end action listener


``` 
how do i sit there and wait for messages from the server

---

