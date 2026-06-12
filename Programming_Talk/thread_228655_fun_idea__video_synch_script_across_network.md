---
title: "fun idea : video synch script across network"
date: 2006-08-03
forum: Programming Talk
---

### Post by ubuntu_demon on 2006-08-03
Hi,

This is just for fun. I might not implement it at all.

Would it be easy to write a simple script to make sure a video gets started exactly at the same time on two different computers across a LAN or internet ? 

I have two pc's with each one monitor. It would be fun if I could script something to be able to watch a video at two monitors at once. (same holds for sound ofcourse).

To make it easier (at least for now) :
-let's say the bios clocks are completely synched
-let's only synch the starting of the videos (so no need for synching after it started to make up for dropped frames)

What is needed :
-doesn't need a gui. It's only for fun.
-I need to find out how to this with a nice and clean script without having to write hundreds of lines of code.
-maybe using avahi/zeroconf
-maybe using python

---

### Post by dabear on 2006-08-03
Really, the most simple way to do this (if you have the Ip address of both computers), would be to set up a socket connection. 

You could set up the client to send keystrokes from the terminal terminal to the server, and the both the server and client could then interpret those keystrokes, and start the movie at the same time.

---

