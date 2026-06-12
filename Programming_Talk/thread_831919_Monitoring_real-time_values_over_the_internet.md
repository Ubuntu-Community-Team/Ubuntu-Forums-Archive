---
title: "Monitoring real-time values over the internet"
date: 2008-06-17
forum: Programming Talk
---

### Post by desheffer on 2008-06-17
I was wondering if anyone had ever developed a web application that retrieved close to real-time values from a server over the internet. The problem I am facing is that the values might change multiple times in one second and I would like to get these updates as quickly as possible. I have considered an Ajax approach where the client polls the server once a second to receive an XML file of all values since the last update. However, this seems like a lot of overhead that would really pound the server. I am afraid the only way to do this might be to develop my own client and server applications that maintain a connection to each other, but I would like to know if there are any easier or existing ways first.

Does anyone have any ideas or suggestions?

---

### Post by pmasiar on 2008-06-17
Looks like stock trading info?

Internet is not reliable enough to provide this, that's why big boys use proprietary data services like Bloomberg.

or is it a Online MUD?

---

### Post by desheffer on 2008-06-17
It's actually particle accelerator data (like magnet and faraday cup values), although stock trading values would probably be quite similar.

---

### Post by slavik on 2008-06-17
anything where a client issues a request will not be real-time. for realtime, you'd need a custom client and a server that would push data to the client along with a timestamp of the reading/information ...

---

### Post by desheffer on 2008-06-17
I guess my question was if there was anything out there already that could maintain a persistent connection so that I wouldn't have to write my own from scratch. I know I could do this by writing my own client and server, but I would like to avoid this if possible. Obviously this would be very difficult (impossible?) using Apache and PHP. Thank you for your help though!

---

### Post by stroyan on 2008-06-17
You could try using a continuously open http connection with
"Content-type: multipart/x-mixed-replace" as discussed in this
old document-
[http://wp.netscape.com/assist/net_sites/pushpull.html](http://wp.netscape.com/assist/net_sites/pushpull.html)

Unfortunately, it seems that Internet Explorer never picked up
support for that feature, even through IE7.
[http://ilia.ws/archives/145-Network-Scanning-with-HTTP-without-JavaScript.html](http://ilia.ws/archives/145-Network-Scanning-with-HTTP-without-JavaScript.html)

---

### Post by CptPicard on 2008-06-17
You might find this helpful:

[http://en.wikipedia.org/wiki/Comet_(programming](http://en.wikipedia.org/wiki/Comet_(programming))

---

### Post by tiachopvutru on 2008-06-17
> **CptPicard said:**
> You might find this helpful:

[http://en.wikipedia.org/wiki/Comet_(programming](http://en.wikipedia.org/wiki/Comet_(programming))

the link misses the closing parenthesis.

---

### Post by desheffer on 2008-06-18
Comet looks to be exactly what I need. I hadn't realized there was a name for that technique and that is a very good list of open source implimentations. Thank you so much!

---

