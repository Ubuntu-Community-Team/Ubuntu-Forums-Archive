---
title: "Storing messages"
date: 2010-03-24
forum: Programming Talk
---

### Post by ukkuku3d on 2010-03-24
Hi all,
to store temperatures and other measured values I use RRDtool - a really great database for time based data.
But I also have "events" which appear irregular, sometimes 10 a minute and then nothing for one or more day. Some of these events even appear not over years, so how to store and evaluate them?
The RRDtool data are displayed on a time based graph, very nice.
It would be perfect, if these events could be inserted into these graph, e.g. as hints, or bubbles and positioned at the correct time.
Events are thinks like:
[LIST]
[*]An engine starts/stops
[*]Somebody pushed a switch
[*]An error occured
[*]A specific (maybe critical) state was entered
[/LIST]
Of course, errors are already handled via Syslog, but this is more human readable format.
Currently I misuse RRDtool with a huge heartbeat to store 32 bits of integer and have a lot of trouble with this. 
Do anybody know about a tool as powerful as RDDtool but for efficient storing asynchronous events?

Thanks a lot
  Achim

---

### Post by skullmunky on 2010-04-19
Hi, I don't really have an answer for you, but now I know about RRDTool which I'll certainly have a use for!  so, thanks...

Is the issue just that your events are sparse so with this you end up with wasteful volumes of empty logs?

---

