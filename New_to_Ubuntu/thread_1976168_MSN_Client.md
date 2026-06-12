---
title: "MSN Client?"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by d4m1r on 2012-05-08
Hey guys, I am looking for a MSN client that ONLY connects to MSN and no other messaging networks. I used to use aMSN, but it has not been updated for 12.04 yet.

Does anyone know of such a client? Also, if I have the .deb install meant for 11.10, would it let me install it on 12.04?

Worst case scenario....Feel free to recommend me **minimalist** multi-service messaging programs with support for MSN.

Thanks in advance!

---

### Post by L3ct3rIII on 2012-05-08
Hello there, d4m1r.

There's was good one out there called Emesene. I say "was" because it was much more MSN Messenger alike on its first version (give a look there: [Great MSN Messenger Clone on Linux]("http://m3rlinez.blogspot.com.br/2007/12/great-msn-messenger-clone-on-linux.html")). Now, even being primarily a MSN client (and this being its main protocol), it supports other mechanisms too, like GTalk and Facebook Chat. But maybe it still can suits your needs, anyway. Visit its page, there you can find info, screenshots and downloads: [Emesene blog]("http://blog.emesene.org").

Hope it can help you.

So long.

---

### Post by d4m1r on 2012-05-08
Thanks for the recommendation! It is very simplistic which I love, and it even performs faster than aMSN!

It's weird because they don't seem to have a 12.04 version on their PPA but I was able to still install it, despite apt-get update giving me 404 errors. What ever version it did install works just fine though.

Thanks again! :cool:

---

### Post by Corvair on 2012-05-28
Great, thanks for the suggestion. I just installed 12.04 on a new build and found out that aMSN has been eliminated from this version... But emesene is in Synaptic, installed it and it works perfect.

---

### Post by Senior_Buckethead on 2012-05-28
Yeah I installed emesene, but drove me mad every time ran apt-get update as they dont have a ppa repository for 12.04, so kept on giving me 404 errors on update.
I had to remove the offending ppa in my /etc/apt/sources.list.d directory.

Perhaps soon they will add 12.04. I just use pidgin and it works ok.

---

### Post by DingusFett on 2012-05-28
I installed emesene on 12.04 through the software centre and haven't had any issues as of yet with it. Found it a lot better than Pidgin since I only use MSN and couldn't work out group conversations in Pidgin.

---

### Post by Senior_Buckethead on 2012-05-28
Dont get me wrong emesene worked great, it was just its ppa i had issues with.
A quick look at at:
[http://ppa.launchpad.net/emesene-team/emesene-stable/ubuntu/dists/](http://ppa.launchpad.net/emesene-team/emesene-stable/ubuntu/dists/)
still shows no ppa for 12.04.

---

