---
title: "http header"
date: 2007-09-24
forum: Programming Talk
---

### Post by nishanthaMe on 2007-09-24
I want send http head request to a file using a c programe.can anyone have an idea?

---

### Post by aks44 on 2007-09-24
0. open a client socket & connect to the server,
1. send a HEAD request according to [RFC 1945 (HTTP 1.0)]("http://www.faqs.org/rfcs/rfc1945.html") or [RFC 2616 (HTTP 1.1)]("http://www.faqs.org/rfcs/rfc2616.html") depending on what protocol version you plan to support (and what the server supports),
2. parse the answer to extract the info you need.

BTW you don't send a HEAD request to a file, but to a HTTP server...

---

