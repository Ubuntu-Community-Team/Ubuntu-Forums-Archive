---
title: "What language should I learn?"
date: 2008-04-05
forum: Programming Talk
---

### Post by alcatraz678 on 2008-04-05
Hey guys, I'm a beginner, so expect me to know just a little in web development.

I'm particularly interested in web development environment, I have experience using XHTML, & CSS.. But I'm not yet proficient. I can develop static website. Not graceful websites though, I want to expand my knowledge so I can develop a website with more interactivity and design in mind.

Please suggest me something that I should learn next, I can search it my own but there's really a lot of languages there. PHP, ASP, Java, Javascript, C#.. So I'll just let the masses decide what should I learn next.

And please give me a good links or a book that I can use to learn the language.

---

### Post by hessiess on 2008-04-05
PHP and javascript. though quite alot of dinamic websites use flash.

---

### Post by pmasiar on 2008-04-05
> **hessiess said:**
> PHP and javascript. though quite alot of dinamic websites use flash.

Wrong. See sticky FAQ, this questions is asked 3 times weekly. 

Start with Python. See wiki in my sig.

Then you need SQL for database access, and maybe JavaScript for AJAX. PHP is messy, avoid it if you can, and Java too. Other option might be Ruby, but IMHO Python is better.

---

### Post by danbuter on 2008-04-05
He said specifically internet pmasiar. So he should learn PHP and Javascript. While Python with Django isn't bad, it's not for beginners or the typical web developer.

---

### Post by hessiess on 2008-04-05
[http://www.w3schools.com/js/default.asp](http://www.w3schools.com/js/default.asp)

[http://devzone.zend.com/article/627-PHP-101-PHP-For-the-Absolute-Beginner](http://devzone.zend.com/article/627-PHP-101-PHP-For-the-Absolute-Beginner)
[http://www.w3schools.com/php/php_intro.asp](http://www.w3schools.com/php/php_intro.asp)

learn javascript first, as it runs in the broser. running PHP requires a web server.

python is ok, but its not used as much in web dev.

---

### Post by alcatraz678 on 2008-04-05
I don't like the W3 tutorials offered there. It's not really helpful because they offer little hints.

Python, please tell me why should it be Python first when starting web development?

---

### Post by danbuter on 2008-04-05
It shouldn't. Python is the easiest to learn general purpose language. For web development, learn Javascript.

---

### Post by lnostdal on 2008-04-05
skip php .. it's not a nice language .. (it has .. interesting .. language design problems)

again, if i met myself back when i was in your situation i'd go for Common Lisp .. JavaScript is not an option but a requirement -- so i won't mention it as you already know you need it

[http://www.gigamonkeys.com/book/](http://www.gigamonkeys.com/book/)
[http://www.lispworks.com/documentation/HyperSpec/Front/](http://www.lispworks.com/documentation/HyperSpec/Front/) 
(the hyperspec can be downloaded for offline reading here: [ftp://ftp.lispworks.com/pub/software_tools/reference/HyperSpec-7-0.tar.gz](ftp://ftp.lispworks.com/pub/software_tools/reference/HyperSpec-7-0.tar.gz) )

as for implementation go for SBCL: [http://sbcl.sourceforge.net/](http://sbcl.sourceforge.net/)

..this is how i install SBCL [http://common-lisp.net/~lnostdal/writings/sbcl.html](http://common-lisp.net/~lnostdal/writings/sbcl.html)

you need a http interface when doing web work: [http://www.weitz.de/hunchentoot/](http://www.weitz.de/hunchentoot/) .. either run it as a stand-alone http/web server or place it behind apache or lighttpd (i use lighttpd .. it's simple and small)

that should be it .. you're good to go

---

### Post by pmasiar on 2008-04-05
> **danbuter said:**
> He said specifically internet pmasiar. So he should learn PHP and Javascript. While Python with Django isn't bad, it's not for beginners or the typical web developer.

Even web developer needs to parse text files in commandline sometime, and I do consider Turbogears cleaner way to develop even small web app, because it gently forces MVC instead of the mess PHP inevitably becomes.

**edit:**... so you need something else beyond PHP, which is Python :-)

Javascript is client-side, you need first develop server-side app to get pages. It is possible to have web app without javascript, but not without serverside code.

---

### Post by Shining Arcanine on 2008-04-05
> **alcatraz678 said:**
> Hey guys, I'm a beginner, so expect me to know just a little in web development.

I'm particularly interested in web development environment, I have experience using XHTML, & CSS.. But I'm not yet proficient. I can develop static website. Not graceful websites though, I want to expand my knowledge so I can develop a website with more interactivity and design in mind.

Please suggest me something that I should learn next, I can search it my own but there's really a lot of languages there. PHP, ASP, Java, Javascript, C#.. So I'll just let the masses decide what should I learn next.

And please give me a good links or a book that I can use to learn the language.

PHP was my first programming language. If you want to learn web programming, I highly recommend that you learn PHP. Here is a free web host that has PHP support:

[http://www.tripod.lycos.co.uk/](http://www.tripod.lycos.co.uk/)

---

### Post by smartbei on 2008-04-05
@Shining Arcanine:

There are quite a few hosts that are better (have no ads, offer more features, etc.) than the one you suggested - see the ones rated high [here]("http://www.free-webhosts.com/webhosting-01.php").

---

### Post by rye_ on 2008-04-05
Rails seems to be a big player 
(I'm trying to plough through it :))

That said, at the moment Rails 2.0 is (relatively) new out, superceding Rails 1.2.  This means all books out at the moment are geared toward Rails 1.2.  There is a difference in the way things are done.

Try [http://railsonedge.blogspot.com/](http://railsonedge.blogspot.com/)


Ryan

---

### Post by alcatraz678 on 2008-04-05
I don't plan to learn a lot of languages.

I indicated that I'm just a newbie. Really newbie. I usually don't want to be treated as a newbie, but please in order for me to learn I need to be treated as a newbie.

Okay here's the thing, I want to learn web development. Should I learn JavaScript first?

Honestly, I tried to read a book about Javascript and I didn't understand it throughly. It's full of deducting numbers, adding numbers, etc etc.. And my point is, what's the numbers all about to do with programming? Because I hate math, and if programming is all about math.. Then I shall force myself to love math.

I read Javascript: A beginners guide 2nd edition.

I'm almost finish but I don't really get it. I mean how can I use all those functions to make a website like Techmeme for example.

Please treat me as a newbie.. I'm eager to learn.

---

### Post by alcatraz678 on 2008-04-05
Here's the reason why I don't want to learn a lot of languages.

[http://duartes.org/gustavo/blog/post/2008/04/02/New-Languages-Considered-Harmful.aspx](http://duartes.org/gustavo/blog/post/2008/04/02/New-Languages-Considered-Harmful.aspx)

I plan to sharpen my knowledge to the languages that I will need most.

---

### Post by ruy_lopez on 2008-04-05
> **alcatraz678 said:**
> 
I read Javascript: A beginners guide 2nd edition.

I'm almost finish but I don't really get it. I mean how can I use all those functions to make a website like Techmeme for example.

On its own, Javascript won't make a dynamic website. You need to use Javascript with HTML DOM and CSS (at a minimum) to get good results.

[The W3Schools website]("http://www.w3schools.com/default.asp") has plenty of tutorials on Javascript, HTML DOM, and CSS, to get you started.

EDIT: Just noticed you dislike W3Schools tutorials. In that case, any library book on HTML/CSS will give you an understanding of the elements and their design properties. No Javascript book should be without a section on using Javascript to access/alter HTML elements and CSS properties through DOM. If your book doesn't have a section on DOM, get one that does, or use the W3Schools DOM reference (not a tutorial).

---

### Post by jdonnell on 2008-04-05
it really depends on your goals. If you just want to make some basic websites then learn php. 

If you want to become a real programmer then don't learn php. Python is a good choice but I wouldn't say it's clearly the best as others have. Ruby would be equally as good as would scheme. Hell, you can even use javascript on the server side with rhino and javascript is a good language despite it's reputation.

---

### Post by Shining Arcanine on 2008-04-05
> **alcatraz678 said:**
> Here's the reason why I don't want to learn a lot of languages.

[http://duartes.org/gustavo/blog/post/2008/04/02/New-Languages-Considered-Harmful.aspx](http://duartes.org/gustavo/blog/post/2008/04/02/New-Languages-Considered-Harmful.aspx)

I plan to sharpen my knowledge to the languages that I will need most.

My recommendation is PHP. It was my first language and it made learning to write code easy.

Of course, by learning PHP, I did not learn about typed variables, scoping, structures and many other things that exist in other programming languages, for which there was a fairly high learning curve, but I did learn quite a bit about algorithms and I found myself writing PHP scripts to solve simple problems in very short periods of time that otherwise would have taken a while to do by hand. I have done well in every computer science class I have taken and I found myself to be very well prepared for discrete mathematics.

---

### Post by jdonnell on 2008-04-07
> **rye_ said:**
> 
That said, at the moment Rails 2.0 is (relatively) new out, superceding Rails 1.2.  This means all books out at the moment are geared toward Rails 1.2.  There is a difference in the way things are done.


the differences are minimal and for anyone that wants to learn rails I highly recommend 'The Rails Way' by obie. It covers 2.0 too!

---

### Post by H264 on 2008-04-07
*sigh* learning how to program (BASIC I don't really count) in Java on my own, I always swore by it, now after learning more about and using other languages I've concluded it does not really matter. What does matter the most is that you stick with it, never looking at another language until you fully understand it and feel comfy with making elegant software. Eventually somewhere along the line you will feel like the language is holding you back to solve a particular problem, only then should you think about learning a different language.

You said Web Dev... there are a couple types, server side and client side, most people seem to start on the client side making boring static pages with HTML, CSS, and maybe something like flash (as much as I hate flash). if you stick to client side, then Javascript is a must, Flash seems to be popular only because its the only choice right now, and Java (I know, applets are _way_ over rated, but they are useful for certain things).

Server side is when things get interesting with lots more possibilities... Really you can use any programming language you want for server side stuff; in reality there are only a few that are used because its much easier to use. I'm not going to tell you which one or two is best (yet), instead let me suggest learning one of the more robust languages. One of the ones where should you want to do something else the language will work well for the problem.

Really the popular ones everyone seems to use includes PHP, Perl, Python, Ruby, Java, and probably a few others I can't think of. Python is probably the most used language, and is popular for server side stuff, same with Java. PHP is used a lot in server side web stuff, but almost never outside of the web. Perl is used some, but it seems by mostly people who started when it was one of a couple/few choices. Ruby came on the scene with RubyOnRails and got everybody excited with RoR, though now I think Python has something kinda like it.

Really all I've done is talk a lot about stuff I know little about, having said that I have a Ruby book sitting on the shelf waiting for me to get into server side programming for my own website. The most experienced and versed people I've talked to about such matters all suggested against going with PHP and Perl, instead suggesting Python or Ruby. Ruby seems to be hyped more than others right now, but at this point I think its past its fad stage, so I would not worry about that.

Above all, never give up the one you choose until you can get stuff done with the language.

---

### Post by runningwithscissors on 2008-04-08
If you are interested in web development I second the PHP suggestion. 

Nevermind these python and rails suggestions. While I like python and ruby, you'll lose interest setting up the framework and fighting with FastCGI and some junk pontificating about how MVC is the dog's ******** before you actually get to any coding.

Install apache with mod_php then put a file called index.php in your web dir containing the line <?php echo 'Hello World.' ?>
That's all, and you've begun web development.

---

### Post by pmasiar on 2008-04-08
> **runningwithscissors said:**
> you'll lose interest setting up the framework and fighting with FastCGI 

This is BS. Both Turbogears and Django come with development server, which is **much** easier to set up than Apache. 'create project' script will create valid project structure and config file with running 'It works!' page. From start downloading TG to 'it works' page, it is less than 15 minutes, max.

FastCGI comes to play **much** later, in production deployment. Years from now.

It is really frustrating how people with little experience or understanding feel free to dismiss superior solution. Such is life on Internet. :-(

---

### Post by tseliot on 2008-04-08
> **pmasiar said:**
> This is BS.
...
It is really frustrating how people with little experience or understanding feel free to dismiss superior solution. Such is life on Internet. :-(
I hope that by BS you mean Bachelor of Science ;)

Don't let your frustration prevent you from following the code of conduct of this forum.

---

### Post by runningwithscissors on 2008-04-08
> **pmasiar said:**
> This is BS. Both Turbogears and Django come with development server, which is **much** easier to set up than Apache. 'create project' script will create valid project structure and config file with running 'It works!' page. From start downloading TG to 'it works' page, it is less than 15 minutes, max.

FastCGI comes to play **much** later, in production deployment. Years from now.

It is really frustrating how people with little experience or understanding feel free to dismiss superior solution. Such is life on Internet. :-(

Actually, I am an experienced web developer. 

My own home site runs on python, with a nice little app I made up myself, no turbogears/django involved.

And I am not talking about 'just' fastcgi and deployment, but the configs as well (I didn't need to touch any configs to set php up with lighttpd on my machine), and the whole MVC thing. Worrying about databases, models, templates etc. can wait. 

If someone wants to start learning web programming, they don't need all that.

---

### Post by lnostdal on 2008-04-08
> **H264 said:**
> Eventually somewhere along the line you will feel like the language is holding you back to solve a particular problem, only then should you think about learning a different language.


yeah, or - this can be quite hard to discover if you never look left or right but only travel in a direct line .. straight ahead - as a race horse

i suppose it might depend somewhat on your personality .. or maybe you'll discover it if you start hitting hitting walls (or other horses? as in crushingly intense forum flame-wars?) .. i dunno

other times it can _feel_ like you're doing something important .. you're writing lots of code; that's good right? .. but really, even if you don't hit a brick wall and go to a complete halt instantly which you would surely notice immediately - you might still be jogging in a tar pit trap while others are taking the highway leaving you way behind looking silly 

.. if you feel this is happening its time to try to change strategy, and if the language don't allow you to do this it's time to look elsewhere .. the problem, is that it might take you _quite_ a lot of time to discover that this is happening if you never look left and right and see others passing you!

but yeah, stick with something for some time .. at least a month or two .. and realize that learning a new language should be a serious investment and not something taken lightly .. it will take you months and years to be equally proficient in that new language -- so you got to make sure it will be worth it and that you understand the problems with your current language and how these are solved in the new language

there are some clear or obvious exceptions though .. some languages are so poor at doing what you're trying to do with them Right Now, that switching to a new language and spending even just a day learning/using it will make you more productive and give results instantly compared with sometimes 0 results from your current language even given your best efforts

(..so yes; language _does_ matter.. i am not, in any way - incorrect here .. anyone who would want to oppose me on this; don't.. i am not in the mood, and i do not have the patience for any discussion regarding this..)

reading this [http://wiki.alu.org/The_Road_to_Lisp_Survey](http://wiki.alu.org/The_Road_to_Lisp_Survey) (and numerous posts and flame-wars on comp.lang.lisp by the many people there, and the articles by Paul Graham and others) and recognizing myself and my current situation (2003-2004) in the flashbacks in those stories .. was what eventually made me decide it was time for a switch .. it turned out to be the Right Thing to do for me .. i can honestly say, for the first time in years - that i now enjoy programming again

---

### Post by ruy_lopez on 2008-04-08
> **lnostdal said:**
> yeah, or - this can be quite hard to discover if you never look left and right but only travel in a direct line .. straight ahead - as a race horse
[...]
or maybe you'll discover it if you start hitting hitting walls (or other horses? as in crushingly intense forum flame-wars?) .. i dunno
[...]
but really, even if you don't hit a brick wall and go to a complete halt instantly which you would surely notice immediately - you might still be jogging in a tar pit trap while others are taking the highway leaving you way behind and looking silly

Flog that metaphor!

---

### Post by lnostdal on 2008-04-08
sorry .. uh, what's "flog"?  (seriously, i have no idea!)

---

### Post by Paul Miller on 2008-04-08
@lnostdal: To "flog" is to "beat," as in with a stick or a whip. 

To the OP: If you're interested in web development, you should definitely be up on Javascript.   Otherwise, assuming this is just a hobby thing, just pick a language and start playing with it; if you like the way it goes, keep going with it.  If you don't, stop and pick up another one.

---

### Post by jdonnell on 2008-04-08
> **runningwithscissors said:**
> While I like python and ruby, you'll lose interest setting up the framework and fighting with FastCGI and some junk pontificating about how MVC is the dog's ******** before you actually get to any coding.

Install apache with mod_php then put a file called index.php in your web dir containing the line <?php echo 'Hello World.' ?>
That's all, and you've begun web development.

I don't know about python, but ruby is very easy to get running on your local machine for learning. Setting it up for production is a different story (but so is php). If you're on windows it's far easier to get ruby running through webrick and mongrel than it is to get php running through apache. If you're on a mac (leopard) then you already have both php and rails ready to go. On ubuntu it's trivially easy to get php or rails running. 

steps for rails:
1. install ruby and rails
2. on the command line run: 
 - $ rails my_new_app
 - this will create a folder called my_new_app containing your rails app
3. cd into my_new_app and run: 
 - $ ruby script/server

You now have a running rails site!

---

### Post by pmasiar on 2008-04-08
> **jdonnell said:**
> I don't know about python,...You now have a running rails site!

Python is similar. But check announcement about [Google  App Engine](http://ubuntuforums.org/showthread.php?t=749285) - free Python+Django webhosting, no-hassle production hosting.

---

