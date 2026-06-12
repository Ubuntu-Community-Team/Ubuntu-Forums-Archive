---
title: "pass string from python server to java client"
date: 2010-11-01
forum: Programming Talk
---

### Post by Shpongle on 2010-11-01
Hi all , basically Im developing my final year project for college that consists of a python server an oracle db backend and an android client.

I have started with the server and coded a small python client to test it and for now it works as expected. Now I have started on the actual client and I want to receive a string upon confirmation on the client that it is connected to the server. 

it works fine going python to python , using 

conn.send('Connected to server') 

where conn refers to the connection  . 
i.e.  conn,addr  =s.accept() #establish a connection with the client

on the python test client I receive this message as soon as the connection is accepted by the server using print s.recv(1024). With the java one however I get nothing and the program just waits 

snippet of the java code
```
        	host = InetAddress.getByName("127.0.0.1"); 
        	link = new Socket(host,port);
        	in = new BufferedReader(new InputStreamReader(link.getInputStream()));
        	
        	//display connection confirmation
        	
        	String message = in.readLine();
        	System.out.println (message);


```

If I can get it in java it will work in android as they use the same socket primitives.

any ideas ? , thanks

---

### Post by juancarlospaco on 2010-11-01
Use SQLite(?)

Have you tried writing the string into a file?

---

### Post by Shpongle on 2010-11-01
the database will store images so I need the binary large object datatype (blob) that oracle offers and Im more familiar with it for the project. I haven't tried to write a file yet as I don't want to incur unnecessary over head on the client side as it will be a mobile application

---

### Post by dwhitney67 on 2010-11-01
> **Shpongle said:**
> 
any ideas ? , thanks

EDIT:  Since you are expecting to receive using readLine(), I assume that the server is sending a newline-terminated string.  Can you confirm this?

--------------------------

I only tinker with Java once in a blue moon, however when I attempted to duplicate the issue you described, I did not have any issues.

Here's the Java code I played with:
```

import java.lang.*;
import java.io.*;
import java.net.*;


public class Client
{
   private Socket socket = null;
   private BufferedReader reader = null;
   private BufferedWriter writer = null;

   public Client(InetAddress address, int port) throws IOException
   {
      socket = new Socket(address, port);
      reader = new BufferedReader(new InputStreamReader(socket.getInputStream()));
      writer = new BufferedWriter(new OutputStreamWriter(socket.getOutputStream()));
   }

   public void send(String msg) throws IOException
   {
      writer.write(msg, 0, msg.length());
      writer.flush();
   }

   public String recv() throws IOException
   {
      return reader.readLine();
   }

   public static void main(String[] args)
   {
      try {
         InetAddress host = InetAddress.getByName("127.0.0.1");
         Client client = new Client(host, 9000);

         client.send("Hello server.\n");
         String response = client.recv();
         System.out.println("Client received: " + response);
      }
      catch (IOException e) {
         System.out.println("Caught Exception: " + e.toString());
      }
   }
}

```
For my server, I used one written in C++.

P.S.  I just tried with a Python server; same result... success.

---

### Post by Shpongle on 2010-11-01
hey dwhitney , thanks for your time , 

this is the line that the server sends upon accepting a client connection 

 self.conn.send('Connected to server')

the client doesn't send a string , it sends an image but thats after it receives the connected to server message from the server.

---

### Post by Shpongle on 2010-11-01
SUCCESS dwhitney your a hero  , thanks you really helped me out , It was the \n I was missing . Thank you so much I really appreciate it.

---

