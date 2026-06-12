---
title: "Understanding Apache httpd (apache server)"
date: 2014-07-23
forum: Programming Talk
---

### Post by IAMTubby on 2014-07-23
Hello,
 I went through a few resources on what exactly apache httpd/apache server (which people informally refer to as apache) does.

_My understanding so far is that,_
Suppose I'm requesting for a page at ubuntuforums.org, apache httpd is just a daemon running on the computer(server) where the ubuntuforums.org website is hosted. When the daemon detects a request from a client(browser) from a user anywhere in the world, it passes the query string, say, [http://ubuntuforums.org/newthread.php/something-something](http://ubuntuforums.org/newthread.php/something-something) to the page at newthread.php and that takes it onwards from there.

Had there been no apache httpd, each website on the internet would have to implement a daemon code to see if any user from around the world is requesting a page from that site - which is not possible.

So basically apache httpd calls a website/webpage into action _only when it is required by someone_ and with the correct parameters from the query string.

Please let me know your thoughts.

Thanks.

---

### Post by SeijiSensei on 2014-07-23
Like most every Internet service, HTTP uses a client/server model.  Clients send requests to servers which process the request and, usually, send a reply.  

One thing I would add to your comment is that Apache (and other webserver software) looks at the hostname specified in the request URL and uses it to determine which information to return.  This enables people to run multiple "virtual hosts" on a single IP address.  My web server answers requests for a half-dozen or so different domain names returning different content to browsers depending on the request URL.

---

### Post by IAMTubby on 2014-07-23
> **SeijiSensei said:**
> 
One thing I would add to your comment is that Apache (and other webserver software) looks at the hostname specified in the request URL and uses it to determine which information to return.  This enables people to run multiple "virtual hosts" on a single IP address.  My web server answers requests for a half-dozen or so different domain names returning different content to browsers depending on the request URL.
Thanks SeijiSensei, that was useful.

---

### Post by CptPicard on 2014-07-24
> **IAMTubby said:**
> Suppose I'm requesting for a page at ubuntuforums.org, apache httpd is just a daemon running on the computer(server) where the ubuntuforums.org website is hosted. When the daemon detects a request from a client(browser) from a user anywhere in the world, it passes the query string, say, [http://ubuntuforums.org/newthread.php/something-something](http://ubuntuforums.org/newthread.php/something-something) to the page at newthread.php and that takes it onwards from there.

You're assuming that there's a PHP interpreter running "behind" Apache. This is often the case, often not. At its most basic, HTML pages are plain static text and that's all Apache was built to serve to begin with. It can be the HTTP protocol "front" for arbitrary processing though.

> 
Had there been no apache httpd, each website on the internet would have to implement a daemon code to see if any user from around the world is requesting a page from that site - which is not possible.

Wow, you're thinking about this in too difficult terms. It's the client that actively calls to a server and that's it. :)

---

### Post by IAMTubby on 2014-07-25
> **CptPicard said:**
> Wow, you're thinking about this in too difficult terms. It's the client that actively calls to a server and that's it. :)
CptPicard, thank you so much for the reply, but what you just said above just tossed my understanding once again. Absolutely, it's the client that makes a request to a server, which means what I said earlier about each website having to implement a daemon code is wrong.

So what then is the function of Apache httpd? Why does it need to be running on the host where the website is hosted? I'm starting to feel why can't it just be done like,
"The browser(client) sends a request to the website and the website runs it's code for that page and returns with the html to be displayed back on the client."

I'm sorry for a blunt question, it's just that I always get confused when I hear the terms apache or web server etc.
But I'm sure I can read up once I get some pointers here.

Thanks.

---

### Post by CptPicard on 2014-07-25
> **IAMTubby said:**
> 
"The browser(client) sends a request to the website and the website runs it's code for that page and returns with the html to be displayed back on the client."

Ok, so... what process would respond to the client on the network socket? What would handle the HTTP protocol? What would check the query URL and map that to some server resource -- either a static page or some dynamic processing? What would handle other nice things to have, like SSL, proxying, URL rewriting, response compression, (basic) authentication and access control...

It is true that you can run things like Tomcat standalone as they have their own HTTP implementation, but especially for production environments, Apache is just way more robust.

---

### Post by IAMTubby on 2014-07-26
> **CptPicard said:**
> Ok, so... what process would respond to the client on the network socket? What would handle the HTTP protocol? What would check the query URL and map that to some server resource -- either a static page or some dynamic processing? What would handle other nice things to have, like SSL, proxying, URL rewriting, response compression, (basic) authentication and access control...
Thanks CptPicard, I'm getting the point.
But while I wasn't aware of all of the steps below, I was under the impression that at least some of them could have been done by the _browser_? Am I totally off?
[B]1. Respond to the client on the network socket 
2. Handling the HTTP protocol
3. Checking the query URL and mapping that to some server resource -- either a static page or some dynamic processing 
4. Handling SSL, proxying, URL rewriting, response compression, (basic) authentication and access control[/B]

> It is true that you can run things like Tomcat standalone as they have their own HTTP implementation, but especially for production environments, Apache is just way more robust.
Also isn't Tomcat( a servlet container basically) only for servlets and jsps, whereas Apache (httpd) for everything really?

---

### Post by CharlesA on 2014-07-26
The majority of what you list above is handled at the web server level. The browser is just the client. It will negotiate SSL and things like compression or encoding, but the server does most of the work.

---

### Post by IAMTubby on 2014-07-27
> **CharlesA said:**
> The majority of what you list above is handled at the web server level. The browser is just the client. It will negotiate SSL and things like compression or encoding, but the server does most of the work.
Thanks CharlesA, for now let me just tell myself that the **client(browser) + web server together** do all the network "stuff" and lays down the framework for html+server-side code to show it's effect. In time, I'll try and understand how much of this is done by the web server and how much by the web client(browser)

> **CptPicard said:**
> It's the client that actively calls to a server and that's it. :)
Thanks CptPicard, I'll understand more, the more I work on it.

Marking the thread as solved for now.

---

