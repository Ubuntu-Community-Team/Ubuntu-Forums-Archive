---
title: "Java Socket Programming Question - Is this Socket Server crash tolerant?"
date: 2010-08-16
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-08-16
I copied most of this code from here:

[http://www.stanford.edu/class/cs108/handouts092/33Sockets.pdf](http://www.stanford.edu/class/cs108/handouts092/33Sockets.pdf)

In the ordinary case, it works fine.  However, the client does not always send a close connection command to the serverAccepter object below, in fact, in my current implementation, it never does, it just crashes abruptly.  I currently handle this by having a general Exception catcher which just does nothing.  The ServerAccepter just loops infinitely looking for a new connection.  I tested this and it seems to work, but is there a cleaner way to handle the case where the client just abruptly drops connection?  For example, the code below usually enters the exception on the *command = instream.readLine();* line.  Is there a way to put that line in some kind of a try block which can test if instream becomes invalid at any time?  Better question, is there a higher-level, but lightweight Java library which handles issues such as this?  I really only need to network two computers directly over a local network in my room.

[PHP]
	// Server thread accepts incoming client connections
	class ServerAccepter extends Thread {
		private int port;
		ServerAccepter(int port) {
			this.port = port;
		}

		@Override
		public void run() {
			String command;
			ServerSocket serverSocket = null;
			try {
				serverSocket = new ServerSocket(port);
			} catch (IOException e) {
				e.printStackTrace();
			}
			
			while (true) {
				try {
					Socket toClient = null;
					// this blocks, waiting for a Socket to the client
					toClient = serverSocket.accept();
					System.out.println("server: got client");
					// Get an output stream to the client, and add it to
					// the list of outputs
					// (our server only uses the output stream of the connection)
					ObjectOutputStream out = new ObjectOutputStream(toClient.getOutputStream());
					BufferedReader instream = new BufferedReader(new InputStreamReader(toClient.getInputStream()));
					while(true)
					{
						command = instream.readLine();
						System.out.println(command);
						if(command == null || command.equalsIgnoreCase("Close"))
						{
							toClient.shutdownInput();
							toClient.shutdownOutput();
							out.close(); 
							instream.close();            		                   		
							toClient.close();                    		
							break;
						}
						else if(writermap.containsKey(command))
						{
							writermap.get(command).addOutputStream(out);
						}
						else System.out.println("Command not understood");
					}                     
				} catch (Exception ex) {
					closeNetworkStream();
					ex.printStackTrace();
				}
			}
		}
	} 
[/PHP]

---

### Post by dwhitney67 on 2010-08-16
A client will terminate in any which way it seems fit to do.  The server cannot dictate this, nor should it make any assumptions as to how the client will terminate (and shutdown it's sockets).

When a client shuts down it's socket, whether gracefully or not, what does the server get within the variable 'command' from this statement?
```

command = instream.readLine();

```
I would expect it to be null.  Can you verify whether this is true?  Without the complete code for the server, I cannot test my hypothesis.

Anyhow, the code you have seems reasonable.  Do you still have issues with detecting that the client has closed it's connection?

---

### Post by phrostbyte on 2010-08-21
Hmm, this might be unrelated but if I where you I'd run each session on it's own thread (looks like the second loop). 

So it should be like this

[Main Program] - (forks new thread) -> [Server Listener] -> (forks thread for each accept) -> [Server Session]

Any shenanigans by the client will cause an exception to be thrown and in Java this means the thread that threw the exception will be killed (in this case, the session's thread). Dirty hack, but it will work.

---

