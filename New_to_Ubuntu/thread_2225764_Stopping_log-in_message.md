---
title: "Stopping log-in message"
date: 2014-05-23
forum: New to Ubuntu
---

### Post by lesliek2 on 2014-05-23
I'm using Ubuntu 12.04 and, if it matters, both Firefox and Chrome as my browsers.

I've started to get this log-in message popping up on my screen every few minutes, whether I have a browser running or not. I don't want to log-in and, so far as I know, have nothing to do with Bloomberg.

I don't know how to stop it popping up. I looked in start-up applications, but found nothing that seemed relevant to me. I went into my cookies on each browser and deleted all from bloomberg, but that hasn't stopped the message either.

What do I do next?

Leslie

---

### Post by dannyboy79 on 2014-05-24
are you certain you or anyone else using this computer has logged into bloomberg website? if not, you should open both browsers and completely clear everything as far as history, cache, the whole nine yards.

---

### Post by Bucky Ball on 2014-05-24
> **dannyboy79 said:**
> are you certain you or anyone else using this computer has logged into bloomberg website? if not, you should open both browsers and completely clear everything as far as history, cache, the whole nine yards.

^^^
This. Let us know what happens.

---

### Post by lesliek2 on 2014-05-25
Thank you to both dannyboy79 and Bucky Ball for replying.

I suspect that I have gone to some Bloomberg website, perhaps even recently, but it wouldn't have required me to log in. (I couldn't have done so anyway; I have no account with them.)

After posting my original query, I did do what dannyboy79 afterwards suggested, but it didn't make any difference.

After hunting around further, I've recently amended my /etc/hosts file by adding to it "127.0.0.1 www.bloomberg.com".

That SEEMS to have stopped the box from popping up, I guess because I'm no longer trying to go to the Bloomberg site myself for some reason I don't understand, so it never gets to ask me for my username and password.

If what I've tried does work, I'd be grateful to be told if I shouldn't be using this method, because of some other problem I've caused myself.

Thanks again,

Leslie

---

### Post by bapoumba on 2014-05-26
Any extension or addon you do not recognize ?

---

