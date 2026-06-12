---
title: "pick second best server..."
date: 2008-04-26
forum: New to Ubuntu
---

### Post by akimatsu123 on 2008-04-26
Hi,

I used the function under System --> Administration --> Software Sources to pick my best server. However, the server it gave me is not working (fast download for update, but cannot download anything afterwards). I know it's the server because i'm using another server now and it works perfectly.

But the server i'm using now is about 1/10 slower than the one i had before. I just picked a server from the same region. My question is, is there a way to pick the SECOND best server, per say? I'm thinking maybe i can remove that dysfunctional server from the server list. How do i do that? 

Thanks

---

### Post by wormser on 2008-04-26
I am unsure if you can pick a second server.  Right now most of them are slow because of the new release.  Speeds will be back to normal in a few weeks.  That one server's issue could be due to large demand.

---

### Post by Joeb454 on 2008-04-26
You could try the Main Server.

Also the GB server hasn't been too bad for me recently :)

---

### Post by akimatsu123 on 2008-04-28
yeah but i live half way accross the world from the states. is there any way to remove that server from the list? there has to be a file somewhere with all those server addresses. any ideas?

thanks,

---

### Post by Joeb454 on 2008-04-28
It should save the one you choose as the new default server :)

---

### Post by wormser on 2008-04-28
All you need to do is change the location in Software Sources.  Check under "other".  Your download sources are located in /etc/apt/sources.list.  I do not think you can have multiple sources because it would give you 2 of each server.  My guess is that it would take everything from the first one listed.

---

### Post by rajaram_s on 2008-04-28
NO, but I always find the update server alone slow even when I was having ubuntu 7.10. Whereas any apt-get is faster...

---

### Post by akimatsu123 on 2008-04-28
> **wormser said:**
> All you need to do is change the location in Software Sources.  Check under "other".  Your download sources are located in /etc/apt/sources.list.  I do not think you can have multiple sources because it would give you 2 of each server.  My guess is that it would take everything from the first one listed.

that file choses which repositories im downloading. i want to change the servers from which im downloading these from. I know that you can choose servers under "other" but i just don't know which one is faster. With Gutsy, i always used the "choose best server" option which gave me a download speed of about 70 kb/s. 

but the server "choose best server" picks is faulty. so im wondering how to remove that server from the list of servers (there are like 200 of them) so that i can use the "choose best server" function again to pick the best server aside from that faulty one. 

thanks,

---

