---
title: "Mono UDP Sockets broadcast."
date: 2007-10-25
forum: Programming Talk
---

### Post by mgazb on 2007-10-25
I have a problem using UDP broadcast
I have threes Feisty systems running a mono/C# socket server that broadcasts using 
```

IPEndPoint(IPAddress.Broadcast, port no)

```
Two of these have the 2.6.20-16 kernel and they throw a 
```

System.Net.Sockets.SocketException no 10051

```
when I call Send.

The third of system has the 2.6.20-15 kernel and operates correctly.

Does anybody know if there was some subtle change between these kernels? 
Alternatively is there a setting that I need to add to use broadcast sockets?

---

### Post by mgazb on 2007-10-25
I explicitly set the broadcast address.

255.255.255.255 doesn't work on the -16 kernel.

192.168.255.255 works on both -16 and -15 kernels.

---

