---
title: "Generic TCP/IP Server platform"
date: 2009-06-08
forum: Programming Talk
---

### Post by CaptainPanick on 2009-06-08
Hi guys,

I am fairly experienced in multi-threaded development within multiple programming languages. I find myself constantly re-inventing the wheel when it comes to server development though and I've just about had enough of it. I often work in the telemetry field where multiple devices communicate to either some desktop application or server. Many of these devices still uses propriety protocols (both binary and text) to communicate to the software. With bolt-on TCP/IP modules that can be integrated into existing circuits more and more of these devices now becomes TCP/IP compatible but still uses the old propriety protocols.

My question is this: are you aware of any generic TCP/IP server platforms/frameworks that one can use to construct your own protocol handler that can then eventually interface with these devices over TCP? I don't care which programming language it is as long as it is multi-platform capable. If it is not, then it should rather run on linux than on Windows. I've looked at a number of "Application Servers" but many of these seems far to complex and heavy for what I need and also seems to support only protocols designed for web applications.

If you reckon that something like JBoss could be suitable for what I'm looking for then so be it, I would take another look at it. There are a number of small sourceforge projects which on the surface looks like it could do the trick but many of them became stagnant over the years as larger more complex Application Servers started taking over.

Your input would be greatly appreciated!

---

### Post by CptPicard on 2009-06-08
How about... 

[http://twistedmatrix.com/trac/](http://twistedmatrix.com/trac/)

---

### Post by CaptainPanick on 2009-06-09
> **CptPicard said:**
> How about... 

[http://twistedmatrix.com/trac/](http://twistedmatrix.com/trac/)

Thank you CptPicard, I just glimpsed over the website and it definitely looks good. I noticed QuickServer but it's development seemed to have been discontinued in 2006. :P

---

