---
title: "WSDL beginner help"
date: 2008-03-30
forum: Programming Talk
---

### Post by georgew77 on 2008-03-30
Ok, I am wanting to interact with an API which uses SOAP, whatever that might be.

I was looking at netbeans and added the WDSL page as a webservice and it seemed to do something, and parsed the functions etc ok but then I got lost on what to do.

So my questions are is netbeans the easiest or best place to start learning how to deal with SOAP/WSDL or is there something easier?

Are there any good libraries or tutorials around that are more helpful?    I was getting quite used to python which I find pretty easy and I can do non-http based C/C++ aswell but have never made it interact with the web.

The WSDL file I am trying to deal with initially is 

[https://api.betfair.com/global/v3/BFGlobalService.wsdl](https://api.betfair.com/global/v3/BFGlobalService.wsdl)

And I would like simply to login and out, initially after that I think I could get along with it - just don't know how to start

Thanks,

G.

---

### Post by nick_h on 2008-03-30
> I was getting quite used to python which I find pretty easy and I can do non-http based C/C++ aswell but have never made it interact with the web.
With python you could try the [Zolera SOAP Infrastructure](http://pywebsvcs.sourceforge.net/zsi.html) (ZSI).  Have a look at the wsdl2py command in section 11.3.

---

### Post by georgew77 on 2008-03-30
Many thanks, havent tried it yet but looks like it could be just the ticket....

G.

---

