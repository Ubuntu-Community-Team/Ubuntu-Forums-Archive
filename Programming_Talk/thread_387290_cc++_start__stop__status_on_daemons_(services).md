---
title: "c/c++: start / stop / status on daemons (services)?"
date: 2007-03-18
forum: Programming Talk
---

### Post by mem on 2007-03-18
I’m currently working on a client-server app that has clients report back system stats (already working), but want to be able to add in the ability for an admin to control the client from the server. Of course security is of some concern with this added functionality, but for now I’d like to be able to:
[LIST]
[*]get the status of running processes
[*]stop running processes (cleanly!)
[*]start services like apache when needed.
[/LIST]
By nature I’m a java developer, so this is somewhat new ground for me. I’ve been looking and haven’t found anything along the lines of best practices for doing system level commands from another program. Any advice / points in the right direction would be helpful. 

Is this really as simple as fork() / exec()? How do permissions play into this? Can anyone point me in the right direction? Thanks for any help!

---

### Post by mem on 2007-03-18
On second thought... I'm not opposed to doing this whole project in python...

Can python do the following:
[LIST]
[*]secure client-server communication
[*]system statistics gathering
[*]XML handling
[/LIST]

---

