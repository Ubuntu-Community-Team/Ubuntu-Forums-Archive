---
title: "Use Java to replace PHP on server?"
date: 2009-06-27
forum: Programming Talk
---

### Post by secondstage on 2009-06-27
In my best attempts to speed up the response times of my web server, I am looking to rewrite the php pages in Java, and compile them. I am unsure if it is possible to even do this though considering the number of features of PHP, and whether or not they are available in Java. Generally the script is static, but the content is what is so dynamic, so I think that using compiled programs for each page would be faster than having the script be compiled on each new request or each page.

Upgrading network bandwidth or server components is not an option for me, as I do not control the network, and do not have the money to buy a newer server, or better components.

Thank you in advance for any possible answer, or idea you may have,
--Secondstage.

---

### Post by Mirge on 2009-06-27
Might consider trying to optimize apache and PHP before switching languages. What specifically is performing so poorly? Got a URL?

---

### Post by wojox on 2009-06-27
Hey secondstage,

I'd personally stick with php scripts for speed. Are you running php as a module or cgi? I've found Java applications to be a little bloated for web design. You could always look into JavaScripting.

---

### Post by Mirge on 2009-06-27
> **wojox said:**
> Hey secondstage,

I'd personally stick with php scripts for speed. Are you running php as a module or cgi? I've found Java applications to be a little bloated for web design. You could always look into JavaScripting.

Java and Javascript are very different things :)

---

### Post by CptPicard on 2009-06-27
Well, there is a huge number of different kinds of web application frameworks for Java out there, but the learning curve in the Java web apps space has always been unfortunately rather steep... you may want to look into JSPs to get yourself started if you really need to switch to Java, which I kind of doubt... :)

---

### Post by Reiger on 2009-06-27
I doubt it will work. PHP is fairly efficient at what it does especially when you consider that it generates little overhead in terms of RAM etc. Whenever I use Java I always feel Java is aimed at much more complex projects by design: and generating a web page simply is not that a complex project.

(Or rather: I find Java is too much of a pain to be of much use if you can simplify your code considerably by not using Java; which is mainly true for smaller projects where the language pretty much dictates how simple a solution will be.)

Quick question: you don't happen to be a fairly competent Java developer who picked up PHP and then proceeded to write PHP code as if it were Java (with an unhealthy OO-constricted-world-view)? Code sort of works best in a particular environment when it is `idiomatic': by which I mean that Python, PHP, Perl and Java all have distinct code design-styles which have been picked up (or were outright built in from the starts) by the people who optimized their interpreters/VMs for it. (And it proves time and again near impossible to beat the language implementations at their own game [providing an efficient language implementation].)

---

### Post by secondstage on 2009-06-27
@Mirge: Optimizing Apache2 would be an option most defiantly, but I am unaware of how to even go about that. I like to believe that my code is efficient, but I'm sure that there are many things that could be improved upon (like MySQL queries, and the such). Do you have any links to sites that would help me on these things, or books to read? Nothing specific is poor in speed, but overall, with how simple the queries are and how simple the page is, I can't help but to think that it could be a bit faster. No, I'm working on a project that can't really be put out public yet, sorry.

@CptPicard: I am not worried about the learning curve. This year will be the first that I will have formal education on computers, and programming, and with a couple things that I have done, the teacher will practically let me sleep in his Java class.

@Reiger: At this point, I am not "competent" in Java, but hopefully soon will be.

All in all, I think that my code could just use some optimization, and maybe Apache2 itself could be helped. Does anyone have sites, books, or other references that would aid in this process? (Note that the server is running Ubuntu, and if there is anything about that that could be hindering speed, or could be worked on, I would love to hear about it)

---

### Post by Mirge on 2009-06-27
> **secondstage said:**
> @Mirge: Optimizing Apache2 would be an option most defiantly, but I am unaware of how to even go about that. I like to believe that my code is efficient, but I'm sure that there are many things that could be improved upon (like MySQL queries, and the such). Do you have any links to sites that would help me on these things, or books to read? Nothing specific is poor in speed, but overall, with how simple the queries are and how simple the page is, I can't help but to think that it could be a bit faster. No, I'm working on a project that can't really be put out public yet, sorry.

@CptPicard: I am not worried about the learning curve. This year will be the first that I will have formal education on computers, and programming, and with a couple things that I have done, the teacher will practically let me sleep in his Java class.

@Reiger: At this point, I am not "competent" in Java, but hopefully soon will be.

All in all, I think that my code could just use some optimization, and maybe Apache2 itself could be helped. Does anyone have sites, books, or other references that would aid in this process? (Note that the server is running Ubuntu, and if there is anything about that that could be hindering speed, or could be worked on, I would love to hear about it)

If you're using MySQL and it is being sluggish, make sure you have proper INDEX's on your tables that get read a lot.

Apache KeepAlives can speed up content delivery as well.

---

### Post by secondstage on 2009-06-27
Would Apache KeepAlive speed up AJAX requests, or any other request for that matter?

---

### Post by secondstage on 2009-06-27
Better Question: How would KeepAlive speed up requests?

---

### Post by Mirge on 2009-06-27
Good way to tell is to try it. A way to see it actually working is using Firebug's network tab. Load a page with decent content, images, etc. You'll notice a connection for each item that it has to download (CSS, JS, images, etc). KeepAlives let you use fewer connections to grab all of the content, which can speed up the page "loading" process quite a bit.

---

### Post by secondstage on 2009-06-27
In looking at the Apache2 configuration file, KeepAlive is already On, and set for 15 seconds, and 100 AliveRequests. I do not know if that is the best to say that so here is the conf file lines.

```
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 15
```

Are those good settings for a not-so-media-rich site?

---

### Post by Reiger on 2009-06-27
> **secondstage said:**
> Better Question: How would KeepAlive speed up requests?

Normally, for each TCP connection you must first do a 3-way handshake. (This is a process whereby both sides affirm they have a point-to-point connection.) 

This is done as follows:
Client: Hi, can I have connection? -> Server
Server: Yes/No you can (not). [Confirms client request as being received] -> Client
Client: If yes: bring it on. If no: tough luck. [Confirms Server response as being received]-> Server.
Server: starts transmitting data stream. 

As you may have notice there are 3 very small read/write requests towards the Internet, and Internet being the sluggish medium that it is (it may take minutes for a response to be received, if at all, on a dial up connection...) this generates considerable overhead.

Now imagine doing this for every single referenced external `piece of data' in a document (e.g. pictures, css files, js files and so on). 

KeepAlive is a higher level feature of the HTTP protocol which basically instructs the underlying TCP stack to re-use the same connection, thereby avoiding the overhead of additional 3-way handshakes.

This benefit can be reaped in parallel over multiple KeepAlive connections, especially if your client has a clear strategy of what content to request first and what next (browsers have).

---

### Post by secondstage on 2009-06-27
Ok, sounds like a pretty good idea to have it on then. 

Are there any other server side changes that could be made to speed up connection or response time?

In using firebug's network monitor, I see that most of the time is used queuing. Is this a result of a slow handshake, or slow up, or down speed?

---

### Post by CptPicard on 2009-06-27
I don't know what your site is actually doing, but as chances are that you have a database -- are you running some heavy queries by any chance?

---

### Post by secondstage on 2009-06-27
I wouldn't call them heavy by any sense. 

95% of the time, they are returning less than 10 rows, from kind-of-well indexed tables. No joins or anything complex. Just using SELECT, DELETE and UPDATE most of the time. I think that I understand indexes pretty well, but let me just get this straight: Put an index on the columns that are going to be used to search, or narrow the result most often, correct?

---

### Post by froggyswamp on 2009-06-27
Switching to Java only makes sense when having huge traffic (or when you know Java better than PHP), otherwise you just won't notice any difference, if so, just try to optimize the SQL queries, usually optimizing the database queries and the caching strategy is what people go for when trying to optimize a given site.
Also, there's a full fledged video discussion on Google video called "Even faster Websites":
[http://code.google.com/events/io/sessions/EvenFasterWebsites.html](http://code.google.com/events/io/sessions/EvenFasterWebsites.html)

---

### Post by pokerbirch on 2009-06-27
Hmmmm, sounds more like the server itself is running slow and NOT your code. Doesn't sound like you're putting much load on it, so even "sloppy" code would go unnoticed. Is the server on a shared host or something?

---

### Post by Mirge on 2009-06-27
Just as an example if you're allowed to specify, how many total rows of data are in the table that you're querying? The table (or tables) that are being slow.

---

### Post by soltanis on 2009-06-27
> **secondstage said:**
> I wouldn't call them heavy by any sense. 

95% of the time, they are returning less than 10 rows, from kind-of-well indexed tables. No joins or anything complex. Just using SELECT, DELETE and UPDATE most of the time. I think that I understand indexes pretty well, but let me just get this straight: Put an index on the columns that are going to be used to search, or narrow the result most often, correct?

1) Are you precompiling your SQL statements (your app may be spending time compiling statements that don't change)?

2) Look into a different storage back-end. Read online at 
[http://dev.mysql.com/doc/refman/5.1/en/storage-engines.html](http://dev.mysql.com/doc/refman/5.1/en/storage-engines.html)
About different storage engines and their trade-offs.

3) PHP can definitely be sped up (poking around the php website gives you some tips on it), and its better to improve existing software than to undertake a complete rewrite of it, especially in something complex like Java which will probably not offer you that much in the way of performance benefit anyway.

---

### Post by secondstage on 2009-06-28
@froggyswamp: I will definitely take the time to look into that.

@pokerbirch: The server itself is slow. I am an independent freelancer (I guess is what you could call it, but I just do this for kicks), so money isn't really what I've got right now especially for something that doesn't return anything yet. The server is hosted in my basement on a residential ADSL line from AT&T with 6mb/s down, and about 320kb/s upload. THe server itself is comprised of an AMD Duron 1.2GHz, with 256MB of pc100 RAM, and two 40 GB HDDs. And that is the exact reason I am trying to find anyway to optimize the site, and maximize speed.

@Mirge: Right now the row count is about 100, but as the site grows, and more content is added I aim to have 1000+ rows in that table. The rows themselves can be broken down into "categories" or "sections". Once that table grows, would it be beneficial to break down the "categories" into individual tables?

@soltanis: 1.) Most of the statements are dynamic, but some are just asking for the top 10 or 20 based on a time column. So just for example's sake: ```
SELECT species, commonName FROM animals WHERE family='dog' ORDER BY time DESC LIMIT 20
``` Where time is the time in which the species was discovered, and family could be considered a category, but the categories would a lot more elements then the average family.

2.) That's a will-do.

3.) I will look around, and hopefully find some things not seen before.

Thank you, all of you for helping with this. Most of these sites, and settings I haven't taken the time to learn about, because I just overlooked them prior.
Thank You again.

---

