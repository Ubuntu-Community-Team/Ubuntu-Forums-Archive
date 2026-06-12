---
title: "web programming question about urls..."
date: 2009-01-05
forum: Programming Talk
---

### Post by hockey97 on 2009-01-05
Hi, I would like to know if there is any way I can encrypt my urls???

 lets say I have  my account.php file  hosted on [www.dinner.com](www.dinner.com) .

well when people go to [www.dinner.com](www.dinner.com) and click to login It would show up on the url as [www.dinner.com/login.php](www.dinner.com/login.php). Now after you login you go to account.php. The url would look like this: [www.dinner.com/account/account.php](www.dinner.com/account/account.php).

it clearly shows the folder that the php file is in.

I have heard that these clues help out hackers on how to breaking or are able to download source code files and learn the structure of the website to have all control over it.

I want to know if I could make it like instead of [www.dineer.com/account/account.php](www.dineer.com/account/account.php)  to be something like this: [www.dinner.com/e14212141/144ead%fad%](www.dinner.com/e14212141/144ead%fad%) 

so that it still will find the file but yet to the client they won't know where the documents are located.

this also would help on image sources on any html. I mean like if you check the source code for html or javascript you can find the links to source codes and could download them and read those source codes.

---

### Post by Tomosaur on 2009-01-05
You can use the apache mod_rewrite to do this. [This](http://articles.techrepublic.com.com/5100-10878_11-5068743.html) gives a pretty good overview, but you'll need to read up on the technical side of things in order to understand how to use it properly.

Of course, there is no substitute for taking security considerations into account during the design phase.

---

### Post by pmasiar on 2009-01-06
URL rewriting is quite complicated, I would not advise to go there. 

In a much simpler way, you can just store mapping for next URL in a session info. But generating webpages with such encoded URLs looks like lots of pain for little gain. Better learn about securing your app, preventing SQL injection etc. If so many people are able to create secure apps without resorting to such convoluted trickery, so should be you :-)

Maybe first step could be to switch to language  with better security history than PHP has :-)

---

### Post by ufis on 2009-01-06
> **pmasiar said:**
> Maybe first step could be to switch to language  with better security history than PHP has :-)

Nothing wrong with PHP's security. It is just wrong implementation by unskilled/uninformed people that cause security holes in PHP applications.
The problem is with the implementation, not with the tool.

If you really feel strongly about hiding the directories that your php files are in (something I feel is not necessary if your implementation is secure) I would also suggest apache mod_rewrite.

Simple mod_rewrite tasks like hiding urls is fairly simple. Something like showing [http://www.dineer.com/account.php](http://www.dineer.com/account.php) in the address bar but actually displaying the [http://www.dineer.com/account/account.php](http://www.dineer.com/account/account.php) page is very simple to do.
Lots of maintenance though - for every page you want to hide (or at least every directory) you will have to have a mod_rewrite entry.
Adding a new page to your site would then probably mean adding another mod_rewrite entry.

Maybe it can be done simpler as the way I explain it. I am not *that* knowledgeable on mod_rewrite. I use it for simple things like having somepic.jpg fetch and display somepic.php which is a php dynamically generated pic.

*The big thing though is to secure your php application.* It is much easier for an attacker to gain access to your site via faulty php (or any other language) code than if they know in what directory your files are.
Exception for some properties files that you would not want anyone to know where they are located, but these will not (should not) be displayed in the url anyway.

---

### Post by drubin on 2009-01-06
> **ufis said:**
> Nothing wrong with PHP's security. It is just wrong implementation by unskilled/uninformed people that cause security holes in PHP applications.
The problem is with the implementation, not with the tool.

Bad work man blames his tools.... 


> Maybe first step could be to switch to language with better security history than PHP has 
Nothing else to say on this topic. But i feel always suggesting another language is not productive as well.

---

### Post by Cracauer on 2009-01-06
> **hockey97 said:**
> 
well when people go to [www.dinner.com](www.dinner.com) and click to login It would show up on the url as [www.dinner.com/login.php](www.dinner.com/login.php). Now after you login you go to account.php. The url would look like this: [www.dinner.com/account/account.php](www.dinner.com/account/account.php).

it clearly shows the folder that the php file is in.

I have heard that these clues help out hackers on how to breaking or are able to download source code files and learn the structure of the website to have all control over it.


This is wrong on so many levels.

First of all, it's extremely rare that bugs in apache made it deliver source code for scripts in the past.  Must have been 10 years or so since the last one.

Second, your script should be written in a manner that even if people read the source code they still can't break into your system.

Actual breakins that happen in the real world right now will give people full access anyway. The location of the script is something that no current attacks need.

---

### Post by pmasiar on 2009-01-06
> **ufis said:**
> Nothing wrong with PHP's security. It is just wrong implementation by unskilled/uninformed people that cause security holes in PHP applications.
The problem is with the implementation, not with the tool.

Exactly. Problem is that there are way too many bad PHP examples around, and it is hard to learn good practices by reading existing code (and beginner cannot tell if example is good or bad). OTOH when using Python/Django, decent **working** 'hello world' app is generated for you, uncluding model-view-controller structure, object-relational mapper (so beginner can get started without learning SQL), edit/update for each table and best practices directory structure. So it is much easier to create good maintainable project. 

In 95% cases, Python/Django is better approach. The only exception would be someone who knows HTML fairly well, and wants to create very simple pages with minimal dynamic content. Django provides guiding hand all the way, unlike raw PHP.

The problem is that in 95% people who advocate PHP have no clue what MVC pattern is, and why it should be used (and never used it).

---

### Post by drubin on 2009-01-06
> **pmasiar said:**
> Exactly. Problem is that there are way too many bad PHP examples around, and it is hard to learn good practices by reading existing code (and beginner cannot tell if example is good or bad). While when using Python/Django, decent **working** 'hello world' app is generated for you, uncluding model-view-controller and best practices directory structure. So it is much easier to create good maintainable project. 

In 95% cases, Python/Django is better approach. The only exception would be someone who knows HTML fairly well, and wants to create very simple pages with minimal dynamic content. Django provides guiding hand all the way, unlike raw PHP.

I agree with you about bad examples!

But the point is php is not a "bad" language same thing with Java they both have their place in the coding world.  Most Java programs are written rather badly because most people started off coding in Java and didn't know any better. Similar idea with php.

Rather then always shun php as a bad language maybe try and help users understand its place in the web environment. 

Coding is not about the language but the coder. You can see a great programmer even if they are coding in a bad language. The same goes with python you could tell if the person coding was a "code monkey" or a coder by the way they code.

---

### Post by pmasiar on 2009-01-06
> **drubin said:**
> Rather then always shun php as a bad language maybe try and help users understand its place in the web environment. 

That's exactly what I am doing! :-)

IMHO Python and PHP focus on same niche (web programming) but because of Python being general language (and designed, not "grown"), it is better fit for web apps, especially now with Django. Really, try Django before talking how PHP is good.

If your app has more than 2 screens, you are so much better off using MVC pattern, and for beginner it is not obvious how to start MVC in PHP because PHP is exactly non-MVC. It takes lots of efforts to write MVC in PHP, while in Django it is 100% effortless - structure is generated for you whan you start new project.

And my favorite feature in web apps is Turbogears and Kid for templating - where Python is used for in-template expression, via extremely cool XML tricks.

> Coding is not about the language but the coder. You can see a great programmer even if they are coding in a bad language. 

Yes but it is easier to be decent programmer in language like Python, because it's structure and community culture is more conductive to apply best practices.

It is easier to be decent craftsman is you use decent tools. And with shitty tools, only real guru can produce decent results. Average craftsman is doomed to failure.

---

### Post by drubin on 2009-01-06
> **pmasiar said:**
> That's exactly what I am doing! :-)

IMHO Python and PHP focus on same niche (web programming) but because of Python being general language (and designed, not "grown"), it is better fit for web apps, especially now with Django. Really, try Django before talking how PHP is good.

I think this is turning into a flame war php vs python. :)

Back onto the URL re-writing thing.

Url re-writing can be great for search engine optimization. some great examples to look at would be wordpress with their /year/month/date/posts-in-english-text is much better then  posts.php?id=234234  How is that make sense to  a standard user?

---

### Post by hockey97 on 2009-01-07
Thanks for the replies. I do know about sql injection and many other hacks hackers use.

I am trying to make my website as secure as I can. I already filtered all inputs for sql inject of any programming code input. 

Now I am working on protecting my website from brute force attacks and also DOS attacks which is hard.

I do know hackers. I asked alot of stuff on what hackers do.

So I know that source code or finding any source code helps in a way. 

So I really want to make sure hackers are in the dark. So I want to encode the url to hide directories where the website files are on my server.

I have seen websites that do encode their url. 

I know a hacker who broke into a college computer system just by going on there website and looking at the source code to the script that logs users into their system to see grades and other information.

The hacker just had to copy that url and past it into the browser and a window poped up and asked if you want to download it which he did.

So I want to prevent such a thing with my website.

---

### Post by Tomosaur on 2009-01-07
> **hockey97 said:**
> 

The hacker just had to copy that url and past it into the browser and a window poped up and asked if you want to download it which he did.

So I want to prevent such a thing with my website.

Your source code shouldn't contain vital information (usernames, passwords, database connection info etc) which would leave the site vulnerable. If you're doing password comparisons with hard-coded strings, for example, then you're asking to be cracked.

Source code is logical.
Information is not.

Keep the two as separate as they can possibly be.

---

### Post by drubin on 2009-01-07
> **Tomosaur said:**
> Your source code shouldn't contain vital information (usernames, passwords, database connection info etc) which would leave the site vulnerable. If you're doing password comparisons with hard-coded strings, for example, then you're asking to be cracked.

/me wonders where you keep your DB connection details?

---

### Post by pmasiar on 2009-01-07
> **hockey97 said:**
> I do know about sql injection and many other hacks hackers use.
... I know a hacker who broke into a college computer system 

You are young and not acculturated... but between us programmers, it is kind of rude to confuse "hackers" and "crackers". 

[http://en.wikipedia.org/wiki/Hacker](http://en.wikipedia.org/wiki/Hacker) - clueless journos ruined the original meaning of "hacker", but there is no reason for a programmer to continue repeating the lie. Especially when talking to other programmers. :-)

---

### Post by snova on 2009-01-07
> **hockey97 said:**
> I know a hacker who broke into a college computer system just by going on there website and looking at the source code to the script that logs users into their system to see grades and other information.

The hacker just had to copy that url and past it into the browser and a window poped up and asked if you want to download it which he did.

So I want to prevent such a thing with my website.

That is the result of misconfiguring the server. Either somebody forgot to deny requests into a particular folder, or the server's mime types weren't set up correctly. Or something else, this isn't my area of expertise.

Screwing with your url's is just annoying...

---

### Post by Mickeysofine1972 on 2009-01-08
I would say that your better using a MVC system like CodeIgniter to manage your URLs

This is one of the best and simple to use PHP frameworks I've ever used and to this day I swear by it.

heres a link: [http://www.codeigniter.com](http://www.codeigniter.com)

Mike

---

### Post by Tomosaur on 2009-01-10
> **drubin said:**
> /me wonders where you keep your DB connection details?

In some other file which is not available to the outside world, perhaps?

Just a quick (and kind-of related, I guess) example is the use of the web.config file in asp.net websites. This file can contain information such as the database connection string, which you then call from the back-end code as a run-time property rather than a hard coded string. While web.config is only an XML file and can be accessed by someone with console access to the server, at least the web server itself will refuse to serve up the file to visitors to your site, even if they explicitly request it. You can even add additional layers of security (encrypting the connection strings etc) if you want.

You don't want to be doing this kind of stuff in your php web page code (particularly if the server goes crazy and starts sending people the php files rather than executing them).

It is far, far easier to keep a separate configuration file secure from prying eyes than it is for you to keep live code secure (ala PHP).

Information (especially information which can lead to a security risk) should be kept outside of the source file, if at all possible. Just like supporting multiple languages in your software, I guess - you keep the UI strings in a seperate, maintainable file which you can modify as necessary, and use your source code to call the relevant string for the required language as and when you need it.

Besides, if you ever want to change the location of your database server - would you rather modify multiple source files, or just one single file?

---

### Post by pmasiar on 2009-01-10
This is **exactly** why I recommend **against** PHP for web programming: because beginner (majority of examples on web; also, simplified code for sake of example) has no idea what best practices are, and how to solve those problems in a right way. Beginner has **no idea** that there are better waus to solve the problem, and she is doing it wrong way - and no idea she should look for a better way.

Compared to that, Django or Turbogears would create for a beginner empty web project with proper structure, model, view-controller, config file, all directories - whole shebang. And without any efforts, beginner can start coding using the best practices.

---

### Post by Mickeysofine1972 on 2009-01-10
Actually, I wrote a CodeIgniter system that does exactly that, you can download it from my site and read about it on the CI forums where I have put easy to follow instructions.

It works along the lines of ruby on rails creates model/views and controllers for what ever you fancy

Mike

---

### Post by drubin on 2009-01-10
> **pmasiar said:**
> Compared to that, Django or Turbogears would create for a beginner empty web project with proper structure, model, view-controller, config file, all directories - whole shebang. And without any efforts, beginner can start coding using the best practices.

But will they understand any thing they are using?

I am very much a bottom up approach them them learn best practises and apply them. 

In essence you are suggesting that we should all aim to understand nothing about how the systems work just use it because it is good practice and it is easy?

There are similar such frame works in PHP.... Weather people choose to use them or out is a *****personal***** choice. 

Often one of the best learning experiences is failing. We all have to fail some time and for a beginner failing at something they are new to is expected it is part of learning. Just like falling down is part of walking.

---

### Post by pmasiar on 2009-01-10
> **drubin said:**
> But will they understand any thing they are using?

Of course they will not know which best practices they are using - that's the whole point of using that approach: it is painless. Later they may learn about the 'whys' of that approach, but as beginners, they have hands and heads full, no point to increase the mental load.

But even if they don't know best practices, and why do it that way, they may benefit from them, making code better structured.

You obviously never used empty project generated by Tubogears, did you? It is programming like always, you just use proper conventions.

drubin> In essence you are suggesting that we should all aim to understand nothing about how the systems work just use it because it is good practice and it is easy?

LOL this is classic rhetorical trick: [http://en.wikipedia.org/wiki/Straw_man](http://en.wikipedia.org/wiki/Straw_man) and I am not falling into your trap :-)  I never said that, and you very well know that, so stop pretending.

drubin> There are similar such frame works in PHP.... Weather people choose to use them or out is a *****personal***** choice. 

Yes, but beginners who need them most are not aware of them, so they don't use them, and don'e even know they should learn about them, and why. Django or Turbogears solves this dilemma, because of Python's mantra: "there should be one obvious way to do it right". This principle is really important for Python community, and it is one of parts of the Python community which makes is better choice for beginners. 

PHP lacks that approach, it is more TIMTOWDI as Perl is.

>  Often one of the best learning experiences is failing. We all have to fail some time and for a beginner failing at something they are new to is expected it is part of learning. Just like falling down is part of walking.

Using the strawman trick you tried on me, I could say: "Oh, so you are basically saying that the more we fail the more we learn? And total failure is the most learned man of all?" :twisted:

But I won't do that. I know that failing is important part of learning, but failing makes sense when student can learn from the failure. It is not obvious to me (and you do not bother to substantiate your claim) how student benefits from **not** having correct code structure, and not even **know** that there are better ways to do it. Student learns by reading good code, having good example is beneficial. But because of PHP culture of [http://en.wikipedia.org/wiki/Worse_is_better](http://en.wikipedia.org/wiki/Worse_is_better) , PHP beginner often learns from code of other beginners, equally bad as her own.

---

### Post by Username33333 on 2009-01-10
I think this my help for new proggraming issues with new people.

---

### Post by Tomosaur on 2009-01-11
> **drubin said:**
> 
Often one of the best learning experiences is failing. We all have to fail some time and for a beginner failing at something they are new to is expected it is part of learning. Just like falling down is part of walking.

I agree with this to an extent - but there is a reason why we have an education system: so you don't repeat the mistakes of the past. If everybody just started from scratch every single time they tried to learn something new, then the general sum of knowledge would never increase past a certain point.

A programmer knows how to solve a problem.
A good programmer knows when the problem has already been solved.

There is absolutely zero point in failing at something if you already know the problem has been solved. Would you rather make a mistake, or just do it the proven way and work out why it's the best (the best does not necessarily mean it is good) solution later on?

---

### Post by drubin on 2009-01-11
> **Tomosaur said:**
> There is absolutely zero point in failing at something if you already know the problem has been solved. Would you rather make a mistake, or just do it the proven way and work out why it's the best (the best does not necessarily mean it is good) solution later on?

To quote a some one i know.
> I would re-invent the wheel a 100times over if it would mean I would learn something.

---

### Post by Tomosaur on 2009-01-11
> **drubin said:**
> To quote a some one i know.

There's nothing wrong with finding out how and why something works - but you are still better off taking the advice of people who have already worked through the problem at hand and have shown you a better way. The whole concept of passing on information (education, the internet, parenthood) is that you do not have to repeat the mistakes those who have gone before you have made and worked through. Sure, you can always **choose** to put your hand in a fire after somebody has told you it will hurt like hell, but you would be **better off** if you didn't sacrifice your hands for the sake of finding out what fire feels like.

---

### Post by drubin on 2009-01-11
> **Tomosaur said:**
> There's nothing wrong with finding out how and why something works - but you are still better off taking the advice of people who have already worked through the problem at hand and have shown you a better way. The whole concept of passing on information (education, the internet, parenthood) is that you do not have to repeat the mistakes those who have gone before you have made and worked through. Sure, you can always **choose** to put your hand in a fire after somebody has told you it will hurt like hell, but you would be **better off** if you didn't sacrifice your hands for the sake of finding out what fire feels like.

I think your analogy is far off I with putting your hand into a burning fire.

I think a much better suited one would be falling off your bicyle while trying to learn to ride it.

Yes you don't jump right into it and race in competitions so falling off a tiny bike going at 5km per hour isn't exactly going to hurt most people. But you will learn not to turn too far left into corners.

Now I am not saying do not learn from other people knowledge quite the opposite I am saying learn from their implementations and try and improve apon them.

Using a frame work that is already written to do what it is supposed to provides very little learning. Yes it most certainly might provide better code but was that code yours???

---

### Post by slavik on 2009-01-11
mod_rewrite is something definately worth learning. Because there will be that one day when you are asked "Have you ever worked with mod_rewrite?" and you will be able to answer "A little bit" vs. "never heard of it"

---

### Post by drubin on 2009-01-11
> **slavik said:**
> mod_rewrite is something definately worth learning. Because there will be that one day when you are asked "Have you ever worked with mod_rewrite?" and you will be able to answer "A little bit" vs. "never heard of it"

To add to slavik mod_rewrite is an [apache module]("httpd.apache.org/docs/2.0/mod/mod_rewrite.html").

@slavik thanks for bring it back on track.

---

### Post by Tomosaur on 2009-01-12
> **drubin said:**
> 
Using a frame work that is already written to do what it is supposed to provides very little learning. Yes it most certainly might provide better code but was that code yours???

I'm not specifically talking about using a framework - just tried and true practices to solve a particular problem. For example: open source software uses this exact approach.

---

