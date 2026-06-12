---
title: "Need beginner's help with port assignment"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by Halfling Rogue on 2008-11-20
I know little to nothing about port assignment, and am having a bit of trouble with a web app.

I'm running a [Grails](http://grails.org) application on Ubuntu Server v8.04. By default, Grails is set up to run on port 8080 ( [http://123.456.78.900:8080/myProject/](http://123.456.78.900:8080/myProject/) ), but I want to make it so that I don't have to specify the port in the URL. I'm not sure if that would require making Grails run on a different port, or changing the server's port details so that 8080 is the default. I don't even know what the server's default port *is* (I'm assuming 80?) or what it's actually using to serve the pages (I can't seem to find Apache anywhere).

The only thing I really know is that Grails can't run on port 80 due to the way it's designed.

Any help with this would be greatly appreciated. :(

**Edit:** Any possibility of having iptables feed port 80 requests to 8080? I'm not really sure how to do that.

---

### Post by Halfling Rogue on 2008-11-20
Bump.

---

### Post by adaptr on 2008-11-20
The default port for the HTTP protocol is 80, and this is hardcoded in all browsers in existence.
So if the application cannot run on port 80 (why?) then you must specify the port in the URL.

---

### Post by Halfling Rogue on 2008-11-20
I've tried running it on port 80 and get an error saying "Server failed to start: java.net.BindException: Address already in use". It's something to do with the server already running on port 80, I think?

I've seen some people mentioning using iptables to forward port 80 requests to a web app; is this feasible?

---

### Post by Halfling Rogue on 2008-11-20
Bump.

---

