---
title: "How efficient are Flex, Yacc and Memphis?"
date: 2009-01-09
forum: Programming Talk
---

### Post by TheMyself on 2009-01-09
As I search the internet, I can't find any project which is mentioned to be made using Flex, Yacc, etc. So, I would like to know how a compiler/interpreter made using the above tools compares to a similar one made "by hand". Also is there any enterprise or scientific software which is developed using these tools?

---

### Post by CptPicard on 2009-01-09
You probably don't see them mentioned explicitly because they are such core tools.

As to the "efficiency" you need to refer to the actual parsing algorithms implemented -- I am sure the algorithm implementations themselves are very good (or someone would have already fixed them to be better). Parsing itself is such a well understood problem that there is no black magic involved that would make a handcrafted solution better -- it is likely to be worse.

---

### Post by SupaSonic on 2009-01-09
I've used Flex for a couple of weeks. It seemed to me more like a toy then an efficient tool. I mean you can do 90% of the stuff you need in 10% time, but the last 10% will take 90% of your time.

It didn't have the the necessary amount of control over, say, display of components. I was trying to make a sort of table where some rows use colspan (speaking in html terms) but eventually I just gave up. Couldn't do it. And it seemed like a trivial task too. Whereas some complex stuff is very easy to do in Flex.

But maybe it was just my lack of experience, who knows.

---

### Post by Tony Flury on 2009-01-09
SupaSonic : I am guessing that the OP is refering to the Flex tool for building and parsing launguage definition - you can use it along with tools such as Bison and Yacc to build your own compilers for standard or alternative languages.

I guess the Flex that you are refering to is adifferent beast although : Adobe Flex I guess for building Flash applications.

---

### Post by TheMyself on 2009-01-09
> **CptPicard said:**
> 
Parsing itself is such a well understood problem that there is no black magic involved that would make a handcrafted solution better -- it is likely to be worse.

That's one thing I needed to know. Thank you. Would you advise me of a text/reference on the theory of these operations?

---

### Post by CptPicard on 2009-01-09
> **TheMyself said:**
> That's one thing I needed to know. Thank you. Would you advise me of a text/reference on the theory of these operations?

I have been looking for one myself, actually, because parsers are one giant black hole in my knowledge unfortunately, but my impression that for example this

[http://www.amazon.com/Compilers-Principles-Techniques-Tools-2nd/dp/0321486811](http://www.amazon.com/Compilers-Principles-Techniques-Tools-2nd/dp/0321486811)

might be good.

---

