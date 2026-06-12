---
title: "[C++] Handling clients connected to a server"
date: 2009-01-24
forum: Programming Talk
---

### Post by thelamb on 2009-01-24
Hello all,

I am coding a client/server in C++ - everything is working so far but I was wondering if my approach is correct or if there is a better way of handling this:

In this version only 64 clients need to be able to connect, in a different application I will write in the future there really isn't a set limit, so please comment if you think my approach will cause serious problems when the number of clients grows.

The application consists of a few classes:
CListenServer - Listen for new connections and accept them.
CClient - contains functions like 'receive' and 'send'.

CListenServer uses select() to check if a new connection is available and accepts it if there is, also it checks all the connected client sockets to see if there is any data waiting for recv().

In the main code I keep a map that contains the socket number as key and a pointer to the client object as value (map<int, CClient*>).

So when CListenServer returns a list of sockets that have data waiting, I can find the correct client object by using map.find(socket) and call the recv function on this CClient.

In the CClient I store the following info of the client:
Socket
IP
GUID (the clients are connected to a game server aswell, the GUID is a unique identifier for each client that is written in the game server's logfile when a client connects - I read this logfile to get the GUID and IP).

So after reading the gameserver's log I have a clientIP and a GUID, I want to assign the GUID to the client object that is connected with 'clientIP'.
I did this with another map(map<string, CClient*>) the string here is the client IP, so I can find the client with map.find(clientIP) and call 'setGUID(GUID)' on this object.

There is also a map with the slot number and the client object, I also get the slot number from the game server's log.

So that is 3 maps already, and later I might need more(like a map between guid and object). Is there a better way to handle this? I read something about hash tables, but I wonder if it is a big improvement when there are just 64 clients(most of the time less anyway).

I hope someone can comment on this and possibly suggest a better way to deal with finding the correct object. Let me know if you need more information.

Chris

---

### Post by thelamb on 2009-01-26
*BUMP*

Anyone has any suggestions for me to look into.

---

### Post by Zugzwang on 2009-01-27
Looks reasonable. You could also use an in-RAM database and store your data there (yes, you can store pointers by converting back and forth to size_t), if that's not overkill.

---

