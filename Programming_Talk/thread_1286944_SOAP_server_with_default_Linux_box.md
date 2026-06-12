---
title: "SOAP server with default Linux box"
date: 2009-10-09
forum: Programming Talk
---

### Post by gbablon on 2009-10-09
Hey all,

I'm trying to set up a very simple SOAP server. Basically, I have a Linux (Debian) box running mySQL. Clients need to pass authentication information to this server (username & password) and be told whether the authentication is valid or not. I know I could just connect to the DB directly from the client, but the idea is to encapsulate the functionality to hide it from the outside world (I don't want the DB connection info to be available on the clients).

Hence, the idea of clients connecting (via Python) to the server through SOAP, passing the authentication string, and being told whether they're OK or not - they really don't need to see what's going on "behind the scenes".

I know one way to make this work would be to setup Apache and PHP, and create the SOAP server with those tools - since PHP makes that a lot easier. But I'd prefer avoiding it I can, to keep as few "breakable" components as possible on the server. I'd prefer building the SOAP server app in Python, connecting it to a port somehow for it to listen on, and forego installing anything extra.

But is that possible? Do I need to be running a web server (ie. Apache) for SOAP to work? Or can any Linux box setup as a server, with an IP address, do the trick? MySQL is running fine without Apache right now...

Any suggestions would be appreciated. Thanks!

---

