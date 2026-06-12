---
title: "Php Vs jsp"
date: 2007-02-11
forum: Programming Talk
---

### Post by Mba7eth on 2007-02-11
Hi all , 
I am about to build a website . But really confused which to use Php or jsp ???? 
Give me ur suggestions !! Waiting :popcorn:

---

### Post by lnostdal on 2007-02-11
Why are you confused by only those two when there are so many others? 

You must already know something about these two or be curious about them. I'd try to figure it out by myself - while asking more specific questions, then make my own decision.

---

### Post by rko618 on 2007-02-11
I don't know anything about the needs of your website but based on my own experience in both PHP and J2EE/JSP I'd definately say PHP is the less complicated one of the two.  I guess it depends though, are you a serious java gruru already?

---

### Post by docetes on 2007-02-11
don't forget about ruby on rails. Ruby is a nifty scripting language and rails is the framework. Check it out before going down the php/jsp route. There is also JAvaserver Faces but there aren't many good tutorials for that on the web

---

### Post by Mba7eth on 2007-02-11
well guys .... I want to learn a new thing . Plus i want it to be a plus for me in work. 
Php is really widely used. but i'm hearing that jsp is very powerfull although slower than other scripting languages. Also i already know java .... It will help alot in jsp .... 
What do you think!?!?!?!?

---

### Post by docetes on 2007-02-11
don't bother with jsp unless its a really simple app. Try Java server Faces

---

### Post by orlox on 2007-02-11
I believe jsp (together with java servlets) is appropiate for BIG thigs....For most things, I believe php turns out to be easier and faster to work with (especially if you take advantage of many of the good MVC frameworks out there...), and examples of how to do almost anything you can think of can be easily found on the web...

Other reason I think php is a good option, is hosting. I truly don't know anything about ruby on rails, but at least in my country, rails and jsp hosting is scarce (if not unexistant).

Other thing I found better of php over jsp, is that installing an apache server with php support, is much easier than trying to install an apache server with tomcat to provide jsp support.

So, my opinion is that jsp+servlet is a good option when you're web application are BIG and have a complex "business logic". Otherwise, i'd simply turn out to php...

---

### Post by Mba7eth on 2007-02-11
Thanks a lot all and thanks a lot to this beautiful forum. 
I'll take every word in my considerations .

Cheers \\:D/

---

### Post by gh0st on 2007-02-12
Just to confuse you a bit more ...you could try Django, it's a Python web framework :)

I've used PHP, JSP, Perl CGI, ASP and ASP.NET over the years and they all have their merits. I know a lot of people rave about Ruby On Rails but I can't comment as I've never tried it. It's on my TO DO list.

I started doing work on the desktop side with Python since moving to Linux and I wanted to try it out on the web. I tried out Django and I have to say I'm really impressed by it as a solid web framework for Python. It's not for everyone but you might wanna check it out before making any decisions.

There is loads of info here: [http://www.djangoproject.com/](http://www.djangoproject.com/)

The community is pretty strong and helpful. I haven't used Django for long and like I say it's not for everyone but speaking personally it's increased my productivity a lot. The Object-Relational Mapper for database interaction is really cool :cool: 

Just thought I'd add my 2 cents :) 

You really have to check out the options for yourself, only you can know what's right for your project.

Good luck.

---

### Post by Dygear on 2007-02-12
JSP Is nice, but PHP is better.

---

### Post by LordHunter317 on 2007-02-13
A comparsion between JSP and PHP is nonsensical and anyone who makes one doesn't know what they're talking about.

JSP is a small part of the J2EE stack allowing you to make Java-powered webpages using a style simliar to ASP or PHP: HTML-esque tags with bits of code embedded throughout.  However, you'll find you won't get far without being an experienced Java programmer and understanding the J2EE servlet stack, or without one by your side.

---

### Post by phossal on 2007-02-13
> **LordHunter317 said:**
> A comparsion between JSP and PHP is nonsensical and anyone who makes one doesn't know what they're talking about.

JSP is a small part of the J2EE stack allowing you to make Java-powered webpages using a style simliar to ASP or PHP: HTML-esque tags with bits of code embedded throughout.  However, you'll find you won't get far without being an experienced Java programmer and understanding the J2EE servlet stack, or without one by your side.

I agree.

If you ever have to participate in a Java-driven site, full of Enterprise Beans and remote calls, and JSP, you'll realize that it would be pretty difficult to think of a reason to use Java in a site at all for most *normal* projects. PHP is so well suited (as it was intended to be) for use in general web tasks that there is virtually nothing you can't do with it. 

Java makes possible the distribution of such radically complicated systems that I don't believe you should learn it *for web development* alone. Once you've sort of mastered Java, then you have to move on to Enterprise Beans, which has a fairly steep learning curve itself. If you don't know *why* you need Java for the web, you probably don't need it.

The intro to PHP books tend to be less than 300 pages. And for good reason.

---

### Post by LordHunter317 on 2007-02-13
> **phossal said:**
> If you ever have to participate in a Java-driven site, full of Enterprise Beans and remote calls, and JSP, you'll realize that it would be pretty difficult to think of a reason to use Java in a site at all for most *normal* projects.I wouldn't go taht far.  Servlets can be ok if you use the right software with them (e.g., Wicket) 


> PHP is so well suited (as it was intended to be) for use in general web tasks that there is virtually nothing you can't do with it. Actually I think it's only suitable for getting hacked but that's just me.

>  Once you've sort of mastered Java, then you have to move on to Enterprise Beans, which has a fairly steep learning curve itself.I don't see why.  No one uses them in the original spec really or as originally intended, and J2EE 5.0 may end up being too little too late.

[quote]The intro to PHP books tend to be less than 300 pages. And for good reason.[/QUOTEe]Yeah, they're universally crap.  The "Pitfalls" section alone should be 300 pages.

---

### Post by phossal on 2007-02-13
Wow. I didn't anticipate a day like today at all. I really dislike the quote game for creating arguments and refuting points. I think it reflects weak writing ability, and is difficult to read at any rate. Forgive me for not including a quote to your post, LordHunter. I trust I'll do a reasonable job of communicating my thoughts, and that you'll do a reasonable job of associating them with the points you've made previously.

Servlets are neat. I've used them in a variety of applications when some existing code made that a reasonable way to proceed. For general tasks, for single-administrator and personal sites, for blogs, I think php handles the associated tasks very well. Security is an issue for all web-accessible servers, regardless of the method they use for delivering content. In general, for creating basic templates, for accessing MySQL, and for creating forms, I think php and javascript together are a more accessible, and acceptable, solution than servlets. PHP strikes me as an easier solution, in the same way that people say development time in perl/python is faster than writing your prototypes in c.

Enterprise Java Beans are *complicated*. There is no denying that, if you read every book available on Java without reading one on Enterprise Beans, you cannot begin to make one, let alone make one work effectively. Speaking generally, most people don't have any need to serialize an object, and ship it to somewhere else for processing, or handle the other complex tasks they're capable of. 

Of course, you won't disagree that pitfalls exist in any language. php has plenty. The US-Tax-Code-Length documentation of Java has a few, too. For a guy who has never used *either*, or a guy who wants speedy development, or is running a simple site, it just seems like php would be a natural choice.

---

### Post by LordHunter317 on 2007-02-13
> **phossal said:**
> I think it reflects weak writing ability, and is difficult to read at any rate.Really, it just shows that English-speaking countries place vastly too much importance on style over content in their writing.

>  Forgive me for not including a quote to your post, LordHunter.You did before you edited, and if you do not then you didn't pay much attention in English class.

> I trust I'll do a reasonable job of communicating what I think, and that you'll do a reasonable job of associating it with what you've said previously.That's just it.  English is far too ambiguous of a language to do that in, especially when points are distinct and the counter-points are unrelated.

I pick quotes and respond with focused points to them to help ensure that a clear distinction is made between unrelated things.

>  For general tasks, for single-administrator and personal sites, for blogs, I think php handles the associated tasks very well.But it doesn't.  Most of the code out there has horiffic track records or is terribly written.  And there's zero good learning material out there.  I've yet to meet a good PHP book.

> In general, for creating basic templates, for accessing MySQL, and for creating forms, I think php and javascript together are a more accessible, and acceptable, solution than servlets.Not really.  PHP lacks templating as part of the core system.  The builtin MySQL driver was an abhorrent engine of hackery and destruction until PHP5, even now you still have to be careful to learn the correct driver.

> Enterprise Java Beans are *complicated*.Yes, but they're also irrelevant.  I don't know why you keep bringing them up, they're a red herring large enough to sink the Titantic.  They have nothing to do with creating web applications unless you want them to.

> For a guy who has never used *either*, or a guy who wants speedy development, or is running a simple site, it just seems like php would be a natural choice.It seems to me that any of the Python frameworks, RoR, or ASP.NET would be far better choices.  They lack the problems both have in common, and lack many problems both share that are unique.  And, they'll likely produce better quality code with less effort than either, too.

---

### Post by phossal on 2007-02-13
You seem to have done a fine job finding and responding to my thoughts, didn't you? ;) Quotes, as you have them, are simply structure anyway. I think you've countered your own point with that, if you had one. They are messy, though. Reading your last post isn't very convenient, and it's less effective than a simple paragraph. I don't think such a layout communicates your ideas the way you may perceive it to do. For example, when I drop in on a new thread, I always skip posts like that. They're a pain. 

More important, you  must be in the mood for an argument today, and I'm not. You've said quite a bit, but it's disjointed and disconnected. I can't possibly pick it apart and respond in a meaningful way - if I could I still care too little to try - so I give up. I can boil down my point to a sentence: Between Java (Servlets, JSP, and EJB) and php, I feel php is much easier to learn, and is the easier language in which to implement, develop and maintain common solutions for a beginning programmer. 

Enjoy your day.

---

### Post by LordHunter317 on 2007-02-13
> **phossal said:**
> You seem to have done a fine job finding and responding to my thoughts, didn't you? ;)But you did a piss-poor job of finding, comprehending, and responding to mine.  Possibly because you didn't take the time to properly identify what you had issue with.  It's not like it's hard, my points are even seperated out structually for you to respond to individually.  This is how a discussion goes after all: you make a point and I respond, then you rebut; we proceed in this fashion until we come to a stalemate or a reasoned agreement.  In this case, since you've made disjoint points, I've intentionally seperated them out so they can be discussed independently, as they should be.  Despite what you may wish to believe, very little of what you've said is actually related: The issues you've raised with J2EE can be discussed independent of what you've said about PHP.  You may try to claim, "But I'm saying one is better than the other," but that's all you've done.  If you'd given actual reasons why one is better than the other (beyond vieled references to learning curve), then perhaps your posts could be discussed as a whole work.  But what you've currently written cannot be because there simply is no unifiying argument.  You've totally and utterly failed to answer why you believe what you believe, and most of the factual claims you've made are either:[list][*]Simply incorrect, or[*]Irrelevant.[/list]

> Quotes, as you have them, are simply structure anyway. I think you've countered your own point with that, if you had one.No, because it was not about structure, it was about *style*.   The two are distinct concept in all languages, natural and computational.  I was distinct in my word choice because it isn't a matter of structure *at all*.

Like I said, it's a real travesty the emphasis we place on style over proper structure, grammar, and comprehension.

> Reading your last post isn't very convenient, and it's less effective than a simple paragraph.No, it's vastly more effective because it prevents confusion of the issues: you know exactly what you've said that I've taken issue with and there's no way to avoid it.

It takes some getting used to, because we don't have such discussion in traditional writing (obviously).  But spoken conversation wouldn't procede like this, nor would most formal debates (and if they did, they still would result in a point-by-point analysis of what you said, because there is no other way to proceed).  So I think you're being unreasonable just because it breaks the text up, which some people find uncomfortable because it means the central message is split up instead of, well, centralized.  But I don't think it unreasonable to expect whomever is reading this to string the pieces together to get the central message.  After all, critical analysis of literature (especially dialgoue) requires this all the time.

> You've said quite a bit, but it's disjointed and disconnected.That's because your original points were disjoined and disconnected and have nothing to do with each other, something I've continually reiterated.  Some of them are simply irrelevant, like everytime you say, "EJB."

> Between Java (Servlets, JSP, and EJB) and php, I feel php is much easier to learn,**Stop, you are wrong.**  By introducing EJB, you are instantly wrong because it is not necessary to learn it at all.  It's an invalid comparsion.

---

### Post by phossal on 2007-02-13
PHP is easier to learn than *any* facet of Java. For general tasks, php is generally easier to implement. By easier, I mean it requires less total learning, less coding, and fewer components. In addition, the most widely used, commercially available hosting services support PHP, but not Java. Your page-long blabbering about language and structure is silly. 

You make a point, contradict it, and then try to imitate me. You're not embarrassed? Saying I'm wrong doesn't make me wrong, it's just useless text. My point was pretty clearly expressed multiple times. It's *one* sentence in most places. Quote that *one* sentence, and explain to the world how it's wrong. You can't. It isn't.

---

### Post by lnostdal on 2007-02-13
Hey, hunter ..

By breaking stuff into tiny little pieces until they are - or seem like to you, axioms representing the message "and thus the message itself" - you'll often miss a major part, or in some cases everything really - of what other people are really trying to say. Like a small set of notes (music) or pixels on a screen, stuff doesn't make sense (or aren't very interesting) in isolation. It's only when you hear a longer sequence of notes or see a larger overview stuff start to make sense. 

If you're like this in real life, I bet you're cringing inside before people even have finished a single sentence. You're keeping in mind what _you're_ going to say as soon as you get a chance to break in at very tiny intervals; missing what could have been potentially interesting totally.

You ever listen to Jazz? It just doesn't make sense. It's chaos, seemingly randomness. But after a while you start tracing patterns in it. You start seeing melodies, music and visual playful shapes emerging from the "random static". But it requires you to both participate and not break things into small parts. It even requires you to participate to the degree where you'll have to use your imagination and fill in the blanks _yourself_ to be able to understand or "see" the message at all. This is the "magic" in high-level human communication. (lossy compression assuming the other end will be able to fill-in/interpret to unseen/hidden high-level language internally?)

You cannot keep perpetually steering a discussion towards an "axiom-level" while dragging in external contexts when the other part, obviously - isn't discussing at that level or with those contexts in mind at that moment - and then expect to be able to prove them "wrong".

That's basically what you do; you break things into small pieces removing the original contexts - then introduce external contexts thus "proving the other person wrong on all accounts". It's stupid.

The parts (in our other discussions) "I don't care about" is the total lack of "magic" or ability and interest from your side in filling in the blanks seemingly at every single level and in regards to every single external context. There will _always_ be blanks. I can with 100% certainty predict that if I where to provide an explanation filling in the blanks at the level you're directing the discussing in at any given moment, you'll mention for me "the blanks I missed"; maybe in a different context or a different level. And so on and so on. I've seen and experienced this many times before with other "trolls". It leads absolutely nowhere at all. Anyone can keep breaking stuff into tiny pieces almost forever, but it's just boring and tedious so most people try to learn to fill in blanks by themselves based on what is provided.

..pixels?

You're watching TV through a small hole teared in a piece of paper. You're complaining because you see heads (or even less) flying by without bodies while trying to convince others that they "Do not understand; heads without bodies are wrong! Damn fools!". ...as some smart guy once said, maybe while observing the "fools":

-- "A clever person solves a problem. A wise person avoids it."

...I don't think I've seen you've done much of either.

.."magic"?

People have a certain "magic" ability to "see" that something is possible -- problems aside ("yes, we know they are there, lordhunter") temporarily. I don't think it's always intuition alone, as there is some quantum level stuff ("all things are connected") going on way inside also. If you've ever played sports you probably know the feeling. Before the ball leaves your hand you know you'll hit the basket and score (plotting backwards from basket to "force" started in body - but both things seem to happen at the same time!). If you've ever done math you sometime get the same feeling. Actually it's a great way to solve problems. You start imagining you already are at the goal, and you somehow (the "magic" high-level internal hidden language) know with 100% certainty that the path to it from where you are now exists - and work backwards to where you stand now. Programming also seem to require an ability to imagine a goal and somehow automatically know whether it is possible to reach it without yet seeing or even "caring", yet - about the path. If you've ever played a musical instrument you'll also know that general "flow", filling in the blanks mentally - is more important than getting the details "perfect".

But I imagine you already know this, you might even be aware of the big overviews ("magic", filling in the blanks, etc. .. whatever) but you take joy in switching contexts proving other people "wrong". You're actually splitting arguments into boring little pieces until they - and eventually even what you originally where saying, start to make less and less sense. You're either very bored or slightly mad - and I'm afraid not in a good way sometimes associated with borderline geniuses. Those people often spend (waste?) a lifetime trying to make others understand, making them see past the problems - often only to be understood after their deaths.

---

### Post by LordHunter317 on 2007-02-13
> **phossal said:**
> PHP is easier to learn than *any* facet of Java.Perhaps, perhaps not.  I feel given the vast amount of misinformation on how to correctly write PHP, it's very difficult.  As hard as Java?  Not sure I can make that call.  Not sure what you're basing your call on, since you refuse to elaborate on a single damn thing you've said.

For example, writing a PHP page to safely just save text from a form into a DB and read back out again is difficult.  There are a ton of gotchas and I bet if I challenged you to do it, you wouldn't do it correctly, at least the first time.

> For general tasks, php is generally easier to implement.Define general, for starters.  

> In addition, the most widely used, commercially available hosting services support PHP, but not Java.So?  Java hosting services are plentiful enough.  Cost for adequate, reasonable, professional hosting are about hte same anyway.

> Saying I'm wrong doesn't make me wrong, it's just useless text. My point was pretty clearly expressed multiple times.And it was wrong, in all places.  Show me where it's a requirement to learn EJBs in order to create website powered by J2EE technology.  It isn't.  In fact, none of the first several Sun tutorials on Servlets deal with EJBs.

> Quote that *one* sentence, and explain to the world how it's wrong. You can't. It isn't.I just did.  I did multiple times.  You're making an invalid comparsion by saying that a person developing a website in Java must learn a technology they do not have to.  You can develop all sorts of websites with Servlet technology and the literally millions of Java Web frameworks out there without using EJBs at all.  In fact, many of them go to great lengths to ensure you don't have to use EJBs (e.g., Spring).

*mumbles something about teaching style over comprehension again*

[quote=Inostdal]By breaking stuff into tiny little pieces until they are - or seem like to you, axioms representing the message "and thus the message itself" - you'll often miss a major part,[/quote]But I didn't.  He doesn't have any message beyond "I think PHP is eaiser".  He's yet to state a **single** factual reason why or even make a reasonable attempt at an appeal to emotion.  His opinion has no support whatsoever.  I get the main message--the issue is that the main message is not only unsupported, it's lost in the noise of all the errors.

> That's basically what you do; you break things into small pieces removing the original contextsShow me where I removed context incorrectly then here.  You cannot do it because it did not happen here.

---

### Post by phossal on 2007-02-13
Jesus Christ. Define *general*? C'mon, man.

---

### Post by lnostdal on 2007-02-13
define how to define general? lol

---

### Post by Ragazzo on 2007-02-13
LordHunter317 seems to be more interested in proving his superiority(?) than having a constructive discussion or helping others. It doesn't help anyone when you give the impression that someone is completely wrong when in fact at least a part of his message was right.

---

### Post by LordHunter317 on 2007-02-13
> **phossal said:**
> Jesus Christ. Define *general*? C'mon, man.Your view hinges on that definition, so it's a reasonable request.  Your other option beyond clarification is retraction.

Thsi is why being careful, specific, and exacting when talking about technology is a good thing.  Does general mean CRUD?  CRUD plus some custom validation logic that isn't easy to implement in a DB?  Full multi-tier J2EE sites?  Does it mean sites with multiple display techs (HTML, some web services tech, WML)?  

For CRUD, you might be right, but I'd be tempted to point to ASP.NET (which, if you can live in a MS world, makes crud really easy) or Oracle Application Express first.

---

### Post by phossal on 2007-02-13
Hunter is a moron if he thinks I said you *have* to learn EJB to develop web apps in Java. I'll break this down for him, since he likes things tiny.

**Argument**
You have to learn *some* extension of the core java language, though, to develop web apps. You'll learn *servlets* or *jsp*. I brought up EJB because, unless you're developing the kind of complex application that uses EJB, it doesn't make much sense to *choose* a java alternative. PHP is easier to learn than any facet of Java. For general tasks, php is generally easier to implement. 

**Reason**
By easier, I mean it requires less total learning, less coding, and fewer components. Java, the core language, I think is more difficult to learn than the core language of php. By learning php, you can effectively build a fairly complex single-server, interactive web site like a blog, a forum, or another type of membership site. I've built simple sites in Java, but they take a lot longer to develop. Compiling of your source files is required. You can't use simple include statements, which makes templating impossible without writing  a class to support it. You need a java-enabled server, rather than basic Apache. The list is *long.*

---

### Post by LordHunter317 on 2007-02-13
> **Ragazzo said:**
>  It doesn't help anyone when you give the impression that someone is completely wrong when in fact at least a part of his message was right.But it isn't.  It just cannot be, because it's too vague.  It's no more right than saying "I like apple pie over peach".

---

### Post by Ragazzo on 2007-02-13
> **LordHunter317 said:**
> But it isn't.  It just cannot be, because it's too vague.  It's no more right than saying "I like apple pie over peach".

I'm not sure what you are referring to now but I don't mean just this thread.

---

### Post by phossal on 2007-02-13
lol I don't think it is. But you're creating a reputation for yourself. I've noticed a lot of  people are developing the same aversion to you in various threads. Sort of abrasive, aren't you?

---

### Post by phossal on 2007-02-13
lol Ragazzo and I posted at the same time, and both of us noted you're unpopular forum-wide. That's funny.

---

### Post by LordHunter317 on 2007-02-13
> **phossal said:**
> Hunter is a moron if he thinks I said you *have* to learn EJB to develop web apps in Java.But that is what you said.  Well, what you said is, "There's no point in bothering if you're not goign to develop a site that requires EJB".  Which is ultimately the same thing, just stated as a threshold instead of an absolute.

> I brought up EJB because, unless you're developing the kind of complex application that uses EJB, it doesn't make much sense to *choose* a java alternative. Why?  Why do you think that.  That's not really any different from making it a requirement, despite how you've chosen to state it.

> Java, the core language, I think is more difficult to learn than the core language of php.PHP5 OO is based on Java OOP, so I don't really believe that.  Using PHP5 OO isn't optional, if you want to write secure and functional sites.

> Compiling of your source files is required.Not of JSPs, if your servlet container is properly configured.

> You can't use simple include statements,You can in JSP.

> You need a java-enabled server, rather than basic Apache.Not difficult to provide.   They're of equal difficulty in Ubuntu.

>  The list is *long.*Then enumerate it.

---

### Post by Wybiral on 2007-02-13
Abrasive is a good word... Indeed.

---

### Post by LordHunter317 on 2007-02-13
> **Ragazzo said:**
> I'm not sure what you are referring to now:rolleyes: Then you should take a course on English.

[quote=phossal]I've noticed a lot of people are developing the same aversion to you in various threads. Sort of abrasive, aren't you?[/quote]I could care less how abrasive I am.  If you'd stop worrying about my style and start focusing on your substance, we'd get somewhere.  However, despite asking for you to elaborate (or at least, noting you haven't elaborated in every single reply to you), you seem unwilling to do that without a superhuman amount of effort to get you to do so.

You still haven't adequately answered the question "Why?"  Where you have, you've either been factually incorrect or too concise to support yourself.

---

### Post by Ragazzo on 2007-02-13
> **LordHunter317 said:**
> :rolleyes: Then you should take a course on English.

I am taking. English is not my mother tongue.

---

### Post by lnostdal on 2007-02-13
i have no idea what we're discussing anymore; it keeps turning into a meta-meta-meta discussion .. do you think java/jsp is easier for a newbie to learn/use than php, lordhunter? do you think the opposite, or do you think they are equal? why? how? etc.?

what "proof" do you have besides your opinion?

in any case just imagine switching sides - or demand/provide the same arguments from yourself before you demand them from others

---

### Post by pmasiar on 2007-02-13
> **Ragazzo said:**
> LordHunter317 seems to be more interested in proving his superiority(?) than having a constructive discussion or helping others. It doesn't help anyone when you give the impression that someone is completely wrong when in fact at least a part of his message was right.

Hunter's style might be not pleasant to read, but without quoting, discussion  just degrades to shouting and waving hands.

ie: Hunter was exactly right (and phossal wrong) that no EJB are needed to develop web pages with plain JSP, but without me quoting it, who is going to find it out at check it out? So you just have to trust me that one :-)

Sometimes often-repeated half-truth is more dangegous than outright lie - with lie it is easier to see is as a lie, with half-truth you are not sure which half is wrong. :-)

So hunter quoted exactly the part which were wrong (in his opinion) and we could discuss just those, instead of attacking the strawman (quoting style).

And personnal attacks does not make anyone right either. IMHO, YMMV

---

### Post by phossal on 2007-02-13
> **pmasiar said:**
> Hunter was exactly right (and phossal wrong) that no EJB are needed to develop web pages with plain JSP

Wouldn't I have had to *say* that to be wrong about it? We're not allowed to bicker, remember? You're facing a ban, as am I. Careful. I could just make some things up, and claim you're wrong about them pmasiar. However, I won't. You prove yourself wrong often enough about the things you *do* say. That's why you were so anxious to jump in, isn't it? You have a bit of a grudge, and any hope of redeeming yourself is tasty, isn't it? But this isn't the time. You've chosen the wrong ally, because he's equally unpopular.

---

### Post by LordHunter317 on 2007-02-13
> **lnostdal said:**
> do you think java/jsp is easier for a newbie to learn/use than php, lordhunter? do you think the opposite, or do you think they are equal? why? how? etc.?I think they're both pretty terrible, for a host of reasons:[list][*]Neither give you a competent templating system OOB.  JSTL is inadequate for a lot of things you want to do.  Java's official stuff for actually placing components on webpages (i.e., their answer to ASP.NET), JSF, is pretty terrible when compared to frameworks like Stripes or Wicket.  It's really a poor copy of Spring MVC.[*]PHP makes writing secure code very difficult to out and out impossible.  Look at the mysql_escape_string() vs. mysql_real_escape_string() debacle for a good example.  Or the addition of gpc_magic_quotes to the language core as a preprocessing option.  Hope your code checks the value of the directive and compensates accordingly, or uses a third-party library that does.[*]PHP's lack of namespacing is a real bane.  Conversely, Java's insistance that path names match namespace names is equally annoying.[*]Both lack good introductory texts for web design.  Java expects you to learn the language, then enough J2EE to do servlets.  PHP books are just poorly written and don't teach you the language very well.[*]PHP's lack of mandatory variable declarations is amazing.  I don't know about you, btu I trnaspose lteters all the time.[*]Safe mode is anything but.[*]Java, in practice, requries a reasonable understanding of Servlets and a web framework to produce anything useful.  It's quite a bit of material to understand and play with.  It's also a lot of infrastructure.  Also, there are many, many to choose from and not everything is as it seems[/list]That's a short list, mostly PHP focused admittedly.

---

### Post by phossal on 2007-02-13
> **LordHunter317 said:**
> *Java expects you to learn the language, then enough J2EE to do servlets*.** Java, in practice, requries a reasonable understanding of Servlets and a web framework to produce anything useful.  It's quite a bit of material to understand and play with.  It's also a lot of infrastructure.**  Also, there are many, many to choose from and not everything is as it seems[/list]That's a short list, mostly PHP focused admittedly.

Right. Hasn't that been my point the whole time? php may have *flaws* but it doesn't require so much *learning*, or *infrastructure.* Thank you for finally making my point your own. Cheers.

Here is how *I* said it:
> PHP is easier to learn than *any* facet of Java. For general tasks, php is generally easier to implement. By easier, I mean it requires less total learning, less coding, and fewer components. In addition, the most widely used, commercially available hosting services support PHP, but not Java. 

---

### Post by lnostdal on 2007-02-13
> **LordHunter317 said:**
> But that is what you said.  Well, what you said is, "There's no point in bothering if you're not goign to develop a site that requires EJB".  Which is ultimately the same thing, just stated as a threshold instead of an absolute.
Why?  Why do you think that.  That's not really any different from making it a requirement, despite how you've chosen to state it.

you're forgetting to quote, or think of - the reasons he mentions to not bother with any java-way in the first place .. that's the difference

> **lordhunter]
PHP5 OO is based on Java OOP, so I don't really believe that.  Using PHP5 OO isn't optional, if you want to write secure and functional sites.
[/quote]
having to deal with types for variables is an issue ..  even though i know almost nothing about jsp i suspect mysql/postgresql access requires some installation of external components etc ..   with php this, and other stuff - is "built in" in most cases

actually said:**
> 
Not of JSPs, if your servlet container is properly configured.

a newbie using php doesn't have to bother with these things at all

[quote=lordhunter]
Not difficult to provide.   They're of equal difficulty in Ubuntu.
[/quote]
i think you'll find way more web-hosts with php-support than java-support .. in some cases this is a valid argument

---

### Post by LordHunter317 on 2007-02-13
> **Ragazzo said:**
> I am taking. English is not my mother tongue.Fair enough.  My point is, a statement like, "PHP is better for general sites than J2EE" is meaingless because "general" means a different thing to everyone, which is the thrust of phossal's argument.

My analogy to just stating "I like apple over peach" is because I never said why I like apple over peach.  If I said something like, "I like apple over peach because the color is more appealing to me," then we have something that can be discussed.  The only point phossal has raised for discussion is the larger learning curve.  Which isn't something I'm contesting but it's not a sufficent reason to prove his statement.

---

### Post by LordHunter317 on 2007-02-13
> **phossal said:**
> Right. Hasn't that been my point the whole time?That's not a sufficent point, in light of the issues I've raised with PHP, for one.  Two, you have to show what relation it has to "general sites" and three, still define that term.

>  php may have *flaws* but it doesn't require so much *learning*, or *infrastructure.*You need to suggest why I should value flaws, especially such fundamental ones, over a higher learning curve.  We don't always make that decision.

[quote=Inostdal]you're forgetting to quote, or think of - the reasons he mentions to not bother with any java-way in the first place .. that's the difference[/quote]**Because they're irrelevant to the correctness of that statement.**  It doesn't matter what else he said, or what context he said it in.  That statement is false, irrespective of context. 

> having to deal with types for variables is an issue Having to deal with not getting an error when using an undeclared variable is an issue too.  Which is worse?  Well, at least in Java, if I get types wrong, my program stops and I know upfront there is a problem.  PHP does no such thing.

> a newbie using php doesn't have to bother with these things at allI'm not aware of any J2EE Servlet container that doesn't start in development mode, so neither does a new J2EE developer.

> i think you'll find way more web-hosts with php-support than java-support .. in some cases this is a valid argumentIrrelevant question. The correct question is, "Are there a sufficent quantity of hosting providers?" and the answer is yes for both.  It's pretty disingenous that people always bring this up.

---

### Post by phossal on 2007-02-13
> **LordHunter317 said:**
> That's not a sufficent point, in light of the issues I've raised with PHP

Sufficient for what? You and I both said the same thing. The sentence I interjected into this thread is a subset of the things you've said, but it's valid none the less. I made a simple comment. You argued that it was false, and then went ahead and validated it. I didn't voice an opinion on the *rest* of the things you've said. I certainly *don't* have to convince you that you should value php's flaws. I don't have to define *general*, or anything else. You've already stated the few things I was trying to communicate - whether they were important or not. I'm going to take a nap now.

---

### Post by lnostdal on 2007-02-13
> **LordHunter317 said:**
> You need to suggest why I should value flaws, especially such fundamental ones, over a higher learning curve. 
you forget that this is not about you .. a three-wheeled bike has critical flaws in its design given the right context

> **lordhunter]
**Because they're irrelevant to the correctness of that statement.**  It doesn't matter what else he said, or what context he said it in.  That statement is false, irrespective of context. 
[/quote]
do you expect me - or anyone else, to believe what you say here? actually said:**
> 
Having to deal with not getting an error when using an undeclared variable is an issue too.  Which is worse?

hey; i thought you where the one with the "facts"

[quote=lordhunter]
Irrelevant question. The correct question is, "Are there a sufficent quantity of hosting providers?" and the answer is yes for both.  It's pretty disingenous that people always bring this up.[/QUOTE]

nah, it's relevant .. almost every server i've worked on has had mod_php available (great for getting simple stuff i don't "care about" up fast) .. i can not say the same about java-based stuff

---

### Post by LordHunter317 on 2007-02-13
> **phossal said:**
> Sufficient for what?To prove PHP is better for "general" sites, whatever the hell that means.

> You and I both said the same thing.No, we have not.

> I made a simple comment. You argued that it was false, and then went ahead and validated it.I've done nothing of the sort, because I didn't say better for "general" sites.  I said I don't like either as an introduction for web programming, and listed reasons why.

> I don't have to define *general*, or anything else.Yes, you do.  That was the statement made.

[quote=Insotdal]you forget that this is not about you .. a three-wheeled bike has critical flaws in its design given the right context[/quote]Nor is that statement.  Stop trolling and respond seriously, or get reported.  I'm more than sick of your tripe.

> do you expect me - or anyone else, to believe what you say here?Yes.    At any rate, if the accusation is I've taken something out of context, the onus is on you to prove the statement has a different meaning in context.  So either do that, or be reported.  Anything else is tantamont to a personal attack.

> nah, it's relevant .. almost every server i've worked on has had mod_php available (great for getting simple stuff i don't "care about" up fast) .. i can not say the same about java-based stuffIgnoring the ancedotal nature of this statement and the fact I've already addressed it in part, it's still a red herring.  Try again.

---

### Post by ComplexNumber on 2007-02-13
ok, guys. cool it down, please. emotions seem to be running slightly too high. either that or the thread gets locked for a cooling off period.

---

### Post by lnostdal on 2007-02-13
> **lordhunter]Nor is that statement.  Stop trolling and respond seriously, or get reported.  I'm more than sick of your tripe.
[/quote]
"reported" -- lol -- how can that not be an argument? seriously said:**
> Yes.    At any rate, if the accusation is I've taken something out of context, the onus is on you to prove the statement has a different meaning in context.  So either do that, or be reported.  Anything else is tantamont to a personal attack.

i still have no idea what you're talking about here

[quote=lordhunter]
Ignoring the ancedotal nature of this statement and the fact I've already addressed it in part, it's still a red herring.  Try again.[/QUOTE]
i have no idea what you're saying here ..  is it not true that most servers i've worked on has had php readily available for me to use for quick simple tasks and that this has had benefits?

if opinions like these are reason enough to be "reported" i'd be more than happy to leave

---

### Post by LordHunter317 on 2007-02-13
> **lnostdal said:**
> i still have no idea what you're talking about hereThen I have little say other than you need to study the rules of logic and debate.  If you're goign to accuse me of making something out of context, then you have to prove with my statements that I actually did so.

> i have no idea what you're saying here ..  is it not true that most servers i've worked on has had php readily available for me to use for quick simple tasks and that this has had benefits?What I'm saying is your experience means nil.  Furthermore, Even if it did mean something, it's not relevant unless you can show that installing and configuring a Servlet container is really that big of a deal.

> if opinions like these are reason enough to be "reported" i'd be more than happy to leaveThe issue is you refusing to act in an adult manner towards me or really anyone.  When you're wrong you run away and you bait when the topic at hand is perfectly apparent.

---

### Post by ComplexNumber on 2007-02-13
ok, thats it. time out. the threads closed for a short while to give you both time to cool off. be nice :)

---

### Post by PriceChild on 2007-02-14
I'm re-opening this thread. As CK's offline and I feel 12 hours is a reasonable time so that other members may step into the debate if they wish to.

Final warning guys :)

---

### Post by lloyd mcclendon on 2007-02-14
define general - sounds rediculous but it does make sense.  php is better for general sites?  wtf does that mean?  

php is better for quick hack dirty sites that are one offs that you **don't have to maintain** and generally don't care about the quality of.  a long time ago, i wrote a webapp in coldfusion.  now i am maintaining said web app - PURE HELL.  forget it.  coldfusion an php are largely the same paradigm, everything mixed together.   <a href="doesEverything.php"> if you're interested in php, look at cf, it's not bad for quick dirty apps.

bad programmers love PHP.  good programmers think long term, for the full lifecycle of a project and usually realize, oh ****, 2 years from now when they want all kinds of new features this is going to be a total clusterfuck and a giant headache for me.  i had to learn the hard way on that one.  

web dev with java is a totally different animal.  setting up tomcat is really not a big deal, if you think it is than just do us all a favor and stick with php.  it is a serious time investment to get good at it, don't expect to be up and running with killer apps in a few days.  

the best thing about it is CHOICES.  there are hundreds of frameworks and tools available to you, you are free to pick and choose what you think will work best for you and continuously evaluate other tools to try and improve your environment.  gotta love all the choices on the other side of the fence.

but php vs jsp is like comparing apples and amd processors, it's just retarded.  jsp can be used by itself to develop entire webapps but that might be the dumbest thing one could do.  it's just one piece of the full j2ee puzzle.  once you get your own version of the puzzle put together, it's pretty damn cool.  i'd bet money that now, after months of tweaking my environment, i could develop any web app you could throw at me twice as fast that you could do with php.  the initial investment is not trivial, but the long term payoff is pretty impressive.

---

### Post by runningwithscissors on 2007-02-14
Yes. PHP is ugly and I shan't defend its rather embarrassing security record, as it is well famous.

However, you can write larger and maintainable projects in PHP. And there are tonnes of examples of those (CMS and forums softwares around the web for example).

---

### Post by phossal on 2007-02-14
I think the whole debate began in response to a comment I made. I was asked to clarify what I said, which I did several times. We boiled it down to a sentence, I think. After everyone else jumped in, and LordHunter was asked to clarify his *own* thoughts, he repeated what I said nearly verbatim. I didn't say PHP was without faults, nor did I say it was *better* in all situations than Java. I made a few simple statements. And that was it.

Whether or not bad programmers use php, or English-speaking countries fail to focus on content, or anything else is of little consequence. The definition of *general* isn't even necessary. Java requires more learning. Perhaps you prefer to say, a *bigger initial investment.* Java requires compiling. Java requires more components. 

There isn't any argument anymore (at least with *my* contribution), as Lord Hunter has stated the same things.

---

### Post by LordHunter317 on 2007-02-14
> **phossal said:**
> I think the whole debate began in response to a comment I made.No, it was in response to several.  Quit being disingenous.

 > After everyone else jumped in, and LordHunter was asked to clarify his *own* thoughts, he repeated what I said nearly verbatim.No, I did not.  If you can't understand the difference between "introductory" and "general" than please stop posting and go look up those definitions.

> I didn't say PHP was without faults, nor did I say it was *better* in all situations than Java. I made a few simple statements. And that was it.Which is hte problem.  Simple is a bad thing unless it's technically accurate.  As others have said besides me, your statements were anything but.

> The definition of *general* isn't even necessary.Yes, it is, to validate your statement.  

> Java requires more learning.No, I'm not sure that's true over the lifetime of a developer.  Upfront, sure.  But you haven't shown why that's a bad thing, so you still haven't supported yourself.

> There isn't any argument anymore (at least with *my* contribution), as Lord Hunter has stated the same things.But I haven't, because I've used them to support other statements.  The fact I'm not debating one point is irrelevant, because I'm still debating your *premise*.  If you can't understand that, please go read up on logical argument and debate.

---

### Post by phossal on 2007-02-14
:) This is totally pointless. You *did* say everything I said nearly verbatim. I *can* quote you. In fact, almost *everyone* repeated what I said to some extent - even the group of goofballs who *hate* me. But your last post did make something clear to me: you have wasted a lot of time as a result of me not plainly saying I didn't *have* a premise. But now we both know.

I think you have totally lost track of what you're trying to communicate. Java requires a bigger *initial* investment. It requires more components, and it requires compiling, among other things. That's what I was trying to say. What were *you* trying to say again?

I'll admit that I would go a step further and say: for *beginning* programmers php requires *a smaller* initial investment, *fewer* components, and *no* compiling. That's a turn-on for *most* beginning programmers because they can accomplish the tasks they want to without being bogged down. I didn't say it was the *right* way. I said, in general (and I defined general early on), php handles the tasks a *beginning* programmer would want to tackle. Is *that* what you meant by *premise?* *That* is what you're arguing against? If so, that's a *conclusion*, not a premise. The *premise* is what we've all agreed on - that Java requires a larger *initial investment*, etc, etc.

Definition of *general*: 
- Basic templates.
- Basic logic (if logged in/ if not logged)
- Basic database access

---

### Post by pmasiar on 2007-02-14
> **phossal said:**
> Wouldn't I have had to *say* that to be wrong about it? 

Wasn't that you who disliked quoting?

Here are your quotes:

> **phossal said:**
> If you ever have to participate in a Java-driven site, full of Enterprise Beans and remote calls, and JSP, you'll realize that it would be pretty difficult to think of a reason to use Java in a site at all for most *normal* projects. PHP is so well suited (as it was intended to be) for use in general web tasks that there is virtually nothing you can't do with it. 

Java makes possible the distribution of such radically complicated systems that I don't believe you should learn it *for web development* alone. Once you've sort of mastered Java, then you have to move on to Enterprise Beans, which has a fairly steep learning curve itself. If you don't know *why* you need Java for the web, you probably don't need it.

When you say "you have to move on to Enterprise Beans" IMHO it "in general" means that you have to learn EJB. For you possibly it means that you don't have to learn EJB.

> **phossal said:**
> I can boil down my point to a sentence: Between Java (Servlets, JSP, and EJB) and php, I feel php is much easier to learn, and is the easier language in which to implement, develop and maintain common solutions for a beginning programmer. 

Again EJB red herring.

BTW I agree with you that PHP is easier to learn, but It does not mean that you need to use EJB to create simple JSP pages (which will be similar to PHP) for enough "simple" pages "in general". And PHP is "in general" more messy language, whatever that might mean.

> **phossal said:**
> 
You have to learn *some* extension of the core java language, though, to develop web apps. You'll learn *servlets* or *jsp*. I brought up EJB because, unless you're developing the kind of complex application that uses EJB, it doesn't make much sense to *choose* a java alternative. PHP is easier to learn than any facet of Java. For general tasks, php is generally easier to implement. 

People might have perfectly good reasons to develop web pages in JSP without EJB, which you repeatedly deny, and then vehemently protest when I point to your misinformation.

> We're not allowed to bicker, remember? You're facing a ban, as am I. Careful. I could just make some things up, and claim you're wrong about them pmasiar. However, I won't. You prove yourself wrong often enough about the things you *do* say. 

You brought EJB red herring 3 times, I don't need to make it up. I wasted my time and got quotes. So *I* was right and *you* were wrong, on record.

Additionally, I really dislike your style of discussion. You like to belittle other people or attack other people in person, without talking about merit of the  opinion they expressed:

> **phossal said:**
> Hunter is a moron if he thinks I said you *have* to learn EJB to develop web apps in Java. 

As I just proved from your quotes (maybe you want to edit them out again) you said just that 3 times.

You also seems to believe (it is projection of your own approach?) that people are here in forum to gain allies and have influence. I believe that most people are like me: want to learn something and share the knowledge, without remembering old grudges, without attacking someone for opinion he expressed weeks ago.

>  That's why you were so anxious to jump in, isn't it? You have a bit of a grudge, and any hope of redeeming yourself is tasty, isn't it? 

No. I ignored all your posts until this thread, and I will ignore you again after posting this. I joined the "discussion" because you attacked Hunter in person when he was right and you were not, which I believe you have no right to do, even if you are annoyed with the way he quotes you.

> But this isn't the time. You've chosen the wrong ally, because he's equally unpopular.

I wonder why you repeatedly mention terms popular/unpopular? I am here not to gain popularity - what a worthless human being I would be if popularity in some forum was a measure of success for me. I am here to learn and help other to learn, and my allies are people who explain.

Your comments make for me my experience here less enjoyable, so I will just ignore them again.

For *you* seems to be important to "win" and to be "popular" - you will even misinterpret opinions of other people with snide remarks and projections of your own positions, to have last word. You won, I added you again on my ignore list and will not bother to read any of your replies. 

It is just not worth the time to argue with you.

You won - you feel better now? Congratulations.

---

### Post by phossal on 2007-02-14
> **pmasiar said:**
> It is just not worth the time to argue with you. You won - you feel better now? Congratulations.
You wrote out a page full of stuff and ended with *that?* That's *crazy*! Nothing about you or your contributions make me feel better. I'm not sure what the *point* of your contributions are. You *love* to give your opinion, but you rarely take the time to *help* anyone. As for him, I'm not sure what he's really trying to say. He asked for clarification, and I gave it. My statements are always so pathetically *simple*. I'm not sure what you're even offering, pmasair.

---

### Post by LordHunter317 on 2007-02-14
> **phossal said:**
> :) This is totally pointless. You *did* say everything I said nearly verbatim. I *can* quote you.[Where did I say PHP is better than J2EE for **general** sites?  I did in fact, not say this.  If you cannot quote me, then I consider this a personal attack, since you're trying to delibrately misinterpret my position.

> I think you have totally lost track of what you're trying to communicate. Java requires a bigger *initial* investment. It requires more components, and it requires compiling, among other things. That's what I was trying to say.**But that's not what you actually said.  You actually said something 100% different.**

You brought up the EJB red herring repeatedly and you use the nasty word "general" several times, neither of which are true, **nor were required to say what you wanted to say.**  Nevermind your statement is false, as I've said, JSPs do not require pre-compliation, the Servlet engine can compile them for you.


> php handles the tasks a *beginning* programmer would want to tackle.Which are?  Again, show me where you told me what they are.

You seem to equate "beginniner" with "quick and dirty".  That's not a definition I agree with.

>  The *premise* is what we've all agreed on - that Java requires a larger *initial investment*, etc, etc.No, it was not.  It was that PHP is better than Java for general sites.  Again, quit being disingenous.

> Definition of *general*: 
- Basic templates.Stop. You are wrong.  PHP does not provide this in the core distribution.

> - Basic logic (if logged in/ if not logged)PHP does not provide this in the core distribution, unless you count HTTP Basic Authentication.

So like I alluded to earlier, you don't know what you're talking about.  With both languages.

---

### Post by M$LOL on 2007-02-14
Well, I love php, but that's just me.

Depends on what your site needs, and which you're more comfortable with.

---

### Post by lnostdal on 2007-02-14
lol @ this thread

edit: 
here's a response i started on yesterday before it was locked btw. .. you know; to keep the stoopid going

> **LordHunter317 said:**
> Then I have little say other than you need to study the rules of logic and debate.  If you're goign to accuse me of making something out of context, then you have to prove with my statements that I actually did so.

i think i said or meant i didn't find any context

> 
What I'm saying is your experience means nil.

 -- what?   ..and of course this must be true since you say so .. lol

> 
  Furthermore, Even if it did mean something, 

what? my experience again? you're not sure?

> it's not relevant unless you can show that installing and configuring a Servlet container is really that big of a deal.

ah, so maybe using java and php is _equally_ easy then ..what was your original argument/point again? i forget

well - no, i'd like you to go first: "show how installing and configuring a servlet container is not really that big of a deal" .. also; apply it to actual newbies in practice (the "HTML-dudes" with limited admin-experience) - so it's not just your opinion speaking .. we gotta be scientific about this

> 
The issue is you refusing to act in an adult manner towards me or really anyone.

i think one difference between me and you is that i do not have to act 

> 
  When you're wrong you run away and you bait when the topic at hand is perfectly apparent.

i never run; i draw back into the shadows and reap the benefits of all the time i'm saving

---

### Post by supirman on 2007-02-14
*snip*

I usually lurk around the forums at points during the day when I need to take a quick break, but that's become much less enjoyable lately due to a few posters who act like spoiled 10 year olds.  

Real mature, folks.

---

### Post by PriceChild on 2007-02-14
I gave you guys a chance be re-opening the thread. In my opinion this has been wasted and you've done nothing with the opportunity, simply using it to bicker with each other and get no-where.

I seem to remember closing a thread on roughly the same tracks not so long ago... and with several of the same faces. May I please sum up what we have learnt...

1. There are many programming languages.
2. Different programming languages *may *be good for different things.
3. Everything else is a matter of opinion.

I suggest you all take the time you have until the next one of these threads to code something useful that the community needs...

Pricey

---

