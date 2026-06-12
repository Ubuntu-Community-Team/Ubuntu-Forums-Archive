---
title: "Python for the Web"
date: 2007-06-05
forum: Programming Talk
---

### Post by LaRoza on 2007-06-05
While reading certain posts in this forum, I found that Python can be used instead of PHP, which I know, for the Web. What would I need to use Python instead of PHP for Web apps? A tutorial would be helpful also. Thanks.

---

### Post by ghostdog74 on 2007-06-05
[Web programming]("http://wiki.python.org/moin/WebProgramming")

---

### Post by pmasiar on 2007-06-05
Big difference between PHP and Python way is, separate presentation from business logic - use [Model-view-controller](http://en.wikipedia.org/wiki/Model-view-controller) approach. You can of course just print text from Python but it is not any simpler that using templates.

First you need to decide if you want to use framework (simpler life but more magic) or for learning sake, you will do more things by hand, so you will know what is happeninig, planning to switch to framework later.

Luckily, Python has simple web server (in 7 lines of Python code)  you can try for your learning, and simples CGI program in Python has just 3 lines with no frameworks in sight - [http://LearnPython.pbwiki.com/WebApplication](http://LearnPython.pbwiki.com/WebApplication)

Django is framework recommended ("pronounced") by Guido, but some developers prefer TurboGears or Pylons (they plan to merge) because those have policy "integrate best of breed Python plugins" - Django has policy "we will do it right for us".  Django is also oriented towards web content management (was created for newspapers), while TG was for more flexible and dynamical web apps, using more AJAX and stuff.

Either way you have access to lots of docs and tutorials. TG (my favorite) published DVD, I am sure that Django is not far behind.

I really like TG's templating system KID (or v2.0: Genshi), where you do not need to learn different template expression language like in other systems - template expressions are in Python, too. And it is fully XML compliant - in fact Guido hates XML and that was one of main (and wrong) reasons he rejected TG, but oh well who cares :-)

Both frameworks have great supportive community and active mailing lists. You may want to check sometimes [http://www.planetpython.org/](http://www.planetpython.org/) , lots of interesting info about recent web apps trends is coming that way.

---

### Post by barmazal on 2007-06-05
omg again MVC language guy !!!

LaRoza, best would be using web framework such as Django or Turbogears. it uses Python as language

---

### Post by LaRoza on 2007-06-05
I would like to write out all the code myself.

---

### Post by barmazal on 2007-06-05
it's great but then you will need to write Python's code yourself too. Since it uses C as low level.

Framework functions made by huge amount of ppl who understand what they write and usually optimize code to point one cannot do.

just my 2 cents.

Python doesn't make you quickly create a web application but frameworks do, since they ease some stuff which will require much more code to re-create.

---

### Post by LaRoza on 2007-06-05
I meant, I like to write out the Python, XHTML, CSS, ECMAscript, PHP, etc myself so I can learn how to use it. I have no intention of boot strapping my own compiler.

---

### Post by pmasiar on 2007-06-05
> **barmazal said:**
> Python doesn't make you quickly create a web application but frameworks do, since they ease some stuff which will require much more code to re-create.

It is so funny how misled are you and how misleading are your commnents. What do you mean by "quickly create web app" what frameworks magically allow? Quickly, comparing to what? 

It all depends:
- how much time you want to spend learnig the framework 
- how good is framework suited to what you want to do 
- how familiar are you with plugins/modules framework uses
- how easy is to substitute different plugins you know/like
etc etc.

You don't have to use framework to write web app. But you can still use templates to generate pages, see wiki I mentioned earlier, to use MVC pattern which so annoys barmazal for unknown reason. MVC is just approach to solve one kind of problem, like recursion, or storing data in database. Why to get upset about it?

There is a joke that it's so easy to create web framework in Python that Python has more frameworks than reserved words :-) Fortunately we are down to less than dozen mainstream frameworks, and 2-3 main (Django, TurboGears, Pylons). The simplest framework is possibly web.py but I am not 100% sure - there are so many of them :-)

I think that your decision to do web app by hand first is very sound, LaRoza. Later, when you switch to framework, you will know exactly what the "magic" does, and how, and can look it up and fix it if needed, because of sound understanding how to do it by hand.

---

### Post by LaRoza on 2007-06-05
I found tutorials for Python on the Web, including CGI. With Python, I should be productive in no time. :)

---

### Post by kallepersson on 2007-06-06
Great, we look forward seeing some cool stuff coming from you soon then.

As for the framework question, I'd go with Django since it's a very popular one, and therefore it'll be easy to get helpe since the community's so big.

---

### Post by LaRoza on 2007-06-06
Thanks for all the replies! You were all most helpful.

---

### Post by aks_! on 2007-10-16
Hi,

I also have some questions about python web developing. I've spend some time now searching for the preferable way of writing python web apps and I still don't know much. :) I am mostly using PHP for web developing but since I use Python (and a bit of C) for my desktop developing, I plan to switch from PHP to Python once I figure it all out.

The main problem I have is that there are publisher handler, psp, cgi and a bunch of frameworks out there, all with their advantages and disadvantages. So far, I've tried publisher handler (which I like quite a lot), psp (too PHPish) and Django (which is also quite great but I don't like being tied to a framework).

The problem with framework (as I see it) is also, that if you want to use it, you have to install it and not all web host providers do so while on the other hand a lot of them installs mod_python and let you configure your handlers.

I am thinking about using publisher handler combined with some template engine (like KID or Cheetah) and maybe some ORM. What do you think? Or is there a simple way to use Django without installing it? (Without using django-admin.py and manage.py?)

Thanks

---

### Post by pmasiar on 2007-10-16
> **aks_! said:**
> psp (too PHPish)

PSP (Python Server pages) is abomination. If you want to mix code and html, your business and presentation layers, you may as well stick with PHP. :-)

**Whole point** of leaving PHP is to have clean and maintainable Model-View-Controller structure.

> Django (which is also quite great but I don't like being tied to a framework).

The problem with framework (as I see it) is also, that if you want to use it, you have to install it and not all web host providers do so while on the other hand a lot of them installs mod_python and let you configure your handlers.

There are plenty of hosting companies who will host your Django (or TG) based website, hosting is NOT a problem.

Framework solves problems for you, so you don't have to know about them. After you gain experience and know what you are doing, you may switch to Pylons, the minimal framework. Or look at Turbogears, which is more flexible than Django.

> I am thinking about using publisher handler combined with some template engine (like KID or Cheetah) and maybe some ORM. What do you think?

To start in web apps area, IMHO you are much better of using mainstream framework with active support. Django is the smooth no-problem 90% solutionas long as doing it Django way is what you want (like Ford T was: you can get a car any color you want, as long as you want black :-) ). To go beyond 90%, Turbogears will let you swap modules, templating systems, ORMs, etc.

>  Or is there a simple way to use Django without installing it? (Without using django-admin.py and manage.py?)

Not sure how you want to use a program without installing it? :-)

It seems like you prefer not to be constrained by some Django choices. Looks like you do have experience with web-based apps, and looking for a flexible solution in Python. I also like Kid templating more than Django way. Use Turbogears or even Pylons, which are alternative mainstream frameworks (and Turbogears moves to be "Pylons with prebuild modules"). They will do less handholding (especially Pylons) and will give you more freedom.

---

### Post by nealmcb on 2007-10-20
I think django is a great way to go.  There are ISPs that provide it pre-installed.
Is is modular enough that you can use your own templating system or orm if you really want, but I think they have designed the ones they use well.

Learn more at

[http://djangoproject.com](http://djangoproject.com)

---

### Post by LaRoza on 2007-10-20
> **nealmcb said:**
> I think django is a great way to go.  There are ISPs that provide it pre-installed.
Is is modular enough that you can use your own templating system or orm if you really want, but I think they have designed the ones they use well.

Learn more at

[http://djangoproject.com](http://djangoproject.com)

Talk about digging up old threads...

Are you involved in this project?

---

### Post by deuce868 on 2007-10-20
Goodness there is some major FUD out there. 

First of all, MVC has nothing to do with language. It's completely based on how you structure your code to function. You can use a MVC method for any language. So please, don't say things like "PHP isn't MVC". 

The big issue with Python as a web tool is deployment. With the release of mod_wsgi this will hopefully get to be much better. Check out the project's wiki
[http://code.google.com/p/modwsgi/](http://code.google.com/p/modwsgi/)

It lists instructions for using it with a bunch of frameworks as well.

As for using a framework/not it's all about how much code you want to reuse. Frameworks come with method for routing requests, templating, integrating your models, etc. I've been working on learning to use Pylons myself. Like any tool, frameworks impose limits in an effort to make things easier. They provide "best practice" methods and take some time to learn.

---

### Post by pmasiar on 2007-10-21
> **deuce868 said:**
> First of all, MVC has nothing to do with language. It's completely based on how you structure your code to function. You can use a MVC method for any language. So please, don't say things like "PHP isn't MVC".

I know that is is possible to write clean MVC code in PHP. The only problem is, nobody bothers, so it is impossible for a beginner to learn it by reading code of existing projects.

Compared to that, TG will generate (quickstart) new  project with proper structure, and running "hello world". Just add your own functions to the controller. Much harder to get it wrong that in PHP.

Even if something is possible to do right, it does not mean it is always done right, especially by beginners.

---

### Post by deuce868 on 2007-10-21
> **pmasiar said:**
> I know that is is possible to write clean MVC code in PHP. The only problem is, nobody bothers, so it is impossible for a beginner to learn it by reading code of existing projects.

Compared to that, TG will generate (quickstart) new  project with proper structure, and running "hello world". Just add your own functions to the controller. Much harder to get it wrong that in PHP.

Even if something is possible to do right, it does not mean it is always done right, especially by beginners.

If you're going to compare things, compare framework to framework, not language to framework. If you want MVC, you can find it:
[http://www.mustap.com/phpzone_post_73_top-10-php-mvc-frameworks](http://www.mustap.com/phpzone_post_73_top-10-php-mvc-frameworks)

So perhaps, the better line would be
> If you're starting out, find a framework you can get your head around and allow it to help you organize your code/logic into a nice MVC-like structure, regardless of the language you choose. In Python you can start with TG, Pylons, even Plone.

---

### Post by pmasiar on 2007-10-21
pls no Plone. Why you would inflict in on inocent beginner? 

I advised Python, because in my professional experience, it is easier to make MVC structure in Python than in PHP, especially if TG will create the whole structure :-)

---

### Post by slavik on 2007-10-22
install the python cgi module for apache2 :)

---

### Post by deuce868 on 2007-10-22
> **pmasiar said:**
> ... it is easier to make MVC structure in Python than in PHP, especially if TG will create the whole structure :-)

TG will, Pylons will, Symfony will, CodeIgnighter will, RoR will, it's called a framework and has nothing to do with language. 

I give up trying to teach the difference between a programming language and the framework tools you use in them.

---

### Post by LaRoza on 2007-10-22
> **deuce868 said:**
> 
I give up trying to teach the difference between a programming language and the framework tools you use in them.

I agree, my PHP code does not mix PHP and markup. In fact, the PHP, CSS, XHTML, and ECMAScript are in different files. There is only one instance in which I mix PHP with my XHTML:

<input type="text" size="27" name="verify" id="verify" /> Enter this number: <?php echo $_SERVER['REMOTE_ADDR'];?>


This is to prevent spam.

---

### Post by pmasiar on 2007-10-22
> TG will, Pylons will, Symfony will, CodeIgnighter will, RoR will, it's called a framework

PHP will not, Python cgi module will not. I want to provide good answer to OP, not play semantic games.

Edit: deuce868, you are probably smart enough to understand it, but instead of suggesting clean MVC-framework for PHP (if such beast exists - I am not sure), you choose to play semantic games. I am not joining. I have a life.

---

### Post by dataw0lf on 2007-10-29
Django  or Pylons.  Gluon has emerged as a more newbie-centric framework, and TurboGears is still out there, but Django and Pylons are beginning to emerge as the two best.  The community around TG has died off quite a bit of late.

Pylons is much more loosely coupled than Django.  This means it's much easier to replace the default ORM (SQLAlchemy;  personally, my favorite, leagues over SQLObject, which is what Django uses by default), templating system, etc.  

Still, I prefer Django for 99% of uses.  The learning curve is relatively steep for a Python framework / library, but it's still pretty easy to gain a grasp on.

If you don't have hosting, I'd suggest WebFaction.  I personally own 5 servers that I have colocated, and a Xen VPS via Linode, and I still use WebFaction for my Django development.  Their shared hosting accounts are phenomenal, and their support is great.

---

### Post by dataw0lf on 2007-10-29
> **deuce868 said:**
> TG will, Pylons will, Symfony will, CodeIgnighter will, RoR will, it's called a framework and has nothing to do with language. 

I give up trying to teach the difference between a programming language and the framework tools you use in them.

But there ARE fundamental differences on how specific languages implement specific frameworks. 

PHP loses, because of it's cluttered global namespace, no existing, elegant way to create your OWN namespaces (!), and it's general ineptitude when it comes to aspects that should be semantic based (iteration, arrays) instead of library based.

You will never win an argument with PHP versus Python as a language.  PHP is readily comparable to Python frameworks, rather than Python itself.

---

### Post by ThinkBuntu on 2007-10-29
How can I put Python code inline into HTML, like .rhtml, Perl with Mason, or any PHP?

* feels guilty for not using Google *

---

### Post by LaRoza on 2007-10-29
> **ThinkBuntu said:**
> How can I put Python code inline into HTML, like .rhtml, Perl with Mason, or any PHP?

* feels guilty for not using Google *

I don't know if you can, but I do not think it is good practice to mix code like that. On MS servers, you can use a script tag with a language attribute of python and a runat="server".

-EDIT On further research, it seems server specific. Look into what server you are using.

---

### Post by dataw0lf on 2007-10-29
> **ThinkBuntu said:**
> How can I put Python code inline into HTML, like .rhtml, Perl with Mason, or any PHP?

* feels guilty for not using Google *
Correct, simple answer: Don't.

If you still feel compelled to, I believe PyHP will ([http://www.freenet.org.nz/python/pyweb/docs/pyhp.html](http://www.freenet.org.nz/python/pyweb/docs/pyhp.html)).

But, please, for the love of baby Jesus, don't do it.

---

### Post by skeeterbug on 2007-10-29
[http://www.djangoproject.com/](http://www.djangoproject.com/)

Don't let the version number fool you either, it has been around as long as rails (around 2 years now). A few major sites use it (curse gaming, pownce). I am using it for my site as well - [http://www.guildreport.com](http://www.guildreport.com)

Run the the tutorial and check out the admin section, you will be amazed.

---

### Post by ThinkBuntu on 2007-10-29
I'm referring to the V of MVC. Like easily dropping variables in and adding handy little if() statements. Not making an ASP site :^)

---

### Post by dataw0lf on 2007-10-29
> **ThinkBuntu said:**
> I'm referring to the V of MVC. Like easily dropping variables in and adding handy little if() statements. Not making an ASP site :^)
Oh, right on.  Whew, you scared the hell out of me there.

There are many templating systems.  Django uses Jinja.  Here's a sample template:
```

{% if comments %}
    {% for comment in comments %}
         <h4>{{ comment.title }}</h4>
         <div style="margin: 0 0 0 10px;font-size: 0.8em;">written by <i><strong>{{ comment.author }}</strong></i> on <i>{{ comment.created_date|date:"F jS Y" }} at {{comment.created_date|date:"P" }} </i></div>
         <p style="padding: 7px; font-size: 0.8em; border-bottom: dashed 1px black;">{{ comment.body }}</p>
    {% endfor %}
 {% endif %}

```

This is straight from my beta comments page that I load with jQuery on my site.  Yes, yes, I know inline HTML (I'm still working on the design), but this gives you a good example of filters (check out the date), conditionals and loops, and text insertion.

---

### Post by ThinkBuntu on 2007-10-29
No shame in using inline CSS for rapid prototyping or overriding tricky styles. Come by [www.CSSForums.org/forum](www.CSSForums.org/forum) if you ever need help: We're growing...slowly.

---

### Post by pmasiar on 2007-10-29
> **dataw0lf said:**
> Django  or Pylons.  Gluon has emerged as a more newbie-centric framework, and TurboGears is still out there, but Django and Pylons are beginning to emerge as the two best.  The community around TG has died off quite a bit of late.

Pylons is much more loosely coupled than Django.  This means it's much easier to replace the default ORM (SQLAlchemy;  personally, my favorite, leagues over SQLObject, which is what Django uses by default), templating system, etc.  

I am not sure why you dismiss TG. maybe because you use Django? :twisted:

TG will switch to Pylons in next version, so TG will be front-to-end integration of Pylons with other modules (like SA, genshi etc). Pylons is meta-framework to build frameworks. :-)

And I do not see any die-out in TG mailing list, in fact converts from Django pop in occasionally, earning for freedom to choose modules which TG provides :-) I know that Django is the "official" way to build web apps in Python, "pronounced" by Guido, because he hates XML and missed how useful XML-based templating like Kid/Genshi is. 

I agree that Django is more popular and recommended to beginners, but TG is targeted more to experts who need less handholding and more freedom to chose components - and TG is alive and kicking, thank you! According to your logic, we should give up on Linux, switch to Windoze and be done with it.

---

### Post by dataw0lf on 2007-10-29
> **pmasiar said:**
> I am not sure why you dismiss TG. maybe because you use Django? :twisted:

Nice way to get defensive.  I merely stated that TurboGears seems to be hemmoraghing users after losing it's project lead, and moving towards merging to Pylons. (and Pylons is NOT a meta-framework).

> 
I agree that Django is more popular and recommended to beginners, but TG is targeted more to experts who need less handholding and more freedom to chose components - and TG is alive and kicking, thank you! According to your logic, we should give up on Linux, switch to Windoze and be done with it.

Ah yes,  the predictable argument of 'OMG U MUST LUV WINDOZE!ONE!'.  Nice.   The fact that you attack me after I state my opinion (which the OP asked for) seems more along Microsoft's lines then mine.  Also, let's please call it 'Windows'.  You sound like an illiterate when you use 'Windoze'.

What it boils down to is use what you deem best for your use.  I recommend Django and Pylons;  there seems to be no reason to use TurboGears when it's about to get consumed by Pylons (and haven't the TG devs announced that there would be significant changes to the API?).  But if you want to use it, fine.  I, in my own, honest, opinion, recommend Django or Pylons.  Which is what the thread was about.

---

### Post by pmasiar on 2007-10-29
> **ThinkBuntu said:**
> How can I put Python code inline into HTML, like .rhtml, Perl with Mason, or any PHP?

First, you know that MVC suggests not to mix any presentation logic to view, to your template. 

Next, what if you need to do some non-trivial processing of the data passed by controller into view? This is **exactly** why I like TurboGears and Kid:  Kid allows me to write **presentation logic** inside of the template, in Python!

So, with correct tools, simple tasks are easy, and hard tasks are possible!

---

### Post by dataw0lf on 2007-10-29
> **ThinkBuntu said:**
> No shame in using inline CSS for rapid prototyping or overriding tricky styles. Come by [www.CSSForums.org/forum](www.CSSForums.org/forum) if you ever need help: We're growing...slowly.

Thanks :) Not much of a designer, so that link may be helpful (although several of my friends are CSS geniuses).  I'm competent with it, but I guess I just don't have the eye that really cool designs require (and I can't use Gimp to save my life).

---

### Post by pmasiar on 2007-10-29
Pylons is not intended for beginners, because developers are not interested in front-to-end tools integration, they use TurboGears for that. It is closer to merging and specialization than "being consumed by".

---

### Post by dataw0lf on 2007-10-29
> **pmasiar said:**
> Pylons is not intended for beginners, because developers are not interested in front-to-end tools integration, they use TurboGears for that. It is closer to merging and specialization than "being consumed by".

I don't see how Django is intended for beginners, either.  Just because their components are more tightly coupled?  And just because Django is simple and Pythonic, which tends to be attractive to beginners, doesn't mean it's intended for beginners.  The same goes for Python itself.

Correlation is not causation.

---

### Post by pmasiar on 2007-10-29
I am not sure about what we argue now. Do you claim that with Pylons is as easy to start as with Django? IMHO, Django is easiest (and good for them) for the price of having only one way to do it, Pylons wants to be the most flexible (for the price of have to integrate tools yourself), and TurboGears tries to stick the ballance: you can pick your components, but you don't have as much freedom as with Pylons, because many choices were made for you. 

IMHO, you may disagree. 

You also claimed TG is dying (not sure on what you based your claim), and I said I seen no signs of that. So what is the problem? 

You want to argue that Django is more "pythonic" than TG? I never claimed that TG is simpler (if that is your definition of "pythonic").

---

### Post by ThinkBuntu on 2007-10-29
> **dataw0lf said:**
> Thanks :) Not much of a designer, so that link may be helpful (although several of my friends are CSS geniuses).  I'm competent with it, but I guess I just don't have the eye that really cool designs require (and I can't use Gimp to save my life).
Same. That's why I'm on a Mac with Photoshop.

---

### Post by dataw0lf on 2007-10-29
> **ThinkBuntu said:**
> Same. That's why I'm on a Mac with Photoshop.

Can't use Photoshop either ;) (and not a big personal fan of Apple products, in general).

---

### Post by dataw0lf on 2007-10-29
> **pmasiar said:**
>  
You want to argue that Django is more "pythonic" than TG? I never claimed that TG is simpler (if that is your definition of "pythonic").
Yes, simple does equate to "Pythonic", at least in part.  You actually partially answered it yourself, too: 
> 
IMHO, Django is easiest (and good for them) for the price of having only one way to do it


These, and other reasons, are why Guido thinks Django is the "Pythonic" way to go.  But he concluded his statement with "use what works best".

Try, "import this"

---

### Post by pmasiar on 2007-10-29
> **dataw0lf said:**
> Yes, simple does equate to "Pythonic", at least in part. 

I agree, but spreading false rumors (AKA FUD) about imminent demise of fellow Python web frameworks seems not very Pythonic to me. :-)

> These, and other reasons, are why Guido thinks Django is the "Pythonic" way to go.  But he concluded his statement with "use what works best".

I think part of reasons why Guido pronounced Django is also Guido's hate of XML. At the time, Kid was preferred templating for TG, now there are many other (and Kid v2 == Genshi is just default, and one of preferred ones). I said why I love Kid, and AFAIK it is not possible in Django to do same thing last time I looked. Did they made big changes recently? Dos Django allows to use Kid/Genshi or like?

> Try, "import this"

Nah, don't try this one on me, I said it more times on this forum than you did :-)

Edit: I see you joined before me, but I did not noticed you around promoting Python recently. I do it all the time. :-)

---

### Post by dataw0lf on 2007-10-29
> **pmasiar said:**
> I agree, but spreading false rumors (AKA FUD) about imminent demise of fellow Python web frameworks seems not very Pythonic to me. :-)
  
But they are merging with Pylons yes?  And there will be changes to the API, yes?  So why not go with Pylons?  They could easily adapt TG's components into Pylons.  Isn't that why TG is merging?

> 
I think part of reasons why Guido pronounced Django is also Guido's hate of XML. At the time, Kid was preferred templating for TG, now there are many other (and Kid v2 == Genshi is just default, and one of preferred ones). I said why I love Kid, and AFAIK it is not possible in Django to do same thing last time I looked. Did they made big changes recently? Dos Django allows to use Kid/Genshi or like?


I think you're attributing negativity to Guido's comment.  Guido recommend Django as the Pythonic way because it is Pythonic, and he prefers it.  Not because he hates other web frameworks.


> 
Nah, don't try this one on me, I said it more times on this forum than you did :-)

Edit: I see you joined before me, but I did not noticed you around promoting Python recently. I do it all the time. :-)

Wow, you're beating me on promoting Python.  Since I visit this forum every couple months or so, unleash a flurry of responses, then disappear back into obscurity again, I don't find this hard to believe.  I haven't posted much since I retired as one of the original Moderators (which included me getting this forum, "Programming Talk", implemented - one of my old stickies still remain).  

Regardless, congratulations on pimping Python.  I just don't think it should be a competition.  

And I never said TG was dead, by the way.  I said the community "seemed to have died off a bit", due to the loss of the lead developer, and it's subsequent announcement that it will be merged into Pylons.  

My argument is:  why even choose TG if it's going to be merged with Pylons?  You can use Pylons, then once TG is merged, use what you like about it.  This seems to be the best answer.  Don't you think?

---

### Post by pmasiar on 2007-10-29
> **dataw0lf said:**
> But they are merging with Pylons yes?  And there will be changes to the API, yes?  So why not go with Pylons?  They could easily adapt TG's components into Pylons.  Isn't that why TG is merging?

No. They just continue what TG was always best in: separating parts, so you can pick the best tool. Now, they separated framework used to bind parts and substituting Pylons for that.

I am sorry I cannot find the link - maybe someone interested in reading through TG user mailing list can do it, and learn a lot as side effect :-)  What they said is, that they talked to Pylons developers and decided to use Pylons as "internal skeleton" for next release of TG, instead of the custom one.

So Pylons will continue to be tool for people who knows what exactly they want (total flexibility) and how to integrate tools, and TG will be one of possible frameworks based on Pylons, but all the integration, front-to-end, will be made for you: SQLAlchemy or SQLObject, dozen of templating systems, etc. As opposite of Django, which has one (very smooth) way to do it, but is not too friendly when you need something else.

> I think you're attributing negativity to Guido's comment.  Guido recommend Django as the Pythonic way because it is Pythonic, and he prefers it.  Not because he hates other web frameworks.

But Guido famously said [Which Part of "No XML" Don't You Understand?](http://www.artima.com/weblogs/viewpost.jsp?thread=146647) when selecting web framework for himself, someone suggested looking at TG. And he himself said he is not expert, and IMHO that pronouncement is flawed. Web  is not possible without XML, and Kid has nice features unmatched in other templating engines AFAICT.

> Wow, you're beating me on promoting Python.  

Yes, I do promote Python daily, as vaccine from Java and even VB which I sometimes need to do at work. Helps to keep my sanity! :-) 

I also have wiki for Python beginners (see my sig). Yes I know it need cleanup - in my copious free time I will do it sometimes :-)

> I haven't posted much since I retired as one of the original Moderators (which included me getting this forum, "Programming Talk", implemented - one of my old stickies still remain).  

Thanks for that! Now we would like to have some kind of karma, because often people with little or no experience give bad advice. Not bad opinion, but plain bad advice. Any ideas how to do that?

> My argument is:  why even choose TG if it's going to be merged with Pylons?  You can use Pylons, then once TG is merged, use what you like about it.  This seems to be the best answer.  Don't you think?

Because Pylon is not concerned about being usable "out-of-the box", like TG is? Ie TG was "widgets" which expect some functionality from framework to make magic (but more flexible magic that Django's :-) ) [Pylons itself](http://wiki.pylonshq.com/display/pylonscookbook/Concepts+of+Pylons) says it wants to be more minimal, and you need to integrate it yourself. TG does exactly that for you.

I don't think it is productive usage of my time to continue nitpicking like this. You retracted your claim  that TG is near dead, and that is enough for now :-)

Edit: Seems like TG will keep kicking for some time: Mark Ramm, one of main developers, [got hired to work full time with TG at Stanford University](http://compoundthinking.com/blog/index.php/2007/09/20/change-the-world-with-turbogears-and-get-paid-to-do-it/). Not bad for a dying project? ;-)

---

### Post by ThinkBuntu on 2007-10-29
> **dataw0lf said:**
> Can't use Photoshop either ;) (and not a big personal fan of Apple products, in general).
Try the [Photoshop Anthology]("http://www.sitepoint.com/books/photoshop1/") (book) from Sitepoint if you're interested. It taught me Photoshop very well. GIMP can do many similar things to PS (save CMYK) but, to put it bluntly, is not user friendly. Given the abilities of the software and scope of the project, in my opinion, they don't even try. (Sorry for the designer flames)

Fireworks might make more sense to you too. It reminds me of an easier version of the old Canvas for those who've been designing for a while.

---

### Post by Wybiral on 2007-10-29
> **pmasiar said:**
> Now we would like to have some kind of karma, because often people with little or no experience give bad advice. Not bad opinion, but plain bad advice. Any ideas how to do that?

I want karma on this forum too.

I also want ubuntu_geek to fix that annoying JS bug (U_G, I will even do it for you if you'd like since I already know what's wrong and how to fix it).

---

### Post by skeeterbug on 2007-10-29
I am fine with the coupled approach with Django. Too many libraries is a problem in Java and Perl. I am pretty sure each component in Django can be de-coupled though (I have yet to need to do this, but they mentioned you can use a different ORM or template system in the docs if you wanted).

---

### Post by runningwithscissors on 2007-10-30
What's with Guido's dislike of XML? I am not crazy about it either but you look at Genshi and then at Django's templating.

Genshi looks far cleaner and is also easier to understand.

And of course, I want to avoid randomly embedding python (or some brand new template language) into my template. That's what makes PHP and sometimes, even Rails, so ugly.

And since most of the templates output XHTML (which is a subset of XML), it's easier if you just use markup in your template instead of complicated code snippets.

---

### Post by pmasiar on 2007-10-30
> **runningwithscissors said:**
> What's with Guido's dislike of XML? I am not crazy about it either but you look at Genshi and then at Django's templating.

Genshi looks far cleaner and is also easier to understand.

And of course, I want to avoid randomly embedding python (or some brand new template language) into my template. That's what makes PHP and sometimes, even Rails, so ugly.

And since most of the templates output XHTML (which is a subset of XML), it's easier if you just use markup in your template instead of complicated code snippets.

Exactly. this is why I consider "no XML in templates" decision a mistake. Also, with XML, you can give your template to a designer to prettify it, and she can see how it would look like even without data, and you know she will not break anything (because web designer tools are smart enough not to touch XML they don't recognize). With templating like Django uses, it is hit or miss.

BTW, sometimes I do want procedures in templates: sometimes data provided by controller need to be processed for view (in a template-specific ways), and in that case, I prefer to do the processing in Python and not in some half-baked small expression language.

---

### Post by WinterWeaver on 2007-10-30
Zope uses a templating language, which is XML compliant. Python scripts are also used with zope.

[www.zope.org](www.zope.org)

It's a bit harder to find hosting for zope tho, and you may pay a bit more for zope hosting.

sample Zope code:
```
<html>
	<title tal:content="template/title">Most Amazing Title</title>
	<body>
		<p>
			This is <b tal:replace="template/title">the Title</b>
			<br />
			The URL is <span tal:replace="request/URL">http://www.example.com</span>.
		</p>
		
		<table boder="1" width="100%">
			<tr>
				<th>Number</th>
				<th>ID</th>
				<th>Meta - Type</th>
				<th>Title</th>
			</tr>
			<tr tal:repeat="item container/objectValues">
				<td tal:content="repeat/item/number">#</td>
				<td tal:content="item/getId">Id</td>
				<td tal:content="item/meta_type">Meta-Type</td>
				<td tal:content="item/title">Title</td>
			</tr>
		</table>
	</body>
</html>
```

---

### Post by pmasiar on 2007-10-30
@dataw0lf: TG has good discussion [Why use TurboGears2 over just Pylons alone?](http://groups.google.com/group/turbogears/browse_thread/thread/265a5ce978041b4b/7d5d45be358c3838#7d5d45be358c3838) 
Mark Ramm said: "Pylons maintains a lot of flexibility by not choosing between ORM's or
template engines, etc.   But that makes it hard to create prebuilt
mini-apps (like a web forum, or a user registration package) which by
necessity need to share with the rest of your site).   It also makes
it harder to build tools like the web based model object creator that
we have in turbogears 1.

At this point none of those things exist in Pylons, and probably never
will, they will be build as TG2 apps so that there is a defined core
that they know they can depend on. "

---

### Post by dataw0lf on 2007-10-30
> **pmasiar said:**
> @dataw0lf: TG has good discussion [Why use TurboGears2 over just Pylons alone?](http://groups.google.com/group/turbogears/browse_thread/thread/265a5ce978041b4b/7d5d45be358c3838#7d5d45be358c3838) 


I guess time will only tell.  Personally, I'll continue to advocate Django and Pylons;  you can continue to advocate TurboGears.

What sites have you done in TurboGears?

---

### Post by skeeterbug on 2007-10-30
> **pmasiar said:**
> 
BTW, sometimes I do want procedures in templates: sometimes data provided by controller need to be processed for view (in a template-specific ways), and in that case, I prefer to do the processing in Python and not in some half-baked small expression language.

Not sure if you are talking about filters in Django here or not. You can write your own filters to extend that functionality, in Python. They force you to create the filter in a Python module instead of in the template, thus making it re-usable. Doesn't seem so bad if you ask me. Maybe I mis-understood your conversation though! :)

EDIT:
Some links on the subject:
[http://www.djangoproject.com/documentation/templates_python/#writing-custom-template-filters](http://www.djangoproject.com/documentation/templates_python/#writing-custom-template-filters)
and
[http://www.djangoproject.com/documentation/templates_python/#writing-custom-template-tags](http://www.djangoproject.com/documentation/templates_python/#writing-custom-template-tags)

---

### Post by vizitorq on 2008-01-19
i recommend using django   [http://www.djangoproject.com](http://www.djangoproject.com)

it rocks my face off!

---

