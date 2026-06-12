---
title: "I'm having trouble with multithreading in Java..."
date: 2010-02-06
forum: Programming Talk
---

### Post by Yes on 2010-02-06
I'm trying to make this chat program, with a server that listens for new clients and other clients' messages, which it then passes along to all the clients.  So, I thought I should make one thread listening for new clients and one for handling input/output.

Then I have a client program which has one thread for listening for user input and giving that to the server, and one that listens for input from the server.  The problem is that sometimes the user input is passed to the server, sometimes it isn't.  And it's never passed back to the client.

I think the problem is with the threads in my client program, could anyone help me figure out what's wrong?  And I know there's a ton of other problems, but this is the big one right now.

Client.java:

[php]import java.net.*;
import java.io.*;

public class Client {
	
	private static final String HANDSHAKE = "IamImme";
	private static  Socket connection;
	private static BufferedReader incoming;
	private static BufferedReader userInput = new BufferedReader (new InputStreamReader (System.in));
	private static String messageIn;
	private static PrintWriter outgoing;
	private static String messageOut;
	private static String myName;


	/*
	 * usage: java Client <user name>
	 */
	
	public static void main (String args[]) {
		myName = args[0];
		
		try {
			connection = new Socket("127.0.0.1", 8080);
		
			incoming = new BufferedReader (new InputStreamReader (connection.getInputStream ())); //creat input/output streams
			outgoing = new PrintWriter (connection.getOutputStream ());
		
			outgoing.println (HANDSHAKE); //send handshake
			outgoing.println (myName);
			outgoing.flush ();
		
			messageIn = incoming.readLine (); //receive and verify handshake
			if (!messageIn.equals (HANDSHAKE))
				throw new IOException ("Connected client not client");
		
			System.out.println ("Connected to " + connection.getInetAddress () + "."); //print grettings
			
		} catch (Exception exc) {}
		
		new UserInput ();		
		new ReadLine ();
	}
	
	private static class ReadLine extends Thread {
		ReadLine () {
			start ();
		}
		
		public void run () {
			while (true) {
				try {
					messageIn = incoming.readLine ();
					if (messageIn != null && (messageIn.substring (0, myName.length()).compareTo (myName)) != 0)
						System.out.println (messageIn);
				} catch (Exception exc) {}
			}
		}
	}	
	
	private static class UserInput extends Thread {
		UserInput () {
			start ();
		}
	
		public void run () {
			try	{			
				while (true) {
					messageOut = userInput.readLine ();
					outgoing.println (messageOut);
					outgoing.flush ();
					System.out.println ("Me: " + messageOut);
				}
				
			} catch (Exception exc) {
				System.err.println ("Error: " + exc);
				return;
			}
		}	
	}
}[/php]

Server.java:

[php]import java.net.*;
import java.io.*;
import java.util.ArrayList;

public class Server {
	
	private static final String HANDSHAKE = "IamImme";
	private static ServerSocket listener;
	private static Socket connection;
	private static ArrayList<BufferedReader> incoming = new ArrayList<BufferedReader> ();
	private static BufferedReader userInput = new BufferedReader (new InputStreamReader (System.in));
	private static String messageIn;
	private static ArrayList<PrintWriter> outgoing = new ArrayList<PrintWriter> ();
	private static ArrayList<String> clients = new ArrayList<String> ();
	private static String messageOut;

	
	public static void main (String args[]) {
		new ListenForConnections ();
		new ReadLine ();
	}
	
	private static class ReadLine extends Thread {
		ReadLine () {
			start ();
		}
		
		public void run () {
			while (true) {
				try {
					for (int i=0; i<incoming.size (); i++) {
						messageIn = incoming.get(i).readLine ();
						System.out.println (messageIn);
						if (messageIn != null) 
							for (int k=0; k<clients.size (); k++) {
								System.out.println (clients.get (i));
								outgoing.get (k).print (clients.get (i) + ": " + messageIn);
								outgoing.get (k).flush ();
							}
					}
				} catch (Exception exc) {}
			}
		}
	}
	
	private static class ListenForConnections extends Thread {
		ListenForConnections () {
			start ();
		}		

		public void run () {
			String clientName;
			
			System.out.println ("Listening on port 8080");
			
			try {
				while (true) {
				
					listener = new ServerSocket (8080); //create server socket
		
					connection = listener.accept (); //listen and accept incoming connection
					listener.close ();
				
					BufferedReader newIncoming = new BufferedReader (new InputStreamReader (connection.getInputStream ())); //creat input/output streams
					PrintWriter newOutgoing = new PrintWriter (connection.getOutputStream ());
			
					newOutgoing.println (HANDSHAKE); //send handshake
					newOutgoing.flush ();
			
					messageIn = newIncoming.readLine (); //receive and verify handshake
					clientName = newIncoming.readLine ();
			
					if (!messageIn.equals (HANDSHAKE))
						throw new IOException ("Connected client not client");
			
					System.out.println ("Connected to " + connection.getInetAddress () + " (" + clientName + ")."); //print grettings
					newOutgoing.flush ();
			
					clients.add (clientName);		
					incoming.add (newIncoming);
					outgoing.add (newOutgoing);
				}
				
			} catch (IOException exc) {}
		}
	}
}[/php]

Thanks very much!

---

### Post by dwhitney67 on 2010-02-07
Along with the overuse of the keyword 'static', which is indicative of a poor, or lack of a, design, you did not perform adequate research into the fundamentals of multi-threaded programming, namely the issues dealing with concurrent access to data types/containers.

Direct from the Java API wrt ArrayList:
```

...

Note that this implementation is not synchronized.  If multiple threads access an ArrayList
instance concurrently, and at least one of the threads modifies the list structurally, it must
be synchronized externally. (A structural modification is any operation that adds or deletes one
or more elements, or explicitly resizes the backing array; merely setting the value of an
element is not a structural modification.) This is typically accomplished by synchronizing on
some object that naturally encapsulates the list. If no such object exists, the list should be
"wrapped" using the Collections.synchronizedList  method. This is best done at creation time, to
prevent accidental unsynchronized access to the list:

   List list = Collections.synchronizedList(new ArrayList(...));

...

```

A little advice; push your code to the side, and start anew.  Avoid using the 'static' keyword; develop in terms of class objects.

You do **not** need to close the server 'listen' socket every time a client connects; use it over and over again.  Each time a client connects, you will be provided with a unique socket for that client which you will need to add to a *thread-safe* container.

When a client disconnects, you need to remove their socket from the thread-safe container; you currently don't even handle this situation.

Avoid looping to read data from each client; read only if you detect activity from an *active* client.  Monitoring client activity can be accomplished using a Selector object.  Read more about the API here:
[http://java.sun.com/javase/6/docs/api/java/nio/channels/Selector.html](http://java.sun.com/javase/6/docs/api/java/nio/channels/Selector.html)

In summary, consider implementing the following classes to perform their respective tasks:
[LIST]
[*]ServerListener (thread used by the server)
[*]ClientHandler (thread used by the server)
[*]ClientReceiver (thread used by the client)
[*]ClientSender (thread used by the client)
[/LIST]

Initialize these object with the constructs (ie socket, container, etc) that each requires.  You should not need to have anything declared 'static', except maybe the handshake string.

P.S.  In some designs, a separate ClientHandler is created for each client that connects to the server, thus obviating the need to maintain a list of clients.  You may want to govern how many clients may connect; if too many connect, your system's performance could be degraded and/or possibly "crash".

---

### Post by kahumba on 2010-02-07
Well I thought I'll write the simplest thing I can figure out and hence didn't implement the quit application mechanism hence sockets might not be closed properly when you force the app to quit hence you might have problems connecting next time you start the app.
Client.java
```

package chat;

import java.net.ServerSocket;
import java.net.Socket;

public class Client implements Runnable {
    private int listenPort;
    private String name;

    public Client(int listenPort, String name) {
        this.listenPort = listenPort;
        this.name = name;
        new Thread(this).start();
    }

    public static final void main(String[] args) {
        new Server();
        Client c1 = new Client(Server.PORT+1, "Brian");
        Client c2 = new Client(Server.PORT+2, "James");

        Server.login(c1.getAddress());
        Server.login(c2.getAddress());

        Client chosen = c1;

        //say let c1 send a message to somebody currently registered on the Server
        for(Address target : Server.getClients()) {
            //make sure not talking to yourself
            if(target.getPort() != chosen.getAddress().getPort() ||
                !chosen.getAddress().getHost().equals(target.getHost())) {
                
                new MessageWriter(target, "Hello, I am " + chosen.getName() +
                    " at address " + chosen.getAddress() + "\n How are you?");
                
                break;
            }
        }

        
    }

    public void run() {
        try {
            ServerSocket serSocket = new ServerSocket(listenPort);

            while(true) {
                Socket socket = serSocket.accept();
                System.out.println("User at address " + getAddress() + " received a message:");
                new MessageReader(socket);
            }
        } catch(Exception exc) {
            exc.printStackTrace();
        }
    }

    public Address getAddress() {
        return new Address("localhost", listenPort);
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}

```MessageReader.java
```

package chat;

import java.io.*;
import java.net.Socket;

public class MessageReader implements Runnable {
    Socket socket;

    public MessageReader(Socket socket) {
        this.socket = socket;
        new Thread(this).start();
    }

    public void run() {
        try {
            byte[] bytes = new byte[1024];
            int read = 0;
            InputStream in = socket.getInputStream();

            while((read = in.read(bytes)) != -1) {
                System.out.print(new String(bytes, 0, read));
            }
            in.close();
            System.out.println("\nDone reading.\n");
        } catch(Exception exc) {
            exc.printStackTrace();
        }
    }
    
}


```MessageWriter.java
```

package chat;

import java.io.*;
import java.net.*;

public class MessageWriter implements Runnable {
    private Address target;
    private String message;

    public MessageWriter(Address target, String message) {
        this.target = target;
        this.message = message;
        new Thread(this).start();
    }

    @Override
    public void run() {
        try {
            InetAddress inet = InetAddress.getByName(target.getHost());
            Socket socket = new Socket(inet, target.getPort());
            OutputStream out = new BufferedOutputStream(socket.getOutputStream());
            out.write(message.getBytes());
            out.close();
        } catch(Exception exc) {
            exc.printStackTrace();
        }
    }
}

```Address.java
```

package chat;

public class Address {
    String host;
    int port;

    public Address(String host, int port) {
        this.host = host;
        this.port = port;
    }

    public String getHost() {
        return host;
    }

    public void setHost(String host) {
        this.host = host;
    }

    public int getPort() {
        return port;
    }

    public void setPort(int port) {
        this.port = port;
    }

    @Override
    public String toString() {
        return "[" + host + ": " + port + "]";
    }
}

```Server.java
```

package chat;

import java.util.Vector;

public class Server {
    public static final int PORT = 8000;
    private static Vector<Address> clients = new Vector<Address>();

    public static void login(Address address) {
        clients.add(address);
    }

    public static Vector<Address> getClients() {
        return clients;
    }
}

```

---

### Post by kahumba on 2010-02-07
Forgot to append sample output:

> 
User at address [localhost: 8002] received a message:
Hello, I am Brian at address [localhost: 8001]
 How are you?
Done reading.


---

### Post by dwhitney67 on 2010-02-07
Kahumba,

Seems like a P2P (Peer to Peer) design approach, where the server merely maintains a list of which clients exist.  A client can connect directly to another peer client, without any data traffic going through the server.  Is this correct?

If my assumption is correct, then perhaps this is the approach the OP should consider.  This would more closely model the typical client-chat applications (ie pidgin).

---

### Post by kahumba on 2010-02-07
Yes, a very rough and simple example without authentication, etc etc, just for the OP to have a basic working example.

---

