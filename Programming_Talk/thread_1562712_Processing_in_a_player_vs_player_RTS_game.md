---
title: "Processing in a player vs player RTS game"
date: 2010-08-28
forum: Programming Talk
---

### Post by Asday on 2010-08-28
I've been thinking about this a fair bit recently, and I just can't get my head around it.

How do you safely and efficiently implement player versus player in a real time strategy game?

The only way I've been able to come up with so far is a *third party* server, which receives input from the players, and sends back to them what they need to know.  There are, however, two major disadvantages with this.  Not everyone has a spare computer meaty enough to handle what I have in mind, (and I can imagine there'd be a trust issue), and if anyone runs a dedicated server, and the game gets popular, a *hell* of a lot of processing power will be required to give everyone a smooth experience.

That kinda lead me onto P2P-esque technology, but that again raises the issue of trust.  Assuming each player's machine handles what it's player is doing, and only sends data to the other computer when units are interacting, there has to be some sort of "hey, is it OK that he did that" check, which could just be mucked up unfairly by memory editing(?), (and in my case, which computer would run the RNG which salts the damage numbers?).  Also also, if the only data sent is interaction data, how does one player know the other isn't just memory editing in resources, or whatever?

Thank you for your time.

---

### Post by Some Penguin on 2010-08-28
*shrug*

Client -> server.

1- Server only shares information that each client would know.

2- Client packets contain instructions; server validates, executes, and controls all game state.

3- Server and client mutually authenticate each other using e.g. RSA-based challenge.

i.e. server and client send each other randomly constructed strings.  The recipient of a string uses an RSA private key to sign it, and includes sufficient information to identify the public key for verification purposes (e.g. name / version number).  The issuer of this challenge has a list of (name / version number) -> RSA public key, pref. in a user-configurable file.  The private keys are NOT distributed with the source code, but are maintained by 'blessed' package maintainers, and binary packages are shipped with settings that trust existing binaries.

---

### Post by Asday on 2010-08-28
Aye, I thought of that, but that requires a third machine, (or at least third process), which needs to be powerful enough to run the fairly heavy AI I was planning, and if one of the players is the owner of the third machine, (or process) that calls up trust again.

---

### Post by Some Penguin on 2010-08-28
Why wouldn't AI be done as part of the clients, not the server?   The server only needs to arbitrate; i.e. maintain game state, receive instructions, validate them (discarding any that violate the rules), alter game state, and provide clients with their altered views.

In addition, with clients getting to validate the server as a trusted binary, it's considerably more difficult for a player (even the host) to monkey with things.

---

### Post by Asday on 2010-08-28
Even with a trusted binary you can still *** about with the memory, can you not?

Anyway, this is all moot, 'cause it's very likely to be a bad idea.  How would it work in P2P?

---

