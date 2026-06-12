---
title: "Using NDesk.DBus in MonoDevelop"
date: 2009-11-21
forum: Programming Talk
---

### Post by Jordanwb on 2009-11-21
I'm trying out Dbus in MonoDevelope. I'm reading NDesk.Dbus's [documentation]("http://www.ndesk.org/DBus_Documentation") trying to figure out what I need to do.

This is my code:

```
using System;
using NDesk.DBus;

namespace BurnoutServer
{
	class MainClass
	{
		public static void Main(string[] args)
		{
			Connection connection = Connection.Open ("tcp:host=localhost,port=23453");
			
			BusG.Init (connection);
		}
	}
}
```

But I get this exception:

> 
Unhandled Exception: System.Net.Sockets.SocketException: Connection refused
  at System.Net.Sockets.Socket.Connect (System.Net.EndPoint remote_end) [0x00000] 
  at System.Net.Sockets.TcpClient.Connect (System.Net.IPEndPoint remote_end_point) [0x00000] 
  at System.Net.Sockets.TcpClient.Connect (System.Net.IPAddress[] ipAddresses, Int32 port) [0x00000] 

Is there a group my user needs to be a member of?

---

