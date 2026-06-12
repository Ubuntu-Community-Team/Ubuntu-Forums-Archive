---
title: "Send resources in networked game"
date: 2009-12-28
forum: Programming Talk
---

### Post by Masterofpsi on 2009-12-28
Hi all. I'm trying my hand at making a networked game using Pygame and Twisted. I've already had some experience writing regular, non-networked games in Pygame, so this is just taking it up a step.

My understanding of networking is shaky at best, but I understand enough to be able to talk intelligently about protocols, tcp, udp, etc.

Right now, I think my biggest impediment to understanding is trying to figure out how a server would get the images, sounds, etc. to the clients. Basically, this is the model I have in my head:

[LIST=1]
[*]The server asks which files, from a list of required files, the client has.
[*]The server asks for checksums of all of the files that the client has.
[*]For files that the client either does not have or has incorrect versions of (as indicated by the checksums) -- the server sends those files over the network.
[*]The user will have options for various kinds of files, telling the program which kinds of files to save and which to delete after use.
[/LIST]

What I'm stuck on is exactly how to get these files to the clients. Should they just go over anonymous ftp? Or is there something else that I'm not understanding?

---

### Post by lloyd_b on 2009-12-28
> **Masterofpsi said:**
> Hi all. I'm trying my hand at making a networked game using Pygame and Twisted. I've already had some experience writing regular, non-networked games in Pygame, so this is just taking it up a step.

My understanding of networking is shaky at best, but I understand enough to be able to talk intelligently about protocols, tcp, udp, etc.

Right now, I think my biggest impediment to understanding is trying to figure out how a server would get the images, sounds, etc. to the clients. Basically, this is the model I have in my head:

[LIST=1]
[*]The server asks which files, from a list of required files, the client has.
[*]The server asks for checksums of all of the files that the client has.
[*]For files that the client either does not have or has incorrect versions of (as indicated by the checksums) -- the server sends those files over the network.
[*]The user will have options for various kinds of files, telling the program which kinds of files to save and which to delete after use.
[/LIST]

What I'm stuck on is exactly how to get these files to the clients. Should they just go over anonymous ftp? Or is there something else that I'm not understanding?

Take a look at libcurl - this provides the functionality to download files via HTTP or FTP (from any webserver, basically), and there are Python bindings for it in the package "python-pycurl".  So all you need to do is have the files on a publicly-accessible webserver somewhere, and the client can easily fetch whichever ones it needs.

And you don't even need to involve the game server in the process - just have a file on the webserver that lists the required files (and their checksums), have the client download that, do the check, and fetch any files that are required.

Lloyd B.

---

### Post by Masterofpsi on 2009-12-29
OK, that makes sense. Thanks for the help.

I have one more question, if anyone can answer. When sending data to clients, does the server generally send the entire game state, or just information about the elements that have changed?

---

### Post by lloyd_b on 2009-12-29
> **Masterofpsi said:**
> OK, that makes sense. Thanks for the help.

I have one more question, if anyone can answer. When sending data to clients, does the server generally send the entire game state, or just information about the elements that have changed?

It depends on the type and complexity of the game.  For a turn-based game, it may be practical to send the entire game state at the beginning of each turn.  For a FPS, however, sending the entire game state 10 times per second or whatever your "network frame rate" is can eat a LOT of bandwidth.

For the most part, "changed only" is how things work on most networked games, because of the bandwidth issues.

Lloyd B.

---

