---
title: "what is sockaddr_un"
date: 2010-10-18
forum: Programming Talk
---

### Post by jamesbon on 2010-10-18
I searched this term on net sockaddr_un I am trying my hands from beejs network programming guide.[http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html)
In this guide it is no where mentioned about struct sockaddr_un
where as I see in linux/un.h
following struct
```

struct sockaddr_un {
        sa_family_t sun_family; /* AF_UNIX */
        char sun_path[UNIX_PATH_MAX];   /* pathname */
};


```
What is the above used for?

---

### Post by dwhitney67 on 2010-10-18
It is used when one sets up either a TCP or UDP *file* socket, as opposed to setting up a virtual socket.

Thus for file sockets, one uses AF_UNIX (or PF_UNIX); for virtual sockets, AF_INET (or PF_INET).

As far as usage is concerned, the receiving and sending of data is done the typical way.  Typically file sockets are used for local communications between processes, however I suppose if the receiver and sender are on distinct systems, and the socket is created in a shared area (that say, is NFS mounted), then it should also be usable.


P.S.  Here's some C++ code I wrote long ago that employs the sockaddr_un:
```

void
Socket::bind(const std::string& socketName)
{
  sockaddr_un addr;

  memset(&addr, 0, sizeof(sockaddr_un));
  addr.sun_family = m_Domain;
  strncpy(addr.sun_path, socketName.c_str(), socketName.size());

  if (::bind(m_Socket, (sockaddr*) &addr, SUN_LEN(&addr)) < 0)
  {
    throw std::runtime_error("Could not bind socket!");
  }

  m_SocketName = socketName;
}

```
The socketName is something like "/tmp/mySocket".

---

### Post by jamesbon on 2010-10-18
> **dwhitney67 said:**
> It is used when one sets up either a TCP or UDP *file* socket, as opposed to setting up a virtual socket.

Thus for file sockets, one uses AF_UNIX (or PF_UNIX); for virtual sockets, AF_INET (or PF_INET).

What is the difference between file socket and virtual socket.

---

