---
title: "Programming multiplayer games, how do I get started?"
date: 2009-09-02
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-09-02
I use C, OpenGL and SDL, and want to learn how client-server multiplayer games work (like quake, teeworlds, cs2d etc..). I already tried googling with keywords "programming multiplayer games network online" but didn't find anything useful.

Can you give me a link to an article or a design document? I already know what is TCP and UDP and how to create a chat program with SDL, but the roles of client and server in real-time shooter are not very clear to me, nor how they communicate, what data to send etc.

Thanks for your time.

---

### Post by WitchCraft on 2009-09-02
You need a good 3d rendering engine (Quake3/Irrlicht)
[http://en.wikipedia.org/wiki/List_of_game_engines](http://en.wikipedia.org/wiki/List_of_game_engines)

> **crazyfuturamanoob said:**
> 
 I already know what is TCP and UDP and how to create a chat program with SDL, 


UDP is the way to go. 
apt-get source openarena for reference

> **crazyfuturamanoob said:**
> 
but the roles of client and server in real-time shooter are not very clear to me, 

Client: rendering, input, untrusted unreliable entity
Server: communication center, information processing & management, trusted reliable entity

> **crazyfuturamanoob said:**
> 
nor how they communicate


Connectionless (faster, render state can get lost, no point in showing it 3 seconds later), Compressed, encrypted, as few as possible.

> **crazyfuturamanoob said:**
> 
, what data to send etc.


Never let players have other players IPs (communication always via server)...

chat, serverinfo, gamestate, player position & acc & velocity, events (shoot, vote)

---

### Post by koonsolo on 2009-09-02
A good starting point are the multiplayer and networking articles you can find at gamdev.net: [http://www.gamedev.net/reference/list.asp?categoryid=30](http://www.gamedev.net/reference/list.asp?categoryid=30) . Not all articles are that good, but you should definitely check out those from gamasutra.

---

