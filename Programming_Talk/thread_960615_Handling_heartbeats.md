---
title: "Handling heartbeats"
date: 2008-10-27
forum: Programming Talk
---

### Post by thelamb on 2008-10-27
Hello all,

I have a question about a project I am doing at the moment, I have a working version already but I would like some feedback on the method I used.

It is a master server that communicates with clients over TCP, the number of clients is unspecified(read: there can be many). Every client has a unique socket number and 'lives' in a CCLient object.
I keep track of all the clients that are connected with a map:
```
map<int, CClient*> CClientMap;
```
Where int is the socket number.

Now I needed a way to make sure that a client is still connected, I cannot rely on the TCP recv() returning <= 0 because I use select() to determine if a socket is ready to be read, I know that select() will flag the socket as readable if the client has disconnected or if there is an error on the socket, but it wont if the client blocks traffic to the MS with his firewall after the connection is already accepted.

When a client connects to the MS and it is accepted, the MS will send the socket number of the client to the client.
Next the client sends a heartbeat every 3 minutes via UDP, the hearbeat looks like: 0 2 <-- where 0 lets the MS know that this is a heartbeat and the 2 is the TCP socket number of the client.

The MS keeps a list of heartbeats it receives during 10 minutes after 10 minutes it compares the socket numbers in this list with the mapCClient list I declared above as follows:
```

for( i; i < CClientmap.size(); ++i )
{
    j = heartBeatVec<int>::iterator;
        it = find( heartbeatfirst, heartbeatend, i->first )
        if( it == heartBeatVec.end() )
            KillClient();
}

```

Please don't look at the syntax, this is just for ilustration purposes.
In words:
I loop through the list of all currently connected sockets, I search for each socket in the list that contains all the sockets that I received a heartbeat from, if it didnt find anything, no heartbeat was received in 10 minutes so the client is killed.

Does this method make sense atall or is there a better/standard way to handle heartbeats?

Thanks in advance for any comments.

---

### Post by dribeas on 2008-10-27
> **thelamb said:**
> I keep track of all the clients that are connected with a map:
```
map<int, CClient*> CClientMap;
```
Where int is the socket number.
[...]
The MS keeps a list of heartbeats it receives during 10 minutes after 10 minutes it compares the socket numbers in this list with the mapCClient list I declared above as follows:
```

for( i; i < CClientmap.size(); ++i )
{
    j = heartBeatVec<int>::iterator;
        it = find( heartbeatfirst, heartbeatend, i->first )
        if( it == heartBeatVec.end() )
            KillClient();
}

```


I usually tend to group client data together, and avoid having to search through different data structures. This also keeps the client state data grouped (whether it has timedout is usually part of what I consider the state of the object). 

Periodically you can check for timeouts and remove the inactive clients from the structure.

---

