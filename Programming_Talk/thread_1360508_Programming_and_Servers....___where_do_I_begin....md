---
title: "Programming and Servers....   where do I begin..."
date: 2009-12-21
forum: Programming Talk
---

### Post by MR.UNOWEN on 2009-12-21
Hello,

So someone asked me to make an app for the iphone that needs to send text and images to and from a server and acts similarly to AIM. I know how to create iphone apps, but I have no experience with servers...   where do I begin?

---

### Post by kahumba on 2009-12-21
That's pretty vague.
If you wanna create an "AIM-like server" from scratch - that's a lot of work, unless it must be very simple with very few features, if that's what you want - first you have to learn server-side programming, pick a language (like PHP) and learn..

---

### Post by Some Penguin on 2009-12-21
Seems you'd be better off using an existing system like an XMPP implementation rather than inventing and implementing your own messaging and presence-detection protocols.

[http://en.wikipedia.org/wiki/List_of_XMPP_server_software](http://en.wikipedia.org/wiki/List_of_XMPP_server_software)

---

### Post by MR.UNOWEN on 2009-12-21
I'll go with Some Penguin idea...

0_0....  once again, I believe I've bit off more than I chew... So obviously I want to spend the least amount of effort to pull this off. If possible, a system that just sets up a one on one connection would be nice as it takes the server out of the picture and has the two iphones communicate between each other. I also want to avoid spending $, so a pre-existing system that doesn't cost me anything would be best.

FYI, I really don't know much about network connections.. so...  ya... I'm in over my head on this one. 

I also need a means to store information, images, audio, text (profile.. etc).

Any advice / direction would be appreciated and thanks for the help so far.

---

### Post by kahumba on 2009-12-21
1 on 1: You still need an external server to at least be able to do the 1 on 1 connection, otherwise how can they know each other's IP to connect to each other?
If I were you I wouldn't take the job unless I'm paid correspondingly to the amount of work needed to be done or if I'd like to learn about such stuff.

---

### Post by MR.UNOWEN on 2009-12-22
So I don't know which to pick or anything for that manner, so what do you guys recommend and what should I start reading on?

---

### Post by Hellkeepa on 2009-12-22
HELLo!

I'd start with reading up on server application architecture, and the TCP/IP stack (or whatever protocol you prefer to implement). Also, read up on authentication, encryption and general network/internet security.

Happy codin'!

---

