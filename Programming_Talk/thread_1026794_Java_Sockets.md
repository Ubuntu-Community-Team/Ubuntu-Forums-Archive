---
title: "Java Sockets"
date: 2008-12-31
forum: Programming Talk
---

### Post by coolkid5 on 2008-12-31
Hello, I've been trying to learn java network programming using a [tutorial]("http://java.sun.com/docs/books/tutorial/networking/sockets/readingWriting.html").

I tried copying and pasting the code from the tutorial into eclipse and changing the parameter in the construction of the socket from "taranis" to InetAddress.getLocalHost()
Here is the code:

```
import java.io.*;
import java.net.*;

public class EchoClient {
    public static void main(String[] args) throws IOException {

        Socket echoSocket = null;
        PrintWriter out = null;
        BufferedReader in = null;

        try {
            echoSocket = new Socket(InetAddress.getLocalHost(), 7);
            out = new PrintWriter(echoSocket.getOutputStream(), true);
            in = new BufferedReader(new InputStreamReader(
                                        echoSocket.getInputStream()));
        } catch (UnknownHostException e) {
            e.printStackTrace();
            System.exit(1);
        } catch (IOException e) {
            e.printStackTrace();
            System.exit(1);
        }

	BufferedReader stdIn = new BufferedReader(
                                   new InputStreamReader(System.in));
	String userInput;

	while ((userInput = stdIn.readLine()) != null) {
	    out.println(userInput);
	    System.out.println("echo: " + in.readLine());
	}

	out.close();
	in.close();
	stdIn.close();
	echoSocket.close();
    }
}

```

When I try to run it, it returns:
> java.net.ConnectException: Connection refused
	at java.net.PlainSocketImpl.socketConnect(Native Method)
	at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:310)
	at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:176)
	at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:163)
	at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:381)
	at java.net.Socket.connect(Socket.java:537)
	at java.net.Socket.connect(Socket.java:487)
	at java.net.Socket.<init>(Socket.java:384)
	at java.net.Socket.<init>(Socket.java:227)
	at EchoClient.main(EchoClient.java:13)

I'm not sure what the problem is though...  Help would be appreciated :)

---

### Post by hellz99 on 2008-12-31
Your problem is on this line:
echoSocket = new Socket(InetAddress.getLocalHost(), 7);

You can actually change InetAddress.getLocalHost() to "localhost" so it's:
echoSocket = new Socket("localhost", 7);

The port you're using is port 7.  First off, this probably isn't the best port to use.  Some linux systems lock out ports under 1024.  Also, assuming port 7 is good on your system, do you have a program listening on 7?  If you don't thats your problem. 

Open a console and type: netstat -l
If you don't see a program listening on 7, then that's why your client isn't connecting and throwing an exception.

---

### Post by coolkid5 on 2008-12-31
I used port 7 because the tutorial says:
> The example program implements a client, EchoClient, that connects to the Echo server. The Echo server simply receives data from its client and echoes it back. The Echo server is a well-known service that clients can rendezvous with on port 7. 

Do I have to unblock port 7 or is there another port I can use to test?

---

### Post by hellz99 on 2008-12-31
Do you get connection refused if you open a console and type:
telnet localhost 7

If so, then I'd say the echo server isnt running.  Again, you can try "netstat -l" to see if anything is listening on that port.

I have code for a echo server at work, but not there.  I did a quick google, try this out.  [http://www.cs.princeton.edu/introcs/84network/EchoServer.java.html](http://www.cs.princeton.edu/introcs/84network/EchoServer.java.html)

Just make sure the port in both the client and the server are the same, and maybe stick with something higher than 1024.  Run the server first, and then the client.

---

