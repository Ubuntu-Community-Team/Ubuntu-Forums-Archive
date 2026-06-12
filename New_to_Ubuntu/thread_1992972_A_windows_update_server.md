---
title: "A windows update server"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2012-06-01
Hi guys.
I've recently changed to a capped internet package so I'm looking for ways to reduce my bandwidth usage.

I want to setup a windows update server on my network so the server downloads the updates and then all my home PCs (and the ones I do for work) will download the updates from the server, vastly reducing my bandwidth requirements.

I'm told I can do this using any of the server variants of windows but as this is a cost saving exercise then paying for a server licence seems silly.

Is it possible to do this with a linux server. I already have a home web server running Ubuntu 11.10,

If it is possible does anyone have any good material to recommend to get me started?

---

### Post by Cheesemill on 2012-06-01
It's not possible to set up a WSUS server as such, but instead you could look into installing Squid as a web cache so that all of the Windows update download packages are only downloaded once.

---

