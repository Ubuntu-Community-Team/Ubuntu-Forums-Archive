---
title: "Some headstart on a little Python project"
date: 2006-02-11
forum: Programming Talk
---

### Post by krypto_wizard on 2006-02-11
I am trying to write a code which has 10,000 nodes and they mimic a Bit torrent like file sharing mechanism.

I am not using threads but just a standalone kind of program which has to deal with lot of data. I personally thought that this program won't make much of a difference in python (or C for that matter).

Any suggestions to write such kind of programs. Its kinda class project and I have been assigned to simulate a BitTorrent like file sharing mechanism where a server has a full copy and then 10000 users come in the swarm. I have to simulate such enviroment. I can assume certain data for upload and download speed for nodes. And finaly I have to present data such mean download time, share ratio of nodes etc.

All your help is greatly appreciated.

Thanks

---

### Post by gord on 2006-02-11
the offical bittorrent site has a nice explanation of how bittorrent works n stuff, non-blocking sockets are a must and i wouldn't use python if i were you, c/c++, allthough iv not had to use python for extreamly large applications, apart from within  a scalable wrapper with caching and such (such as django within apache)

---

### Post by Lord Illidan on 2006-02-11
Python will be extremely slow...

---

### Post by krypto_wizard on 2006-02-11
Why will it be extremely slow ? Any comparison metric you can give.

Thanks

[QUOTE=Lord Illidan]Python will be extremely slow...[/QUOTE]

---

