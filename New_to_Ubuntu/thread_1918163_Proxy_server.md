---
title: "Proxy server"
date: 2012-01-31
forum: New to Ubuntu
---

### Post by dolphin194 on 2012-01-31
[B][COLOR=Red]NOTICE: I am completely allowed to do this. This is *not* meant for accessing sites I am not supposed to go on[/COLOR]
[/B][COLOR=Red]I know that most threads with "Proxy" in the title have to do with getting to sites they're not supposed to go on.[/COLOR]
[B]
What happened[/B]
My dad has just screwed something up in our router settings, and I can't access Google anymore because if it. I need to be able to access Google. He doesn't like me in the router because he thinks I will make it worse. (I am sick of Bing and Yahoo)

So I want to set up a proxy server that will allow me to work around what he screwed up.

**What I want to do**
I want to host it on a computer in my grandpa's house, and access it with my computer at my dad's house. It's running Xubuntu. I want it to work with the Mozilla Firefox on my computer at my dad's house running Ubuntu 11.10.

How can I set this up?

This is only temporary until he fixes whatever he did.

[COLOR=Blue]_*Don't worry. My dad is fine with me doing this, as long as it doesn't mess with his settings.*_[/COLOR]

---

### Post by dolphin194 on 2012-02-01
Bump

---

### Post by Lars Noodén on 2012-02-01
You could put [Varnish](https://www.varnish-cache.org/) or [Squid](http://www.squid-cache.org/) on the computer at your grandfather's house and have it configured to only accept connections from 'localhost'  Then you could set your grandfather's router to forward SSH to that machine and tunnel in using SSH.  If you go that route it would be advisable to turn off password authentication and use [keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys).

---

