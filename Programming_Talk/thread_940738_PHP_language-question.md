---
title: "PHP language-question"
date: 2008-10-07
forum: Programming Talk
---

### Post by hoboy on 2008-10-07
I want to start a new web language, I have google I want to learn a language that is widelly used, it seemed like php is, i am right that php is a very popular web language ?
and how is the curve of learning it ?
tks

---

### Post by pmasiar on 2008-10-07
see stickies.

PHP is popular but Python is arguably more useful - more generic, useful also outside of web, and easier to learn because of more logical design.

Also, read links in my sig - how to ask questions to get better answers. :-)

---

### Post by themusicwave on 2008-10-07
The major web languages are(in no particular order):

PHP
Python
Perl
ASP .Net
Java (JSP and such)

I would say for someone just learning I would stick to the PHP,Python,Perl subset.  This is primarily because ASP .Net requires expensive tools.  Additionally, .Net and Java are significantly more complex than the others.

PHP is certainly the most common of the three on webservers.  One major consideration your need to look at is what does you target server run.  Often, I would prefer Python, but if a server only supports PHP then I use PHP.

If you don't have a target webserver, then pick whatever you like and find a server that supports it.  For my wedding website I used Python because I liked it best.  So I wrote it first on my computer and then got some Python hosting for it.

---

### Post by Reiger on 2008-10-07
Right. Let's get this out of the way: Python can be used. So can PHP. How useful your language is depends more on the programmer and his needs than on the language itself, and at any rater PHP conveniently offers more things than you will likely need for more subjects than you'll ever touch.

At any rate PHP is a very popular CGI ('webprogramming') language, with great support on various platforms. The learning curve is, IMO, a minor bump in an otherwise straight line. Of course you will sooner or later run into a few particular cases in which PHP might act counter intuitive to you but that will be the case with virtually every language, anyways. 

E.g.: if you're used to Java you will be at first befuddled by why on earth $my_array=array_push($my_array,$my_additional_array) will cause your $my_array to become a number; but if you were used to C, and pointers you would've typed: array_push(&$my_array,$my_additional_array) and all would've been fine.

---

### Post by DrMega on 2008-10-07
> **hoboy said:**
> I want to start a new web language, I have google I want to learn a language that is widelly used, it seemed like php is, i am right that php is a very popular web language ?
and how is the curve of learning it ?
tks

PHP is really popular, and will meet most people's needs. As someone else already said, an important consideration is who will be hosting your website. Different hosts implement different features, usually a subset of the range available. PHP is on most commercial hosting packages that I've looked at.

PHP is, in my opinion, really easy to learn. Partly because it lets you get away with a lot of stuff that other languages wouldn't allow, but mainly because it is just a clear, well structured language. There is also the added bonus that it can be almost as high level or low level as you need, as there are huge libraries of functions of stuff for it.

You also need to ask yourself what you want out of it. Are you looking to do this for fun, some specific project, or to build your career, or some other reason(s)? If it's for the career, then look on the various recruitment sites and see what employers are demanding. If it's for fun then your options are limitless.

---

### Post by pmasiar on 2008-10-07
Even if PHP is relatively easy to learn, it is not as clean and simple as Python is (OOP helps). If OP is green beginner, you are **much** better off to learn programming first, without additional complexity of HTML and web. Just plain commandline, cannot get any simpler than that.

---

### Post by ghostdog74 on 2008-10-07
> **hoboy said:**
> I want to start a new web language, I have google I want to learn a language that is widelly used, it seemed like php is, i am right that php is a very popular web language ?
and how is the curve of learning it ?
tks

yes PHP is a popular web language. curve of learning? depends on whether you have any prior experience in programming. Even if you don't have any, PHP is easy to learn. So what are you waiting for?

---

### Post by LaRoza on 2008-10-07
> **hoboy said:**
> I want to start a new web language, I have google I want to learn a language that is widelly used, it seemed like php is, i am right that php is a very popular web language ?
and how is the curve of learning it ?
tks

PHP, Python and Ruby are very popular for server side scripting. Any language can be used for it though, even C (don't do it though, it is very TDS).

The basics of PHP are very easy (C syntax, procedural, with OO added).

PHP also allows for very poor design as you can put PHP code anywhere and that makes messy code very tempting in the beginning.

PHP is extremely easy to find good hosts for. I use freehostia.com, which is completely free and has a lot to offer.

My wiki has information on all the languages listed.

---

### Post by DrMega on 2008-10-08
> **LaRoza said:**
> PHP also allows for very poor design as you can put PHP code anywhere and that makes messy code very tempting in the beginning.

There is that:)

I'm not sure you can really get round that fully, you can even write bad but functional code in a strongly typed fully object oriented language.

I guess one of the hardest jobs for a learner programmer is finding *good* examples. Not because there aren't any (there are many), but because there are so many bad examples floating about as well.

If I had to re-learn from the beginning, I reckon I would start by buying a tutorial book of the format that leads you through a whole project (there are so many about), and would use the web to supplement it, rather than the other way round. I wouldn't recommend anything from Sams though (Teach Yourself Advanced Particle Physics in 10 Seconds type of thing).

---

### Post by LaRoza on 2008-10-08
> **DrMega said:**
> There is that:)

I'm not sure you can really get round that fully, you can even write bad but functional code in a strongly typed fully object oriented language.


You can, by putting the static markup in separate files (or a database) and including them. My site has no markup in index.php for example, just a web page object (my own class).

@OP Also, I forgot. If you are not already knowledgable about XHTML and CSS, then PHP will be...confusing at best and useless at worst. If you want to learn to program, then I recommend Python. PHP is only a good choice as a first language if you are already knowledgable about webdesign.

---

### Post by DrMega on 2008-10-08
> **LaRoza said:**
> You can, by putting the static markup in separate files (or a database) and including them. My site has no markup in index.php for example, just a web page object (my own class).

I know. I meant you can't really get round the fact that many languages let you get away with a lot of bad practices. I didn't mean that there is no way to avoid the bad practices, just that someone with little or no experience might not know what practices are considered good or bad.

---

### Post by LaRoza on 2008-10-08
> **DrMega said:**
> I know. I meant you can't really get round the fact that many languages let you get away with a lot of bad practices. I didn't mean that there is no way to avoid the bad practices, just that someone with little or no experience might not know what practices are considered good or bad.

Well, PHP seems to encourage it a bit more than other languages. It is a fine language, except for its global namespace and its weak typing.

---

### Post by DrMega on 2008-10-08
> **LaRoza said:**
> Well, PHP seems to encourage it a bit more than other languages. It is a fine language, except for its global namespace and its weak typing.

That's why I suggested it is good for beginners. You can get something functioning quickly for very little effort.

---

### Post by LaRoza on 2008-10-08
> **DrMega said:**
> That's why I suggested it is good for beginners. You can get something functioning quickly for very little effort.

Only if you know XHTML, otherewise, it is an awkward CLI language (or GTK).

---

### Post by ghostdog74 on 2008-10-08
> **LaRoza said:**
> it is an awkward CLI language (or GTK).how so? any examples?

---

### Post by LaRoza on 2008-10-08
> **ghostdog74 said:**
> how so? any examples?

Well, my attempts to use PHP for CLI apps were awkward. Makes sense, as PHP was originally just C libraries for a single person's home page.

---

### Post by ghostdog74 on 2008-10-08
> **LaRoza said:**
> Well, my attempts to use PHP for CLI apps were awkward. Makes sense, as PHP was originally just C libraries for a single person's home page.
what were you trying to do back then? I have used PHP for cli apps and its fine. Its just like Perl.

---

### Post by LaRoza on 2008-10-08
> **ghostdog74 said:**
> what were you trying to do back then? 

I don't remember. I just remember that with my knowledge of PHP and Python (I knew more PHP at the time), Python was easier to use for what I was doing.

> 
I have used PHP for cli apps and its fine. Its just like Perl.

"Just like Perl"? I wouldn't call that "fine" :-D

---

### Post by ghostdog74 on 2008-10-08
> **LaRoza said:**
> 
"Just like Perl"? I wouldn't call that "fine" :-D
i mean the syntax. And when i say fine, i mean its fine to use PHP for command line apps. Its just another scripting language with "batteries"

---

### Post by LaRoza on 2008-10-08
> **ghostdog74 said:**
> i mean the syntax. And when i say fine, i mean its fine to use PHP for command line apps. 

I suppose. I want better than fine though.

> Its just another scripting language with "batteries"
I wouldn't say that, "just another" implies equality. PHP lacks a lot when compared to other languages when it is outside the webserver.

---

### Post by ghostdog74 on 2008-10-08
> **LaRoza said:**
> 
I wouldn't say that, "just another" implies equality.

let me clarify. "just another" doesn't imply equality but just "it can be used to program cli apps as well"

> 
 PHP lacks a lot when compared to other languages when it is outside the webserver.
lacks what alot? Pls give an example and treat this as my learning experience.

---

### Post by LaRoza on 2008-10-08
> **ghostdog74 said:**
> let me clarify. "just another" doesn't imply equality but just "it can be used to program cli apps as well"

Oh, OK. I know it can be, but it isn't what I'd recommend for using to learn to program though.

> 
lacks what alot? Pls give an example and treat this as my learning experience.
Well, I am not entirely familiar with the entire standard library of any language, but PHP lacks a lot that I've seen that Python has. Even if it has everything Python has, it has this type of namespace: [http://www.php.net/quickref.php](http://www.php.net/quickref.php). Now, I had when I read your statement thought of a few functions Python has, but I didn't think PHP had and I searched that and it turns out PHP does have those particular ones, but the fact I use to your my browsers searching in page function to find it is a bad sign. No logical structure.

Also, PHP isn't widely used for non web related tasks. It was originally intended for Personal Home Pages, and its design reflects that still.

---

### Post by pmasiar on 2008-10-08
> **ghostdog74 said:**
> [PHP] lacks what alot? Pls give an example and treat this as my learning experience.

- OOP. Namespaces make programming so much manageable, instead of global namespace of 5000 functions
- common design. Different but similar functions have parameters in different order - obviously added by different people without the unifying idea.
- designing UI without MVC pattern is abomination, no excuses.
- weakly typing is wrong. Right way is dynamic but strong typing: less quirks, less unexpected surprises.

Yes, hosting is commonplace and cheap, but PHP as language sucks, IMHO.

---

### Post by ghostdog74 on 2008-10-09
> **pmasiar said:**
> - OOP. Namespaces make programming so much manageable, instead of global namespace of 5000 functions

I think newer version of PHP addresses this.

> 
- designing UI without MVC pattern is abomination, no excuses.

i am sure there PHP MVC frameworks around

> 
- weakly typing is wrong. Right way is dynamic but strong typing: less quirks, less unexpected surprises.

maybe will be addressed in future versions?

> 
Yes, hosting is commonplace and cheap, but PHP as language sucks, IMHO.
its all in the mind. if you think it sucks, then it sucks :)

---

### Post by LaRoza on 2008-10-09
> **ghostdog74 said:**
> 
its all in the mind. if you think it sucks, then it sucks :)

Nope, my vacuum is still not working, Mr. Geller.

---

### Post by drubin on 2008-10-09
> **ghostdog74 said:**
> I think newer version of PHP addresses this.


i am sure there PHP MVC frameworks around


maybe will be addressed in future versions?


its all in the mind. if you think it sucks, then it sucks :)

1) Yes it does
2) Yes there are code [http://codeigniter.org/](http://codeigniter.org/) | [http://drupal.org/](http://drupal.org/) | [http://smarty.net](http://smarty.net) 
3) Yes php 6 will have added features. Lots of them

4) A bad work man blames his tools.

---

### Post by DrMega on 2008-10-09
> **LaRoza said:**
> Only if you know XHTML, otherewise, it is an awkward CLI language (or GTK).

You don't need to know xhtml or even plain old fashioned html (although without that knowledge you'd be quite limited in what you could do web wise).

When I was finding my feet with PHP, I deliberately avoid any html at first just to remove unnecessary complexity (although I'm fine with html). My first php page did nothing more than some basic arithmetic and a plain text output into a page.

---

### Post by LaRoza on 2008-10-09
> **DrMega said:**
> You don't need to know xhtml or even plain old fashioned html (although without that knowledge you'd be quite limited in what you could do web wise).

Ok, "need" as in "needing air" is not right.

> 
When I was finding my feet with PHP, I deliberately avoid any html at first just to remove unnecessary complexity (although I'm fine with html). My first php page did nothing more than some basic arithmetic and a plain text output into a page.

Um. How is that an advantage or even desirable? It works, yes, but it is not valid, requires the use a server and a web browser (when Python and Ruby have interactive prompts).

---

### Post by rnodal on 2008-10-09
> **LaRoza said:**
> Ok, "need" as in "needing air" is not right.



Um. How is that an advantage or even desirable? It works, yes, but it is not valid, requires the use a server and a web browser (when Python and Ruby have interactive prompts).

There is also php-cli which works great.

-r

---

### Post by LaRoza on 2008-10-09
> **rnodal said:**
> There is also php-cli which works great.

-r

Yes, I know. I mentioned that. I haven't forgotten about it. I don't know about "works great", as I said it was awkward to use at times.

---

### Post by ghostdog74 on 2008-10-09
> **LaRoza said:**
> (when Python and Ruby have interactive prompts).

there are no lack of programmers in this world.:)
[phpsh](http://www.phpsh.org/)

---

### Post by rnodal on 2008-10-09
> **LaRoza said:**
> Yes, I know. I mentioned that. I haven't forgotten about it. I don't know about "works great", as I said it was awkward to use at times.

I'm sorry. That's what happens when you just read the last post only. I'm sorry again.

-r

---

### Post by pedrotuga on 2008-10-09
If we take away the typical easily identified ones, this is probably the most recurrent discussion.
It wasn't even the topic starter to  come up with it, he just asked if php was appropriate to get started.

My answer is yes, it is very simplified and therefore simpler. I believe ( in fact i know it for a fact ) its creator valued simplicity and easy usage. One can argue that structural strictness, naming integrity and others were disregarded. Well... that can actually be true, it just turns out not be much of a turn down compared with positive characteristics I just pointed.

PHP is probably the most used language in web application development at the moment.

I haven't heard a single PHP programmer saying that python, ruby, perl or others are worse structured or worse designed in general than PHP.
I haven't really done any ruby and I am not so fluent with perl, but python syntax is for sure cleaner than PHP, and many other languages.

Deployment and documentation have central importance in here. For the same reason PHP is a hugely popular web scripting it didn't became popular for desktop applications, its UI libraries/bindings have a non trivial deployment while deploying a PHP webapp is about as trivial as it can get.
As for documentation PHP.NET is worthy of the word 'masterpiece'. A search for 'documentation' on google will return php.net on the top of the list.

Yes, there is many PHP MVC frameworks, in fact more and more diverse than in any other language.
Yes, there is kick *** software written in php. Just google 'open source php'.
No, there is nothing in PHP that encourages poor code. If I should give an honest opinion about that I would say that is a rather lame argument. But that's just my opinion.

To touch the syntax itself a bit... It is very easy. A beginner can do a lot just by using simple function calls, the access to data structures is just there to the joy of the masses. Using the same syntax one can use an array as a stack, a queue, hashtable, tree, list, etc.
Automatic casting does save a lot of work too.

General string manipulation is not really as deathly powerful as in perl, but it comes really close to it, keeping it very simple. 

I would say PHP is a whole new concept, is a bit like rock & roll, it came to shake right away, no mater if it doesn't' follow all the rules or if it does something supposedly wrong, it just rocks, and it's here to stay.

All this being said, I use more python and perl these days than PHP, my own choices.

SO.. don't get full by all the insults made to PHP, it is a very capable language (these forums we are using are written in PHP for example).
Python, perl (and many other i believe) are also great languages, made also by very intelligent people. It really isn't a big of a deal if you pick one over the other. Just enjoy the technology.

---

### Post by LaRoza on 2008-10-10
> **ghostdog74 said:**
> there are no lack of programmers in this world.:)
[phpsh](http://www.phpsh.org/)

I guess I should google first eh? :-)

Well, Python has a much bigger user base and demand on the desktop and more portability (the same arguments about using PHP on the server, over Python...)

---

### Post by DrMega on 2008-10-10
> **LaRoza said:**
> Um. How is that an advantage or even desirable? It works, yes, but it is not valid, requires the use a server and a web browser (when Python and Ruby have interactive prompts).

But the OP was talking about web development I thought, so you'd need a server and browser anyway.

---

### Post by LaRoza on 2008-10-10
> **DrMega said:**
> But the OP was talking about web development I thought, so you'd need a server and browser anyway.

Yes, but I said that to learn to programm with PHP you should know XHTML otherwise it is just a poor method of doing things that are much easier in other languages. I also said PHP is a good first language if one already is familiar with web design.

You said it could be used without using XHTML, which is a silly thing, because one can use other languages and more convenient interfaces.

---

### Post by DrMega on 2008-10-10
> **LaRoza said:**
> Yes, but I said that to learn to programm with PHP you should know XHTML otherwise it is just a poor method of doing things that are much easier in other languages. I also said PHP is a good first language if one already is familiar with web design.

You said it could be used without using XHTML, which is a silly thing, because one can use other languages and more convenient interfaces.

It depends on who you're going to ask to host your finished site. If the objective is to learn web development with a view to ultimately building a site which is going to be live, it would be best to learn a language that most hosting companies support. PHP is a safe bet because most hosting firms support it nowadays.

---

### Post by ghostdog74 on 2008-10-10
> **LaRoza said:**
> Yes, but I said that to learn to programm with PHP you should know XHTML otherwise it is just a poor method of doing things that are much easier in other languages. I also said PHP is a good first language if one already is familiar with web design.

You said it could be used without using XHTML, which is a silly thing, because one can use other languages and more convenient interfaces.

Totally not true.

---

### Post by LaRoza on 2008-10-10
> **ghostdog74 said:**
> Totally not true.

You think using PHP on a server and using a browser to get the results is not silly compared to Python, Ruby (and now, PHP) interactive prompts and scripts?

Also, your Swiftian rebuttal has me staggering.

---

### Post by ghostdog74 on 2008-10-10
> **LaRoza said:**
> You think using PHP on a server and using a browser to get the results is not silly compared to Python, Ruby (and now, PHP) interactive prompts and scripts?

let me clarify again. This statement made by you
[QUOTE=LaRoza]
You said it could be used without using XHTML, which is a silly thing, because one can use other languages and more convenient interfaces.
[/quote]
I said its not true, because PHP can be used without using XHTML, just like any other languages. I am not talking about the web. You can write PHP scripts to automate tasks just like any other, and that's not silly

Does that clarify what i meant?

---

### Post by pedrotuga on 2008-10-10
I am not a system designer or whatsoever. But since php's birth that it obviously needs something to interpret/compile/run it.
Therefore you can use that exact same application to whatever you need, being it pipe your scripts through the cgi,a command line, an rpc layer, whatever you need.
Apart from that php cli has been out there for quite a long time now.

Most PHP developers that have been around for quite a while were in fact perl programmers. They switched to php for some reason. I would say is more practical when it comes to write a web application, and in the end that's what it comes down to.

Though possible, very little scripting is made in PHP, I see everybody using perl for their server maintenance tasks, I myself use it more for that purpose than PHP. Once again, it's a matter of what's more practical, I find perl more practical for this purpose, I don't think I'm the only one.

---

### Post by DrMega on 2008-10-10
> **ghostdog74 said:**
> Totally not true.

> **LaRoza said:**
> You think using PHP on a server and using a browser to get the results is not silly compared to Python, Ruby (and now, PHP) interactive prompts and scripts?

Also, your Swiftian rebuttal has me staggering.

There's no need for us to bicker about it:)

Perl and PHP are just two examples of a wide range of languages, each with its own pros and cons.

Perl is not a language I have familiarised myself with, but from a web development point of view it seems to me (and I may be wrong) that Perl started out as a scripting language for desktop/server stuff but not really for the web, and later found popularity on the web. Whereas PHP started out in the web world and more recently found a fan base in non-web roles. Without knowing much about Perl, I can only base its merits on the fact that it is popular, so must be pretty good, but from a purely practical point of view, most web hosting firms I've looked at support PHP but only a few support Perl, and there seems to be a lot more PHP samples and tutorials floating about than Perl ones for web development.

---

### Post by LaRoza on 2008-10-10
> **ghostdog74 said:**
> 
I said its not true, because PHP can be used without using XHTML, just like any other languages. I am not talking about the web. You can write PHP scripts to automate tasks just like any other, and that's not silly

Does that clarify what i meant?

I was referring to someone who used PHP with a server and a web browser but without using XHTML. That is what I called silly.

I said PHP in the cli was "awkward" although that is entirely subjective and due to my personal experiences.

---

### Post by LaRoza on 2008-10-10
> **DrMega said:**
> 
Perl is not a language I have familiarised myself with, but from a web development point of view it seems to me (and I may be wrong) that Perl started out as a scripting language for desktop/server stuff but not really for the web, and later found popularity on the web.
It started out for text processing tasks. It later became the de facto standard for CGI scripts.

CGI is outdated now, and Perl has gone beyond its original design of course. 

> 
 Whereas PHP started out in the web world and more recently found a fan base in non-web roles. Without knowing much about Perl, I can only base its merits on the fact that it is popular, so must be pretty good, but from a purely practical point of view, most web hosting firms I've looked at support PHP but only a few support Perl, and there seems to be a lot more PHP samples and tutorials floating about than Perl ones for web development.

Most hosts support Perl and Python to some degree, although it isn't always advertised.

---

### Post by DrMega on 2008-10-10
> **LaRoza said:**
> Most hosts support Perl and Python to some degree, although it isn't always advertised.

If it isn't advertised, and isn't listed in the terms and conditions, then you can't count on it working even if it is there. A host may move your site to a new server which doesn't have that support, and when your site stops working and you complain to them they can just say they weren't contracted to support it anyway, so you're on your own.

---

### Post by LaRoza on 2008-10-10
> **DrMega said:**
> If it isn't advertised, and isn't listed in the terms and conditions, then you can't count on it working even if it is there. A host may move your site to a new server which doesn't have that support, and when your site stops working and you complain to them they can just say they weren't contracted to support it anyway, so you're on your own.

I meant, they often don't make a big deal of it, or put it under some other name, like supporting a variety of frameworks which use it.

---

### Post by DrMega on 2008-10-10
> **LaRoza said:**
> I meant, they often don't make a big deal of it, or put it under some other name, like supporting a variety of frameworks which use it.

Just as an aside (kind of related about hosts supporting or not supporting stuff), once when I was contracting, I developed an e-commerce site for a client in ASP. They chose ASP as they had already chosen the hosting company who had a package called "Business and Commerce Premier" which supported ASP and MSSQL among other things. I developed and tested the code on my machine and then uploaded it to their server. Parts of it didn't work, although they worked fine on both mine and my business partners machine. It turned out that the bit bit that didn't work, which involved moving files about on the server, was because the hosts had locked down the rights in relation to file movements. I had a big discussion with them about this over the phone, which turned into a row. I asked them to explain how a package called "Business and Commerce Premier" could not allow the kind of operations that would be typical of a commercial business application. We didn't win and the client had to make do without that particular functionality. They were not happy but hey, they chose the hosting company so what could I do? :)

---

