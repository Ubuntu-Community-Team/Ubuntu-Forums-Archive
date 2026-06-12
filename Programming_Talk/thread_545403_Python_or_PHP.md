---
title: "Python or PHP?"
date: 2007-09-07
forum: Programming Talk
---

### Post by DBGOTD on 2007-09-07
I've been doing web development for a little while now, but until now hadn't really needed to write any actual web apps or server side scripts. HTML/CSS/Javascript had sufficed until this point. Now I'm at an impasse. 

At work I use Java, VB, (and [SIZE="1"]assembler + sql[/SIZE]) so i've already put alot of time into those languages (well okay, sql isn't a programming language). Now that i've come to the point where I'm being asked to do some more sophisticated work on websites (which I do on the side) i'm having a really hard time deciding what to use. I already have an okay working knowledge of Python, and very little knowledge of PHP. BUT, I know that PHP is far more prominent when it comes to web related coding, and has a much larger number of resources and prospective work. 

If I used Python, it would be with Django which seems pretty promising from what I've done with it so far, but every time I think about devoting my time to one or the other it makes my head hurt. I can't put my time into both, so any advice on the situation? What do people here think is the more sensible path?

Thanks for any input.

---

### Post by pmasiar on 2007-09-07
Executive Summary: definitely Python and not PHP. Your choice of Django (simpler to use) or Turbogears (more flexible and powerful)

Will you host your web server inside department? or you will pay for shared/dedicated hosting?If you can avoid PHP, don't go there. I was told couple times it is possible to create clean maintaineable code in PHP, but it looks like it is rather hard and not obvious.

Compared to that, both leading Python web app frameworks enforce model-view-controller, but do it gently: they generate sample project for you, according to best practices, with files separated in proper directories, config files, MVC, stylesheet etc., and "hello, world" page up and running - you just need to add your own stuffing.

Django is OK. It makes 90% of job easy for the price making last 10% of customization hard. It has one way to do things, and does it all you. If you are fine what it does for you, it is solid.

Another Python web app framework (which for various reasons I use) is Turbogears. [http://turbogears.org/](http://turbogears.org/) It has different approach: TG strives to integrate best tools for each task, front-to-back. Many of tools are exchangeable, like templating, ORM.

So for many components, TG is largest "customer" and support of TG is important for them. It allows TG to define API and they implement it, and TG can swap between tools. Like it supports half a dozen templating systems, 2 object-relation mappers, etc.

TG uses absolutely superb templating system, Kid.
templating language is XML with python-like attributes, so you can write stuff like <span py:for="item in mylistofdicts">${myfunction(item)}</span>

where myfunction() is function (defined in template in Python), returning valid XML snippet. Extremely slick and powerful! Web designers love it too: It is valid XML with some attributes in py: namespace, which are ignored by web design tools.

Bonus: with object-relation mapper like SQLObject or SQLAlchemy, you don't write CRUD SQL at all: all is generated from model written in Python. You can also use SQLite for development and MySQL for production - mappers hides differences.

To get the flavor, read or watch [Wiki in 20 minutes](http://docs.turbogears.org/1.0/Wiki20/Page1) (also screencast), hour including TG download and install. Warning: [On ubuntu](http://docs.turbogears.org/1.0/InstallUbuntu) you need to install prerequisites and then install TG using tgsetup.py, Synaptic loads one wrong module.

PHP is more prominent in hosting, but Python hosting improved radically in recent year or two: there are many companies providing python hosting, both Django and TurboGears.

---

### Post by Mirrorball on 2007-09-07
Is this site for you or for your company? If it's for you, you should know that although Python is generally a better language, PHP hosting is A LOT easier to find and less expensive. If it is for your company, Python will be better, but you should look into Ruby and Ruby On Rails too, because it's more established than Python. Django didn't have a 1.0 release yet.

---

### Post by maddog39 on 2007-09-07
Personally as a PHP developer, I dont agree with any of those Python statements. My hosting has support for Python and I have been playing around with it for a while. So while all those Python libraries like Django and TurboGears, your host has to set them up separately along with other libraries like mysqldb, at special request. Unless of course you happen to find one which supports all those things out of the box. And when I tried making a more complex web app in Python, I found it much harder and much more time consuming then how I would've done it in PHP which a set of libraries which I use. Also, I find that a very large portion of PHP applications, if the person was taught properly as I was, are very readable and maintainable applications. I think Python's strongest area right now is with console and desktop applications. I feel very strongly that Python just isn't ready for building quick, yet robust web applications. Thats my 2 cents.

---

### Post by pmasiar on 2007-09-08
> **maddog39 said:**
> your host has to set them up separately along with other libraries like mysqldb, at special request. 

of course you need to pick hosting company friendly to Python - but there is choice now.

>  when I tried making a more complex web app in Python, I found it much harder and much more time consuming then how I would've done it in PHP which a set of libraries which I use. 

Of course learning something new is harder than using well-known old. But that is not the case with OP: he needs to learn either PHP or Python.

> if the person was taught properly as I was, are very readable and maintainable applications. 

Yes. But you need to make extra efforts to create proper MVC structure - PHP does not naturally guides you, just the opposite :-) TG will create **functioning** project skeleton with proper MVC structure, it is hard to screw it.

---

### Post by emperon on 2007-09-08
This is the most stupid question I've ever heard.

Avoid the followings at all costs:

PHP, C++, VB.

Although Python is not my first choice, it is far more superior than anything PHP could offer. Stay away from PHP and never look back. PHP has completed its mission.

---

### Post by realstraw on 2007-09-08
Why don't you just use Java and struts, if you already have a lot of experience with it? Unless you're sick of Java and want to learn something new :)

---

### Post by chamaracal on 2007-12-27
When compare python with PHP for web development PHP is better than many other web development languages.It may be simple but it is strong as well.For a web developer you have any thing you want in PHP and no need of large effort to find those.for large codes php is more manageable than python.

---

### Post by ghostdog74 on 2007-12-27
> **DBGOTD said:**
> I can't put my time into both, so any advice on the situation? What do people here think is the more sensible path?
Thanks for any input.
take the advice of this thread with a pinch of salt.  Everybody who has their own preferences of web development frameworks will come in and tell you what they like. If 100 people come in and tell you 100 different programming languages that they think are more superior than either the 2 you mentioned, what would you do ? You can get yourself more aspirins to cure your headache?

The most sensible path is , unfortunately too bad for you, is to try to learn both(or a few others) and see for yourself. You can't put your time into them? Learn some time management then.Sleep later in the night to read up etc, ... everything will work out for you in time to come.

---

### Post by Modred on 2007-12-27
> **Mirrorball said:**
> Is this site for you or for your company? If it's for you, you should know that although Python is generally a better language, PHP hosting is A LOT easier to find and less expensive.
On the "less expensive" note, I've seen VPS hosting with Python installed (and you can ssh in to add more modules yourself) for as low as $6.95/month.

[quote=Mirrorball]If it is for your company, Python will be better, but you should look into Ruby and Ruby On Rails too, because it's more established than Python. Django didn't have a 1.0 release yet.[/QUOTE]

Lack of a 1.0 release hardly means that stable releases have not been made.  Anyway, Rails might be a good idea, at least for looking, now that version 2.0 has just come out.  I used the previous version of Rails for a few projects, and it's nice, but overall I tend to prefer Python over Ruby for most general programming, so my web development will probably start reflecting that soon.

---

### Post by Wybiral on 2007-12-27
> **chamaracal said:**
> ... for large codes php is more manageable than python.

That's hilarious. You should be a comedian!

---

### Post by ghostdog74 on 2007-12-27
> **Wybiral said:**
> That's hilarious. You should be a comedian!

why is it hilarious?

---

### Post by Wybiral on 2007-12-27
> **ghostdog74 said:**
> why is it hilarious?

Even if they believe that PHP is as manageable as Python, it doesn't make any sense to me to say that PHP is MORE manageable than Python considering Python has, to name a few:

[LIST]
[*]Well designed OOP system
[*]Doesn't encourage the mixing of XML and server code
[*]Namespaces, unlike PHP (where all the standard library, which is huge, is global and everything is imported globally)
[/LIST]

So even if someone considers PHP to be as manageable as Python, it's ridiculous to say that it's MORE manageable considering Python has so many features who's sole purpose is manageability.

---

### Post by ghostdog74 on 2007-12-27
> **Wybiral said:**
> 
So even if someone considers PHP to be as manageable as Python, it's ridiculous to say that it's MORE manageable considering Python has so many features who's sole purpose is manageability.
I agree with you and Python's good points, but that's because that's our choices and both our tastes are the same. WRT charmaracal , he may be a PHP expert who finds the opposite is true, and that's his choice. So its probably not appropriate to say "ridiculous" regarding his post. In fact, your post on "you should be a comedian" is not warranted at all. Of course, that's also your choice. 

PS: I also believe PHP exists for a reason.

---

### Post by Wybiral on 2007-12-27
> **ghostdog74 said:**
> I agree with you and Python's good points, but that's because that's our choices and both our tastes are the same. WRT charmaracal , he may be a PHP expert who finds the opposite is true, and that's his choice. So its probably not appropriate to say "ridiculous" regarding his post. In fact, your post on "you should be a comedian" is not warranted at all. Of course, that's also your choice. 

PS: I also believe PHP exists for a reason.

I think you're misunderstanding me. I'm not saying that PHP is bad or that it shouldn't exist, I'm saying that they are going too far to make that statement. Python is just as manageable (IMO more). It's use of OOP and clean, organized namespaces and standard library make it plenty manageable. It wasn't an attack on PHP, I simply found it humorous that someone would make such a bold statement. Maybe if they posted some explanation for their opinion, I wouldn't have giggled, but until then it's just a prejudice statement that seemed like a joke to me.

---

### Post by CptPicard on 2007-12-27
For what my €0,02 is worth, I honestly can't avoid the impression that the more knowledgeable a programmer is, the more negative the view on PHP is as well. Personally I think PHP is a mess and produces horrible results unless you go out of your way to enforce discipline.

A corollary is that PHP supporters tend to be the ones who simply have an "opinion" based on the fact that PHP is all they know, so they tend to be defensive of it... I honestly have never seen a good, well-reasoned pro-PHP argument.

There is a lot to be said for expert consensus.

---

### Post by ghostdog74 on 2007-12-27
> **Wybiral said:**
> I think you're misunderstanding me.

No I think you don't get my point in my previous post.
> 
 I'm not saying that PHP is bad or that it shouldn't exist, I'm saying that they are going too far to make that statement. Python is just as manageable (IMO more). It's use of OOP and clean, organized namespaces and standard library make it plenty manageable. It wasn't an attack on PHP

I know, so there's no need to reiterate.

> 
 I simply found it humorous that someone would make such a bold statement. Maybe if they posted some explanation for their opinion, I wouldn't have giggled, but until then it's just a prejudice statement that seemed like a joke to me.
The whole point I am getting at is your post telling charmacaral to become a comedian. Even if you think its a joke, you can be more subtle in your approach.

---

### Post by ghostdog74 on 2007-12-27
> **CptPicard said:**
> 
A corollary is that PHP supporters tend to be the ones who simply have an "opinion" based on the fact that PHP is all they know, so they tend to be defensive of it...

if its corollary, then you should prove it that PHP is all they know and they tend to be defensive. Can anybody explain then, why PHP is still being used? and no, I am advocating PHP. I am still a Python fan, but I remain objective here.

> 

I honestly have never seen a good, well-reasoned pro-PHP argument.

There is a lot to be said for expert consensus.

You have never seen it, but that doesn't mean it doesn't exist. T

---

### Post by Wybiral on 2007-12-27
> **ghostdog74 said:**
> The whole point I am getting at is your post telling charmacaral to become a comedian. Even if you think its a joke, you can be more subtle in your approach.

Oh, so you're saying I need to be more polite? I legitimately thought it was a joke for a second (yes, I giggled). Maybe if they had backed up their statement with an explanation or example, I would have realized they were being serious. Personally I'm offended that you would insinuate me being such a rude person (and I personally find that rude).

---

### Post by ghostdog74 on 2007-12-27
> **Wybiral said:**
> Oh, so you're saying I need to be more polite? 

yes, in fact, you shouldn't have posted that comment at all.

> 
I legitimately thought it was a joke for a second (yes, I giggled). Maybe if they had backed up their statement with an explanation or example, I would have realized they were being serious. 

Like i said, he may find PHP more maintainable than Python, and that's his choice. You may like coffee, i may like tea, do i need to prove to you that tea is indeed better than coffee?

> 
Personally I'm offended that you would insinuate me being such a rude person (and I personally find that rude).
You shouldn't be offended. If you have left the comment to yourself, all this wouldn't have come about. By the way, I am not insinuating, because your post doesn't sound like you are genuinely joking, therefore I find it rude that you say i am insinuating.

---

### Post by Wybiral on 2007-12-27
> **ghostdog74 said:**
> yes, in fact, you shouldn't have posted that comment at all.

OK, I'll take that into consideration next time. Sorry I hurt your feelings. :(

> **ghostdog74 said:**
> Like i said, he may find PHP more maintainable than Python, and that's his choice. You may like coffee, i may like tea, do i need to prove to you that tea is indeed better than coffee?

If you said that tea was more caffeinated than coffee, then yes, I would expect you to explain how or why. The poster didn't say "I prefer PHP" they said "PHP is more manageable". There is more than a subtle difference in semantics.


> **ghostdog74 said:**
> You shouldn't be offended. If you have left the comment to yourself, all this wouldn't have come about. By the way, I am not insinuating, because your post doesn't sound like you are genuinely joking, therefore I find it rude that you say i am insinuating.

Well, I find it rude that you find it rude that I found it rude that you insinuated it to be rude that I legitimately thought a comment was a joke. Please hit the report button and let the moderators do their job next time instead of accusing me of being a rude person.

---

### Post by skeeterbug on 2007-12-27
Jumping in before the thread is locked. Not sure why people asked forums what language they should use. You are certain to start a flame war between the fan boys. There are more important factors than the language, (libraries, where the application is going to run, etc). Use the right tool for the job, if you don't know which tool you should be using, you should be doing the research on it. No forum user is going to give you insight on your project/needs.

---

### Post by bobrocks on 2007-12-27
Quite a few posts are comparing PHP to Django and TG which are python frameworks that do the MVC for you which is a tad unfair.  I don't think Python has built in templating to avoid mixing of presentation with buisness logic, but maybe it does.  PHP also has its own Rails-like frameworks, symfony is one I think.

Comparing bare languages; for pleasure I would go python, if I was looking to get a job after I would say having PHP on your CV would still carry more weight in web development.  Try them, play with them and see how you feel.  PHP can be done well without too much trouble if people understand the design pattern you are expecting.  I built an MVC style site and forum in PHP4 (when OO stuff was really bad) for someone and I would say the code was clean and simple, well they had no problem taking it over.  It was also incredibly easy to learn and work with PHP. 

Personaly Django is near the top of my list of things to learn properly, I've read the beta book and I really like it.  Need to improve on my python skills aswell.

---

### Post by KCPokes on 2007-12-27
I love how all these threads turn out.  

To the OP, as was stated you will need to take the opinion of others and compare it to your own.  As you can see, there are always two sides to each arguement thus you'll need to make your own decision.  Given your background, already, one probably makes more sense then the other, which I'm sure you can determine pretty quickly.  But from there you need to consider all factors, such as hosting, complexity of the application, and really what you are wanting to take from all this.  As was stated, and I agree, it does seem that the more "seasoned" the developer the more likely they are to be in the Python camp.  That said, there are a lot of people that tend to try to kill a fly with a sledghammer; I find languages like Perl and PHP to be appropriate depending on the taks at hand, as, for lack of a better statement, they are "quick and dirty".  Your mileage may vary.

---

### Post by Peyton on 2007-12-27
Okay, I'm going to avoid the whole Python versus PHP war. You stated that you've put a lot of time into VB. Do you mean classic VB or VB.NET? If the latter is the case, then it might make sense from your position to look into ASP.NET, especially if you don't want to look into another language.

---

### Post by ghostdog74 on 2007-12-27
> **Wybiral said:**
> OK, I'll take that into consideration next time. Sorry I hurt your feelings. :(

No, don't be. I am only a bystander and I am not the one who says PHP is more manageable blah blah. 


> 
If you said that tea was more caffeinated than coffee, then yes, I would expect you to explain how or why. The poster didn't say "I prefer PHP" they said "PHP is more manageable". There is more than a subtle difference in semantics.
 
It seems you still don't get I am saying. "PHP is more manageable" is his viewpoint. Just like you said Python is more manageable, its also your own viewpoint. However, you have shown why Python is more manageable, but he has not. So before he does that, you shouldn't comment anything, other than maybe ask him to provide examples.

> 
Well, I find it rude that you find it rude that I found it rude that you insinuated it to be rude that I legitimately thought a comment was a joke. Please hit the report button and let the moderators do their job next time instead of accusing me of being a rude person.

No where in your post to him says you are joking. Its always like this. Writing is more difficult than actually saying out verbally. by saying out, you can add emotions such as a joking tone or something and the recipient will get it that you are actually joking. But when it comes to writing, we all should be careful and tactful not to offend. Now if I tell you go become a comedian because you made a statement that you strongly believe in and I don't, will you be happy?

---

### Post by Wybiral on 2007-12-28
> **ghostdog74 said:**
> It seems you still don't get I am saying. "PHP is more manageable" is his viewpoint. Just like you said Python is more manageable, its also your own viewpoint. However, you have shown why Python is more manageable, but he has not. So before he does that, you shouldn't comment anything, other than maybe ask him to provide examples.

I don't know where you read that, I never said "Python is more manageable", I was only defending Python by bringing up some possible reasons why it's at least as manageable as PHP. I personally do think Python is more manageable than PHP, but I'm not asserting that as a fact, I've expressed that it's just my opinion. You need to lighten up a little, nobody was hurt. If the poster feels offended by my sense of humor, then they can report me to the moderators (you too).

---

### Post by LaRoza on 2007-12-28
> **Wybiral said:**
> I don't know where you read that, I never said "Python is more manageable", I was only defending Python by bringing up some possible reasons why it's at least as manageable as PHP. I personally do think Python is more manageable than PHP, but I'm not asserting that as a fact, I've expressed that it's just my opinion. You need to lighten up a little, nobody was hurt. If the poster feels offended by my sense of humor, then they can report me to the moderators (you too).

As a PHP user and supporter (unlike a certain member of this forum who hasn't posted in a while), I fully admit PHP can be hard to manage and easily allows messy code.

However, it can be used wisely (*cough* like me).

Python would be a more ideal language, but PHP has too much of my time and current code to change.

If anyone feels offended by my post, report Wybiral. :)

---

### Post by ghostdog74 on 2007-12-28
> **Wybiral said:**
> I nobody was hurt.

you think so?

> 
 If the poster feels offended by my sense of humor, then they can report me to the moderators (you too).
nah, i don't have such thoughts in the first place. Just be tactful (while joking) next time.

---

### Post by Perfect Storm on 2007-12-28
Amazing how childish people can be when talking about code languages and such.

If such pop up again, I'll not hesitate to deliver a handful of infractions.

Thread closed.

---

