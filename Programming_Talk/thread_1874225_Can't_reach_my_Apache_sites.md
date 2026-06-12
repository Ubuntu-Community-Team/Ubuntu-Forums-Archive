---
title: "Can't reach my Apache sites"
date: 2011-11-02
forum: Programming Talk
---

### Post by der_mythos on 2011-11-02
Hi there,

I am trying to get a local Apache server to run properly.

But suddenly I can't even reach the standart localhost site.

My ErrorLog looks like this:

```

[Wed Nov 02 20:57:41 2011] [notice] caught SIGTERM, shutting down
[Wed  Nov 02 20:57:42 2011] [notice] Apache/2.2.20 (Ubuntu)  PHP/5.3.6-13ubuntu3.2 with Suhosin-Patch configured -- resuming normal  operations

```


Actually don't got any Clue how to fix this. I disabled all my Sites but can't get a Connection here ...


Any Ideas?

---

### Post by karlson on 2011-11-02
> **der_mythos said:**
> Hi there,

I am trying to get a local Apache server to run properly.

But suddenly I can't even reach the standart localhost site.

My ErrorLog looks like this:

```

[Wed Nov 02 20:57:41 2011] [notice] caught SIGTERM, shutting down
[Wed  Nov 02 20:57:42 2011] [notice] Apache/2.2.20 (Ubuntu)  PHP/5.3.6-13ubuntu3.2 with Suhosin-Patch configured -- resuming normal  operations

```


Actually don't got any Clue how to fix this. I disabled all my Sites but can't get a Connection here ...


Any Ideas?

I don't think this belongs in this forum.

SIGTERM usually means that something is trying to stop Apache.  I'd start with cron.

---

### Post by der_mythos on 2011-11-02
Actually I can't believe this is a Cron, cause this appears every time I restart my Apache :(


Btw: looked it up and it seems that there are no crons for my user.

Any Ideas?



PS: if this is realy the wrong forum, could somebody move this please?

---

### Post by karlson on 2011-11-02
> **der_mythos said:**
> Actually I can't believe this is a Cron, cause this appears every time I restart my Apache :(


If you are restarting your Apache why is there the question about what is in the log?

> 
Btw: looked it up and it seems that there are no crons for my user.

Any Ideas?


If your question is really about why you can't access your localhost site I suggest you first try to telnet to the port apache is listening on on localhost and see if you can connect there.  Once connectivity is confirmed try "GET /" and see what happens.

---

### Post by der_mythos on 2011-11-02
> **karlson said:**
> If you are restarting your Apache why is there the question about what is in the log?



If your question is really about why you can't access your localhost site I suggest you first try to telnet to the port apache is listening on on localhost and see if you can connect there.  Once connectivity is confirmed try "GET /" and see what happens.


Thank you for your reply. Unfortunately i'm new to all this server stuff. Could you explain your post further more please :)

---

### Post by karlson on 2011-11-02
> **der_mythos said:**
> Thank you for your reply. Unfortunately i'm new to all this server stuff. Could you explain your post further more please :)

```

sudo netstat -apn | grep http

```
What's the result?
```

telnet localhost 80

```

Does it connect?  Does connection timeout?

If it does connect
```

GET /

```
What's the result?

---

### Post by der_mythos on 2011-11-03
Ok thank you :)


```

sudo netstat -apn | grep http
```

Gives me nothing. Here's an empty result.


Ok but I can connect via the Terminal and I get this result (that's what I'm looking for :) )

```

Connected to localhost.
Escape character is '^]'.
GET /
<html><body><h1>It works!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html>
Connection closed by foreign host.

```



Does anybody has a clue why I can't get this result in my browser?

---

### Post by der_mythos on 2011-11-04
No one?

---

### Post by gsmanners on 2011-11-04
Maybe you should try a different browser (like Midori).

---

