---
title: "Website Applications?"
date: 2007-05-22
forum: Programming Talk
---

### Post by Dylnuge on 2007-05-22
Hi there,

I am looking for a good web application language. I am looking at PHP and Ruby on Rails. I don't love the ruby programming language, perhaps a similar language in Python would be nice. If anyone has suggestions, please post them.

Thanks

---

### Post by Mirrorball on 2007-05-22
[Django]("http://www.djangoproject.com/") is a Python framework for web development; it's similar to RoR.

---

### Post by pmasiar on 2007-05-23
> **Dylnuge said:**
> I am looking for a good web application language. I am looking at PHP and Ruby on Rails. I don't love the ruby programming language, perhaps a similar language in Python would be nice.

Django suggested above is one of possible solutions: it was designed to handle "content-management systems" and do it quickly, if you do it the way Django wants it to do - Django has own solutions to most problems, but might not be "best of breed". 

If you want more flexibility to which modules to use, TurboGears is another popular framework designed to be flexible and integrate "best of breed" solutions.

But if your app is just couple of simple pages, then plain old cgi and any teplating system (to separate HTML out of your code) might be the simplest way to go. Check [http://LearnPython.pbwiki.com/WebApplication](http://LearnPython.pbwiki.com/WebApplication)

---

### Post by Dylnuge on 2007-05-23
So what is the difference betwen a framework, like Rails, Django, or TurboGears, and a web language like PHP?

---

### Post by barmazal on 2007-05-23
php is scripting language commonly used for web applications
mainly zope, django and turbogears are frameworks based on scripting language called python
frameworks are number of functions made in order to ease with production
each language has it's own frameworks, as php the most popular web scripting language it has wider choice of frameworks and ready open source web applications

python and rails gets much attention because they are new to many programmers but bottom line you won't get much quality out of these simply because less ppl use them and ruby and python make no sense as programming languages when it comes to something "heavy" this is why their "masters" call these languages "ease to learn but hard to moderate".


anyway if you on Windows give a shout to MS .net probably the best framework if not or you anti MS then try php [http://www.opensourcecms.com/](http://www.opensourcecms.com/) this site might help you with php frameworks

php has great number of good frameworks, well python starts getting too just not Rails

just don't get scared from CMS - content management systems it's just framework with ready GUI.

---

### Post by Dylnuge on 2007-05-23
What are some PHP frameworks that are popular, then?

---

### Post by barmazal on 2007-05-23
i've used MODx, it's not easy but quite flexible.

try with Wordpress and Joomla those are most common CMS, one for blogs and other one for portals. With these you will have basic idea what web application should look like after these you would know what should be done and then you can choose for yourself whatever suits you.

---

### Post by Dylnuge on 2007-05-24
Just a question, but why would I be using windows if I browse these forums?

Thanks for all the replys, looking over everything now.

---

### Post by barmazal on 2007-05-24
i'm Windows user who browse these forums. I find many interesting open source and free projects which i enjoy to use. Ubuntu forums are quite large which makes them attractive to Windows users as well. Hopefully some day there will be functionality i need from OS on Ubuntu (mainly software and not OS itself) so i won't be needed to use Windows but for now there is no. I'm not open source type of person or anti-MS one either. So i enjoy both of the worlds.

---

### Post by pmasiar on 2007-05-24
What a bunch of BS from someone who obviously does not know Python or Ruby - is a PHP jock.
> **barmazal said:**
> php is scripting language commonly used for web applications
mainly zope, django and turbogears are frameworks based on scripting language called python
frameworks are number of functions made in order to ease with production
each language has it's own frameworks, as php the most popular web scripting language it has wider choice of frameworks and ready open source web applications

python and rails gets much attention because they are new to many programmers but bottom line you won't get much quality out of these simply because less ppl use them and ruby and python make no sense as programming languages when it comes to something "heavy" this is why their "masters" call these languages "ease to learn but hard to moderate".


anyway if you on Windows give a shout to MS .net probably the best framework if not or you anti MS then try php [http://www.opensourcecms.com/](http://www.opensourcecms.com/) this site might help you with php frameworks

php has great number of good frameworks, well python starts getting too just not Rails

just don't get scared from CMS - content management systems it's just framework with ready GUI.

Looks like poor sucker OP went off according to this bad advice. But what I co now? Waste time refuting this BS? Is OP still around, interested in other opinion?

PHP is bloody mess. Python and Ruby web app frameworks were created by people who got burned by messy PHP. Read up on model-view-controller approach. PHP mixes this together, MVC separates this so you can handle (and extend) this to big projects.

---

### Post by glenndavy on 2007-05-24
hey dylnuge - 
What sort of 'site' are you wanting to make? Thats probably the starting point for a discussion like this - unless you know you want to work programtically - it may well be worth your while to follow the CMS path... though i've never found one I like, and tend to wish I hadnt put the time into them.

I use ROR in my day job, and if I was pragamatic and honest, I'd have to say that you can't beat it for quick, fast, clean development - but at night, I like flirting with other web frameworks - and I gota say I like TurboGears. I havent decided what I like more Rails or TG - both the same, but very different - but thats another discussion... BUT I will say if you're not into learning new languages for the sake of it, getting things done in python and TG will provide a simpler and more direct path than Rails will.  I havent looked at django for over 18mths - but I enjoyed that too.

As for php - its where I started - its so easy to write php, that its tempting to just start writing your site in php - especially if you are already comfortable with SQL- this will be your undoing IMHO,  make sure, if  you use PHP, that you do it in some sort of framework - and as yet i havent investigated these - though Im keen to check out CakePHP. The reason to make sure you do this, is that if you don't you will over time end up cobling together your own, and interesting as it is - its a lot of time you didnt need to spend, unless you conciously choose to set out and create your own framework - cool, fun, time consuming and probably not with a high return on time invested.

Coming from a place where I didnt really know what to look for in a framework initially when I originally  assessed various frameworks, what I wish someone had told me then is that:
 * The chosen framework uses the MVC paradigm (django doesnt, but its close enough for my purposes)
 * The chosen preferably framework uses a dynamic languge - you're just not going to beat python or ruby really (again only IMHO). I'll never again use VB to put together a website, I'll check in on PHP from time to time, to see what its up to and what frameworks do - you'll always get php work if thats what you want. 
  * The chosen frame work has  a good ORM (object relational mapper) for handling databases. There are different philosophys on whats 'good' in an ORM - don't get too hung up on that at this stage, and dont be put off by religous attiudes to this
  * The method of writing views (generally  a 'templating' language) needs to be enjoyed by the person designing the pages.


good luck - hope this is a little informative
glenn
edit: Just noticed above post - dont know how i missed it
rofl - hope this moderates that a little - don't be shy about ruby or python - its really much easier to be productive with these simple tools and a text editor than it is with MS.net and visual "i still don't belive I paid 2000$ for this shite (yes I really did)" studio - especially if you have to write code that needs to be maintainable - writing well tiered code or MVC code with .net framework is !@##$%!  compared to other frameworks. If you decide to go .net,  check out caslteproject - i havent looked at it yet, but am keen to have a play - it fits loosley into my criteria. 
I dont get the statement: "but bottom line you won't get much quality out of these simply because less ppl use them"  - many many people use them, perhaps not the same masses that use vb, but they are a passionate and choosy many people, and they use them because they pick the right tool for the job, not play it safe following path of least resistance to get a job. The quality of these frameworks is often fantastic, especially when compared with certain commercial offerings. and in my experience the productivity gains from learning a competent language (and framework) are enormous.

---

### Post by glenndavy on 2007-05-24
> **pmasiar said:**
> What a bunch of BS from someone who obviously does not know Python or Ruby - is a PHP jock.


Looks like poor sucker OP went off according to this bad advice. But what I co now? Waste time refuting this BS? Is OP still around, interested in other opinion?

PHP is bloody mess. Python and Ruby web app frameworks were created by people who got burned by messy PHP. Read up on model-view-controller approach. PHP mixes this together, MVC separates this so you can handle (and extend) this to big projects.

I dont know if I 100% agree with pmasjas analysis - its not the langauge that mixes the m, v, and c, together. Instead its a frame work that separates them - thats why if you go php, make sure you use a framework - its possible to write non mvc sites in ruby or python too, if you really want too. Having clarified that,   I think he's right in the essence of what he says and its worth taking his point - pythons namespaces, and syntax, and dynamic nature for example encourages clean code (lol - "beautiful code" to quote dhh from ROR), without repetition. unlike php - ( think of php as a sharp knife, easy to cut your self and make a bloody mess if you're in experienced) - you can write clean code in php, but its dammed easy not to.

---

### Post by barmazal on 2007-05-24
glenndavy, the question is whether you need to reinvent the wheel or to fast develop end product with lowest costs. Not sure how many big projects /WEB2 would prefer having something like Joomla or even more primitive CMS/framework as first step rather developing something new and pricey from beginning without to know the success. This is what i meant by PHP CMS/frameworks popularity advantage over RoR and Zope.

You don't need to write blog in 5 minutes yourself using functionality already built to RoR or Zope, you can use Wordpress which made in years by great number of developers.

Am i clear now?

---

### Post by Dylnuge on 2007-05-24
OP=Original Poster? Just guessed, but if so, then yes, I am still here. I have not finished making my decision.

My site will be to host some applications I am making in my spare time. I do know programming, primarily Java and Python.

---

### Post by glenndavy on 2007-05-24
barmazl, 

ahh...sorry - I misunderstood your gist, I thought you were describing ruby and python as languages. I still don't know that I agree with your point, but at least now I see its not an unreasonable one - apropos cms's.
 I agree re-inventing the wheel is often not smart, and the same can often be said for CMSs (or web frameworks as i pointed out to OP) - and yes there are a great many  CMS's in PHP, that are mature, established and more than capable.  However if you're using wooden wheels, and someone invents 'spokes', or even titanium alloy, then revisiting how you make a wheel is probably worth while. Perhaps this metaphor fits or perhaps it doesn't - i haven't yet evaluated any ruby/python cms's, but will be soon, and should probably keep being dogmatic about this point till then.

---

### Post by glenndavy on 2007-05-24
> **Dylnuge said:**
> OP=Original Poster? Just guessed, but if so, then yes, I am still here. I have not finished making my decision.

My site will be to host some applications I am making in my spare time. I do know programming, primarily Java and Python.

you know python? 
<chant type="hypnotic" repeat="adnauseum">Turbo gears</chant>

---

### Post by RedSquirrel on 2007-05-24
> **barmazal said:**
> Hopefully some day there will be functionality i need from OS on Ubuntu (mainly software and not OS itself) so i won't be needed to use Windows but for now there is no.

Just out of curiosity, what are you missing on Ubuntu? Is the functionality that you lack related to web/software development or something else? You referred to .net earlier, but is there something more?

---

### Post by pmasiar on 2007-05-24
> **Dylnuge said:**
> OP=Original Poster? Just guessed, but if so, then yes, I am still here. I have not finished making my decision.

My site will be to host some applications I am making in my spare time. I do know programming, primarily Java and Python.

OP=Original Poster. Correct

Don't make a decision on first advice of complete stranger, you don't know her agenda or bias. (My bias is Python :-) )

If you know Python, you'd be wasting your time on PHP, seriously. People are running away from PHP. Yes, if you have good project standard, you *can* create clean code - but who does that? Even in 2-3 pages, Python (plan CGI, no frameworks) is as easy as PHP. More pages than that, and framework will make more sense. Python is universal language, used beyond web apps. Tell us more about your proposed app - TurboGears and Django and focused on different ways of doing web apps. Django is more content-management-like.

---

### Post by barmazal on 2007-05-25
**[COLOR="DarkOrange"]pmasiar[/COLOR]** , i have no bias. Strict coding is what i understand and the reason behind much lesser mistakes. For languages. For frameworks MVC is interesting and makes sense but it's not something came from Python or Ruby. It probably exist before those languages even became a hype in last few years. 

There are many "model controller view" frameworks for PHP but my advice was to use already existing content management system or at least look up to code how this thing works. MCV may seem having more sense for those who worked on other type of frameworks but beginner should learn existing systems to know how and where to use some functionality. If he ever intend to make something more complicated then having query from DB to page.

There large amount of PHP based content management systems with all needed to produce website quickly and effective. Since large amount of developers made those so probably security and features are far more advanced than what beginner can program by his own.

**more ppl code  =  more ppl use  = more development occurs in area.**

I can claim the same about .net. If you know Java then Mono (Linux .NET) project with C# on Linux will make perfect sense for you as Java almost identical to C#. 

**I gave my advice, last time i posted something much less offensive as yours i've got ban for some few weeks.**

**[COLOR="DarkOrange"]RedSquirrel[/COLOR]**, read bold sentences above. It's not proper forum to compare Linux with Windows. I will get ban and before that will be flamed to death, maybe even hacked as Gimp community often does.

---

### Post by glenndavy on 2007-05-25
hey there OP, if you're still around and not over this chat you might find this interesting
[http://oodt.jpl.nasa.gov/better-web-app.mov](http://oodt.jpl.nasa.gov/better-web-app.mov)

---

### Post by glenndavy on 2007-05-25
> **barmazal said:**
> **[COLOR="DarkOrange"]pmasiar[/COLOR]** , i have no bias. Strict coding is what i understand and the reason behind much lesser mistakes. For languages. For frameworks MVC is interesting and makes sense but it's not something came from Python or Ruby. It probably exist before those languages even became a hype in last few years. 


Apparently MVC came from the '70's  as a sound paradigm for programming apps served to terminals hanging off main frames - long before ruby, python,php, perl, or the web.

> **barmazal said:**
> 
[but my advice was to use already existing content management system

yep may be more practicle in many ways - i wonder what his agenda is - we havent heard much about what he really wants. I'm guessing he's wanting to write code more than anything, but only he could say.

I tried several CMS's for different projects - generally found it wasnt worth the effort of learning then hitting brick walls - each to his own. One thing I never tried was plone I have to admit- you tried it? whats you're preferred CMS?

> **barmazal said:**
> 
I can claim the same about .net. If you know Java then Mono (Linux .NET) project with C# on Linux will make perfect sense for you as Java almost identical to C#. 


perahps if he knows java - struts or something like that?

> 
**I gave my advice, last time i posted something much less offensive as yours i've got ban for some few weeks.**

truley? got a link to the  thread?

---

### Post by pmasiar on 2007-05-25
> **barmazal said:**
> **[COLOR="DarkOrange"]pmasiar[/COLOR]** , i have no bias.

barmazal, I am sorry to be first to break it for you, but obviously you have a bias :-) Everyone has a bias. Everyone has certain preferences about the future and works for them. If someone says she has no bias, it's one of two: 
1) she is not experienced (and introspective) enough to understand that, in fact, she does have a bias
2) she is outright, consciously lying to you about not having a bias. So pick your poison :-)

Call me a cynic, if you want, I don't care much,been there done that have scars to prove it. I've seen hypes and fads. I remember when people were talking about article "GOTO statement considered harmful" (google it) and if this new approach, "structured programming" is just a fad, or will it stay. :-) It was before exceptions, and people argued that you need GOTO to handle exceptions structured way... ahh those were times...

In example, simple proof of your bias (I let you to explain which case it is):

> Python (...) became a hype in last few years.

[Python](http://en.wikipedia.org/wiki/Python_%28programming_language%29#History) (started before 91) is more than 4 years *older* than [PHP](http://en.wikipedia.org/wiki/Php#History) (started 94), yet you put Python in same "hype" bag as [Ruby](http://en.wikipedia.org/wiki/Ruby_%28programming_language%29#History) (started 95). This IMHO shows that your first experience in web programing was in PHP, and you were not aware of these other options. Which makes sense, a lot of beginners started with PHP, because programming web apps in Perl or Python in and of '90 demanded level programming skills they lacked. And this is also reason why there are so many really messy PHP programs - because barrier of entry for PHP couple years ago was lower.

Please note I have nothing against you in person, you might be decent PHP coder who tries to make clear PHP code. I just claim that in average, it is not the case (and you might be above-average PHP coder). It just IMHO shows your bias. And your other advice is also clouded by PHP, non-MVC thinking.

"frameworks MVC ... exist[ed] before those languages "

You are right. IIRC first language with MVC pattern was Smalltalk. Old times indeed. BTW I never claimed Python is first language using MVC pattern. Python is using many good ideas from other languages, and it shows it strength.

> There large amount of PHP based content management systems with all needed to produce website quickly and effective.

quick and dirty :-)

And PHP approach, which could make sense 5 years ago, makes less sense now, when simple, clean web app framework exist for both Ruby and Python. Especially Python is universal language, which is used for web apps only as afterthought (because it is so good and flexible in sohisticated text processing). Python's author Guido, in 2004 said he is not interested in using Python in web apps. It was just before he was hired by Google :-)

---

### Post by barmazal on 2007-05-25
**[COLOR="DarkOrange"]glenndavy[/COLOR]** i know what you mean not worth an effort but it could be great tool to learn from or use in case you just want something done. Web moving towards step where is no solid site that sells but interesting content. If i can get Wordpress which has RSS, Google Sitemap, Categories/Dates and fine back office i would prefer using it and trying to modify rather making my own Wordpress.

As for good CMS/framework. You can try it MODx. Generally speaking it already has many objects to which you send parameters. It's not that ease as it may seem. Though im not interested to produce back office on such levels,  prefer using already done stuff in case there something i need i do my own as addition.

It has it's disadvantages like small community which causes longer periods for development editions but i can live with it.

[http://modxcms.com/](http://modxcms.com/)


**[COLOR="DarkOrange"]pmasiar[/COLOR]**

let me clarify, 

calling Python hype of last years doesn't mean Python is younger than PHP. Python became a hype recently which means it started to gain popularity compared to other languages, same as Ruby which came out somewhere in mid 90'. It's not the Python but it's web frameworks which spoken about but again it's makes my point even stronger. Why younger PHP language is more popular? Coz Python had nothing to offer for the most dynamically progressing related to computers issue WEB. Now it has, don't get much excited though.

Python doesn't use MVC but frameworks you referring to or way of programming. Same can be done on any other language if it found important or easier to track.


Google doesn't ring a bell for me, application they have could be done on any language, especially large applications which better to be complied on server and not scripted.

Real proof would be having Python powered sites with the same amount as PHP ones. Python doesn't need special hosting like RoR, JavaEE or .NET. It can use simple LAMP server same as PHP, which is cheap but still there is no much Python, there is no much books about Python there is almost nothing about it compared to everything else (except RoR).

---

### Post by pmasiar on 2007-05-25
> **barmazal said:**
> calling Python hype of last years doesn't mean Python is younger than PHP. Python became a hype recently 

Calling language "a hype" without any arguments shows again your bias, BTW :-)

Python was (and still is) for a long time popular language outside of web app area, so it was below *your* radar. You might be surprised: many people do not need web frontend, and PHP has nothing for them, so they use other languages.

> Why younger PHP language is more popular? Coz Python had nothing to offer for the most dynamically progressing related to computers issue WEB. Now it has, don't get much excited though.

PHP was more popular for web apps couple years ago, but is slowly fading. Now, people burned by messy code, and learned basics of programming, are looking beyond PHP. And found MVC-based solutions in more universal languages.

Admit it, mixing code and presentation layers, and PHP does, does not scale for real big applications (and MVC is accepted solution).

> Python doesn't use MVC but frameworks you referring to or way of programming. Same can be done on any other language if it found important or easier to track.

I have hard time understanding what did you meant by that.

> Google doesn't ring a bell for me, application they have could be done on any language, especially large applications which better to be complied on server and not scripted.

Well, Google rings bell for most people :-) And they decided *not* to use PHP. maybe they are smart and know why, and you don't?

> Real proof would be having Python powered sites with the same amount as PHP ones. 

like this [serving 500,000 pages/hour](http://www.djangoproject.com/weblog/2007/may/25/curse/)


> there is no much books about Python there is almost nothing about it compared to everything else (except RoR).

...because Python is so simple to learn you can get away with online books and docs. Ie java has more books because is harder to learn.

**Dylnuge**, if you are still around: My point is, PHP might be easy to start with, but will not scale well for bigger, multi-page applications. And simple apps with couple pages are equally easy to do in Python, even without MVC, just plain templates. So learning PHP will not prepare you for real applications. And python you can use as generic language, instead of bash, for database access, or for GUI programming. Has libraries to do many, many things way beyond area of PHP.

---

### Post by foresth on 2007-05-25
> **Dylnuge said:**
> What are some PHP frameworks that are popular, then?

[http://www.symfony-project.com](http://www.symfony-project.com)

Very powerful.

---

### Post by barmazal on 2007-05-25
pmasiar, your last line compromise all Python community said for few years but anyway your replies seem to be outta this world so it must be my english which not used as should be. Anyway good luck with whatever you use MVC Python or non MVC Cobol.

---

### Post by winch on 2007-05-25
> **barmazal said:**
> Why younger PHP language is more popular? Coz Python had nothing to offer for the most dynamically progressing related to computers issue WEB. Now it has, don't get much excited though.

Php is more popular because it was pretty much designed to be embedded in a web server and it got there early. It was easy and cheap to install and easy to use. Pretty much the only alternative for a long while was perl.
By the time python arrived (mod_python didn't exist until 2000) php was well established and installed on pretty much every cheap webhost.

---

### Post by Dylnuge on 2007-05-25
Thanks. I am looking most seriously at Django, simpily because based on what was said here and the fact that I have (some) Python experiance. TurboGears also looks nice. A while ago, PHP had been the only web standard I had heard of, hence the reason I was originally leaning toward it. However, the Python frameworks look much better then the PHP frameworks (I did give symphony a look over).

Thanks for all the help :)

---

