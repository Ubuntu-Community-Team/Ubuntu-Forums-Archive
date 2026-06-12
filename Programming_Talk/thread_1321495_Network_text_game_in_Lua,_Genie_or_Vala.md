---
title: "Network text game in Lua, Genie or Vala"
date: 2009-11-10
forum: Programming Talk
---

### Post by kumoshk on 2009-11-10
I'm wanting to make a text-based strategy game with network functionality (i.e. so I can play it with other people over the Internet&#8212;or at least through the network).

It is planned to be turn-based.

So, I want to program it in either Lua, Genie or Vala. However, I'm having some trouble figuring out how to do the network side of things.

This is about all I could find for Vala on network programming:
[http://live.gnome.org/Vala/GIONetworkingSample](http://live.gnome.org/Vala/GIONetworkingSample)

I found similar stuff for Lua with Lua Socket.

However, none of that seems to say a thing about how to communicate with my own program through the network. It all seems to be about web browsing, pinging, http servers and the like.

I need to do the following:
&#8226; Send text to any connected computer using my program (from my program)
&#8226; Allow variables in my program to be altered from any connected computer using my program.

How do I do this?

---

### Post by kumoshk on 2009-11-10
Hmm, after some research, I'm thinking that I don't want to use LuaSocket or that Vala library at all.

It seems that a MySQL server is more what I'm after. Does this sound right to you?

However, I'd rather have a dynamically chosen server (i.e. from one of the people playing the game) rather than have my own dedicated server for the MySQL database that may or may not be running the game (although I'm likely willing to try that route if there's good reason to do so&#8212;I do know how to deal with port forwarding and all).

Any ideas or input?

---

### Post by aanderse on 2009-11-10
do you want players to have to download a client to play your game, or just browse to a web site? from your description it sounds like you can go either way here.

i think any of vala, genie, lua, or php would be a great choice to code this type of game. choose the language that best suits you. if you go the vala route there are several apis you can use for connecting to other machines.

so first decide if you want this to be a web based game or a client download game.

---

### Post by kumoshk on 2009-11-11
I definitely want people to have to download it (I don't want it to be played within a web browser). Do you know any API I can use to connect with another machine? Or rather, can you name them? You said Vala had some.

Also, if it's one of the ones I already mentioned, do you know how I would go about doing it? The tutorials don't seem to document the specifics on this type of functionality for some odd reason.

Any of these languages should work. If I start programming in Lua, I can always use an .so file made with Vala, or embed Lua into Vala. Genie seems capable of using Vala code.

My only real concern about Vala is that sometimes I get segmentation faults for more complex things that involve certain libraries. Not sure why. Hopefully that wouldn't happen here, though. Maybe it's just because it's still in development. I'm sure they'll fix things eventually, though. I'm still curious about solutions you can supply for both of either Vala or Lua, though (Genie, too, if it makes a difference).

---

### Post by kumoshk on 2009-11-11
This site tells of a way to share files from computer to computer with Lua:
[http://www.lua.org/pil/9.4.html](http://www.lua.org/pil/9.4.html)

Can I send/receive Lua objects themselves, without having to unpickle them from text files?

What about text? Can I send text without sending it in files?

---

### Post by kumoshk on 2009-11-11
Luasocket seems like it might be a viable option, however, luasql doesn't even seem to work at all on my machine (Ubuntu 9.10, 64-bit). I believe it did the same thing on 9.04.

Anyway, I try ```
require("luasql")
``` and it can't find it (it is installed and it is searching in the right paths). So, I figure maybe I should try the .so files in the luasql folder instead. So, I type this and get the following result:
```
> require("luasql/mysql")
error loading module 'luasql/mysql' from file '/usr/lib/lua/5.1/luasql/mysql.so':
	/usr/lib/lua/5.1/luasql/mysql.so: undefined symbol: luaopen_luasql/mysql
stack traceback:
	[C]: ?
	[C]: in function 'require'
	stdin:1: in main chunk
	[C]: ?

```

Anyway, I guess it's the socket route for me, but I'd still like to use MySQL in Lua some day, though more for efficiency than client-server connections (so Sqlite would probably be fine&#8212;it gives the same error, by the way).

---

