---
title: "Web server performance"
date: 2008-10-02
forum: Programming Talk
---

### Post by Rich78 on 2008-10-02
I'm looking for what is hopefully not too much of a generic answer.

Which distribution of Linux would be best for a very light weight and fast web server?

Is Ubuntu Server up to much in this department or should I consider another distro (Debian?)?

I'm not looking for biased views, just informed and hopefully experienced ones.

I was considering Solaris for its renowned robustness, but some reading is leading me to conclude it may not perform as quick a Linux?

I'm essentially looking to run Ruby on Rails with a PostgreSQL backend.  Probably on Apache.

Open to any suggestions

Thanks

---

### Post by tinny on 2008-10-02
Any server distribution will be fine. In terms of application performance I think the OS you use is likely to be the least of your concerns. You should be looking to use an OS that you can be productive with. For me this would be Ubuntu Server Edition or Debian, because I use Ubuntu all the time. I suspect that the answer will be the same for you, as you have posted this question on the Ubuntu forum :-)

---

### Post by CptPicard on 2008-10-02
Tinny is right, but if I'm really pushed, I'd say that maybe Gentoo and some lightweight http server (if Apache isn't light enough) would be the answer... but again, this would be the speed-kiddy approach. Most probably you really aren't that limited in performance.

Then again on second thought, on a truly limited machine, you'd be hard pressed to get the compilation of Gentoo done. ;)

---

### Post by xlinuks on 2008-10-03
Red Hat HPC on Sparc + JBoss Application Server + Oracle

---

### Post by LaRoza on 2008-10-03
> **xlinuks said:**
> Red Hat HPC on Sparc + JBoss Application Server + Oracle

How does this have anything to do with the OP's question?

The OP asked about a distro, not an expensive enterprise system, using Ruby, not Java, and using a free database server.

---

### Post by skeeterbug on 2008-10-03
I wouldn't rule out FreeBSD either.

---

### Post by tinny on 2008-10-03
> **xlinuks said:**
> Red Hat HPC on Sparc + JBoss Application Server + Oracle

Totally nonsensical 

> **skeeterbug said:**
> I wouldn't rule out FreeBSD either.

What no Windows server + IIS skeeterbug :)

---

### Post by Rich78 on 2008-10-03
Thanks for the informative replies.

I know what you're saying about productivity but generally in a Rail environment once the server is configured (I suppose that falls under productivity) the app is the same.

I know we now have the attitude of processing power, memory and storage is cheap nowadays but I don't think it should lead us to be lazy with architecture design.  

Which is why I think an OS plays an important role in a web server environment.  Surely a server running with no GUI and other processes that aren't needed is going to out perform an equivalent running excess processes?

I know hardware is speedy now and maybe other factors play a part before it comes down to this as you're also relying on the machines in the connection path but I would have thought it should still be taken into account?

For instance I was surprised to learn of Open Solaris having a GUI only design from base install, sure you can remove it post install but it's a non sensical over head in a server environment.  I may be a bit old fashioned but I don't really see a place for a GUI on a server environment.  

Especially when you're mainly going to be using SSH to configure it anyway.

---

### Post by skeeterbug on 2008-10-03
> **tinny said:**
> 
What no Windows server + IIS skeeterbug :)

OP stated he was going to run apache and RoR. Though he could run anything in front of mongrel.

I wrote my employers site in RoR - [www.mission3](www.mission3)
We are a .NET shop but we are open to other technologies as well. ;)

---

### Post by tinny on 2008-10-03
> **skeeterbug said:**
> OP stated he was going to run apache and RoR. Though he could run anything in front of mongrel.

I wrote my employers site in RoR - [www.mission3](www.mission3)
We are a .NET shop but we are open to other technologies as well. ;)

And that my friend makes you the exception to the rule (in a very positive way) :-)

---

### Post by CptPicard on 2008-10-03
> **Rich78 said:**
> 
I know we now have the attitude of processing power, memory and storage is cheap nowadays but I don't think it should lead us to be lazy with architecture design.

Agreed, but the kind of architecture design that actually matters here is in your application, not the OS platform. Most importantly in a typical web application your database design and access is the place where the most common performance screw-ups happen.

> 
Which is why I think an OS plays an important role in a web server environment.  Surely a server running with no GUI and other processes that aren't needed is going to out perform an equivalent running excess processes?

The vast majority of total time is spent doing I/O with db and network plus some processing inside your application. The OS overhead is totally negligible, unless you really *are* running some other heavy processes alongside, which of course you wouldn't want to do.

It's true that you don't need a GUI for a server, but really, any distribution will do in general from performance standpoint... although Debian is good for servers because it really is rock solid.

---

### Post by skeeterbug on 2008-10-03
> **tinny said:**
> And that my friend makes you the exception to the rule (in a very positive way) :-)

Thanks.

Also to the OP. The basic way to setup rails is to run the app via mongrel.

[http://mongrel.rubyforge.org/](http://mongrel.rubyforge.org/)

Their site will walk you through setting up a reverse proxy in apache. Lighttpd is not recommended by the mongrel team.

[http://mongrel.rubyforge.org/wiki/Apache](http://mongrel.rubyforge.org/wiki/Apache)

Use a distro you are comfortable with, it probably won't make much of a difference.

---

### Post by Rich78 on 2008-10-03
Thanks for the replies.

This quote from the link says it all with Mongrel/Apache deployment model though.

"Apache's mod_proxy_balancer module is a fully blocking module and with 
the default httpd.conf you're going to max out in the 120-160 requests/ 
second range on a decent box. You can tune up its proxying to about a 
1000 req/sec. 
So yes the net result is that you can really only put a couple of 
mongrels behind apache's proxy engine (about 2 "hello world" rails 
mongrels)."

It's not surprising as mongrel is more of a test webserver and not much cop in the real world, so hiding it behind Apache and running multiple instances isn't going to make it perform any better.

It would be a much better solution to run Apache as the main web server to ROR.

---

### Post by skeeterbug on 2008-10-03
> **Rich78 said:**
> Thanks for the replies.

This quote from the link says it all with Mongrel/Apache deployment model though.

"Apache's mod_proxy_balancer module is a fully blocking module and with 
the default httpd.conf you're going to max out in the 120-160 requests/ 
second range on a decent box. You can tune up its proxying to about a 
1000 req/sec. 
So yes the net result is that you can really only put a couple of 
mongrels behind apache's proxy engine (about 2 "hello world" rails 
mongrels)."

It's not surprising as mongrel is more of a test webserver and not much cop in the real world, so hiding it behind Apache and running multiple instances isn't going to make it perform any better.

It would be a much better solution to run Apache as the main web server to ROR.

That quote was talking about a limitation in apache's proxy engine and has nothing to do with mongrel. If they are saying you can increase it to 1000 and run two mongrels, that means the mongrel server can handle 500 requests per second. That is not bad by any means. If you are getting hundreds of thousands of hits you are going to have hardware load balancing to multiple apache servers.

If you really think your application is going to hit those numbers, maybe you should look into a different framework that isn't known to have scaling issues like RoR.

---

