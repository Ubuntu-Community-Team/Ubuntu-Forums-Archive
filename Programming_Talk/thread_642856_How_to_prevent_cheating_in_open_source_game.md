---
title: "How to prevent cheating in open source game?"
date: 2007-12-17
forum: Programming Talk
---

### Post by Jay_Bee on 2007-12-17
I am planning on making a web page for my game (in making) where users will be able to post their scores.
My question is - how to prevent hacking of the scores data in an open source game?:confused:

---

### Post by pedro_orange on 2007-12-17
You could always try & obfuscate certain sections of code :)

Or you could just trust the open soruce community not to cheat

---

### Post by lswest on 2007-12-17
or you could use a Creative Commons License, and protect your work that way (not too sure how to explain it, but a quick google search should give you an idea of what it is).

---

### Post by Wybiral on 2007-12-17
The game "Cube" ran into this issue pretty heavily a number of times. Because it was open source, people could give themselves infinite weapons and health, etc...

Eventually they found a pretty stable solution of making the server regulate some of the data, as well as giving moderator power to the players to take care of cheating as a community.

This doesn't directly apply to your problem, but you might build the score uploading system into the game. If it's possible for you to make your server dish out some of the game components and check the results for sanity. Basically, if the game is 100% client-end based, then it's going to be near impossible to stop people from sending false data (open source or not).

Suppose it's a number guessing game (for a simple example) the server could send the number instead of having it generated on the client-end, then it can check the results that the client sends back.

It might help if you describe the game some.

---

