---
title: "Problem with Glib IOchannels, Gnet, and event watches"
date: 2014-12-03
forum: Programming Talk
---

### Post by TinkerTaylor on 2014-12-03
I thought I would acquaint  myself with GTK+, Glib and related libraries so I started to write a small SNTP client application. The application simply sends and receives an UDP packet. The Gnet reference mentions that instead of polling a socket to check if it is writable or readable, one can add watches with g_io_add_watch() and perform the reading and writing in a callback function. I use the same callback function to both read and write to the socket.

The problem I have is that after I send/write an UDP packet, it returns very quickly so that I am still in the callback when the "socket readable" event (G_IO_IN) is dispatched. I assumed that the event would be delayed until I left the callback and then the callback would be called again, but now with the new condition. But this seems not to be the case. It is not at all picked up while in the in the callback and thus I never receive the event indicating  "socket readable". 

So could somebody please explain to me which is the best way, in Glib, to handle events that arrive when already in a callback for a different event? There must be mechanism for this since it is hardly acceptable to miss events. Multiple threads maybe? 

I tried to remove the watch when entering the callback and then adding it again just before leaving, but it did not work.

---

