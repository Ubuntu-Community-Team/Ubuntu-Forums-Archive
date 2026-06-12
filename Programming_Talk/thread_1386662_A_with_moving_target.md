---
title: "A* with moving target"
date: 2010-01-20
forum: Programming Talk
---

### Post by aanderse on 2010-01-20
I've been using A* pathfinding algorithm to find paths between 2 positions in an online game I'm working on for fun.
The attached image shows a representation of my A* nodes and how they are connected:
The red squares are A* nodes, the black squares are obstructions (the player cannot walk there, like a building, a river, etc...), and the blue lines represent a connection between 2 A* nodes.

I've drawn a little stick man to demonstrate the size/scale of a player compared to the average A* node.
No A* node will have any obstruction within it, so if a player wants to move around within an A* node they simply walk in a straight line (the shortest path).
Typically in a 2d game like this A* nodes are very small (1x1 unit, the size of a player) but I decided to take the alternate approach (large A* nodes,  compared to the size of a player) mentioned here to significantly reduce the number of A* nodes in a map.

Finding a path between 2 static points has been working great, but now I would like to implement chasing behaviour for actors.
I've put a little thought into a way to calculate a path from an npcs current position to a moving target but would like to get some input from anyone else who might have some experience with this.
I suppose the problem comes from my constraints...

My current constraints are that this is all calculated on the server (online game) so I need to calculate all paths in advance (when the server gets the request for an npc to chase a player) and send the path to all clients (I can't keep sending updates every couple frames).

Thank you for any help.

---

### Post by Senesence on 2010-01-21
> **aanderse said:**
> My current constraints are that this is all calculated on the server (online game) so I need to calculate all paths in advance (when the server gets the request for an npc to chase a player) and send the path to all clients (I can't keep sending updates every couple frames).

Well, if you have more than one player in the gamespace, and all the players can "see" one another, wouldn't you have to send updates whenever a player moves, or performs some other action that the rest of the participants have to be aware of?

So, in the case of sending path updates, those updates would have to be sent not just to the player that's being chased, but also to all the other players that can "see" that particular npc.

You might as well just do the straightforward thing and run everything on the server, while sending nothing more than position/orientation updates for all relevant objects.

Actually, I think that's basically how most network multiplayer games work: the client sends player state, the server responds with the data that represents the game state, and on it goes.

---

### Post by aanderse on 2010-01-21
> **Senesence said:**
> Well, if you have more than one player in the gamespace, and all the players can "see" one another, wouldn't you have to send updates whenever a player moves, or performs some other action that the rest of the participants have to be aware of?

Yes.

> **Senesence said:**
> So, in the case of sending path updates, those updates would have to be sent not just to the player that's being chased, but also to all the other players that can "see" that particular npc.


Yes.

> **Senesence said:**
> You might as well just do the straightforward thing and run everything on the server


Agreed. I do.

> **Senesence said:**
> while sending nothing more than position/orientation updates for all relevant objects.

The position is usually multiple positions though, a path which the player is supposed to follow (go to first position, then go to the next position, continue following all positions until you've hit the final position in the list of positions the server has sent.)


To clarify:
On any given client when the player clicks on terrain they send a  message to the server basically saying "I want to move to position X" and the server then path finds from players current position to where the player said they wanted to move and it comes up with a list of positions which the player needs to follow to get there. The server then sends this list to all other players (including the player who requested) and on those clients the corresponding actor will then follow that path. I need to calculate this path in advance so I can send it to all players in the game.

---

### Post by Senesence on 2010-01-21
> **aanderse said:**
> The position is usually multiple positions though, a path which the player is supposed to follow (go to first position, then go to the next position, continue following all positions until you've hit the final position in the list of positions the server has sent.)

If you're really doing everything on the server, the client should not be responsible for following the path. Instead, it should just get game-state updates 10 times per second (or something like that), in which the only data sent is the next position, and the next orientation of all relevant objects.

In short (what I'm saying here): the client should not be aware of any "path"; it should just act like a dumb rendering terminal, and render objects at the given position/orientation. The server should actually move entities from one node to the next.

---

### Post by aanderse on 2010-01-21
> **Senesence said:**
> If you're really doing everything on the server, the client should not be responsible for following the path. Instead, it should just get game-state updates 10 times per second (or something like that), in which the only data sent is the next position, and the next orientation of all relevant objects.

In short (what I'm saying here): the client should not be aware of any "path"; it should just act like a dumb rendering terminal, and render objects at the given position/orientation. The server should actually move entities from one node to the next.

The server does all of the "real" work. The client is sent the path so that the server doesn't need to send updates "10 times per second (or something like that)".

If I send a position 10 times a second I will send 10 positions a second for the entire duration of the move, but if I just send a list of positions (the path) once at the beginning I will only send 2 or 3 positions for the entire duration of the move. So compare sending 50 positions (a move which takes 5 seconds) to each and every client vs sending 3 positions to each and every client. All the client needs to do is some very simple interpolation between the positions in the path. If you had some sort of argument for security then I could see your point, but considering the client is merely rendering and not making any decision with this path, the fact of lag for each and every position update (occurring multiple times a second), and the fact that having the client interpolate between 2 positions costs almost nothing I can't see any benefit to your suggestion.

Yes I understand in an online game you want to offload as much as you can to the server, but keep in mind why: security and synchronization. Your suggestion does not offer any extra security, and it actually makes synchronization worse. Hence my desire to calculate paths in advance.

---

### Post by Senesence on 2010-01-21
> **aanderse said:**
> If I send a position 10 times a second I will send 10 positions a second for the entire duration of the move, but if I just send a list of positions (the path) once at the beginning I will only send 2 or 3 positions for the entire duration of the move.

Unless your players are willing to stand still for the "duration of the move", you're going to have to send updates no less frequently.

Sending one position 10 times per second is much better than sending 3 positions 10 times per second.

> Your suggestion does not offer any extra security, and it actually makes synchronization worse.

I'm interested to know why it makes synchronization worse, if you could be so kind as to explain your reasoning.

Thanks.

---

### Post by aanderse on 2010-01-21
> **Senesence said:**
> Unless your players are willing to stand still for the "duration of the move", you're going to have to send updates no less frequently.

If you mean "stop clicking the mouse repeatedly" when you say "stand still" then I do assume my players are willing to do that. If you click on location X and your character starts moving towards location X it would be illogical to continually click on location X.

For a 5 second move your method would have 50 position updates, while I would have 3. If the player started wildly clicking, though, my method could have well over 50 clicks within that same 5 second time period. This could be worth some consideration... I'll ponder this more.


> **Senesence said:**
> I'm interested to know why it makes synchronization worse, if you could be so kind as to explain your reasoning.

The synchronization issue assumes my players aren't clicking like wild monkeys who were given mice. Again, this may be something I need to ponder more...

We both had very different assumptions entering into this thread.  Once I reconsider my assumptions I would love to continue this thread.

Thank you.

---

### Post by grayrainbow on 2010-01-21
You can try search for dead reckoning. And as a whole...A* for local player to run on server...doesn't sound quite logical for me. Even the games you play in the browser(flash, java, silverlight) run mostly on your local machine, and server is basicly for synchronization, and updates of other players of course(npc included), that's if the game is not p2p(in your case it's not).
Anyway, about that what I get as original question in the thread(npc chasing player), assuming you don't want to deal with transfer of ownership and a like(most times I am a big fan of that), think sending list of nodes(path) will be enough, and depending how you do your path mesh(net of nodes in your case) you may not need to update it very frequently.
And remember that game is not something else but world that you create, and you are kind of god there, which mean you can cheat however you like. For example one npc could always see through walls and start calculating it's moves, just activation of that calculated moves will happen later so player wont feel it like a cheat.

---

