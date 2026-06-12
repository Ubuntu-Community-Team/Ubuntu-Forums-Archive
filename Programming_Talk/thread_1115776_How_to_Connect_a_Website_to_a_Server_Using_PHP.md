---
title: "How to Connect a Website to a Server Using PHP?"
date: 2009-04-04
forum: Programming Talk
---

### Post by Penguin Guy on 2009-04-04
I know very little about HTML or PHP or Servers, so can someone give me a very basic idea what I should do to get a website on a server to connect to another server.

I want the website to connect and download data at 23:00 - 8:00 (preferably at midnight). The data must be stored for use during the day. The website should check the server for updates every night. It would also be nice to have a bit of background information on how servers work.

---

### Post by shadow_code on 2009-04-04
Well I guess you'd have to figure out:

[LIST]
[*]What format the data is in
[*]Is the server publicly available (or in the local network)
[/LIST]
The easiest way would probably be to serve the data over the Web (from the server) and then PHP could easily save this to a database.

---

### Post by slavik on 2009-04-04
> **Penguin Guy said:**
> I know very little about HTML or PHP or Servers, so can someone give me a very basic idea what I should do to get a website to connect to a server.

I want the website to connect and download data at 23:00 - 8:00 (preferably at midnight). The data must be stored for use during the day. The website should check the server for updates every night. It would also be nice to have a bit of background information on how servers work.
please clarify on what you are trying to complish.

---

### Post by Penguin Guy on 2009-04-05
The server requires a password and the format is XML. I'm mainly interested in getting connected with the server rather than the reading XML part.

---

### Post by shadow_code on 2009-04-05
Is the server in the same local network as the Web Server (the website)? Otherwise it will need to be accessible from the Internet (it's own IP etc).

---

### Post by Penguin Guy on 2009-04-05
No, it is not local. Yes, it is acessable from the internet with a password.

---

### Post by cabalas on 2009-04-05
How do they make the data available, you say it needs a password but what protocol are they using http, ftp, etc?

---

### Post by samjh on 2009-04-05
> **Penguin Guy said:**
> I know very little about HTML or PHP or Servers, so can someone give me a very basic idea what I should do to get a website to connect to a server.

I want the website to connect and download data at 23:00 - 8:00 (preferably at midnight). The data must be stored for use during the day. The website should check the server for updates every night. It would also be nice to have a bit of background information on how servers work.

???

Your request doesn't really make sense.  A "website" doesn't connect to a server, because a website resides on the server.  A user's web browser connects to a server and renders the website served by that server in the browser window.

If you want the server which hosts a website to connect to a different server and download data, then you can accomplish that using a [cron]("http://en.wikipedia.org/wiki/Cron") job and [bash]("http://en.wikipedia.org/wiki/Bash") scripts (if the server is Linux).

---

### Post by Penguin Guy on 2009-04-06
Yes I want the website to connect to *another* server, and it is using http.

---

### Post by cabalas on 2009-04-06
This doesn't really seem like the sort of thing a webpage should be doing, if I was you I would just set up a cron job and use wget/curl to grab the file(s).

---

### Post by Penguin Guy on 2009-04-06
Ok, I'll take you guys advice and just forget it. Thanks for helping anyway.

---

