---
title: "New project, the JoltProject.com"
date: 2009-11-04
forum: Programming Talk
---

### Post by NetSkay on 2009-11-04
hey guys, not sure where to post this, but this thread seemed most relevant.
My friend and I are currently a bit over half a year in development of the Jolt Project. As we progress development, we have entered the stage of beta testing, where we are looking for a user base willing to test and submit bugs, features, and design improvements.
Jolt Project is a revolutionary messaging network much like IRC, but our hope is that we will reach and exceed IRC standards by providing better support, centralized project management unlike IRC forks, and robust APIs for the client and server.
The project was part of the commuart.com project however, commuart.com halted mid-summer and my friend and I already had a large code base, so we figured we will continue and develop our software solution as an open source project for the community.

The code is not yet released as we try to reach a stable version and finalize designs and construct our website, however we have put up a beta sign up form, so i welcome anyone to check us out at [http://joltproject.com/](http://joltproject.com/) and hopefully help us push this new product into the world.

Thank you.

Screenshots:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=134926&stc=1&d=1257470430[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=134927&stc=1&d=1257470430[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=134928&stc=1&d=1257470430[/IMG]

---

### Post by kavon89 on 2009-11-04
> the server is being developed under the asynchronous networking model in python with complete event based logic and the client is built using Javascript.

Isn't Python a very slow language to be used for the server? Also, since the client is in Javascript, one can assume this is like IRC in a web browser, right?

I signed up to test it.

---

### Post by Can+~ on 2009-11-04
The website looks nice, but could you remove the shadow effect for the text. It looks ok on the headings, but no so pleasant to read on a long piece of text.

> Isn't Python a very slow language to be used for the server?

Interesting question. I don't know how much fast is python over PHP, or a java server. But usually, the big "bottle neck" is on the network, and not so frequently on the server (unless having big volumes of I/O).

---

### Post by NetSkay on 2009-11-04
i dont blame people asking this question because before we even began development, i had hard time agreeing on a language, and thats right, the big bottleneck is not gonna come from the interpreter but from IO, database queries, networking IO and such... we chose python because its a very modular language, and modules can be loaded/unloaded removed and etc. without ever stopping the daemon service, where if we had used a compiled language such as C++ or some other C derivative, we have to consider compilation for a particular system, changes could not be applied on the fly, etc...
plus, twisted framework allowed for easy C like implementation of callbacks with very powerful asynchronous model...
and lastly, these days computer are very fast and efficient, so CPU utilization is not a problem, we are however developing a load balancing technology that interconnects all selected server instances into a giant infrastructure, making each server a node, and essentially the client cannot distinguish the difference from server A, B or etc.

addressing the IRC question, no not really, this is a solution completely different from IRC, unlike IRC, we offer privilage classes, modes, class order, topics, and much much more, we have yet to compile our feature list...

---

### Post by NetSkay on 2009-11-05
bump! and added screenshots!!!

---

