---
title: "Mono and Unix Domain Socket"
date: 2012-06-04
forum: Programming Talk
---

### Post by DaveOInCO on 2012-06-04
I am new to Ubuntu and am building a single program that works equally well under Windows and Linux using .Net/Win and Mono/Linux.  The challenge that I'm trying to solve is how to open LIRC (which as I understand it uses a Unix Domain Socket by default) using namespaces that are available on both platforms and therefore avoid having two different versions of the program. 

I know that I can change LIRC to listen on TCP 8765 but I'd like to avoid that option if at all possible.  If was to use this option, the code would be

```
Me.mClient = New System.Net.Sockets.TcpClient("localhost",8765)
```  

  So does anyone have any suggestions on how to revise this to open a 'Unix Domain Port" ?  Do you open /usr/share/lirc as a filestream?    

Thanks

---

