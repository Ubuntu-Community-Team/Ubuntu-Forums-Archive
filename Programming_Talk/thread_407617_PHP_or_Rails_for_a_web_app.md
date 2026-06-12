---
title: "PHP or Rails for a web app?"
date: 2007-04-12
forum: Programming Talk
---

### Post by darrenm on 2007-04-12
Which do you think is best for the front end to UbuntuGatewayServer?

I can do PHP or Rails to a certain degree. I'm at a juncture where I can go big into one or the other but I can't really do both at the same time as I'll just confuse myself.

The app needs to run system commands, shell scripts and do a fair bit with a MySQL database. To look pretty will be a bonus. It will need a tight user auth system, take a lot of input from the users, do a fair bit of logic processing and do lots of tests on the data that is submitted. I also want a file upload and parse capability.

I'm loving Rails at the moment and it seems once you get into it you just speed along but PHP is a bit more free-form and a bit more proven at this kind of thing where I will have to change the Rails conventions in a few places to get it do what I want but then this extra fudging will be necessary in PHP anyway to get to the same point.

Should I do it in PHP first then after all the lessons have been learnt etc, rewrite it in Rails? Or should I just jump into Rails now and build up a kick-*** AJAX front-end? Or for the type of app it needs to be should I go with convention and all the loads of support and use PHP?

---

### Post by pmasiar on 2007-04-12
Just read [article about twitter](http://www.radicalbehavior.com/5-question-interview-with-twitter-developer-alex-payne/) claiming to be biggest Rail app. Guy says that Ruby is slow, even more slow than Python, to the point it is hard to scale up. Just FYI.

---

### Post by skeeterbug on 2007-04-12
> **pmasiar said:**
> Just read [article about twitter](http://www.radicalbehavior.com/5-question-interview-with-twitter-developer-alex-payne/) claiming to be biggest Rail app. Guy says that Ruby is slow, even more slow than Python, to the point it is hard to scale up. Just FYI.

I doubt a personal server that a handful of administrators are connecting to constitutes as a big web application. I would really like to see some numbers behind his claim too. We get quite a bit of traffic on our site [http://www.mission3.com/](http://www.mission3.com/) and have no problems. It is just a single box.

He also mentions it can't talk to more than one database at a time? 
[http://wiki.rubyonrails.com/rails/pages/HowtoUseMultipleDatabases](http://wiki.rubyonrails.com/rails/pages/HowtoUseMultipleDatabases)

Here is a success story:
[http://earthcode.com/blog/2007/02/four_mongrels_digg_and_lifehac.html](http://earthcode.com/blog/2007/02/four_mongrels_digg_and_lifehac.html)


I honestly think this guy would have had problems in PHP too.

---

### Post by pmasiar on 2007-04-12
With all due respect to your app, looks like [twitter](http://en.wikipedia.org/wiki/Twitter) is used by more than "a handful of administrators". Looks like lots of messages going in and out, potentially much more *users* and *traffic* than your very specialized bioscience website. Other than that, I prefer Python and TurboGears :-)

---

### Post by darrenm on 2007-04-12
I assumed Skeeterbug to be talking about the UbuntuGatewayServer frontend when talking about a personal web server with a handful of administrators.

Python is a beautiful language. But it seems Turbogears and Django aren't quite documented or popular enough to have lots of support to fall back on as of yet. I may be wrong.

If I take the PHP route I'll have to do a LOT more coding but it should be relatively straightforward.
If I take the Rails route I'll do a lot less coding but I'll be scratching my head a bit getting my very specific requirements to fit in with convention over configuration.

---

### Post by skeeterbug on 2007-04-12
> **pmasiar said:**
> With all due respect to your app, looks like [twitter](http://en.wikipedia.org/wiki/Twitter) is used by more than "a handful of administrators". Looks like lots of messages going in and out, potentially much more *users* and *traffic* than your very specialized bioscience website. Other than that, I prefer Python and TurboGears :-)


Darren was right, I was talking about his project. I tried DJango, and I originally liked the idea of Python, but I could never come to terms with the formatting. I just recently tried messing with some perl/cgi, but my host wouldn't install mod_perl on apache for me. DBIx was neat, but not as easy as AR. I agree that RoR isn't the fastest thing out there, but that article is full of fictional crap. I wouldn't use Ruby's speed as a factor to use it on this type of project.

There is a decent sized admin section on our site. Sometimes it is months before I even touch anything on it, and it is *ALWAYS* easy to go back and maintain the code.

---

### Post by gh0st on 2007-04-12
> **pmasiar said:**
> With all due respect to your app, looks like [twitter](http://en.wikipedia.org/wiki/Twitter) is used by more than "a handful of administrators". Looks like lots of messages going in and out, potentially much more *users* and *traffic* than your very specialized bioscience website. Other than that, I prefer Python and TurboGears :-)

...or try out Django as an alternative to TurboGears. Nothing against TurboGears I've never tried it but I use Django quite a bit and it rocks :)

[http://www.djangoproject.com/](http://www.djangoproject.com/)

Check it out if you're interested in alternatives to rails. It is very similar in some respects but uses Python instead of Ruby. It's still new and developing but the future looks good I think

---

### Post by skeeterbug on 2007-04-12
> **gh0st said:**
> ...or try out Django as an alternative to TurboGears. Nothing against TurboGears I've never tried it but I use Django quite a bit and it rocks :)

[http://www.djangoproject.com/](http://www.djangoproject.com/)

Check it out if you're interested in alternatives to rails. It is very similar in some respects but uses Python instead of Ruby. It's still new and developing but the future looks good I think

RoR needs to clone what DJango does in the admin interfaces. Scaffolds in Rails are nasty, in DJango it's lovely and you could use it in production 90% of the time, with scaffolds you have to pretty much redo the interface, 100% of the time.

---

### Post by Mirrorball on 2007-04-12
I also prefer Django. Between PHP and Ruby, I'd choose PHP only because I already know it well and there are good PHP frameworks too. If you choose RoR, please don't put a lot of Ajax just because you can. Write an application that works even when Javascript is disabled, then add Ajax to make it more **usable.**

---

### Post by darrenm on 2007-04-13
> **skeeterbug said:**
> I agree that RoR isn't the fastest thing out there, but that article is full of fictional crap. I wouldn't use Ruby's speed as a factor to use it on this type of project.

Yeah speed isn't really an issue here as long as it can take one or two people running it at once clicking a few things ;)

> **gh0st said:**
> ...or try out Django as an alternative to TurboGears. Nothing against TurboGears I've never tried it but I use Django quite a bit and it rocks :)

[http://www.djangoproject.com/](http://www.djangoproject.com/)

Check it out if you're interested in alternatives to rails. It is very similar in some respects but uses Python instead of Ruby. It's still new and developing but the future looks good I think

Interesting. I would like to put all my eggs in one basket by going big into one language. I started doing Python previously and was enjoying it but as I started this project I realised I needed to leave Python while I got heavily into Ruby or PHP as they seemed the best for this type of thing. If Django can do everything RoR can do with relation to quick development, easy DB, scaffolding, well documented, good books (like Agile Development with Rails) then I would be very interested into using it.

> **Mirrorball said:**
> I also prefer Django. Between PHP and Ruby, I'd choose PHP only because I already know it well and there are good PHP frameworks too. If you choose RoR, please don't put a lot of Ajax just because you can. Write an application that works even when Javascript is disabled, then add Ajax to make it more **usable.**

Seems to be a lot of support for Django. I'll have to look into it. Can it do the nice drag and drop stuff and autocomplete of Script.aculo.us that Ruby can? Thats the only AJAX I want, just to make it more functional for admins to drag and drop users, domains and autocomplete settings etc.

---

### Post by darrenm on 2007-04-13
Right that's it. Django it is. I've only been playing a bit and so far it rocks.

---

### Post by deuce868 on 2007-04-13
When it comes to system scripts I much prefer python. The libraries available make writing some decent system management scripts pretty nice, easy, and clean. 

When it comes to the web end, I've ended up just writing PHP front ends that call the python scipts behind the scenes. I know it better and deployment is just a lot easier than trying to put together the parts required for something like turbogears. 

Of course this is all a series of simple things, but if you're going to be doing scripts to manage a system I'd seriously take a look at Python.

---

### Post by Mirrorball on 2007-04-13
> **darrenm said:**
> Can it do the nice drag and drop stuff and autocomplete of Script.aculo.us that Ruby can? Thats the only AJAX I want, just to make it more functional for admins to drag and drop users, domains and autocomplete settings etc.
You can add scriptaculous to any page at any site. Django doesn't have a preferred Javascript library like RoR, you can use any of them: scriptaculous, JQuery, Dojo... Just download it and add it to your page. You'll have to write Javascript yourself to add a behavior to an HTML element, but with these frameworks, it's easy. But RoR still makes it even easier to add Ajax to a page.

---

### Post by gh0st on 2007-04-14
> **darrenm said:**
> Right that's it. Django it is. I've only been playing a bit and so far it rocks.

Django is really new, even newer than Rails but it's gaining momentum I think. Personally I prefer Python to Ruby as a scripting language, just my own preference really. There aren't a lot of books for Django yet it's too new, the Django book is available on the site but it's still being written and won't be in print for a while I think.

After playing with Django and Rails a bit I think they both have areas where they excel. I tried Django first and I think the ORM is much better, the pre-built Admin interface is great as well. I find it strange that you have to write the SQL scripts to create databases in Rails whereas Django will generate the SQL for you from scratch, doing things like Many-To-Many relationships is so much easier in Django because of this I find. It knows to create a link table and just does it for you. Some people will prefer the control they get from writing their own SQL but I suspect people who feel like that wouldn't be using Rails or Django in the first place.

I think you can tell what my favorite is, I'm just a Python guy at heart :)

Rails is far more popular at the moment and has the media buzz but I think Django isn't far behind. Version 1.0 of Django is really close now I think, it will be interesting to how the frameworks compare in a years time. Django is catching up fast, it can't stay a secret forever.

---

### Post by runningwithscissors on 2007-04-14
I like Pylons the best of the Python frameworks. Just feels very easy to use (from a programmer's point of view).
Of course they haven't got a 1.0 release out, so don't throw your lot in with it in the case of a large project just yet.
Just keep the option in mind, however.

---

### Post by darrenm on 2007-04-14
> **gh0st said:**
> Django is really new, even newer than Rails but it's gaining momentum I think. Personally I prefer Python to Ruby as a scripting language, just my own preference really. There aren't a lot of books for Django yet it's too new, the Django book is available on the site but it's still being written and won't be in print for a while I think.

After playing with Django and Rails a bit I think they both have areas where they excel. I tried Django first and I think the ORM is much better, the pre-built Admin interface is great as well. I find it strange that you have to write the SQL scripts to create databases in Rails whereas Django will generate the SQL for you from scratch, doing things like Many-To-Many relationships is so much easier in Django because of this I find. It knows to create a link table and just does it for you. Some people will prefer the control they get from writing their own SQL but I suspect people who feel like that wouldn't be using Rails or Django in the first place.

I think you can tell what my favorite is, I'm just a Python guy at heart :)

Rails is far more popular at the moment and has the media buzz but I think Django isn't far behind. Version 1.0 of Django is really close now I think, it will be interesting to how the frameworks compare in a years time. Django is catching up fast, it can't stay a secret forever.

I know exactly where you're coming from. Rails has a lot of nice features but the fact that Django is in Python wins it for me. Well actually its the admin interface but I do prefer Python to anything. Ruby is nice in that it forces you to be OO in everything which makes the whole language a bit easier to understand when everythings an object. But I love the way Python will do just about anything and it really makes sense. The main thing that people have against Python is forced indenting which I prefer anyway. Theres something nice about Python, I just can't help really enjoying working with it.

For my app I can use the admin interface and just put my backend stuff directly into the functions that the views call or I can make the calls to backend scripts from the functions.

So Django fits my needs perfectly. I would have done the backend scripts in Python anyway so tying it all up together and having a templatable admin pre-built for me wraps it up.

---

### Post by gh0st on 2007-04-14
> **runningwithscissors said:**
> I like Pylons the best of the Python frameworks. Just feels very easy to use (from a programmer's point of view).
Of course they haven't got a 1.0 release out, so don't throw your lot in with it in the case of a large project just yet.
Just keep the option in mind, however.

Wow I've never heard of Pylons, you learn something new everyday :) I'll have to check it out and see what it's about.

Thanks for the tip.

---

### Post by pmasiar on 2007-04-14
Python has more web frameworks than reserved keywords :-)

At PyCon 2005 there was influential presentation about Python web frameworks and "too many to choose from" syndrome, which is against Python mantra "there should be one obvious way to do it right", and people asked Guido for a pronouncement. Guido said he does not do web apps... Then he got hired by Google to [make a web app for them](http://www.artima.com/weblogs/viewpost.jsp?thread=146149). He liked Django most, and pronounced it as default Python web framework, but many pythonistas consider Django un-pythonic, too closed to itself, and too oriented to content presentation (as compared to web-based apps).

TurboGears was created as integration of "best of breed" pythonic tools and Pylons as meta-framework to standardize and  integrate tools - Pylons and TurboGears plan to merge.

BTW Django is not that young - is almost as old as Rails, but just was developed without much public input, used for about a dozen newspaper-like websites before going public.

---

### Post by gh0st on 2007-04-15
I knew Guido was working for Google, I heard he was making a web app for them and he was also doing some stuff with Django. Maybe he'll extend it a bit or something. I also read that he is allowed to spend half of his work hours just working on Python, thats pretty cool. What's TurboGears like then pmasiar? I have to admit I haven't really looked into it yet. I know there are a couple of books out, is it more mature than Django? 

I haven't done any major work with Django yet, just been playing with it out of curiosity, maybe TurboGears is something I should look into more. It does seem like Python has a lot of web frameworks at the moment. It is kinda unpythonic :D

---

### Post by pmasiar on 2007-04-15
I didn't used Django, just doing some research comparing things.

Django was created all by same team, it is tightly integrated, and uses lots of magic to hold things together. People say it works great if you like all parts as is, without changes. When you want to tweak parts in and out, Django is not happy. But is is mature, with all parts documented by same team in same style. "Magic removal" is next step for them, make it more open and easier to swap parts. It was created for newpapers, as content management system, so it is optimized towards that kind of apps.

TurboGears was created as integration of "best of breed" parts, developed by outside groups, so is not as homogenous as Django is. And parts ar often superior to those in Django: object-relation mapper SQL alchemy is best of Python ORMs, etc. In TG, it is easier to swap parts and add new plugins. Some groups are so interested in TG as best promotion of their part that they work together with TG team to make it integrate better. Some very smart web developers, not satisfied with "my way or highway" approach of Django, work on TG, and on Pylons. TG are said to merge with Pylons, and are designed for tricky apps, beyond capabilities of simple context management system as Django is.

But this is all from comparisons of Python gurus smarter than me, I looked at Django but never used it, because I decided TG better fits my needs.

>  It does seem like Python has a lot of web frameworks at the moment. It is kinda unpythonic :D

20 is maybe too many. But 3, designed for different niches and different approach, are fine. Just one might be not enough - no competition, no cross-pollination, stagnation.

---

### Post by Mirrorball on 2007-04-15
> **pmasiar said:**
> "Magic removal" is next step for them, make it more open and easier to swap parts.
It's not the next step, it was two or three steps ago. :)

---

### Post by gh0st on 2007-04-15
> **pmasiar said:**
>  I looked at Django but never used it, because I decided TG better fits my needs.


I looked at Django first, played with it, liked it, then glanced (and I do mean glanced) at TurboGears and thought I may as well use Django I already know it does what I want.

I might look at TG again in the future though if I have a less conventional app to do. I suppose it's the same thing that always get's said sooner or later in these threads "use whatever suits the job" :D

Most people I speak to just seem to want content management systems at the moment and Django is designed for that.

---

### Post by kfries6 on 2007-04-28
I think you are asking the wrong question.

PHP and Rails are similar in the pages they can put out, but that is where the similarities end.  RoR is much closer to Java than PHP.  I can not speak for the two Python offerings.

PHP is a scripting language.  It was originally designed to automate Perl by providing shortcuts.  PHP has grown grealy since its Personal Homepage Processor days.  However, it still lacks many tools that cause it to still be best suited for web pages (futher explaination on that in a moment).  PHP is fantastic a providing interactive pages with some basic customizations.  But in the end, its just a web page generator.  A great one, but really nothing more.

Java and Rails are a different type of environment.  These environments retain state, and really treat the web page sent back as simply a I/O mechanism.  These are actually closer to being applications running on a server.  However, instead of firing up dialog boxes using GTK or QT, they use HTML and a web browser.

In many ways this is a subtle difference, and in many ways it is not.  Your question should be closer to: am I writing a web portal where people can come in and check the latest news, contribute to a blog, etc (in which case use PHP) or am I writing a more conventional application where users can log into this application, and perform more conventional project tasks such as setting priorities, assigning work tasks, deadlines, etc. (in which case I would use rails).

Both tools can be used for either type of web site.  Rails has more structure and a persistance than does PHP.  That stucture can help, or get in the way.  With a more traditional application that just so happens to go across the web, Rails is a godsend.  But that structure is bothersome in a fast update, interactive driven web portal.

So I ask, what are you really going to use it for... and how do you expect to deliver that content?

I hope this helps
Kevin Fries

---

