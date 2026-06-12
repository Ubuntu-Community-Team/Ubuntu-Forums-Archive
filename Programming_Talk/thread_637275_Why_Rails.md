---
title: "Why Rails?"
date: 2007-12-10
forum: Programming Talk
---

### Post by ThinkBuntu on 2007-12-10
Recently, Rails' surge in popularity has begun to show itself in deployment by major companies, most notably the Yellow Pages. Why is it that this is the only non-Java, non-Perl, non-ASP.NET framework that is getting play from big-time sites? Is there a Kool-Aid about, or is there a serious reason that developers are choosing Rails over TurboGears, Django, and alternative Ruby frameworks? Availability of developers doesn't seem to be an issue, as neither language has a huge coder base.

---

### Post by achron on 2007-12-10
My own experience with Rails is that it is remarkably easy to adopt... never had a Rails or Ruby class. In fact my indirect introduction to Rails was an offhand comment by one of the two Chief Architects at my company about "programming by convention". When I inquired about what he meant, he directed me to the Ruby on Rails site, which led me to the "Agile Web Development with Rails" book.

I'm not going to be evangelical and argue what language or framework is "better"... in the end, its a question of what tools afford you the greatest efficiency?

Simply put, Ruby and Rails "sings" to me, and that alone makes it a great tool, and one that I enjoy working with...  Your mileage may vary... but then, you are free to choose your own toolbox.

---

### Post by pmasiar on 2007-12-11
There is couple (many) months delay between technology became accessible, and being understood, mature and widely deployed in apps. RoR has about 2-3 years head-start on Python Rail-like web frameworks (first version of Django and TG became available IIRC late 2005), so it is only recently (last year) what Dj and TG-based apps are being deployed.

And I would not say that ie Django is not deployed on big-time sites - just that those sites (like washingtonpost.com) might be less vocal about tusing Django, because web apps are not their primary business. And satchmo is complete e-shop. [http://www.djangosites.org/](http://www.djangosites.org/) lists 902 Dj-based sites.

Turbogears is even less easy to notice, because whole point is to create sophisticated app, and you don't want to get competition hint how you did that. More customizations.

I assume that within 6-12 months we will see more Python-based web apps in style of Rails (rapid app development) based on Django and/or Turbogears.

---

### Post by ThinkBuntu on 2007-12-11
What's interesting is that it seems Django took down the link on their site about the Post (I was just comparing deployments earlier, as you can see by this post). And if people were to choose their web frameworks simply based on usage by major websites, we'd all be using Perl Mason :^)

The main reason I'm curious about these sort of things is because they reflect two very important things: The demand for different skills in the job market (if Ruby is being massively adopted now, anyone who wants a web dev job would do well to learn Ruby and Rails) and the general web development climate.

---

### Post by pmasiar on 2007-12-11
> **ThinkBuntu said:**
>  if people were to choose their web frameworks simply based on usage by major websites, we'd all be using Perl Mason :^)

Not me: only people who did not get burned by Perl yet.

> The demand for different skills in the job market (if Ruby is being massively adopted now, anyone who wants a web dev job would do well to learn Ruby and Rails) and the general web development climate.

Java web app fanboys left Java, and stampeded to Ruby. Ruby is for many of them first language with dynamic typing, and first experience with duck typing is like magic. People who used Perl before understand  need for readability, Ruby fanboys are yet to learn that important lesson. Ruby is clean enough that it may work good enough for some time, but RoR is "one size fits all" kind of solution.

In the end bigger Python community will create more and more diverse solutions, but for now it is Ruby and Python neck by neck, IMHO. Do you have different stats?

---

### Post by ThinkBuntu on 2007-12-11
> **pmasiar said:**
> Not me: only people who did not get burned by Perl yet.
Story?

---

### Post by pmasiar on 2007-12-11
Well, it is not much of a story. 

I participated in a Perl project, loved the duck typing (my first time using it) and the freedom it gives you, fought off idea doing the app in Java, using CGI::Application MVC framework instead. Without strong project management and coding standard, project code is a mess. Now i know why Perl in called "write-only language": you can write the code quickly, and it runs OK. But 6 months later (after programming in java or something), you cannot recognize your own code, and you forgot little Perl quirks which make it work (difference between scalar and list context, default variables, etc). And forget about fixing code written by someone else, who has different style of code formatting - you need to reformat it first to be able to comprehend it.

Perl is like jealous mistress: it is pleasant when you spend all the time with her, but will not  forgive if you was 6 months away and want to come back. Not a chance. :-) Well I do hope gals reading this will not get offended and report me for this - I really cannot afford any more bad points, so if you are offended, MSG me and I delete it. :-)

I see lots of Perl in Ruby, even Ruby enthusiast admit it. Sure it is quick to whip some running code in Ruby, but when you will need to fix it year later? Python is also more obvious (than Ruby or Perl) for non-programmers (scientists) who are important part of our team.

Don't take me wrong, I would prefer to make my next project (web apps is what I do) do in Python, of course, but I can take Ruby (or even PHP or Perl) over Java, ASP.NET in VB/C# or any such abominations. But I would do Java/Struts or ASP/VB if my boss decides so, or if I have to maintain such app for living - I just prefer not to (and told so my boss).

I think that most important insight what Guido has, is that programs are being read more often than written, and programs are for communication between human minds, and only secondary for computers.

"Readability counts"
"Special cases are not special enough to break the rules"

Trust me, you want to write code as if next guy who will maintain that code was gun-crazy maniac who knows where you live. :-) Because it might be you! :-)

---

