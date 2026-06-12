---
title: "Ideas for safety while socket programming"
date: 2010-12-23
forum: Programming Talk
---

### Post by skytreader on 2010-12-23
I've been doing some Socket programming lately in Java. I noticed that my CPU usage peaks when I run server programs (I don't have another computer to test my stuff on; I point the IP addresses to 127.0.0.1). Things got so heated up one session that my computer shut down on its own will (to prevent hardware damage, I believe). Any ideas on how I may program "safely", in the future?

(Right now, whenever I run my Socket stuff, I'm thoroughly watching my System Monitor and close the program whenever things start to look critical.)

And oh, I'm on an AMD Turion 64 X2 Laptop. 2GB RAM, 1GB video card. I've been doing some chat-like programs with a GUI. I figure that as I do more complicated stuff, my CPU might just go kaplooey! . Any suggestion is appreciated. Thanks!

---

### Post by Queue29 on 2010-12-23
If you show me some code, I'll show you where you're doing it wrong. ServerSockets wait for and respond to interrupts. They consume 0 cpu cycles in the meantime.

---

### Post by skytreader on 2010-12-23
> **skytreader said:**
> I noticed that my CPU usage peaks when I run server programs...

Oops. That's some miswording on my part. My CPU usage peaks when a client connects to the server, not when I run it. Nonetheless, as I've been awakened to the possibility that this might be a problem on my Threads (I forgot to mention that my programs are Sockets+GUI+**Threads**) here's some code (command-line interface, for brevity).

What this code does is create some "chat board" on the server. That is, clients connect to a server and from there they can send messages. All their messages are displayed on the server creating some kind of chat board (the messages are not disseminated to every client connected, just displayed on the server).

The server:

```
import java.net.ServerSocket;
import java.net.Socket;
import java.io.*;

public class ThreadedServer{
	
	private static void startChat(){
		try{
			System.out.println(":::CHAT SERVER:::");
			ServerSocket server = new ServerSocket(16981);
			System.out.println("Waiting for someone to connect...");
			
			while(true){
				Socket client = server.accept();
				
				DataInputStream UsernameInputStream = new DataInputStream(client.getInputStream());
				
				while(UsernameInputStream.available() == 0){}
				
				byte[] uname = new byte[UsernameInputStream.available()];
				UsernameInputStream.read(uname);
				String username = new String(uname);
				Thread st = new ServerThread(client, username);
				st.start();
				System.out.println(username + " joined the chat.");
			}
		}
		catch(Exception e){
			e.printStackTrace();
		}
	}
	
	public static void main(String[] args){
		startChat();
	}
}

```

My extension of Thread:
```
import java.net.Socket;
import java.io.*;

public class ServerThread extends Thread{
	private DataInputStream dis;
	private Socket client;
	private String username;
	
	public ServerThread(Socket client, String username){
		try{
			this.client = client;
			this.username = username;
			dis = new DataInputStream(client.getInputStream());
		}
		catch(Exception e){
			e.printStackTrace();
		}
	}
	
	public void run(){
		try{
			while(true){
				while(dis.available() == 0){}
				
				byte[] msg = new byte[dis.available()];
				dis.read(msg);
				String message = new String(msg);
				
				if(message.equals("#out#")){
					client.close();
					dis.close();
					break;
				}
				
				System.out.println(username + ": " + message);
			}
			escape();
		}
		catch(Exception e){
			e.printStackTrace();
		}
	}
	
	private void escape(){
		System.out.println(username + " left the chat.");
		System.out.println("escaped.");
	}
}

```

And the client:
```
import java.net.Socket;
import java.io.*;

public class BoardChatClient{
	private static final String NICKNAME_PROMPT = "Please enter a conversation nickname: ";
	
	private static class Chat{
		private void chat(){
			try{
				System.out.println(":::CHAT CLIENT:::");
				System.out.print("Connecting...");
				Socket client = new Socket("127.0.0.1", 16981);
				System.out.println("Done.");
				BufferedReader br = new BufferedReader(new InputStreamReader(System.in));				
				DataOutputStream dos = new DataOutputStream(client.getOutputStream());
				
				System.out.print(NICKNAME_PROMPT);
				String username = br.readLine();
				
				while(usernames.contains(username) || username.equals("")){
					if(username.equals("")){
						System.out.println("Blank usernames are not allowed.");
					}
					else{
						System.out.println("That name is already taken.");
					}
					
					System.out.print(NICKNAME_PROMPT);
					username = br.readLine();
				}
				
				usernames.add(username);
				dos.write(username.getBytes());
						
				String message = "";
				
				do{
					System.out.print("you> ");
					message = br.readLine();
					dos.write(message.getBytes());
				} while(!message.equals("#out#"));
			}
			catch(Exception e){
				e.printStackTrace();
			}
		}
	}
	
	public static void main(String[] args){
		new Chat().chat();
	}
}

```

Some visualization of my CPU activity...

Server Starts:
```

                  |
                  |
                  |
                  |
   _/^\          /|   /\
__/    \___/\___/ |__/  \___/\_/\___

```
(Low activity on both processors)

Client connects```

                  |
                  |        /\
  /\         /\   |   /\  /  \
 /  \_  /\  /  \  |__/  \/    \   /\
/     \/  \/    \_|            \_/
                  |

```
(Approximately 50% on both CPUs)

Two clients connected```

    __  /--\    _/-|__/-\   _/\_/\
   /  \/    \  /   |     \_/      \_/
__/          \/    |
                   |
                   |
                   |

```
(Approximately 100% on both CPUs)

It's not very nice but I hope you get my point :D. I stop things when fluctuations get rarer on the almost 100% (that is, when the graph has a straight line on 100%).

---

### Post by dwhitney67 on 2010-12-23
Don't call the available() method like you have done here ANYWHERE in your code:
```

while(dis.available() == 0){}

```

This function will return 0 until there is data available to read.  Since it is safe to assume that your CPU can operate a lot faster than you can type and hit the carriage return key, your system is going to be wasting a lot of cycles.  This might explain why your system is being over-exercised.

Consider calling readUTF(); this will block until data has been received.
```

	public void run(){
		try{
			while(true){
				// while(dis.available() == 0){}
				
				// byte[] msg = new byte[dis.available()];
				//dis.read(msg);
				//String message = new String(msg);

                                String message = dis.readUTF();
				
				if(message.equals("#out#")){
					client.close();
					dis.close();
					break;
				}
				
				System.out.println(username + ": " + message);
			}
			escape();
		}
		catch(Exception e){
			e.printStackTrace();
		}
	}

```

P.S.  If the 'message' string is null, then that might indicate that the client has disconnected.  You probably should have something like:
```

if(message == null || message.equals("#out#")){
    client.close();
    dis.close();
    break;
}

```

---

### Post by skytreader on 2010-12-26
Thanks for the tip dwhitney67. It runs well (and safe) for my message transactions. However, it doesn't seem to hold up when I use readUTF() for the username transaction.

Code:

ThreadedServer accepts usernames

```
import java.net.ServerSocket;
import java.net.Socket;
import java.io.*;

public class ThreadedServer{
	
	private static void startChat(){
		try{
			System.out.println(":::CHAT SERVER:::");
			ServerSocket server = new ServerSocket(16981);
			System.out.println("Waiting for someone to connect...");
			
			while(true){
				Socket client = server.accept();
				
				DataInputStream UsernameInputStream = new DataInputStream(client.getInputStream());
				System.out.println("code is blocking...");
				String username = UsernameInputStream.readUTF();
				System.out.println("done blocking. Starting thread.");
				Thread st = new ServerThread(client, username);
				st.start();
				System.out.println(username + " joined the chat.");
			}
		}
		catch(Exception e){
			e.printStackTrace();
		}
	}
	
	public static void main(String[] args){
		startChat();
	}
}
```

BoardChatClient sends usernames:
```
import java.net.Socket;
import java.io.*;

public class BoardChatClient{
	private static final String NICKNAME_PROMPT = "Please enter a conversation nickname: ";
	
	private static class Chat{
		private void chat(){
			try{
				System.out.println(":::CHAT CLIENT:::");
				System.out.print("Connecting...");
				Socket client = new Socket("127.0.0.1", 16981);
				System.out.println("Done.");
				BufferedReader br = new BufferedReader(new InputStreamReader(System.in));				
				DataOutputStream dos = new DataOutputStream(client.getOutputStream());
				
				System.out.print(NICKNAME_PROMPT);
				String username = br.readLine();
				
				while(username.equals("")){
					System.out.print(NICKNAME_PROMPT);
					username = br.readLine();
				}
				System.out.println("Read username to be: " + username);
				dos.write(username.getBytes());
				System.out.println("wrote to dos: " + username);
				String message = "";
				
				do{
					System.out.print("you> ");
					message = br.readLine();
					dos.write(message.getBytes());
				} while(!message.equals("#out#"));
			}
			catch(Exception e){
				e.printStackTrace();
			}
		}
	}
	
	public static void main(String[] args){
		new Chat().chat();
	}
}
```

Not really concerned this time (as I will explain later) but I'll post it anyway. My extension of Thread:

```
import java.net.Socket;
import java.util.Vector;
import java.io.*;

public class ServerThread extends Thread{
	private DataInputStream dis;
	private Socket client;
	private String username;
	
	private final String NICKNAME_PROMPT = "Please enter a conversation nickname: ";
	
	public ServerThread(Socket client, String username){
		try{
			this.client = client;
			this.username = username;
			dis = new DataInputStream(client.getInputStream());
		}
		catch(Exception e){
			e.printStackTrace();
		}
	}
	
	public void run(){
		try{
			System.out.println("Thread running.");
			while(true){
				String message = dis.readUTF();
				System.out.println(username + ": " + message);
			}
		}
		catch(EOFException eofe){
		}
		catch(Exception e){
			e.printStackTrace();
		}
		finally{
			escape();
		}
	}
	
	private void escape(){
		try{
			client.close();
			dis.close();
			System.out.println(username + " left the chat.");
			System.out.println("escaped.");
		}
		catch(IOException ioe){
			ioe.printStackTrace();
		}
	}
}
```

When a client connects, the text "code is blocking..." appears. After I enter my username, nothing happens to server (and the thread doesn't even start) but the client displays

```
:::CHAT CLIENT:::
Connecting...Done.
Please enter a conversation nickname: uname
Read username to be: uname
wrote to dos: uname
you>
```

Not even the messages I enter in the you> prompt can get the server past the blocking code. However, when I end client, server throws an EOFException for readUTF().

Thanks for any help.

---

### Post by dwhitney67 on 2010-12-26
Sorry, but my tip may have lead you astray.  I don't program in Java often, thus I may have made a mistake to recommend the readUTF().  Upon going through the Java API, I found references to BufferReader, so I took a chance and went with that.  Here's what I got for the Server side:

Server:
```

import java.net.ServerSocket;
import java.net.Socket;
import java.io.*;

public class Server
{
   private ServerSocket myListener;

   public Server(int port) throws IOException
   {
      myListener = new ServerSocket(port);
   }

   public void startChat() throws IOException
   {
      while (true) {
         Socket client = myListener.accept();

         if (client != null)
         {
            Thread handler = new ClientHandler(client, this);
            handler.start();
         }
      }
   }

   public static void main(String[] args)
   {
      try {
         int    port   = 16981;
         Server server = new Server(port);

         server.startChat();
      }
      catch (IOException e) {
         e.printStackTrace();
      }
   }
}

```

And for the ClientHandler thread used above:
```

import java.net.Socket;
import java.io.*;


public class ClientHandler extends Thread
{
   private Socket myClient;
   private Server myServer;
   private String myUsername;

   public ClientHandler(Socket client, Server server)
   {
      myClient = client;
      myServer = server;   // this is in case the thread needs to reference it's parent thread.
   }

   public void run()
   {
      try {
         **BufferedReader br = new BufferedReader(new InputStreamReader(myClient.getInputStream()));**

         // get user name
         do {
            myUsername = br.readLine();
         } while (myUsername == null || myUsername.isEmpty());

         // get message(s) from user
         while (true) {
            String message = br.readLine();

            if (message == null)
              break;

            System.out.println(myUsername + ": " + message);
         }
      }
      catch (EOFException e) {
         // do nothing
      }
      catch (Exception e) {
         e.printStackTrace();
      }
      finally {
         try {
            myClient.close();
            System.out.println("User " + myUsername + " has left the chat room.");
         }
         catch (IOException e) {
         }
      }
   }
}

```

---

