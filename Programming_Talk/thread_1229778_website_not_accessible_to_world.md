---
title: "website not accessible to world"
date: 2009-08-02
forum: Programming Talk
---

### Post by sailingboarder on 2009-08-02
hello,
i have set up a wordpress blog on my main machine as a quick way to get started with a web presence. however, at my college, student machines are not accessible to the outside world. i do, however, have webspace on the cs department webservers. i am looking for a way to forward requests to my machine through a webpage on the cs servers, using something similar to frames.
however, all requests for the blog must come from the cs server, and not the client's browers
i have already tried frames, which worked correct from within the college network, but not from without
does anyone have any other suggestions?

---

### Post by .Maleficus. on 2009-08-02
So what you're basically trying to do is use your CS department's server as a router, correct?  Ie, all requests on port 80 to that machine will forward to your computer?  It's going to be a bit work of to do, if possible at all.  Google "computer as router" and take a look at some of the results.  If you have space on the server already though, I'd just FTP the site to the server.  It'll save quite a few headaches.

---

### Post by sailingboarder on 2009-08-02
basicaly, the cs sys admin won't let me run wordpress("it's not secure enough"), thus I am running it on my own system instead. I want to have a page that is hosted on the cs server than can act a a virtual client, requesting pages from my machine and serving them to the user.
Currently,
[PHP]
<?php
readfile('http://mymachine/');
?>
[/PHP]
works for the main page, but then none of the links work

---

