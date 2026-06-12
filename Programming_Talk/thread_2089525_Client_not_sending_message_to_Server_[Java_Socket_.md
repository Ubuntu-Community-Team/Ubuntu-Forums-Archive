---
title: "Client not sending message to Server [Java Socket Programming]"
date: 2012-11-29
forum: Programming Talk
---

### Post by vikkyhacks on 2012-11-29
```

/* Server.java */
import java.net.*;
import java.util.*;
import java.io.*;

class Server
{

        public static void main(String[] args) throws Exception
        {
                ServerSocket server = new ServerSocket(6666);
                Socket conn = server.accept();
                BufferedReader in = new BufferedReader(new InputStreamReader(conn.getInputStream()));
                String a = in.readLine();
                System.out.println(a);
        }

}

```

and here is the ..
.
```

/* Client */
import java.net.*;
import java.io.*;

class Client
{

        public static void main(String[] args) throws Exception
        {
                Socket client = new Socket();
                client.connect(new InetSocketAddress("localhost",6666));
                BufferedWriter out = new BufferedWriter(new OutputStreamWriter(client.getOutputStream()));               
                out.write("Hey, this is client",0,3);
        }

}

```

After running i get 
```

/*  SERVER  */
meow@VikkyHacks:~/Arena/java$ javac Server.java && java Server
null

/*  CLIENT  */
meow@VikkyHacks:~/Arena/java$ javac Client.java && java Client

```

**I am expecting a message after the client connects saying, _"Hey, this is client"_**

---

### Post by Unterseeboot_234 on 2012-11-29
Using a Terminal that you cd into the project folder, you have designated current directory, javac SocketServer.java and when that compiles you run it (with the cd still designated)

java SocketServer

You do have a server running waiting for one line of input. Prove it by opening another Terminal

telnet localhost 6666
*(you get)*
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Howdy from from client // this is typed in

The Terminal window running SocketServer echos Howdy from... and exits. Because the server shut down telnet quits also.

So, it looks like class Client.java needs PrintStream. And make sure it is ^$ cd projectFolder and run in its own Terminal.

====================
// Socket programming with the streams has to be clear in your mind about which side is sending. So, to use your Server.java here is my SocClient.java

```

import java.io.IOException;
import java.io.PrintWriter;
import java.net.InetSocketAddress;
import java.net.Socket;

public class SocClient {

    public static void main(String[] args) {

        try {
            Socket socket = new Socket();
            socket.connect(new InetSocketAddress("localhost", 6666));
            PrintWriter out = new PrintWriter(socket.getOutputStream(), true);
            out.println("Howdy from client");
            socket.close();


        } catch (IOException e) {
            e.printStackTrace();
        }

    }
}

```

---

### Post by dwhitney67 on 2012-11-29
> **vikkyhacks said:**
> 
**I am expecting a message after the client connects saying, _"Hey, this is client"_**

That's a lofty expectation considering you are telling write() to only send 3 characters.

Perhaps you should place your string literal within a String object so that you can get the string's length.  After writing the string, you should flush() the buffered writer (actually, the OutputStreamWriter).

Something like this (for the Client):
```

                String msg = "Hey, this is client";
                out.write(msg, 0, msg.length());
                out.flush();

```

---

### Post by vikkyhacks on 2012-11-30
> **Unterseeboot_234 said:**
> You do have a server running waiting for one line of input.
```
 PrintWriter out = new PrintWriter(socket.getOutputStream(), true);          

```

Actually even I was using the same tutorial you just sent, But I don wish to use PrintWriter,
I wanna go easy with the class like

BufferedReader x BufferedWriter
InputStream    x OutputStream
DataInputStream x DataOutputStream


> **dwhitney67 said:**
> Perhaps you should place your string literal within a String object so that you can get the string's length.  After writing the string, you should flush()

Actually I did try placing using String Object but that din work and got messed up using 3 in the program, The part I din do was flush. I used your code and it works perfectly ...

---

