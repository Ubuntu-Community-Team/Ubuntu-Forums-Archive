---
title: "[SOLVED] Arrrg!  Help pls - need alternate way to &amp;quot;ping&amp;quot; - workaround needed"
date: 2008-11-26
forum: Programming Talk
---

### Post by luckylucky on 2008-11-26
I was going to write a short perl script to ping a long list of domains ending in .ca (canadian) extension as I have to daily check if active or not.  Problem is, as it turns out, that you can't ping .ca domains (the government of canada disabled pinging to all .ca domains).  

I'm stuck, but have a few "ideas" but need help for someone to at least point me in a good direction.

I'm contemplating a script, perl or even a simple javascript, that could take a list of domains in a separate document and one by one check if the site is active.  I figure that a simple http request could suffice... if anything returns then we consider it "active", but if nothing returns it's dead.

**[COLOR="Red"]Is anyone aware of such a code in either perl or javascript that would basically return with a "true/false" to an http request? [/COLOR]** I've tried to find such a code or method but to my limited knowledge haven't turned up anything yet and thus am hoping (praying) that someone could tip me off in the right direction.  Thanks in advance!

---

### Post by pp. on 2008-11-26
> **luckylucky said:**
> the government of canada disabled pinging to all .ca domains).

If so, they've un-disabled that for me just now.

IOW I have been able to ping a site ending on .ca. Your problem might lie elsewhere.

---

### Post by luckylucky on 2008-11-26
> **pp. said:**
> If so, they've un-disabled that for me just now.

IOW I have been able to ping a site ending on .ca. Your problem might lie elsewhere.

Ummm... what domain did you ping?  I'll try it myself... sorry, I don't mean to be rude, but right now I'm having difficulty believing that.  Maybe I'm the idiot here, and I'd like to see it working.

---

### Post by pp. on 2008-11-26
user@terra:~$ ping government.ca
PING government.ca (65.39.183.210) 56(84) bytes of data.
64 bytes from forwarding.baremetal.com (65.39.183.210): icmp_seq=1 ttl=51 time=183 ms

---

### Post by luckylucky on 2008-11-26
Arggg and more arrgg!  You're right!!!  Damn, this brings up another issue, some hosts disable pinging (I guess so you can't dos them).  

I guess I still need the http solution then anyhow as I might get false "dead" reports if using ping... but if http is down then that counts.

So thus my question still stands, though my logic for requesting the helpful information has changed.

---

### Post by luckylucky on 2008-11-26
To clarify I believe I must have misinterpreted what i read about canada not allowing .ca pinging... I found something about this by googling based on this problem.  Maybe it's the government of canada websites that was implied?  I don't know.  Oh well, I feel dumb now... but I guess a solution based on http is still needed.  Googling around for that info now.

---

### Post by pp. on 2008-11-26
> **luckylucky said:**
> Maybe it's the government of canada websites that was implied?  I don't know.  Oh well, I feel dumb now

It's hard to say, and there's no reason to feel dumb. If I'd feel dumb each time I was mistaken I'd be president of the dumb society.

Perhaps it would be useful if you defined for yourself more clearly what exactly you need to find out about a site.

Are you interested in web sites or the servers they're running on? (In my example above one is [http://www.government.ca](http://www.government.ca) and the other forwarding.baremetal.com)

Do you need to know whether the server is running or whether it services http requests (I've found webservers which responded to ping but not to HTTP).

Also, you should realise that finding out whether a web site is alive or not apparently takes an appreciable amount of time. Just point your browser at a site which does not respond and count the time until it declares the site to be un-reachable.

---

### Post by ghostdog74 on 2008-11-26
instead of using ping, you can use tools like nmap.

---

