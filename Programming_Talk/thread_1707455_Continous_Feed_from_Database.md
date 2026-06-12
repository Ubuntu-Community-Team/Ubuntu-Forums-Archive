---
title: "Continous Feed from Database"
date: 2011-03-15
forum: Programming Talk
---

### Post by jesuisbenjamin on 2011-03-15
Hello there,

I'm very curious about how programming works, although i have so little time to find out everything by myself through practice.

As i begin to get a sense of how Databases like mySQL are working and displayed with PHP, Java etc. I have difficulty understanding how a continuous feed of data can me made.

Since i don't know what i am talking about, i may use the wrong words. With continuous data feed i mean for instance the case of online games where your actions and that of the other players are affecting your display instantly.

How can this happen? Is it the same as a PHP page loading every minute, but faster? Or is there any different technology at work?

Thanks for clearing this up.

Cheers.
Benjamin

---

### Post by robots.jpg on 2011-03-15
Most online games send back and forth a relatively small set of  information about what's going on.  Usually the location and  direction+speed of each visible player, NPC, etc. and updates when items  are moved from one container to another.  It's up to the game client to  display all of that to the player, and to make guesses about the new  location of a character whenever some time has passed without hearing  from the server.  Likewise, if the client and server go some stretch of  time without communicating, the information on the server can be updated  with whatever the client tells it has happened during that time.
 
 How closely tied together the information on the client and server are  determines what kind of cheats have to be guarded against, and how  playable the game is for people with different connection speeds.  In  games  like Ultima Online, your running speed could actually be limited by your  ping time, since the client and server had to agree on your position  every time you moved from one tile to another.  In games that are more flexible, people could sometimes interrupt their connections intentionally so they appeared to be in a different place to another player.  When they reconnected, they would appear to "jump" back to the correct location from wherever the other clients guessed them to be.
 
 
Regarding the database, the world just isn't saved to storage  continuously in most games. They all have different methods for dealing  with it, but you'll probably notice that when there's a server crash,  everything tends to be rolled back by 10-20-whatever minutes.  That's  most likely the time that has passed since the last save of whatever  area you're playing in.  These can also be a source of exploits.

---

### Post by jesuisbenjamin on 2011-03-15
Nice story :popcorn:
I had imagined it as an option to guess, but thought it would be a silly and complicated thing to do. But now that i read your message, i guess it's just inevitable.
It seems then to me that in case of on-line games, the safest would be a turn-based game, since it would provide full update of what's on the server before playing.
But i guess making a good client that can cope with delays is where the art of programming comes into account :)

Does your example on online-games mean there is no such thing as continuous data feed from a server? Is it always provided in clusters?

Cheers.
Benjamin

---

### Post by robots.jpg on 2011-03-15
Basically.  If you want information to be stored centrally in  a database while multiple users are changing it, there's going to be a limit to how many transactions and  queries you can perform in a given amount of time.  Maybe it's possible to do better with some kind of peer-to-peer setup.

---

### Post by Some Penguin on 2011-03-16
> **jesuisbenjamin said:**
> 
Does your example on online-games mean there is no such thing as continuous data feed from a server? Is it always provided in clusters?

At a fairly primitive level, data is transmitted in packets --  you don't have dedicated physical connections (well, normally...), so you need overhead for routing information and the like rather than /just/ sending data. 

It is not entirely unheard of to use UDP i.e. best-effort-but-not-guaranteed delivery.  Netrek permitted (well, permits... although there probably is a fairly reduced player base these days) 16 players from widely distributed geographic locations to play in the same real-time game -- the option to use UDP provided a trade-off where you might drop individual packets, but less time was spent reordering packets or retransmitting so your overall experience was usually better than w/ TCP.  UDP means you don't get such things as persistent connections, so you need to think carefully about what you send in each request... (in the case of Netrek, you're not really transmitting game state, but instructions on what your ship is trying to do -- the server controls all game state, withholds information you're not allowed to know such as the locations of cloaked ships, and is free to ignore nonsensical orders).

---

### Post by jesuisbenjamin on 2011-03-17
> **robots.jpg said:**
> Basically.  If you want information to be stored centrally in  a database while multiple users are changing it, there's going to be a limit to how many transactions and  queries you can perform in a given amount of time.  Maybe it's possible to do better with some kind of peer-to-peer setup.

Thanks for that.
And it makes me wonder: what determines this limit? I suppose the more powerful the server the faster the queries. And the volume of transactions depends on the connection i presume?
If you look at a game like Age of Empires Online (I've seen videos of it only), it seems incredibly fast. If character A hits character B in a game, the server and client must be sure B is still at the same position when that happens right? Now some multiplayer games have hundreds of thousands of players, and client may have few hundreds items simultaneously on display which can be changed remotely. How fast the data must flow for the game to run smoothly? It must be seriously fast right?

With regard to the queries on the server database. Are they processed sequentially? If thousands of players query simultaneously, they may come sequentially to the database even if separated by milliseconds only. Is this again a matter of how powerful the server is to cope with a large amount of queries like this?

How is peer-to-peer making a difference? I understand how peer-to-peer is good for file exchange or for a small number of simultaneous users. How do you suppose it works in the case of massive numbers of users interacting with a single database? 

Thanks for clearing this up, these questions keep bugging me until i understand :P

Cheers,
Benjamin

---

### Post by jesuisbenjamin on 2011-03-17
> **Some Penguin said:**
> 
It is not entirely unheard of to use UDP i.e. best-effort-but-not-guaranteed delivery.

I didn't know about UDP till now. It sounds weird but very interesting, although i am not sure to understand the concept of "dropping packages", which i understand as holes in a sequence of data, right?

Thanks.
Benjamin

---

### Post by robots.jpg on 2011-03-17
> **jesuisbenjamin said:**
> 
If you look at a game like Age of Empires Online (I've seen videos of it  only), it seems incredibly fast. If character A hits character B in a  game, the server and client must be sure B is still at the same position  when that happens right? Now some multiplayer games have hundreds of  thousands of players, and client may have few hundreds items  simultaneously on display which can be changed remotely. How fast the  data must flow for the game to run smoothly? It must be seriously fast  right?

Like I said above, the servers the players connect to are most likely  handling all of that in memory, without even touching the database. For a  large game, there's probably a pool of redundant virtual servers  handling different parts of the game world.  A server running one region  might drop out of the rotation to commit everything to the database,  while another mirrored server picks up the processing right where the  first one left off.  I don't work in online games though, so it's just a  guess.  

What I meant about peer-to-peer was just the idea of offloading some of  the server's work to whatever players are in a specific area of the  game.  If you have 20 people all fighting in one spot, do all of their  actions really need to be passed through the main server and then back  out to everyone else, or is there a safe way to let them process things  among themselves and check in with the server less often?

---

### Post by jesuisbenjamin on 2011-03-17
> **robots.jpg said:**
> Like I said above, the servers the players connect to are most likely  handling all of that in memory, without even touching the database. 

Now i seem to understand! I was imagining the engine backing up continuously the data in the database, which would be too time consumming. While in fact what you suggest is that the data is live in virtual memory, backed up only once in a while.

> **robots.jpg said:**
>  What I meant about peer-to-peer was just the idea of offloading some of  the server's work to whatever players are in a specific area of the  game.  If you have 20 people all fighting in one spot, do all of their  actions really need to be passed through the main server and then back  out to everyone else, or is there a safe way to let them process things  among themselves and check in with the server less often?

I see. But then again, doing so would risk cheats (in the case of a game), unless you are sure players play against each other, with their respective client keeping others in check.

Thanks for that :)

B.

---

### Post by Some Penguin on 2011-03-17
> **jesuisbenjamin said:**
> I didn't know about UDP till now. It sounds weird but very interesting, although i am not sure to understand the concept of "dropping packages", which i understand as holes in a sequence of data, right?

Thanks.
Benjamin

Yup.  Updates get lost.  Throw in a sequence number and the intended recipient can notice, however.  It was fairly common for Netrek clients provided estimates of packet loss as well as latency and standard deviation thereof -- *inconsistent* latency being difficult to adjust to.

In a peer-to-peer architecture it /is/ possible to make it fairly difficult to forge packets (through the use of encryption; the clients need to access the keys, but you can make it not worth most peoples' time to extract them if you really care to).    You do have all sorts of potential problems once the keys are extracted and malicious clients are written, however.

---

### Post by jesuisbenjamin on 2011-03-18
@Robots.jpg
Wait, now i am doubting. If i understood correctly, and if indeed data is saved to the database once in a while, then how is the client informed of the current status of the data before it is saved?
For what i know the client should request the data from the database, not from a running engine on the server, right?

@Some Penguin
Sounds like complex thing to program with to me :s

---

### Post by robots.jpg on 2011-03-18
> **jesuisbenjamin said:**
> @Robots.jpg
For what i know the client should request the data from the database, not from a running engine on the server, right?


I'm saying there's an engine running on the server holding in memory everything the clients could possibly need to know.  When it comes to the actual gameplay, you can basically forget about databases except as a way of making sure everything isn't lost if something goes wrong.

---

### Post by jesuisbenjamin on 2011-03-18
> **robots.jpg said:**
> I'm saying there's an engine running on the server holding in memory everything the clients could possibly need to know.  When it comes to the actual gameplay, you can basically forget about databases except as a way of making sure everything isn't lost if something goes wrong.

Ha, i didn't know it was possible for the client to directly request data from the engine. I thought the engine first had to save the data in some file before the client could request that file to be transfered. Do you have more information about this?

Is it also possible to inform the client of the difference between prior and current status only to limit the data transfer? I guess it makes more sense than transferring all the data each time.

I find this so cool to learn :popcorn:
Thanks

---

### Post by Some Penguin on 2011-03-18
It tends to be a very, very bad idea to have clients connect directly to your databases -- now you're exposing implementation details like table schema and essentially committing to leaving them unchanged.

---

