---
title: "stuts1/struts2 or spring?"
date: 2009-04-10
forum: Programming Talk
---

### Post by konqueror7 on 2009-04-10
i'm trying to go into web programming with java, and started to decide between struts1 and spring... i chose struts1, and i have been half-way through my studying, then i stopped. then now, i returned, and eventually was faced to rethink if i have chosen the right framework. struts1, so far, has been good for me...some of my classmates who were working already, told me to use spring and now struts2 instead...

i'm asking, which would be a better framework for me to learn, in which i could get a working application easy, and could give me a better chance of having to use it in real dev't (since i will be looking for a job in 3months, currently working freelance), and perharps, your own view of its advantages and disadvantages...great ORM support would also be great...

also, if you could somehow give resources for me to study it...also i'm open for other framework suggestions...oh, i've already done web apps with PHP, so web app dev't for that matter is not that foreign to me...

---

### Post by hoboy on 2009-04-10
Well SpringFramework is a great framework to understand, try [http://wicket.apache.org/](http://wicket.apache.org/) and [http://www.icefaces.org/main/home/](http://www.icefaces.org/main/home/)
and of course jsf these are very good to web framework to understand.

---

### Post by konqueror7 on 2009-04-10
thanks for the reply...will check this out tommorow, going to sleep now...;)

---

### Post by CptPicard on 2009-04-10
Struts is totally archaic. Spring on the other hand is an attempt to do architecture the right way, and can actually be used as a backbone for all kinds of projects.

I would suggest you take a good look at Groovy on Grails, which IMO is the most interesting webdev-on-Java thing at the moment. It is backed by Spring and Hibernate.

---

### Post by konqueror7 on 2009-04-11
i just read about groovy on grails, and i like the thing that it integrates both hibernate and spring into the framework...also by having to hide most of the configuration from the developer (which i also hate; i use jpa and hibernate as the provider for my persistence, just to get away from those xml configs)...

---

### Post by jespdj on 2009-04-11
The problem is that there are literally hundreds of web application frameworks, which makes it hard to choose. Struts is one of the older web frameworks and is considered to be obsolete by many people.

---

### Post by Asham on 2009-04-11
> **jespdj said:**
> The problem is that there are literally hundreds of web application frameworks, which makes it hard to choose. Struts is one of the older web frameworks and is considered to be obsolete by many people.

Does this statement take Struts 2 into account? From what I've heard, it's better/easier/more modern than Struts 1. I, of course, have used only Struts 1 and would not recommend it unless you like to maintain code **as well as a bunch of config files** that are crucial for the application to work.

Doesn't Spring suffer from this too, lots of XML config files?

---

### Post by konqueror7 on 2009-04-11
yeah, me too i hate those frameworks with too many xml config,,,i tried an introduction with spring, and it definitely has still some xml configs...

i just read that wicket (as hoboy) suggested was targeting on less xml configs to the developer, sounds promising...also just read about ICEfaces, looks good to me, maybe i will try this after i select my current web MVC framework...

---

### Post by chrisjsmith on 2009-04-11
They are all hideous and so are J2EE containers.  Spring is terrible with regards to configuration - I've been using it for 4-5 years (both in Java and .Net with Hibernate/nHibernate).  The mindset/learning curve required to get something basic working is huge.  It's a non starter for new projects these days.

I live in London, UK and I'm seeing a trend recently where people are just doing stuff in PHP as time to market is lower.  

The cost of change is waaaay too high with Spring/Struts etc.

Yes I have included Struts 2 in that.

(Disclaimer: This bitterness is from working with J2EE for a number of years - save yourself the pain).

(Disclaimer 2: We're also knocking 80 million transactions a day through Spring ironically so it's solid but painful)

---

### Post by CptPicard on 2009-04-11
I have a feeling that those who diss the configuration in J2EE/Spring have not actually done any of that in the past couple of years, using proper tools.

Both Spring, J2EE and Hibernate are annotation-based these days. It helps a lot. Add Netbeans into the mix and stuff happens almost as if by magic -- strangely, web developing has only recently become actually somewhat enjoyable using this combination (and perhaps Django on the Python side for more lightweight things).

The architectural learning curve is pretty steep but at least you no longer get stuck at the XML before you have a chance of seeing what the whole thing actually looks like.


> **chrisjsmith said:**
> (Disclaimer 2: We're also knocking 80 million transactions a day through Spring ironically so it's solid but painful)

Yeah, well, that's the point. PHP never felt "solid" and the language is an awful mess in the design sense, and most PHP coders are totally incompetent when it comes to proper architecture, database design and all that. 

I was actually working with a lead dev of something that wanted to become a major dotcom, and the guy actually had a very impressive project under his belt, and I left the project disgusted when it became apparent he did not understand what a foreign key was, "did not see the reason" to use joins, and would have wanted to essentially design the database along the lines of "one database per component/small set of tables"...

---

### Post by chrisjsmith on 2009-04-11
Nothing wrong with PHP.  It's just not very restrictive and isn't type safe so you have to be careful.  As you state, it's usually the developers that suck.  Most don't even know what a class is let alone understand basic design patterns.  I've built some large, well designed, very robust, scalable software with PHP.

> **CptPicard said:**
> I was actually working with a lead dev of something that wanted to become a major dotcom, and the guy actually had a very impressive project under his belt, and I left the project disgusted when it became apparent he did not understand what a foreign key was, "did not see the reason" to use joins, and would have wanted to essentially design the database along the lines of "one database per component/small set of tables"...

Sounds like the muppets I'm working for (I inherited the junk before you ask and am the lead architect unfortunately).  12 schemas, 1000 tables between them.  No foreign keys between schemas.  Lots of missing foreign keys between tables.  Tables with 20-100 million rows+ and no indexes because the capacity planning was botched.  Product way too complicated which is the real issue.

Annotations are ok, but the web container is slow to come up with annotations (think nearly 5 minutes to bring that up with Hibernate maps).  All that introspection is evil.

---

### Post by CptPicard on 2009-04-11
> **chrisjsmith said:**
> Nothing wrong with PHP.

Except that it's like the ugly ******* child of C and HTML... ;)

> 
Sounds like the muppets I'm working for (I inherited the junk before you ask and am the lead architect unfortunately).

I feel for you. :) It's incredible how lost some people can actually be with basic stuff. And to think that this dude was there to write the original Youtube, no less -- I had high hopes about his competence. But unfortunately, it was not to be. In retrospect, it is no wonder that it had to be totally rewritten when it later ran into capacity problems.

He still doesn't agree to use any frameworks whatsoever, but writes everything himself from scratch. And I suspect it shows -- he was close to granting me access to the CVS, but started backpedalling when I started asking difficult questions about his designs after seeing the awful database schema, and being told that "I am surprised you're not capable of reading from one database and writing to another"... (as if I actually ever would voluntarily move most of db functionality into application code).


> 
Annotations are ok, but the web container is slow to come up with annotations (think nearly 5 minutes to bring that up with Hibernate maps).  All that introspection is evil.

Well, you do set it up just once and then run it for a long while..

---

### Post by Reiger on 2009-04-11
> **chrisjsmith said:**
> Nothing wrong with PHP.  It's just not very restrictive and isn't type safe so you have to be careful.  As you state, it's usually the developers that suck.  Most don't even know what a class is let alone understand basic design patterns.  I've built some large, well designed, very robust, scalable software with PHP.

Quite. PHP is a bit like JavaScript: it offers a lot of good to both the beginner and the advanced users alike, but it can bite back hard to the intermediate coder who doesn't think or prototype at all before doing; more so with JavaScript than with PHP because PHP has a less ambiguous syntax (each variable is a $something; and string concatenation is -thank god- not overloaded in a language where the common denominator of everything is the string type).

Incidentally: JavaScript is used again in numerous interesting applications, think the Plasma `framework' for KDE 4, lightweight identation plugins for Kate.

---

### Post by pmasiar on 2009-04-11
> **CptPicard said:**
> He still doesn't agree to use any frameworks whatsoever, but writes everything himself from scratch. ... and being told that "I am surprised you're not capable of reading from one database and writing to another"...

Seems like classic symptoms of a [http://c2.com/cgi/wiki?CowboyCoder](http://c2.com/cgi/wiki?CowboyCoder) and [http://c2.com/cgi/wiki?CowboyCoding](http://c2.com/cgi/wiki?CowboyCoding)

---

### Post by CptPicard on 2009-04-11
If only he had been any good I might have managed it. But of course, you're not "good" by any measure if you hack stuff up the way he did. :)

---

