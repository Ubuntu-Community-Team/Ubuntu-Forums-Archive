---
title: "Java - getting NFL scores"
date: 2009-12-21
forum: Programming Talk
---

### Post by travmanx on 2009-12-21
Is there an open-source way (in Java please), to read an NFL score tracker site (ESPN, Yahoo, ect) and gather a certain set of text (score).

Or even just a pointer on how to do this. I am completely baffled on where to start. I just want to put a window that displays scores up underneath username (top right corner) which is the easy part :P.

Thank you in advanced.

---

### Post by andrewc6l on 2009-12-21
The easy (and brittle) way to do this is to parse the results out of an HTML page. Create a URL for your page, and send it openStream(). Example code is here:
[http://www.davidreilly.com/java/java_network_programming/#2.3](http://www.davidreilly.com/java/java_network_programming/#2.3)

Once you have the page in a String, you can use the regular String/regex tools to get the values out.

This approach is bad because if the HTML changes, you'll probably have to change your code. A better choice would be to find somewhere that served the values you want in XML - but for certain classes of data (such as sports scores, where $ is involved), that's uncommon.

---

### Post by Can+~ on 2009-12-21
Finding an RSS feed could prove more useful.

---

### Post by jobo3208 on 2009-12-21
I once tried to do something like this: a program to automatically tally fantasy football scores. I used the HTML approach. (I didn't know any better.) It took me a long time before I finally had something that would parse all 50-something stats. Then, as I was nearing completion, NFL.com had a huge UI overhaul. All the code became worthless, haha. Also, Yahoo fantasy sports started doing free real-time scoring. So I abandoned the project.

So, anyway, avoid HTML if you can. As for better-formatted alternatives, I don't know what's out there. I do know that there are companies that charge for such data, so I have to wonder if there are any free alternatives...

But I agree with the previous post -- an RSS feed sounds like a good place to start.

---

