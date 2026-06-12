---
title: "I need advice to speepd up php site"
date: 2010-09-02
forum: Programming Talk
---

### Post by hoboy on 2010-09-02
A friend has made php site, the site got very popular,when they are ltos of users it jut gets slow, they are more users then anticipated, now the site is slow, what can one do to make php site faster ?
This is the site [www.maliweb.net](www.maliweb.net)
I will be pleased to heare any suggestions.

---

### Post by James78 on 2010-09-02
That domain looks like it's parked.

---

### Post by hanniph on 2010-09-02
1. Optimize your php code
2. Optimize database queries, use indexes
3. Use some sort of caching. For example, [http://memcached.org/](http://memcached.org/)

If that does not help, buy more hadware ;)

---

### Post by hoboy on 2010-09-02
> **James78 said:**
> That domain looks like it's parked.


James.what does domain parked mean ?

---

### Post by simeon87 on 2010-09-02
> **hoboy said:**
> James.what does domain parked mean ?

[http://en.wikipedia.org/wiki/Domain_parking]("http://en.wikipedia.org/wiki/Domain_parking")

Are you sure you've got your friend's domain there?

---

### Post by worksofcraft on 2010-09-02
Well I think the site looks very nice in deed. There are several things you can do to make it faster. The first thing is to simply rent hosting space with a company that has good internet connectivity and competent server hardware. Choose one that is close to the population centers you hope to reach.

Secondly, PhP means that your server is parsing all your web pages and interpreting scripts for every user that accesses the pages. PhP is hundreds of times slower than any compiled language and your server has to hunt for it in amongst all the HTML so it is hideously inefficient!

Try to strip the PhP out of most of your pages turning them into straight HTML. Then concentrate the PhP only where you really need server side processing.

Good luck :)

---

### Post by James78 on 2010-09-02
> **worksofcraft said:**
> Well I think the site looks very nice in deed. There are several things you can do to make it faster. The first thing is to simply rent hosting space with a company that has good internet connectivity and competent server hardware. Choose one that is close to the population centers you hope to reach.

Secondly, PhP means that your server is parsing all your web pages and interpreting scripts for every user that accesses the pages. **PhP is hundreds of times slower than any compiled language and your server has to hunt for it in amongst all the HTML so it is hideously inefficient!**

Try to strip the PhP out of most of your pages turning them into straight HTML. Then concentrate the PhP only where you really need server side processing.

Good luck :)
Lool. That's a very good observation, that'd only come from someone who's very experienced in working with compiled languages. ;)

---

### Post by hoboy on 2010-09-02
Thanks guys for your advices

---

### Post by Hellkeepa on 2010-09-02
HELLo!

Just wrote a long post, which I then lost to hitting alt + x accidentally.. *Grumbles*

Short list of the most common ones:
[list=1][*]Reduce the number of times "echo" and the PHP tags are used, to an absolute minimum.
[*]Join SQL queries that are used in loops, and move them out of the loop.
[*]Reduce the number of files that are included by the files.
[*]And lots of other things.[/list]
If you want to, I could have a look at the files. Optimizing and securing PHP applications is something I do for a living, and I could give you a good price quote on it.

Happy codin'!

---

### Post by hoboy on 2010-09-03
> **Hellkeepa said:**
> HELLo!

Just wrote a long post, which I then lost to hitting alt + x accidentally.. *Grumbles*

Short list of the most common ones:
[list=1][*]Reduce the number of times "echo" and the PHP tags are used, to an absolute minimum.
[*]Join SQL queries that are used in loops, and move them out of the loop.
[*]Reduce the number of files that are included by the files.
[*]And lots of other things.[/list]
If you want to, I could have a look at the files. Optimizing and securing PHP applications is something I do for a living, and I could give you a good price quote on it.

Happy codin'!

Thanks but I am putting my service for free.

---

### Post by eeperson on 2010-09-03
Step 1: Determine the cause of your slowdown.

It could be CPU, it could be IO, etc.  You won't know until you look.  Otherwise you could be wasting your time optimizing the wrong thing.

---

### Post by lisati on 2010-09-03
> **James78 said:**
> That domain looks like it's parked.

Showing up "for sale" here:> The domain maliweb.com is for sale.

---

### Post by simeon87 on 2010-09-03
> **lisati said:**
> Showing up "for sale" here:

That's the same, see the link I posted earlier. They buy the domain, put some ads on it and try to earn money by selling it. It's parked because it's not really in use.

---

### Post by hoboy on 2010-09-04
> **simeon87 said:**
> That's the same, see the link I posted earlier. They buy the domain, put some ads on it and try to earn money by selling it. It's parked because it's not really in use.

simeon87 I don't think that you are right that it is for sale, not that I have heard of, I am just try to help to speed up the traffic on the site,  but I am not php programmer,I program in java,python, .Net that is why I was asking for some advices.

---

### Post by simeon87 on 2010-09-04
> **hoboy said:**
> simeon87 I don't think that you are right that it is for sale, not that I have heard of, I am just try to help to speed up the traffic on the site,  but I am not php programmer,I program in java,python, .Net that is why I was asking for some advices.

There's no real website at the given address, it's just some pages with advertisements and a 'for sale' message at the top really.

By the way, you say you want to "speed up the traffic".. does that mean you want to make the website faster or that you want to draw more traffic to your website? That are two very different questions. By the way, if it's the latter, consider hosting a real informative website at the address, it'll be much easier that way to generate traffic.

---

### Post by hoboy on 2010-09-04
> **simeon87 said:**
> There's no real website at the given address, it's just some pages with advertisements and a 'for sale' message at the top really.

By the way, you say you want to "speed up the traffic".. does that mean you want to make the website faster or that you want to draw more traffic to your website? That are two very different questions. By the way, if it's the latter, consider hosting a real informative website at the address, it'll be much easier that way to generate traffic.
Well the website has lots of traffics, it has been very popular then what the owner had anticipated, it is not mine I just want to help to speed up the site.

---

### Post by hoboy on 2010-09-04
> **simeon87 said:**
> There's no real website at the given address, it's just some pages with advertisements and a 'for sale' message at the top really.

By the way, you say you want to "speed up the traffic".. does that mean you want to make the website faster or that you want to draw more traffic to your website? That are two very different questions. By the way, if it's the latter, consider hosting a real informative website at the address, it'll be much easier that way to generate traffic.
Could you please clarified when you said that there is no website at the giving address ? here is the link i am talking about
[http://www.maliweb.net/](http://www.maliweb.net/) this site is running.

---

### Post by hoboy on 2010-09-04
> **simeon87 said:**
> There's no real website at the given address, it's just some pages with advertisements and a 'for sale' message at the top really.

By the way, you say you want to "speed up the traffic".. does that mean you want to make the website faster or that you want to draw more traffic to your website? That are two very different questions. By the way, if it's the latter, consider hosting a real informative website at the address, it'll be much easier that way to generate traffic.

Sorry a correction it is not [www.maliweb.com](www.maliweb.com) but [www.maliweb.net](www.maliweb.net) my mistake.

---

### Post by schauerlich on 2010-09-04
EDIT: ignore me.

---

### Post by simeon87 on 2010-09-04
> **hoboy said:**
> Sorry a correction it is not [www.maliweb.com](www.maliweb.com) but [www.maliweb.net](www.maliweb.net) my mistake.

Ok I see what you mean, that's slow indeed. Follow the advice posted earlier, in particular what eeperson said: first determine what needs to be optimized and then modify accordingly.

---

### Post by Hellkeepa on 2010-09-04
HELLo!

From having a look at the HTML code, I suspect a lot of the time goes to the first point on my list. Though, as mentioned by **eeperson**: You need to profile the page first, to identify where the bottlenecks are.

Happy codin'!

---

### Post by lisati on 2010-09-04
> **hoboy said:**
> Could you please clarified when you said that there is no website at the giving address ? here is the link i am talking about
[http://www.maliweb.net/](http://www.maliweb.net/) this site is running.

The link I looked at earlier must have been the ".com" site.
I had a look at [http://www.maliweb.net/](http://www.maliweb.net/) 

It took a little while to load on my system, particularly with all the images. I think that part of the problem is that you might be trying to do too much on one page, but that's just my opinion.

---

