---
title: "Linux, Windows and Linger - TCP/IP"
date: 2011-09-26
forum: Programming Talk
---

### Post by Blutkoete on 2011-09-26
Hello!

I ran into a mysterious problem lately with one device re-transmitting a TCP packet *after* the connection was reset by the receiver device.

I'm absolutely no expert on the matter, but while googling through the net and books I found a small difference in the way Linux and Windows appear to handle *lingering* that might be the cause of my problem:

[Source A]("http://msdn.microsoft.com/en-us/library/ms739165%28v=VS.85%29.aspx") states that Windows discards the queue of the socket and returns control to the caller when **l_onoff** is **0**. Fine. Two Linux/Unix sources I found ([here]("http://developerweb.net/viewtopic.php?id=2982") and [in German] [here]("http://books.google.de/books?id=dofKNkyanLYC&pg=PA743&lpg=PA743&dq=%22l_onoff%22+Linux&source=bl&ots=d8wHzx08vs&sig=RyQNQb2vlcypbIaSCVEgAqGNM4Q&hl=de&ei=C4p8TrzYDMid0QWAufEK&sa=X&oi=book_result&ct=result&resnum=1&ved=0CCAQ6AEwAA#v=onepage&q&f=false"), page 743 at the bottom) state that Linux discards the queue if **l_onoff** is **1** and **l_linger** (the time to linger) is **0**. For **l_onoff** = **0** the two sources say that control is returned to the caller, but the socket is closed *after* the queue is transmitted.

Is that correct? I found Linux forums as well where people state that Linux will discard the queue if you set **l_onoff** to **0**, so I'm confused.

What's right and what is wrong?

The faulty device has **l_onoff** set to **0** with Linux, and so might send the already queued re-transmission even after the controlling program thinks it has closed the socket.

Thank you very much, and sorry that I deal with powers at the moment that I don't understand,

Blutkoete

---

### Post by karlson on 2011-09-26
> **Blutkoete said:**
> Hello!

I ran into a mysterious problem lately with one device re-transmitting a TCP packet *after* the connection was reset by the receiver device.

I'm absolutely no expert on the matter, but while googling through the net and books I found a small difference in the way Linux and Windows appear to handle *lingering* that might be the cause of my problem:

[Source A]("http://msdn.microsoft.com/en-us/library/ms739165%28v=VS.85%29.aspx") states that Windows discards the queue of the socket and returns control to the caller when **l_onoff** is **0**. Fine. Two Linux/Unix sources I found ([here]("http://developerweb.net/viewtopic.php?id=2982") and [in German] [here]("http://books.google.de/books?id=dofKNkyanLYC&pg=PA743&lpg=PA743&dq=%22l_onoff%22+Linux&source=bl&ots=d8wHzx08vs&sig=RyQNQb2vlcypbIaSCVEgAqGNM4Q&hl=de&ei=C4p8TrzYDMid0QWAufEK&sa=X&oi=book_result&ct=result&resnum=1&ved=0CCAQ6AEwAA#v=onepage&q&f=false"), page 743 at the bottom) state that Linux discards the queue if **l_onoff** is **1** and **l_linger** (the time to linger) is **0**. For **l_onoff** = **0** the two sources say that control is returned to the caller, but the socket is closed *after* the queue is transmitted.

Is that correct? I found Linux forums as well where people state that Linux will discard the queue if you set **l_onoff** to **0**, so I'm confused.

What's right and what is wrong?

The faulty device has **l_onoff** set to **0** with Linux, and so might send the already queued re-transmission even after the controlling program thinks it has closed the socket.

Thank you very much, and sorry that I deal with powers at the moment that I don't understand,

Blutkoete

I think it's time to download and read the source code. :)

---

