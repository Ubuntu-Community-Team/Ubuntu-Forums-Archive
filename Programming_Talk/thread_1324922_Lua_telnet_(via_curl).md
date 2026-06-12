---
title: "Lua telnet (via curl?)"
date: 2009-11-13
forum: Programming Talk
---

### Post by kumoshk on 2009-11-13
I'm trying to figure out how to write a program in Lua with Lua-based telnet functionality.

Basically, I have a server program (it uses LuaSocket) that can send objects to the client. The client, I think, needs to have telnet functionality. I want the server to send stuff to the client, and have the client able to display that data (although it may be a cross-platform GUI client&#8212;so it needs to be able to do more than display it to the command-line).

I can already send text to a pre-made telnet client, but I want to make my own client in Lua so that it can have other GUI/graphical functionality dependent on the data received.

I've heard that cURL for Lua might offer this functionality, but I have no idea how to use it. Here's a link with some information about luacurl:
[http://luacurl.luaforge.net/](http://luacurl.luaforge.net/)

I should note that the luacurl library I have seems a little different than this documentation. For instance, to create a new curl object, I *think* I use curl.easy_init() or such instead of curl.new(), as the latter is nil. I don't know what parameters to use with the c:setopt(option, value) method, and I have a feeling my version requires more than two parameters, but I'm not really sure.

Here's a link with an example that uses LuaSocket in the manner I mentioned:
[http://www.tecgraf.puc-rio.br/~diego/professional/luasocket/introduction.html](http://www.tecgraf.puc-rio.br/~diego/professional/luasocket/introduction.html)

Anyone have any ideas? Do I even need telnet for this, or can I use LuaSocket on the other end, somehow? I'm guessing I can, but I'm not sure how.

---

### Post by kumoshk on 2009-11-13
Hmm. It almost looks like it can be done with LuaSocket. I found the following URL:
[http://www.tecgraf.puc-rio.br/~diego/professional/luasocket/tcp.html](http://www.tecgraf.puc-rio.br/~diego/professional/luasocket/tcp.html)

However, when I connect and then send some text, the server responds, but it doesn't print the text. Is it supposed to? (The client does when the server sends it.) How does the server handle received text? Here's my client code:
```
socket = require("socket")
client = socket.connect(myServerIPAddress, 1995)
client:send("Here's my text!")
client:close()
```

I notice that this client functionality works from within the server program itself, with it as the localhost, but not from the client program.

---

