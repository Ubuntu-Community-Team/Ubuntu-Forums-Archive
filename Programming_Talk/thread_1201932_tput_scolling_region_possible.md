---
title: "tput scolling region possible?"
date: 2009-07-01
forum: Programming Talk
---

### Post by bodselecta on 2009-07-01
I'm trying to build a shell menu system for starting/stopping services, running jobs etc but want to provide options to view running logs or view a process status in the same console area without scrolling the view

i.e. i have a fixed top menu with message output below, but i want to watch the last 5 lines or so of output from that message, into a an area of the console, so there's no scrolling or the top menu scrolling out of view

Is it possible to use tput to update only a region of console, or do i have to redraw the menu and display the message region when i want to refresh the log message region?
Thanks for any help

---

### Post by bodselecta on 2009-07-02
sorry for bumping my thread, but did I put this in the wrong discussion forum?

And if I did, sorry but which discussion forum should I post in?
thanks

---

### Post by benj1 on 2009-07-02
yes correct forum.


now unless i misunderstood, couldn't you just rewrite the bottom 5 lines?

other than that im not sure.

---

### Post by bodselecta on 2009-07-02
Thanks benji, that's sort of what I was thinking but I'm new to tput, though i've done console dialogs with cobol/cics years ago
I've been looking through tput capabilities for the last few days and really wanted to know if I'm going down the right route or if there's a better way...
Am i right in thinking that I should just 'head' the output of 5 lines to a point on the terminal, clear the output from that point to the end of the terminal  then 'head' the output again all in a timed loop?
Does that mean I'll need to calculate how many terminal lines are taken up by the head output?

---

