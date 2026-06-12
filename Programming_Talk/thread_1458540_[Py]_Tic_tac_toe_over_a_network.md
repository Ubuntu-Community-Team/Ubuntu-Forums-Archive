---
title: "[Py] Tic tac toe over a network"
date: 2010-04-20
forum: Programming Talk
---

### Post by Asday on 2010-04-20
I thrashed out a wery basic noughts and crosses program in about an hour for local use, and now want to expand it, so the user can play locally against someone, (as is it's current functionality), or play over a network against someone else.

I got as far as thinking that one instance of the program would play as host, leading to something like this:

```

host                    client
open port
wait for connection     open port
                        connect to specified address
connect to whatever
    just connected      wait for board
choose who goes first
if host goes first
    take turn
send board              take turn
wait for board
                        send board

```etc., but I can't figure out how to use what I've already got, and expand upon it.

---

### Post by smartbei on 2010-04-20
You may want to seperate your code into several parts - the "gui" part, which is present in both the host and the client, and is in charge of displaying the board, the "game engine" part, which is mostly in the server and is in charge of creating the board after every turn, and the "network interface" part, which must be seperate - for the host is is accepting a connection, and for the client it is connecting to the host.

As I see it, it makes more sense for the client to send in just the coordinates of the place where it wants to place the symbol (X or O), rather than the whole board. After the host receives it, it sends the board out to both the client and the gui portion of the host program.

I hope this helped you some. Since this is a relatively small project, you may want to just thrash it out, and then see how you could have done it better (and perhaps re-write if you have the patience).

---

### Post by Asday on 2010-04-21
I figured it'd be a good idea to send the whole board, so the checkvalid() could be executed on the client, and it'd only send valid moves, rather than (client) send co-ords, (server) reject co-ords re-request, (client) roll back board take move send co-ords, etc.

---

### Post by Tony Flury on 2010-04-21
Just a thought - 

The tic tac toe board is so simple it can be coded fairly simply as as single integer between 0 and (3^9) -1  (19682) - so you don't actually need to send much data across to transmit the board.

How did i get to this : 

Imagine the board as a set of squares numbered 0 to 8...

each square can be empty an X or a O.
give empty squares value of zero, Xs value of 1, Os value of 2.

now treat this string of 0,1 & 2 as a base 3 number - and you get between 0 and 19682.

this simple coding also make it easy to determine valid moves and valid boards, as it effectively acts as a checksum.

it Might also i think be used to detect wins easily - that depends how obsfucated you want to make the code :-)

Enjoy.

---

### Post by Asday on 2010-04-23
Haha, you just blew my mind.  >_<

I was just going to send the

```

board = [[[""],[""],[""]],
         [[""],[""],[""]],
         [[""],[""],[""]]]
```

---

### Post by Some Penguin on 2010-04-23
> **Asday said:**
> I figured it'd be a good idea to send the whole board, so the checkvalid() could be executed on the client, and it'd only send valid moves, rather than (client) send co-ords, (server) reject co-ords re-request, (client) roll back board take move send co-ords, etc.

Server-side control of game state and validation of client-provided input is usually a saner approach.  What if somebody writes a dishonest client that sends a board where he's already won, regardless of the previous state, for instance?  Granted, nobody's going to bother for Tic-Tac-Toe (and if somebody ever *wins*, then somebody is doing something seriously wrong, at least for 3x3...). but it's a good habit to write servers that don't trust clients without some verification (*).

Likewise, if you wanted to implement something like, oh, Liar's Dice or Stratego, the game might rapidly become pointless if you're transmitting the full game state to each client, because hidden information is a substantial part of the game.  Clients can't illegally reveal information if it's never sent to them in the first place.


(*) Example:  RSA-based authentication in Netrek, to restrict the use of clients to 'blessed' clients.  Even with such clients, the server tracked all state, and processed only legal commands, and determined the results of all actions.  In a more serious client-server system, the clients should also have some way of verifying the server's identity.

---

### Post by nvteighen on 2010-04-23
Ok, my experience on networking is exactly -1, so I may be awfully mistaken about this.

In such a situation, I'd go for something similar as what I do with GUIs. Take the input in, and then have a "bridge" procedure that updates the real board object and the GUI board simultaneously (and taking care that this procedure is the only way to manipulate both objects). 

So, I'd take the local input (coordinate) and update the GUI and also send that input through the network (in some magical way I should learn about). Then, the receiver will take that input exactly as it were a local user's... update the board and the GUI. Maybe you can even abstract the whole local/net input into the very same thing, but I'm not sure.

That's what I'd do, but taking account of my complete ignorance on the matter :P

---

### Post by CptPicard on 2010-04-23
See "Twisted".

---

### Post by Asday on 2010-04-23
Normally I don't trust clients when designing stuff like this, but this is a:  Ad hoc, and b:  Tic-tac-toe.  No-one's going to bother cheating, and even if they do, who gives a ****.  :3

There are easier ways of cheating, too, you could just open up the plaintext user file, and change the wins number to 9001.[SIZE="1"][1][/SIZE]

Re:  Twisted:  That looks super-awesome, and I'm definitely going to look into it for my next project.

[SIZE="1"][1]  How do I work around this, anyway?  I have a dictionary, which is pickeled into a file, named after the user, and within the dictionary, there's a "passhash" index, which is equal to their password sha221'd (I think.  I just picked a random hash function.)  I'd like to do something like that to the whole contents of the file, so if the right password's put in, it's all easily readable, but if the wrong one is, the file comes out as nonsense, so they can't just edit things.  I've googled around before now, for a seperate project, but found only PyCrypto, which refuses to work.[/SIZE]

---

