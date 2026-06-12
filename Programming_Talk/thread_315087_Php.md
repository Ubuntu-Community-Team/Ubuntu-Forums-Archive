---
title: "Php?"
date: 2006-12-08
forum: Programming Talk
---

### Post by haxer on 2006-12-08
Hello i wounder how to learn php the best way? the education style or the hard way?;) Which books are preferd? :-k

---

### Post by pmasiar on 2006-12-08
I am not PHP expert, I actively avoid PHP, everybody knows I promote python, but I happen to believe that learning non-hard way is always better :-) 

[O'Reilly]("http://www.oreilly.com/") books are *very* good, and cookbook-style books will help you get started quickly. O'Reilly has also [Intro to PHP ]("http://oreillylearning.com/courses/introphp/") course, where they will provide you with web server and personal tutor (for $400). 

For free: your local library might have some books about PHP, and  [wikipedia]("http://en.wikipedia.org/wiki/Php") gives you bunch of links (and also explains *why* I dislike PHP).

---

### Post by haxer on 2006-12-08
Ok but whats the different between php and python? Can I write an website in python?
:-k whats the best books about python?

---

### Post by pmasiar on 2006-12-08
PHP is for webpages only (and rather hard to maintain pages, too). Python is universal language, good for many things, also for websites, but also so many other things. Designed to be easy to learn, read, clean, but powerfull. Google and NASA uses it too. It is already installed on your Ubuntu computer. 

try [Instant Hacking]("http://www.hetland.org/python/instant-hacking.php") to get the feeling.

There are [many books]("http://wiki.python.org/moin/IntroductoryBooks") for python, for beginners or advanced programmers, something might be in your library, some are free online books.

Best book depends what are your computer background and goals. [pygame]("http://en.wikipedia.org/wiki/Pygame") might be good start - learn programming by programming games - with many games accesible in source code to learn from.

Websites are rather simple: programs starts, reads parameters, and outputs valid HTML page. For simple tasks, use CGI module (included in Ubuntu), more advanced: there are many popular web frameworks, like Django and TurboGears

---

### Post by coder_ on 2006-12-08
Ruby on Rails looks pretty easy to maintain and develop in (And from my experience so far, it is very much so).

Also, Rails code comes out beautiful compared to PHP in my experience and Rails code is very easy to read.

Maybe just try out a few of the languages/frameworks in question and see how you like each one and choose your favorite to learn further?

Here is a small list of frameworks and languages to give you ideas (In format of framework + language):
- TurboGears + Python
- Django + Python
- Ruby on Rails + Ruby
- CakePHP + PHP
If I recall correctly, all of those are based on the Model-View-Controller idea, which is neat and easy.

---

### Post by maddog39 on 2006-12-08
> **pmasiar said:**
> PHP is for webpages only (and rather hard to maintain pages, too). Python is universal language, good for many things, also for websites, but also so many other things. Designed to be easy to learn, read, clean, but powerfull. Google and NASA uses it too. It is already installed on your Ubuntu computer. 

try [Instant Hacking]("http://www.hetland.org/python/instant-hacking.php") to get the feeling.

There are [many books]("http://wiki.python.org/moin/IntroductoryBooks") for python, for beginners or advanced programmers, something might be in your library, some are free online books.

Best book depends what are your computer background and goals. [pygame]("http://en.wikipedia.org/wiki/Pygame") might be good start - learn programming by programming games - with many games accesible in source code to learn from.

Websites are rather simple: programs starts, reads parameters, and outputs valid HTML page. For simple tasks, use CGI module (included in Ubuntu), more advanced: there are many popular web frameworks, like Django and TurboGears

I believe you are sadly mistaken. PHP can do all the stuff python can do. For example:

[http://gtk.php.net/](http://gtk.php.net/)  - GTK+ Wrapper for PHP4 and 5
[http://www.php.net/manual/en/features.commandline.php](http://www.php.net/manual/en/features.commandline.php)  - Making CLI/CGI scripts in PHP

I have been programming PHP for 2 years now, actively. I've tried Python and really liked it for application development, however it's way too hard to use and setup for web development/web applications and still isnt widely supported in many webhosts. Also, your comment about how PHP can only make websites, is a common mis-conception by many people.

---

### Post by pmasiar on 2006-12-08
> **maddog39 said:**
> I believe you are sadly mistaken. PHP can do all the stuff python can do. For example:

I have been programming PHP for 2 years now, actively. I've tried Python and really liked it for application development, however it's way too hard to use and setup for web development/web applications

I might be slightly merrily mistaken about PHP - but you are *greatly mistaken* about python :-)

Python has libraries for almost anything! Does PHP have libraries for statistics? R (open-source standard for pro statistics) has RPy. Python runs on nokia phones. Using IronPython you can script .NET - the only scripting language Microsoft has (and under open-source license). And many more - I don't care about most.

I agree that 2 years ago, web application under python sucked. But after Google hired Guido (python's "father") and made him program a web application :-) situation is much different. Rails was wake-up call for python community (and Guido).

And we agree that pyhon is cleaner, more readable: unlike PHP, it forces newbie to write clean code. 

And I really appreciate this discussion. I understand that there are many languages (8K+ in total), optimized for many different tasks, and language you know is often easier to bend a little than learn new one. It needs to be fun.

---

### Post by haxer on 2006-12-08
Now im lost :) ill try out the links you guys gave me hope it will be learning for me i think it will or i did something wrong :P but python sound good hard but stabil if it works :) ;)

---

### Post by KoRnholio on 2006-12-08
The problem with Python for web development is finding a host that supports it.  Every webhost, even a bunch of Windows hosts, give you PHP now.

So before setting your sights on learning Python for web development, you have to do some research into hosts first, and god help you if you already paid for hosting, which doesn't support it.

Not saying that it's *hard* to find Python-supported hosting, but it's just not as universal as PHP.  Even a bunch of free hosts will give you PHP.

You're right that PHP *lets* you write bad code, but you can still write beautiful code in PHP.  Same idea with C++, and the arguments Java proponents use against it.

I agree that Python is uber-flexible, though.

---

### Post by bvanaerde on 2006-12-08
Some useful links for PHP:
[php.net]("http://php.net"): information about every function that exists in PHP, along with a lot of useful comments
[w3schools]("http://www.w3schools.com/php/default.asp"): a PHP tutorial

But the best thing to learn it, is to just try it out. If you've got a bit of knowledge on C or Java, you'll be up & running in no time.

---

### Post by Burgresso on 2006-12-08
This is my take:

If you want to learn to program, start with python.

If you want to create websites, learn PHP.

Of course, programming includes creating websites...

---

### Post by maddog39 on 2006-12-09
Currently I have a paid webhost called [ASmallOrange]("http://asmallorange.com/") and they cheaply and reliably offer PHP, Ruby + Rails, and Python via FastCGI. PHP5 is also availible and that runs in FastCGI as well. But only with mere luck did I strike this find. I own a small free psot2host and have beent trying to get python to work right with apache for ages. Was never successful. If python made it easier for hosts to intergrate it with their current setup, I think it would be much more largely adopted.

---

### Post by pmasiar on 2006-12-09
> The problem with Python for web development is finding a host that supports it.

To start learning CGI, don't waste time and money on complicated web frameworks on paid hosting. Python is "bateries included" language - it includes plain old CGI module. **All you need is cgi-enabled directory on your own box:** just install apache, use localhost, and couple months later, **when** you have something worth to show, you can host it somewhere.

Bonus tip: for CGI in python, always 'include cgitb' - your erros would have nice traceback as in command lime. Real lifesaver.

> You're right that PHP *lets* you write bad code, but you can still write beautiful code in PHP.

For a newbie with little experience or guidance, what would be better as *first language* to learn: one which readily allows creating messy, non-maintainable code, or the one which with little effort guides newbie to write code easy to read and maintain? I bet you read PHP coding standards only *after* you realized your code is a mess, *and* fought for weeks to clean it up, *and lost the battle*, right? 

Or did you really want me to believe you that you started PHP by reading "best practices in clean PHP code"? :-)

No flamewars please. I don't *hate* PHP or anything. I've seen nice programs done in it, with functionality I would like to have. But if a beginner asks me for my *professional opinion*: "Is PHP a good language to start learning CGI programming?" I have to say: No, (locally hosted) python with cgi, cgitb, sqlite and htmltmpl for simple templating is preferable. IMHO, of course, YMMV. :-)

> I agree that Python is uber-flexible, though.

Now that's something we can agree on! :-)

---

### Post by maddog39 on 2006-12-13
Well just a personal experience, I have found that CGI never works, I can't even manage to get a perl script to work using CGI::Carp using CGI, i've also tried python before using CGI, same problem. Take into consideration that this spans across many hosts and no support desk has been able to sort the problem. PHP just works, upload it and it works.

You could always make beautiful code like this in PHP. This is my code too, just and FYI.

[http://madbb.svn.sourceforge.net/viewvc/madbb/trunk/includes/class_database.php?revision=31&view=markup](http://madbb.svn.sourceforge.net/viewvc/madbb/trunk/includes/class_database.php?revision=31&view=markup)

An example of code you could and should model after and I believe  this is some of the neatest PHP source out there.

---

### Post by ifokkema on 2006-12-19
> **pmasiar said:**
> For a newbie with little experience or guidance, what would be better as *first language* to learn: one which readily allows creating messy, non-maintainable code, or the one which with little effort guides newbie to write code easy to read and maintain?
The second option seems best. **However**, while not even using Python I had to explain someone who was fighting a couple lines of code for hours **not** to use tabs and spaces for indentation. Don't see it, but just doesn't work.
I do like the flexibility PHP gives you if you come from C(++), Java, etc. You can take your own coding style with you.

> **pmasiar said:**
> I bet you read PHP coding standards only *after* you realized your code is a mess, *and* fought for weeks to clean it up, *and lost the battle*, right?
Yes / Not so much / Hell no :)

---

### Post by pmasiar on 2006-12-19
> **ifokkema said:**
> I had to explain someone who was fighting a couple lines of code for hours **not** to use tabs and spaces for indentation. 

It would not happen if s/he used IDLE, default python IDE. It is **bad** to go against defaults - defaults are there for a reason. If you go around, do your homework and be prepared to handle problems. Same as in any other program.

> I do like the flexibility PHP gives you if you come from C(++), Java, etc. You can take your own coding style with you.

I understand this position - whitespace rigidness was my reason why I rejected python when i seen it first time. As a result, I wasted 3 years learning perl :-(

One of important python goals is code readability. To be able to read someone else's code, the code needs be aligned in the way you are used to, right? At least me, when making non-trivial change in someone else's code, first thing will realign it.

Python solves issue of proper alignment in the radical way: alignment is syntax, everyone has same alignment. So you can read everybody's code, goal (readability) is much closer now.

Hey, I have no problem everybody uses his favorite language. But if a beginner asks me (explicitly or implicitly) what would be best first language to learn, or best language to do (almost any) task X, I am professionaly bound by Ubuntu honor code to give him or her my honest best advice. Which would be, of course, to use python. :-P

---

### Post by maddog39 on 2006-12-19
> One of important python goals is code readability. To be able to read someone else's code, the code needs be aligned in the way you are used to, right? At least me, when making non-trivial change in someone else's code, first thing will realign it.
Yeah, well that's one of the problems with PHP. Whenever I have to work with someone whom uses the 'sloppy' coding style:
[PHP]
if ($var)
{
     if ($var2)
     {
          $var2 = "some code here";
          echo $var2."\n";
     }
}
[/PHP]
When I use the 'neat' coding style:
[PHP]
if ($var) {
     if ($var2) {
          $var2 = "some code here";
          echo $var2."\n";
     }
}
[/PHP]
I have a really hard time reading others' code. Although something else that just came to mind, PHP has equivalents to all standard C functions and you can probably take C code from almost any command line application, change the syntax, combine header files and the such, and it will work in PHP. So I guess it just depends really.

---

### Post by Mirrorball on 2006-12-19
Python is my favorite language by far and I think it's a lot better than PHP for anything but web development. I really wanted to use Python for web development, but I changed my mind after reading how to set up a Django application.  On the other hand, any cheap host has PHP, installing it yourself is easy and running a script is ridiculous. Python is pure beauty but PHP5 isn't bad either. It has a C-like syntax, but weakly typed and with Java-like OO features.

---

### Post by pmasiar on 2006-12-20
> **Mirrorball said:**
> I really wanted to use Python for web development, but I changed my mind after reading how to set up a Django application. .

I used python with no stinky frameworks: plain old CGI, in cgi-enabled directory, with cgitb to help in debugging and htmltmpl for templating - cannot get any simpler than that. It might not survive a slashdot attack, but it was just fine for our research - and so simple to set up and use - especially compared with java/tomcat/struts nightmare [what is am trying to set up now]("http://ubuntuforums.org/showthread.php?t=321885"). Java experts, please help!

---

### Post by Mirrorball on 2006-12-20
Frameworks are great and Django is one of the best, at least until you read things like "When deploying Django sites on mod_python, you'll need to restart Apache each time you make changes to your Python code." So it's Zend Framework for me. It works well on my cheap shared server account.

---

### Post by ifokkema on 2006-12-20
> **pmasiar said:**
> It would not happen if s/he used IDLE, default python IDE. It is **bad** to go against defaults - defaults are there for a reason. If you go around, do your homework and be prepared to handle problems. Same as in any other program.
What?
1) To go against defaults is bad?!!?? You don't like having your own preference? You never touch any setting whatsoever?
If it's default, it can change. Otherwise, it's a set feature. So if it can change, apparently it means enough people prefer not to use the default. It's what makes us Human. Our choices. Why the heck are there that many programming languages and not one default one?
2) If everybody went around doing their homework, we wouldn't have any sloppy PHP code generators (uhm... programmers) out there :)

Not here to create a flame war - using IDLE could've helped him, but other prefer using one IDE for all languages they program in :)

---

### Post by ifokkema on 2006-12-20
> **maddog39 said:**
> Yeah, well that's one of the problems with PHP. Whenever I have to work with someone whom uses the 'sloppy' coding style:
...
I have a really hard time reading others' code.
Neither of these coding examples are sloppy. They use different bracing styles, that's all. These styles have their own names and fan bases, and are used and followed strictly in various coding style rules for that matter ;)

This is sloppy coding:
[PHP]
if ($var){if ($var2)
{$var2 = "some code here";
echo $var2."\n";}}[/PHP]
Ok, I think I went a little overboard there. That was **VERY** sloppy ;)

---

### Post by pmasiar on 2006-12-20
> **ifokkema said:**
> What?
1) To go against defaults is bad?!!?? You don't like having your own preference? You never touch any setting whatsoever?
If it's default, it can change. Otherwise, it's a set feature. So if it can change, apparently it means enough people prefer not to use the default. It's what makes us Human. Our choices. Why the heck are there that many programming languages and not one default one?

OK I went little overboard. It is not default - it is **recommended** way to do things. **Python is unusual - whitespace is significant**. If you want your freeform indentation, python is **not** language for you. If irrelevant freedom (to indent any way you choose) is more important than code readability, fine with me. I prefer to use same indentation that everybody else is using, so I can read their code and they can read mine. Readability is important to me. 

I understand that code readability is very strange concept for PHP programmers - lots of PHP code looks like authors never thought about readability. You may possibly belong to this PHP category too :-P

Python's motto is: **there should be one obvious way to do it right**. Freedom to do things in different wrong ways is false freedom, IMHO. Yes, heresy: in python, there is **one true way** to indent the code. It is restricted by syntax. You can use freeform editor (which mixes spaces and tabs) to edit python code on your own risk. 

Default (or recommended) way is: (1) use one of several IDE (one comes installed with every python - IDLE), or (2) set editor to replace TABs with SPACEs. If not, there is  (3): face consequences. 

I like my preferences, but I also have priorities. Different ways to indent is not between them.
 
> 
2) If everybody went around doing their homework, we wouldn't have any sloppy PHP code generators (uhm... programmers) out there :)


Python tries hard to help people do right think without much homework. Like indent code properly :-)

> Not here to create a flame war - using IDLE could've helped him, but other prefer using one IDE for all languages they program in :)

You can use any IDE with python if you set it properly handle whitespace.

Yes, if you ... spit ... against the wind, you get messy. Blame the wind? Programming is hard. One of the reasons is, code is so flexible. So people think they **have** to twist it in every possible way, because they **can.** Surprise, your decisions have consequnces.

**Let's step back, how we got here?**

Original poster asked how to learn PHP - language used mostly for web-based apps. I suggested different language (python) also used for web app. I strongly believe that python is easier than PHP. IIUC, ifokkema thinks that being able to freely mix spaces with tabs when doing intendation is important feature of the language. Python lacks this feature, I concede. Let us disagree on priorities and kill this thread. I have only one condition: don't make me read your code :-P

---

### Post by maddog39 on 2006-12-20
> I understand that code readability is very strange concept for PHP programmers - lots of PHP code looks like authors never thought about readability. You may possibly belong to this PHP category too
Uhh.. hellooo, thats why I find PHP frustrating, because I am a code neat freak and my code has to be 'perfect' so to speak and I never want to work with anyone on a project because they will mess up my readability standards lool.

---

### Post by ifokkema on 2006-12-22
> **pmasiar said:**
> If irrelevant freedom (to indent any way you choose) is more important than code readability, fine with me.
I sense judgement here... :P

That was not my point... I just brought up a downside of the forced indentation.

> **pmasiar said:**
> I understand that code readability is very strange concept for PHP programmers - lots of PHP code looks like authors never thought about readability.
Hmm.... I'd say this only goes for new programmers in any C-style languages, and only if they have no theoretical background in programming, and if they find sloppy code examples. Like.. uhm... me, when I started a couple of years ago :) My code is quite readable now if I may say so.

> **pmasiar said:**
> IIUC, ifokkema thinks that being able to freely mix spaces with tabs when doing intendation is important feature of the language.
Hell no! Like I said; the guy I mentioned got into trouble because he used a standard IDE that he used for other languages as well, he imported code from someone else (or maybe switched computers, I don't know) and the code got stuffed with both tabs and spaces. It looked fine on screen, but did not run. That's all.

I myself prefer proper indentation for PHP and other C-style languages. I don't expect other programmers to do it exactly my way (outside of my project, that is). As long as they are consequent with their indentation, so you can follow the code :)

---

### Post by mr_niceguy on 2007-02-03
> **haxer said:**
> Which books are preferd? :-k

Hello haxer, I realize this is an old post but if you are still thinking about this, I know a lot of people find ["PHP for the World Wide Web"](http://www.amazon.com/World-Second-Visual-QuickStart-Guide/dp/0321245652/sr=8-3/qid=1170542706/ref=pd_bbs_sr_3/105-3868594-1431634?ie=UTF8&s=books) to be a helpful book. I once bought the same author's PHP and MySQL book and quite enjoyed its clarity.

As others have noted, PHP remains a great fit for small projects where you have a couple pages of dynamic content but larger projects are better served with a well implemented framework such as [Ruby on Rails](http://rubyonrails.org). I have also used PHP frameworks with a reasonable degree of success (e.g. [Code Igniter](http://codeigniter.com), [Zend Framework](http://framework.zend.com/)) but none of them have the full feature set of Rails. Also, after taking the time to probe the source code on a number of the more popular PHP frameworks I can tell you that Code Igniter and Zend Framework are just about the only ones I can recommend.

Not surprisingly Python has some good frameworks too. (e.g. [Django](http://djangoproject.com), [TurboGears](http://turbogears)) Again, Python is a better platform for an object oriented framework than PHP. That being said I would still recommend Ruby on Rails to a beginner since it has greater mindshare and is even easier to learn and use.

---

### Post by supirman on 2007-02-03
> **maddog39 said:**
> Yeah, well that's one of the problems with PHP. Whenever I have to work with someone whom uses the 'sloppy' coding style:
[PHP]
if ($var)
{
     if ($var2)
     {
          $var2 = "some code here";
          echo $var2."\n";
     }
}
[/PHP]
When I use the 'neat' coding style:
[PHP]
if ($var) {
     if ($var2) {
          $var2 = "some code here";
          echo $var2."\n";
     }
}
[/PHP]
.

How is the first 'sloppy', and the second 'neat'?  I find the second harder to read, especially in larger files.   Extra spacing can certainly make code easier to read, hence putting the opening brace on a new line is much more aesthetically pleasing to me.  Not to mention it's the defined coding style of the company where I work...

---

### Post by lnostdal on 2007-02-03
(edit: uhm .. i haven't really read any of the previous posts by the way .. flat forums seem impossible to navigate in)

note that the only thing that adds visual structure in the end is indentation .. 

you can go from this:

```

void someFunction()
{
  if(1)
    {
      a();
      b();
      c();
    }
  else
    {
      d();
      e();
      f();
    }
}

```

..to this..

```

void someFunction()
{
  if(1) {
    a();
    b();
    c();
  }
  else {
    d();
    e();
    f();
  }
}

```

..to this..

```

void someFunction(){
  if(1){
    a();
    b();
    c();}
  else{
    d();
    e();
    f();}}

```

..and even..

```

void someFunction()
  if(1)
    a();
    b();
    c();
  else
    d();
    e();
    f();

```

..and instantly know that a, b, c belongs in the then-part and d, e, f belongs in the else-part - in all the examles ..  your eyes do not look for syntax, only indentation when looking for structure and meaning at this level

think the matrix: [http://www.gigamonkeys.com/book/they-called-it-lisp-for-a-reason-list-processing.html#there-is-no-list](http://www.gigamonkeys.com/book/they-called-it-lisp-for-a-reason-list-processing.html#there-is-no-list) (no spoon, no syntax, no parenthesizes -- only pure structure) 

this is why xml is so mind-numbingly stupid by the way; no one cares about the closing element .. hm - well, maybe the PHBs do .. it only adds verbosity:

```

<person>
  <name>lars</name>
  <age>26</age>
</person>

```

..would in any sane parallel universe have been replaced with:

```

(person
  (name lars)
  (age 26))

```

..because you see instantly that name and age "belongs to" the person by ways of indentation..    

i challenge any person here to read any significantly sized xml-structure with no newlines and no indentation in it; it is impossible without indentation anyways so why bother with the extra end-tags in the first place?

---

