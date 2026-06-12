---
title: "School Networking Project"
date: 2009-07-11
forum: Programming Talk
---

### Post by TheBuzzSaw on 2009-07-11
Our class final involved choosing a project idea, having that idea approved by the instructor, and then executing the idea.

A friend and I teamed up, went a bit beyond the call of duty, and came up with this:
[http://code.google.com/p/cs460f/downloads/list](http://code.google.com/p/cs460f/downloads/list)

We'd be interested in seeing if the program works for any of you. It requires two computers at least (or a computer and Virtual Box) connected over LAN. The program itself requires SDL, SDL_image, SDL_ttf, and SDL_net (all in the repositories unless you use the Windows version; that one is entirely self-contained). Run it from the command line:
```
./cs460f <port> [host]
```

Whoever acts as server just needs a port. Whoever acts as client (can be many) needs port and host address.

Don't get your hopes too high: it just places several mice cursors into a shared window.

The source code is available for anyone who wants to take a peek (in the Google Code site).

Feedback is welcome! We're debating on what to replace the various mouse cursors with. :P

---

