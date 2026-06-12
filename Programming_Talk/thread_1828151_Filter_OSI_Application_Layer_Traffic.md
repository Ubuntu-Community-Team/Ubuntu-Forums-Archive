---
title: "Filter OSI Application Layer Traffic"
date: 2011-08-18
forum: Programming Talk
---

### Post by Dacto on 2011-08-18
I'd like to create an application layer network traffic filter to filter application layer protocols like http, ftp, etc.
However my search regarding information about programming with the OSI and how to "tap" into a certain layer has been fruitless.

Before embarking on this adventure I thought that being an open source OS, it would be easier to find information, code example or other open source projects that accomplish what I'd like to do. This is not the case.

It seems finding information on Window's Winsock2 LSP was easier, but now I want to code the same thing for Linux.

Can anyone shed some light or resources on this topic?

Thanks

---

### Post by juancarlospaco on 2011-08-18
Search for LibPCap

---

### Post by Dacto on 2011-08-18
> **juancarlospaco said:**
> Search for LibPCap

I'm not looking for a packet capture library or packet analyzer.
In my reading on how the winsock2 lsp was designed, they based it on a Linux equivalent. This isnt packet capture. At application level, you're not required to mess with network traffic packets, you have the actual http (for example) protocol there.

Application layer firewalls can do this.

I'm just not sure how to "tap" into that layer on Linux.

---

### Post by The Cog on 2011-08-18
I don't think what you are asking for is possible. The layers are logical only. For instance, a web server that talks HTTP will generally do its own decoding of the TCP stream, using its own HTTP library routines. The only possible layer outside of the program itself is at the socket library layer. You could possibly replace the system socket library with your own library that intercepts socket streams or datagrams, but any understanding of higher layer protocols than that will have to be built into your filtering software.

---

### Post by juancarlospaco on 2011-08-19
&#8593; What he say, computers only understand 0 and 1, others are just representational smoke and mirrors...

---

