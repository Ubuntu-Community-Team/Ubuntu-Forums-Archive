---
title: "socket programming: creating multiple streams"
date: 2018-05-11
forum: Programming Talk
---

### Post by vandanachadha on 2018-05-11
I am working on an app to start multiple streams in listener and  caller modes after creating sockets. Right now, if I start one stream,  the process kind of hangs because the stream is waiting for data. So  this is clear to me that I need to start the stream in an async kind of  process, so that the rest of the app keeps working.
  Do I start the stream in:
  
[LIST]
[*]separate threads 
[*]separate processes using fork 
[*]also read about select, will that work 
[*]Does blocking/non-blocking sockets solve this problem. 
[/LIST]
  This app is being done in c++.

---

### Post by TheFu on 2018-05-12
Either a separate thread or different process.  On Unix systems, a separate process isn't a big deal.  On Windows, you'd definitely want a separate thread due to the huge overhead for every process on that platform.

I should say, that last time I did anything like this was in the 90s, so newer methods might exist of which I'm unawares.  Any updated Advanced Socket programming book should show all the options with sample code.

---

