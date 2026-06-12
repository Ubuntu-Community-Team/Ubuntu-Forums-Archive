---
title: "Pythons twisted?"
date: 2008-02-04
forum: Programming Talk
---

### Post by Wybiral on 2008-02-04
I'm trying to familiarize myself with the twisted library so I can incorporate networking into some of my applications. I followed the tutorials on their site and found it simple to setup a server/client for event-based communication. The problem came when I wanted to write a client program that has its own main loop... Twisted uses its reactors main loop (initiated by reactor.run)

I assume I could just start a thread for either my programs loop and twisted and somehow mutex the events so they collect in my main loop, but I was wondering if there were an easier (or more traditional) way to do this in twisted. My main loop is also very time-sensitive so it has to manage its own intervals.

Maybe twisted is overkill for my needs, if so, what's the best way to run a simple client for polling and sending messages over a connection (one that will work with my design)?

EDIT:

Wow, I just realized how easy this would be to use the socket module. If I can't find a simple enough solution, that's what I'll do. I'm still open for suggestion though.

---

### Post by ghostdog74 on 2008-02-04
Maybe you can see[ this ]("http://www.woodpecker.org.cn/obp/pages.wiki.woodpecker/TwistedBook/attachments/")for inspiration.

---

### Post by Wybiral on 2008-02-04
> **ghostdog74 said:**
>  ... 

Thanks, that looks like a good book. Unfortunately it doesn't look like it covers much of the asynchronous features of twisted, but regardless it looks like a must-have for twisted development.

---

