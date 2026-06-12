---
title: "Responsiveness with asynchronous I/O"
date: 2011-01-31
forum: Programming Talk
---

### Post by t1497f35 on 2011-01-31
Hi folks,
Do Gnome/glib's gio async functions perform I/O in the same thread (and hence on same CPU core - but this is less important) from where they've been called (typically from the "event thread")? If so, doesn't it mean that to get better/good user interface responsiveness (especially when lots of I/O is involved) one should be using multiple threads instead?

This idea came from [a book]("http://www.amazon.com/Programming-POSIX-Threads-David-Butenhof/dp/0201633922") I'm reading, plus I've googled and found similar statements for example on [M$'s site]("http://msdn.microsoft.com/en-us/library/wewwczdw.aspx").

I'm also asking because Transmission's **Gtk+ GUI** when downloading a few torrents at once typically becomes extremely unresponsive (and hence very annoying)  despite me having an Intel Core i5, so I thought it could be because of async I/O as suggested (indirectly) in the sources above.

---

