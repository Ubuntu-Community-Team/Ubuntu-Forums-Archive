---
title: "commercial +static library + packaging"
date: 2009-07-02
forum: Programming Talk
---

### Post by leblancmeneses on 2009-07-02
i developed a c library i want to sell commercially for use in embedded devices. 

Using archiver utility I created a static library.

now i know everything can be cracked and stolen but for legitimate companies what is the common way to sell your static libraries (make it difficult enough so they just call for another license)?  


Also can i create the static library using ar tool on linux and would it work in their C compiler if i provide headers?  Or will i need an archive tool specific to compiler? 
Example:
if I create static library on linux and attempt to link library on windows app.  
Would i be required to build the static library on windows or is .a compatible with any c like compiler.



also if i have two static libraries:
companyname.structures.a
companyname.text.a  -- text depends on structures.a

and all companies paid for was companyname.text.a
would companyname.text.a have only the bits of pieces it used from companyname.structures.a and nothing more.   This way i just provide buyer companyname.text.a with headers and that is it.?  (I assume so but want to make sure)



What are technologies that help me constraint # of developers or specific developers or specific project?  I know that some methods is to use a hardware approach (key fob)

Some compilers use a server like [http://www.macrovision.com/](http://www.macrovision.com/) that check if your license has expired.

however none of this approaches help me.. as from i see is once they have the .a they never have to pay for project license fee again ...  is this true?


Thanks,

lm

---

### Post by benj1 on 2009-07-02
> **leblancmeneses said:**
> 

What are technologies that help me constraint # of developers or specific developers or specific project?  I know that some methods is to use a hardware approach (key fob)

Some compilers use a server like [http://www.macrovision.com/](http://www.macrovision.com/) that check if your license has expired.

however none of this approaches help me.. as from i see is once they have the .a they never have to pay for project license fee again ...  is this true?


why are you asking this on an open source forum?
i don't think many people here will be against proprietary software per se, but i don't think they will help you implement DRM.

or to be more positive, im guessing youve used ubuntu, and would hope that you found it refreshing not having to sign up to stupid licence agreements, or deal with windows genuine advantage (or what ever they call it now) etc etc. 
maybe your customers would appreciate that too, and it would allow you to do your job coding rather than worry about IP issues. and thats before talking about open source routes, you could release it open source, let people use it, then they can hire you the expert (you wrote it) to sort issues, add features, etc. 
Im not an expert on embedded c library market dynamics, but i assume that most customers would be larger companies would be willing to pay for something like that.

---

### Post by leblancmeneses on 2009-07-02
```

why are you asking this on an open source forum?
i don't think many people here will be against proprietary software per se, but i don't think they will help you implement DRM.

```

I am actually posing the question to individuals interested in development/programming which means commercial and open.  This forum does not require it be specifically to GPL/LGPL/BSD/MIT/... licensed code.

I wouldn't consider this topic popular but some of us grown ups need to feed our families.


So for you working individuals ... how are companies you all work for manage this similar situation?

I'm not asking complete solutions just some hints/ideas to be dropped.


Thanks,

lm

---

### Post by benj1 on 2009-07-02
> **leblancmeneses said:**
> 
I am actually posing the question to individuals interested in development/programming which means commercial and open.  This forum does not require it be specifically to GPL/LGPL/BSD/MIT/... licensed code.

I wouldn't consider this topic popular but some of us grown ups need to feed our families.


So for you working individuals ... how are companies you all work for manage this similar situation?

I'm not asking complete solutions just some hints/ideas to be dropped.


Thanks,

lm
well i am a working individual (although admittedly not in the software industry).

yes the first paragraph was not overly positive, but i did say "most people aren't against proprietary software per se" me included, and i am against DRM, theres always a way round it, its annoying for users and distracting for IP holders.
my second paragraph was constructive in offering alternatives, that would still feed your family.

i didn't mean to be rude, apologies if you felt that, but i think its legitimate, as this is a forum for an open source OS, to challenge your closed source business model

---

### Post by monraaf on 2009-07-02
Well, maybe this forum doesn't require questions to be about Open Source code, that doesn't mean that there aren't more appropriate forums for these kinds of questions.

The positive side for you is that you would likely find more developers there with the same kind of paranoid Windows mindset that you apparently have, and you'd be more likely to get an answer with all the ins and outs of constraining other developers.

---

### Post by dwhitney67 on 2009-07-02
> **leblancmeneses said:**
> ...

I'm not asking complete solutions just some hints/ideas to be dropped.

If you have some s/w that you believe is worthy of being used in embedded systems, why not contact the vendors that develop/sell Operating Systems for that niche market.  Companies that come to mind are [Green Hills]("http://www.ghs.com/"), [Wind River's VxWorks]("http://www.windriver.com/products/vxworks/"), and [MontaVista]("http://www.mvista.com/").

The latter company repackages Linux to be lean/mean, and provides the tools for easy customization of the Linux OS (kernel and certain apps).  So when they sell a product, they are not selling Linux per se, but instead selling their configuration tool and support.

All of the aforementioned OSes are found in avionics systems (including UAVs), satellite systems, communication systems (telephone, servers, etc)... all the way down to small everyday items, such as mobile telephones.

---

### Post by nvteighen on 2009-07-02
Wait a minute. Commercial is not opposite of Free Software/Open Source. You can sell Free Software, look at Red Hat. If your program is better than anything else outside, people will buy it to cover their needs, for sure.

Of course, being Free Software, you won't be able to avoid other people redistribute your program for free or commercially... The Red Hat trick there is to sell support and services, rather than the OS... It's like they said: "Ok, you can grab Red Hat legally for free or for less from somewhere else and we don't mind, but you won't get our premium client support in case something goes wrong".

Maybe you could take that idea?

---

### Post by leblancmeneses on 2009-07-02
dwhitney67

Thanks didn't even cross my mind.  I've used [http://www.lynuxworks.com/](http://www.lynuxworks.com/) and [http://www.mentor.com/products/embedded_software/](http://www.mentor.com/products/embedded_software/) when I use to work in software defined radios.  I'll definitely entertain that idea for a while.


That said here is the real picture:

This is the product:
[http://www.robusthaven.com/Products.aspx?type=products&name=peg](http://www.robusthaven.com/Products.aspx?type=products&name=peg)

This tool can be used in a variety of ways since it is a generic parser that runs based on grammar rules.

1 big thing which dwhitney67 sounds like he is involved in is implementing ICD, interface communication documents,  this defines protocol (message format (bits/bytes) + sequence of messages) to properly implement an interface. (big companies have lots of these)

Another use is parsing file formats in an embedded device.. example say I needed to send from C# gui  new setting for microcontroller to use.    Example: software defined radio, software defined transmission controller, or parse standard message formats like:  http protocol, RS-274X,

(or say you needed your own xml parser because tinyxml isn't good enough for your needs or needed to be in c ... I have a sample xml parser with ~4 lines of rules.)


Typically to send/receive documents through multiple hmi services parsers would need to be created on both sides.  now some things can be pushed as contracts through use of CORBA but you start getting in high cost ranges not fit for PIC development where my target is at the moment.  My tool exports C#, C code and i'm working on C++/Java/PHP versions today so you write rules once and my ide exports code.


what i have as you can see in screenshots is initial start of GUI to aid in grammar rule definition + testing.  

And c static library that is code covered with unit tests. 


So at this moment all i can sell is GUI since it looks like i cannot protect/constrain static library from usage.

Now once a user learns peg rules they can basically create their own interpreter pretty easily and open source an IDE and just distribute the static library.

that is my problem


lm

---

