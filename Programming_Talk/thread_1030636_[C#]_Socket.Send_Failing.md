---
title: "[C#] Socket.Send Failing?"
date: 2009-01-04
forum: Programming Talk
---

### Post by efexD on 2009-01-04
Well, after trying to connect to a basic server, I get nothing. No messages. Nothing. It seems like it just hangs. Does this have to do with it being on linux or am i doing something wrong?

```

using System;
using System.Net;
using System.Net.Sockets;
using System.Text;

class Program
{
	public static void Main()
	{
		IPAddress serverIp = IPAddress.Parse("24.81.233.184");
		IPEndPoint serverPort = new IPEndPoint(serverIp, 4837);
		Socket sock = new Socket(AddressFamily.InterNetwork, SocketType.Stream, ProtocolType.Tcp);
		try
		{
			sock.Connect(serverPort);
			Console.WriteLine("Connected to server.");
		}
		catch (SocketException e)
		{
			Console.WriteLine("Couldn't connect to server!");
			Console.WriteLine(e.ToString());
			sock.Close();
			return;
		}
	}
}


```

---

### Post by dwhitney67 on 2009-01-04
The code you posted works fine when I tested it against a server running on my local system and on a server running on a remote system.  The only thing I had to change was the IP address and the port number.

You may want to verify that your server is set up correctly to accept connections.

P.S.  I compiled and ran your code in the following manner:
```

gmcs client.cs
mono client.exe

```

P.S.S.  The server I tested with is written in C++.

---

### Post by efexD on 2009-01-04
Well if it didn't connect shouldn't the catch tell me? It's not showing anything.

---

### Post by directhex on 2009-01-04
Socket.Send has no timeout (stupid, I know)

Try [http://channel9.msdn.com/forums/TechOff/41602-TcpClient-or-Socket-Connect-timeout/?CommentID=212796](http://channel9.msdn.com/forums/TechOff/41602-TcpClient-or-Socket-Connect-timeout/?CommentID=212796) for a timeout-enabled code

---

### Post by efexD on 2009-01-04
Oh okay, there we go, thanks guys :)

---

