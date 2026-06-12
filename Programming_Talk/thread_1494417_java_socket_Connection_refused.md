---
title: "java socket Connection refused"
date: 2010-05-26
forum: Programming Talk
---

### Post by pavel989 on 2010-05-26
```
java.net.ConnectException: Connection refused
at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:310)
	at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:176)
	at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:163)
	at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:384)
	at java.net.Socket.connect(Socket.java:546)
	at java.net.Socket.connect(Socket.java:495)
	at java.net.Socket.<init>(Socket.java:392)
	at java.net.Socket.<init>(Socket.java:206)
	at client.Requester.<init>(Requester.java:12)
	at client.Requester.main(Requester.java:80)
```

i keep getting that at this line:
requestSocket = new Socket("127.0.0.1", 2004);

i surrounded it with a try/catch. and i allowed 2004 in ufw.
i get the error regardless or not if i have a server running on that port. itd be on the same box.

i cannot figured whats wrong. Can anyone please help me? ive been stuck on this for days

---

### Post by dwhitney67 on 2010-05-26
Regardless of the programming language being used, a connection refused is indicative that nobody (ie a server) is listening on the port that you specified.

I would recommend that you first check that there are no firewalls enabled on your system, and if that is not the issue, then recheck your server to verify it is indeed listening on the port.

You can use the command "netstat -at" to verify which TCP port(s) are being actively used on your system.

---

### Post by pavel989 on 2010-05-27
```
pavel@pavel-netbook:~/scripts$ netstat -a | grep 2004
tcp6       0      0 [::]:2004               [::]:*                  LISTEN     
pavel@pavel-netbook:~/scripts$ 

```

that means that there is a server there right? (i ran the command  while the server java app is running)

---

### Post by shadylookin on 2010-05-27
can you try telneting into your server? 

telnet 127.0.0.1 2004

---

### Post by pavel989 on 2010-05-27
```
pavel@pavel-netbook:~/scripts$ telnet 127.0.0.1 2004
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.

```

i guess that means its working? idk much about telnet

---

### Post by shadylookin on 2010-05-27
> **pavel989 said:**
> ```
pavel@pavel-netbook:~/scripts$ telnet 127.0.0.1 2004
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.

```

i guess that means its working? idk much about telnet

Yep that means it establishes a connection. It rules out a firewall issue, but doesn't do much to help the situation. 

What version of java and javac are you running? If you're using the GCJ version then try open-jdk and if you're using openjdk try the sun one.

---

### Post by Some Penguin on 2010-05-27
That String parameter is supposed to be a host name.  "127.0.0.1" isn't one.  If you want to specify by IPv4 address, try using one of the constructors that takes an InetAddress, because that's what they're for.

---

### Post by dwhitney67 on 2010-05-27
> **Some Penguin said:**
> That String parameter is supposed to be a host name.  "127.0.0.1" isn't one.  If you want to specify by IPv4 address, try using one of the constructors that takes an InetAddress, because that's what they're for.

Actually, this is not true.  "127.0.0.1" is universally known to represent the localhost.  Additionally, the Java Socket API indicates that what the OP is attempting is legal; read more here: [http://java.sun.com/javase/6/docs/api/java/net/Socket.html#Socket(java.lang.String,%20int](http://java.sun.com/javase/6/docs/api/java/net/Socket.html#Socket(java.lang.String,%20int))

The only issue I see is that the OP's server appears to be setup for IPv6 communications, whereas his client is using an IPv4 setup.

When I run a server on my system that is using an IPv4 socket, the 'netstat' output appears as:
```

$ netstat -at | grep 9000
tcp        0      0 *:9000                  *:*                     LISTEN

```
Note the difference in the output of the first column compared to what the OP posted.  I am not at all familiar with IPv6, but I would like to know how 'telnet' handled it.


P.S.  Here's a simple client app that I used to test with my C++-written server:
```

import java.net.*;
import java.io.*;


public class ClientSocket
{
   public static void main(String[] args)
   {
      try
      {
         String addr = "127.0.0.1";
         int    port = 9000;
         Socket sock = new Socket(addr, port);

         if (sock != null)
         {
            OutputStreamWriter os = new OutputStreamWriter(sock.getOutputStream());
            InputStreamReader  is = new InputStreamReader(sock.getInputStream());
            BufferedReader     br = new BufferedReader(is);

            String msg = "Hello Server\n";
            os.write(msg, 0, msg.length());
            os.flush();

            String reply = br.readLine();
            System.out.println(reply);

            sock.close();
         }
      }
      catch (IOException e)
      {
         System.out.println(e.toString());
      }
   }
}

```

---

### Post by pavel989 on 2010-05-27
well whether i do 

Socket("localhost", 2004);
Socket(InetAddress.getLocalHost(), 2004);

or
InetSocketAddress addr = new InetSocketAddress(2004);
requestSocket = new Socket(addr.getAddress(), 2004);

i get all the same error

---

### Post by ja660k on 2010-05-27
is your server running.
is your server listening for connections on port 2004?

you will always be able to telnet 127.0.0.1.. because that's you.
the problem is not the firewall because 127.0.0.1 is you.

there must be something in your server code,
i did socket programming in java a while ago... but i still remember a bit.
try pastebin your code for both client and server

---

### Post by pavel989 on 2010-05-27
[http://pastebin.com/6tH3BzrJ](http://pastebin.com/6tH3BzrJ)

---

### Post by dwhitney67 on 2010-05-27
> **ja660k said:**
> 
you will always be able to telnet 127.0.0.1.. because that's you.
the problem is not the firewall because 127.0.0.1 is you.


He performed the telnet correctly; he specified the port number.  Without the port number, the default port is used... and on many systems, nobody is listening on it.

As you pointed out, and which has also been stated earlier, the OP needs to go through each item in this list:

1.  Is the server operating properly?
2.  Is the server using IPv6 or IPv4?  (The client looks like it is using IPv4).
3.  Repeat the telnet exercise; this time with "telnet -4 127.0.0.1 2004"
4.  Then again with "telnet -6 127.0.0.1 2004".

---

### Post by pavel989 on 2010-05-28
well the server didnt give me any errors, so i assume its running correctly, and im almost positive this is all ipv4.

ill post the telnet in a few hrs (sorry for the delay)

---

### Post by audiofreq on 2010-05-29
I've got the same problem.

2 machines

Server on A
B cannot connect

Server on B
A can connect

Only difference is Machine A has been updated to 10.04 and B is the previous version.

When server running on A:
tcp6       0      0 [::]:4567               [::]:*                  LISTEN     

When server running on B:
tcp6       0      0 [::]:4567               [::]:*                  LISTEN     

No firewall running.  :confused:

---

### Post by dwhitney67 on 2010-05-29
> **pavel989 said:**
> [http://pastebin.com/6tH3BzrJ](http://pastebin.com/6tH3BzrJ)
EDIT: The statements below are incorrect; the binding of the socket does take place when the ServerSocket is instantiated.
--------------------------------------------------------
[COLOR="White"]Sorry for the delay in my response to your code.

Question... when were you planning to bind the 'providerSocket' to an address?

All joking aside, a Server must perform the following steps when setting up a socket?

1.  Open socket
2.  Bind the socket
3.  Listen on the socket
4.  Accept connections.

You can read more about Java' ServerSocket here:
[http://java.sun.com/javase/6/docs/api/java/net/ServerSocket.html](http://java.sun.com/javase/6/docs/api/java/net/ServerSocket.html)

In your code...
Step 1 above is covered when you instantiated the ServerSocket.

Step 2 above is _missing_.

Steps 3 and 4 above are covered by the accept() call.[/COLOR]


P.S.  In the future, please do not use PasteBin to post your code.  Post here on the forums, preferably without the line numbers.

---

### Post by dwhitney67 on 2010-05-29
> **audiofreq said:**
> I've got the same problem.


Without seeing your code, all I can say is maybe you do, or maybe you don't.

Try running these two sample apps:

Server.java:
```

import java.net.*;
import java.io.*;


public class Server
{
   private ServerSocket mySocket;
   private boolean      myRunFlag = true;

   public Server(String host, int port)
   {
      try
      {
         mySocket = new ServerSocket(port, 5, InetAddress.getByName(host));
         mySocket.setReuseAddress(true);
      }
      catch (IOException e)
      {
         System.out.println(e.toString());
      }
   }

   public void run()
   {
      myRunFlag = true;

      while (myRunFlag)
      {
         try
         {
            System.out.println("Waiting for client to connect...");
            Socket clientSocket = mySocket.accept();

            if (clientSocket != null)
            {
               System.out.println("Client to connected...\n");
               handleClient(clientSocket);
            }
         }
         catch (IOException e)
         {
            System.out.println(e.toString());
         }
      }
   }

   public void stop()
   {
      myRunFlag = false;
   }

   private void handleClient(Socket socket)
   {
      try
      {
         OutputStreamWriter os = new OutputStreamWriter(socket.getOutputStream());
         InputStreamReader  is = new InputStreamReader(socket.getInputStream());
         BufferedReader     br = new BufferedReader(is);

         while (true)
         {
            String msg = br.readLine();

            if ((msg == null) || msg.equals("quit"))
               break;

            System.out.println("Received: '" + msg + "'");

            os.write("Send me your thoughts, or 'quit' to end...\n");
            os.flush();
         }

         socket.close();
      }
      catch (IOException e)
      {
         System.out.println(e.toString());
      }
   }

   public static void main(String[] args)
   {
      Server server = new Server("127.0.0.1", 9000);

      server.run();
   }
}

```

Client.java:
```

import java.net.*;
import java.io.*;


public class Client
{
   public static void main(String[] args)
   {
      try
      {
         String addr = "127.0.0.1";
         int    port = 9000;
         Socket sock = new Socket(addr, port);

         if (sock != null)
         {
            OutputStreamWriter os = new OutputStreamWriter(sock.getOutputStream());
            InputStreamReader  is = new InputStreamReader(sock.getInputStream());
            BufferedReader     br = new BufferedReader(is);

            String msg = "Hello Server\n";
            os.write(msg, 0, msg.length());
            os.flush();

            String reply = br.readLine();
            System.out.println(reply);

            sock.close();
         }
      }
      catch (IOException e)
      {
         System.out.println(e.toString());
      }
   }
}

```

---

### Post by gmargo on 2010-05-29
> **dwhitney67 said:**
> 

2.  Bind the socket

Step 2 above is _missing_.



Are you sure?  I don't see that his bind step is missing - he called ServerSocket(port, ...) which does the bind. (I don't claim the rest of it works, but that part looks like it's binding.)

BTW, *_thank you_* for providing working code examples!

---

### Post by dwhitney67 on 2010-05-29
> **gmargo said:**
> Are you sure?  I don't see that his bind step is missing - he called ServerSocket(port, ...) which does the bind. (I don't claim the rest of it works, but that part looks like it's binding.)

Yeah, the binding is taking place, presumably to "ANY_ADDR".  I guess I'm the one who needs to read the API a bit more carefully.

---

### Post by audiofreq on 2010-05-29
Sorry I had to rush to test what you sent.

On my "Machine A" which can open a socket and ONLY accepts connections from the same machine, your code worked.  But like I said local connections work here anyway.

If I keep your server file open and try telnet from "Machine B" i get connection refused.


On "Machine B" which accepts connections both locally and from "Machine A", your code works locally.  But then when I try telnet into this port from "Machine A" nothing.  So it seems like a step backwards for what my problem is.  So maybe we don't have the same problem.

But i really rushed through that.  I'll have a proper look tomorrow when I have a bit of time.

---

### Post by dwhitney67 on 2010-05-29
I presume you are not using the two-arg constructor for ServerSocket; this is the one that fingered earlier, but was wrong in my assumption of its use.

When the two-arg constructor is called, it binds the given port to any/all interfaces on the system.  If you are using the code I posted earlier, which binds specifically to "127.0.0.1", then there is no way for a client application to reach that socket from an external machine.

Replace the ServerSocket constructor to use only the first two parameters, and you should be good.

---

### Post by pavel989 on 2010-05-30
heres the thing tho, im running this from the same machine. and the 2 telnet commands bring to a blank line after telling me that ^] is the escape sequence or something like that

---

### Post by audiofreq on 2010-05-30
> **dwhitney67 said:**
> I presume you are not using the two-arg constructor for ServerSocket; this is the one that fingered earlier, but was wrong in my assumption of its use.

When the two-arg constructor is called, it binds the given port to any/all interfaces on the system.  If you are using the code I posted earlier, which binds specifically to "127.0.0.1", then there is no way for a client application to reach that socket from an external machine.

Replace the ServerSocket constructor to use only the first two parameters, and you should be good.


Yeah you were right but I still experience the same problem.

Exact same code (removed third parameter on both machines).

A can connect to B
B cannot connect to A...

I think the problem is not with Java but with some sort of configuration deeper down.

Have you checked your java.policy file?  I'm using the exact same file on both machines so i know it's not that.

---

### Post by dwhitney67 on 2010-05-30
> **pavel989 said:**
> heres the thing tho, im running this from the same machine. and the 2 telnet commands bring to a blank line after telling me that ^] is the escape sequence or something like that
telnet is a nice tool to determine if you can connect via an open port on a system, whether remote or local.

If you are successful in connecting, don't expect telnet to be able to interpret the UTF serialized object (String) that you are sending.  Just be grateful that it connected, for this tells you that the server accepting the connection.

I have two systems within my local area network which are able to communicate with each other; there are no firewalls enabled.  Unless your systems are setup differently, I cannot comprehend why you would have trouble having one system sends messages to another.

---

### Post by pavel989 on 2010-05-30
> **audiofreq said:**
> Yeah you were right but I still experience the same problem.

Exact same code (removed third parameter on both machines).

A can connect to B
B cannot connect to A...

I think the problem is not with Java but with some sort of configuration deeper down.

Have you checked your java.policy file?  I'm using the exact same file on both machines so i know it's not that.



java.policy?


oh btw, i should probably specify that i am debugging this in eclipse. also, i tried changing the port that the client tries to connect to and still a no go

---

### Post by pavel989 on 2010-06-01
i found this forum post: [http://www.daniweb.com/forums/post667566.html#post667566](http://www.daniweb.com/forums/post667566.html#post667566)

apparently, adding a server socket to the same port, before the socket, made it work. dunno why or how, but i wont complain.

thanks for all the help!

---

### Post by dwhitney67 on 2010-06-01
> **pavel989 said:**
> i found this forum post: [http://www.daniweb.com/forums/post667566.html#post667566](http://www.daniweb.com/forums/post667566.html#post667566)

apparently, adding a server socket to the same port, before the socket, made it work. dunno why or how, but i wont complain.

thanks for all the help!

You already had a ServerSocket created (well, at least per what I saw in the code you posted earlier).  So I don't have a clue as to what you are referring to, unless of course it is the following, which is then "masking" the issue you were having:
```

// Create a listener socket for the server
serverSocket = new ServerSocket(4000);

echoSocket = new Socket(localhost, 4000);
```

The code above creates TWO sockets, with the second being specifically bound to the localhost interface.  The other is supposedly bound to all interfaces (of your system).

For most purposes, creating these two sockets is unnecessary, but perhaps the fellow that wrote that code had a specific requirement to output only to the localhost, and not to an outside source.

You should not see this as a solution to the issue you were having.

---

### Post by pavel989 on 2010-06-01
> **dwhitney67 said:**
> You already had a ServerSocket created (well, at least per what I saw in the code you posted earlier).  So I don't have a clue as to what you are referring to, unless of course it is the following, which is then "masking" the issue you were having:
```

// Create a listener socket for the server
serverSocket = new ServerSocket(4000);

echoSocket = new Socket(localhost, 4000);
```

The code above creates TWO sockets, with the second being specifically bound to the localhost interface.  The other is supposedly bound to all interfaces (of your system).

For most purposes, creating these two sockets is unnecessary, but perhaps the fellow that wrote that code had a specific requirement to output only to the localhost, and not to an outside source.

You should not see this as a solution to the issue you were having.


the example you gave is what i did. 

however i guess i didnt specify, but the server app and client app are 2 seperate applications. they are not run from the same app

---

### Post by dwhitney67 on 2010-06-01
The server uses a ServerSocket, and the client a 'regular' Socket.  Yes, these are typically done in separate applications.

The server binds, listens, and accepts.

The client connects.

Then the conversation begins between the two.


P.S.  As I attempted to discuss earlier, the server can bind and listen during the instantiation of the ServerSocket.  Something like:
```

socket = new ServerSocket(2004);

```

---

