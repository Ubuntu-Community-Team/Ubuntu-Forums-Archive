---
title: "Distributed computing / Linux search"
date: 2006-01-23
forum: Programming Talk
---

### Post by Cousindaddy on 2006-01-23
In light of the recent news of the US government subpoenaing search engine records, I was wondering if the Linux community could create it's own search engine.  Couldn't distributed computing be used to crawl and catalog the web?  If so, we could all enjoy a rubust search engine that wouldn't store the searcher's information.

---

### Post by engla on 2006-01-23
Even though Viro talks about some limitations, there is no reason a free search engine can't be made. There must already be some out there, but I don't know about any big projects to make one that really is big and really works (the way google etc works)

As a Wikipedian I know but don't really keep track of Wikia, some kind of free search engine. [ [http://search.wikicities.com/wiki/Search](http://search.wikicities.com/wiki/Search) ] I have no idea how they are doing and what you really can use it for, but why not start there and see what they mean with the concept of a "free and open source search engine"

Edit: Is something seriously broken? I read two posts, then posted my own.. now I see this as post #2 and the ones I read before I posted as #1 and #3...

---

### Post by Viro on 2006-01-23
I take it you mean something like Kazaa, in the way searches are carried out. I can see a few reasons why this isn't going to be too possible, namely speed. Google crawls the web, and caches the results it finds. When you execute a query, see how fast the results are returned. Then, marvel at the amount of results that were returned. In order to have such speedy results, you need a cluster like what Google has. Having a loose network of computers spread around the globe may work, but it will be as slow as molasses. 

Another problem is the repeatability of the results. When you search for a particular term, you always get the same result, until it is updated by Google. With P2P searches, you cannot guarantee that you will always get the same results. Imagine what happens when the information you want is on the computer of some guy who has just decided to shut it down for the night? To alleviate this problem, we're back to square one. We need a centralized server (or cluster of servers).

Distributed computing has it's uses, but you need to remember that all the tasks that are done via distributed computing aren't time sensitive. You don't have someone waiting impatiently at the other end while your computer processes the latest Seti/Folding/Climateprediction@HOME work unit.

---

### Post by Viro on 2006-01-24
The problem isn't so much a 'free' search engine. Such a thing can easily be done. After all, Yahoo started out of the dorm of its founders so you can easily host a search engine on your own home PC.

The problem is, that the web has grown immensely, since 1995. It is no longer feasible to run such a search engine on a single computer, and you will need a high speed cluster, like what the major search engines have. That will cost money, and is out of the reach of most volunteers. Distributed computing won't work, as I have detailed in my previous post. 

The problem with existing search engines if I understand Cousindaddy correctly, is that they log your searches, meaning if someone wanted to they could get a history of the searches you performed. This is a big no-no for privacy watchers, and hence the suggestion of creating a loosely knit distributed network of computers thatt act as search engines. Anything centralized will not do either, for this provides a good target for lawsuits and subpoenas ;). So the wiki stuff is out of the question.

---

### Post by Cousindaddy on 2006-01-24
I was thinking more in terms of distributed computers crawling the web and compiling a catalogue which could then be accessed by others.  There would have to be a central, organizing body to direct each of the distributed spiders.  The DMOZ might be a good place to start with the distributed computers building upon that.  The Linux search software would have the distributed computing feature coded into it - i.e., to use the search software, you have to agree to allow your computer to crawl the web.
I'm not a programmer, so I really don't know if something like this could ever work.  But if it could, I would be willing to allow my computer to participate.

---

### Post by ruik on 2006-09-19
I know this is a bit old but have you checked this: [www.majestic12.co.uk](www.majestic12.co.uk)?

---

