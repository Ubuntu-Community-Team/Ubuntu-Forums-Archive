---
title: "Please help!!! Programming dilema"
date: 2007-08-20
forum: Programming Talk
---

### Post by CostaRica on 2007-08-20
Hi.  I switched from Windows (VS2005 and MS Access programming) to this wonderful world of Free Software.

I want to program an application to run in Ubuntu with MySQL.  I need to learn a programming language with an IDE that let's me develop with a GUI designer, among other things.

I am an optometrist who has been dreaming of moving to the open-source programming world, but first I need to program an application that helps me with my office so that I can develop more time.

I am not a professional programmer, but do have OO and SQL knowledge.

I started with Java and Eclipse, but I want to know which language is also the most Open-Source-Philosophy-Oriented from C++, Phyton, Perl, Ruby, Java, etc.

I know this post is getting long, but I need to express my feelings to someone.

When you analyse the Free Software & Open Source world you see clearly that the OS to go is GNU-Linux, that the database engine is basically good with either MySQL or Postgres (among others), that there are GREAT applications (OpenOffice, Scribus,Inkscape,etc) that are so easy to use, but when it comes to programming languages...you get so confused!!!  

Some questions:

- Is Java really Open-Source?
- Is C++ too tedious to program?
- Which programming language is better for my purpose (MySQL, GUI designer), something in that sense like VS2005? (please do not feel offended)
- C++, Java, Ruby, Perl, Phyton...???

I REALLY appreciate your comments!!!

---

### Post by Keith Hedger on 2007-08-20
I'd go for c/c++ and python together, c because it's compiled and therefore FAST and is probably most widely used (Please don't flame me!) and python (I personaly don't like the language) because a lot of plugins/config programs etc are written in it but it is quite slow (not so good at handling large numbers of data).
But the best answer is to look around and choose the language you like and that DOES THE JOB FOR YOU!

---

### Post by raijinsetsu on 2007-08-20
If you already have experience with Java, stick with it. It doesn't sound like you're going to need the performance of C or C++... Plus, Java programs you make should work on every platform.

---

### Post by LaRoza on 2007-08-20
> **CostaRica said:**
> 

I want to program an application to run in Ubuntu with MySQL.  I need to learn a programming language with an IDE that let's me develop with a GUI designer, among other things.

Some questions:

- Is Java really Open-Source?
- Is C++ too tedious to program?
- Which programming language is better for my purpose (MySQL, GUI designer), something in that sense like VS2005? (please do not feel offended)
- C++, Java, Ruby, Perl, Phyton...???

Python works well with MySQL and Ubuntu and is easy to learn. I would recommend that.

I don't know about the IDE and GUI designer, I use GEdit, Vim, or KWrite.

0. Java is not Open-Source, but is friendly 
1. For what you want, yes
2. Python
3. Maybe Perl, or Ruby, if you don't want Python

You might want to use SQLite if you don't need a database server.

---

### Post by CostaRica on 2007-08-20
> **raijinsetsu said:**
> If you already have experience with Java, stick with it..

What about the GUI Designer?  Which one do you recommend?

---

### Post by raijinsetsu on 2007-08-20
Well, Java doesn't really need a GUI designer... You just derive from already existing Frames, and then add buttons, etc.
You can get a very simple GUI in no time...
There are many commercial GUI builders for java out there. Just do a search for "java gui designer" or "open source java gui designer".

---

### Post by pmasiar on 2007-08-20
Python is fast enough, and simpler to develop in that most other choices. You definitely don't need hassle of C++.

Do you want to develop for desktop, or more modern browser-based apps?

---

### Post by CostaRica on 2007-08-20
> **raijinsetsu said:**
> Well, Java doesn't really need a GUI designer. .

Sometimes I feel like a weird guy because I ask about GUI designers.  When you go to the MS world (which I do not want to go back to, no matter what) a GUI designer is a must.  - Is that such a bad programming habit?

---

### Post by CostaRica on 2007-08-20
> **pmasiar said:**
> 
Do you want to develop for desktop, or more modern browser-based apps?

Thanks for bringing this up.  My application is for 4 stores that need to synchronize to a database server, but I prefer to have a local copy of the database in each store in case the internet doesn't work (welcome to the third world!).

The reason that I have not thought of a browser-based application is that I feel (probably incorrectly) that I loose control of the application.  For example, the user can run several browser windows at the same time, and I feel that the desktop applications have more power regarding the User Interface experience in general.

Am I talking like I am living in the 80's?

---

### Post by mikeodf on 2007-08-20
Just to add a voice to Costa Rica, the Optometrist. I am 59 years old and have needed to learn 20 computer languages in the past 35 years. most of them currently obsolete. What a waste. Wish i'd spent the time learning a beautiful language like french that still is used. Anyway I guess there is one lingua franca of programmers and that is C ( the native language of GNU-Linux etc). Most others have a lot in common with C so you can build on that.
Mike

---

### Post by pmasiar on 2007-08-20
4 servers working separately - is it a fall-back with reduced usability, or standard more, with synchronization of databases overnight?

Even running on local intranet, having web-based front-end is simpler: to update, you update just one server, not all client computers.

Don't worry about opening too many windows (although it **is** a valid concern): every windows has a session, and if user wants to submit something from long-forgotten window, you can check the session, and reject the operation).

Doing it in modern fashion makes your app future proof, gives you opportunity to learn modern technologies, and dip into more active communities.

Just take a look at Python and Turbogears, spend couple hours following the tutorials. You will be so jealous for new technology you will never think about doing it old way! The SQLObject/SQLAlchemy object-relational mappers are alone worth the efforts (you mostly don't need to write SQL for basic CRUD operations, until some really tricky query)

You are right that desktop has more control - we are wrestling that back from browser using AJAX. Of course it is still not complete desktop experience, but ease of deployment, scalability, and future-proofing pays for that.

---

### Post by CostaRica on 2007-08-20
Thanks a lot, pmasiar.  I will check that.

---

### Post by pmasiar on 2007-08-20
> **mikeodf said:**
> Most others have a lot in common with C so you can build on that.
Mike

You are not seriously suggesting to build the whole app in C, do you? Would you want him to fail so badly? Why write user-level app in C, when you can use higher-level language (even java, gosh!) and write/debug it faster?

The only speed which really matters in userland is **speed to market**, IMHO. If it is fast enough (response in 2 sec or less), speed increase does not matter. And with database app, most of time program waits for **database response**, and database response delay is the same for C or Python call. Writing it in C will increase overall speed only a little, we been there before, I hope I don't need to explain again why. :-)

---

### Post by shawnhcorey on 2007-08-20
> **CostaRica said:**
> I am not a professional programmer, but do have OO and SQL knowledge.

Do you having any acquaintances that are professional programmers?  Could you bribe them (try beer) into helping you set up an IDE?  BTW, don't let them touch your keyboard; it'll be faster if they do but you'll learn more if you do all the typing.

> Some questions:

- Is Java really Open-Source?

Yes, each year Sun promises to release Java as open source.

> - Is C++ too tedious to program?

Yes.

> - Which programming language is better for my purpose (MySQL, GUI designer), something in that sense like VS2005? (please do not feel offended)
- C++, Java, Ruby, Perl, Phyton...???

For GUI, use [Glade]("http://glade.gnome.org/").

For programming, use [Perl]("http://lists.cpan.org/showlist.cgi?name=beginners").

---

### Post by AlexThomson_NZ on 2007-08-20
> **pmasiar said:**
> You are not seriously suggesting to build the whole app in C, do you? Would you want him to fail so badly? Why write user-level app in C, when you can use higher-level language (even java, gosh!) and write/debug it faster?

Hey, I have been using C for GTK programming for all of about 2/3 months now, and I've reached the stage that (using Glade) for most apps I do now, the bottleneck is the GUI design rather than the code back-end.  I think scaring people off using C is a bit misguided- you do realize there are actually one or two user-level apps out there written in C right?  I know you are an evangelist for Python, but coding an app in C is not THAT unthinkable is it! ;)

> Writing it in C will increase overall speed only a little, we been there before, I hope I don't need to explain again why. :-)
No, you really don't.  I do agree here though, the difference in running speed will not likely be a major issue to consider...

---

### Post by pmasiar on 2007-08-20
> **shawnhcorey said:**
> For programming, use [Perl]("http://lists.cpan.org/showlist.cgi?name=beginners").

No, definitely not Perl. Even if Perl is not obsolete yet, it certainly is becoming obsolete. If you want modern "scripting" language, go for Ruby or Python (both comparable with Perl expresiveness, but cleaner). My personal preference is Python (with TurboGears web app framework), but ask your local guru.

Why perl is becoming obsolete? Perl 6, next generation, is years overdue, and overly complicated: see this [periodic table of operators](http://www.ozonehouse.com/mark/blog/code/PeriodicTable.html) and no, they are serious, it is **not** a joke. Trust someone who spend couple years creating Perl monster: **just say no!** I know what I am talking about. Don't try that at home, kids. :-)

---

### Post by pmasiar on 2007-08-20
> **AlexThomson_NZ said:**
> do you do realize there are actually one or two user-level apps out there written in C right?  I know you are an evangelist for Python, but coding an app in C is not THAT unthinkable is it! ;)

1) I do: even more than that, 2) yes I am, 3) of course it is not :-)

But why? Did you tried to use modern object-relational mapper in a dynamic language, which just creates all database CRUD for you like a magic?

---

### Post by AlexThomson_NZ on 2007-08-20
> **pmasiar said:**
>  But why? Did you tried to use modern object-relational mapper in a dynamic language, which just creates all database CRUD for you like a magic?

Yep, nice isn't it (I have done DB apps it in Perl and Ruby, although only Ruby for an 'enterprise' level app)

For this app, Python probably is a good choice, I misread your comment somewhat and got the impression you were implying C is impractical for ALL user-level apps, rather than this particular one

// My bad :)

---

### Post by shawnhcorey on 2007-08-20
> **pmasiar said:**
> No, definitely not Perl. Even if Perl is not obsolete yet, it certainly is becoming obsolete. If you want modern "scripting" language, go for Ruby or Python (both comparable with Perl expresiveness, but cleaner). My personal preference is Python (with TurboGears web app framework), but ask your local guru.

Your personal preference is Python because of your personal preferences.

Python is just as esoteric as Perl.  For example, in Python you say "0:n"; in Perl, "0..$n" but in English, "0,1,2,...,n"  Neither one of them is looks like the English language method.

What language do you want to learn: Perl, that is named after a semi-precious stone; or Python, that's named after a bunch of clowns?

Besides, Python can't do arithmetic:

```
$ python
Python 2.4.4c1 (#2, Oct 11 2006, 19:53:58) 
[GCC 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 1/2
0
>>> ^D

```

---

### Post by pmasiar on 2007-08-20
> **shawnhcorey said:**
> Your personal preference is Python because of your personal preferences.

Not so: I have first hand experience with rather average web based app in Perl (not to big, not too simple, not too smart programmers doing it), and compared with my other projects, I participated (and it was quite a lot), that one is quite a disaster: for couple of reasons, one of them was the selection of the language. I was in love with Perl at the time, and I fought vigorously against switching to Java, but now I think Java was better solution and would be easier to maintain than the mess we have now.

So it is not only preferences, it is also battlescars :-)

> Python is just as esoteric as Perl.  

Not so. There is big difference in community attitude. Perl community is proud of is famous for its "TIMTOWDI" - There is more than one way to do it. Python motto is "there should **one** **obvious** way to do it **right**". Python has nothing like [Perl golf, yearly obfuscation contest, and poetry competitions](http://en.wikipedia.org/wiki/Perl_golf#Perl_golf). Having one good way - less chances to do it wrong.

Looking at those Perl programs, who really **are** the clowns?

> What language do you want to learn: Perl, that is named after a semi-precious stone; 

Another concept you have 100% wrong: [pearl](http://en.wikipedia.org/wiki/Pearl) is organic by nature, it grows inside a mollusk, is closer to horns or claws than to stone. :-)

> Python, that's named after a bunch of clowns?

But **what** a clowns! You Don't like having fun? Obviously, you do not expect inquisition. But then, nobody does :-)

> Besides, Python can't do arithmetic:

This is one of bad decisions for which Guido apologized, but it is still kept in for backward compatibility but will be eliminated in Python 3.0, coming to PC near you in 2008 (which BTW cannot be said about Perl 6). Until then, use "1.0/2" and you will get correct result.

I have nothing against Perl hackers: I was lucke enought to be on one Perl conference, I enjoyed Damian Conway presentation (he is quite incredible: going for 2 hours, entertaining and fun talk about coding!), I enjoy reading "State of the Onion" and consider Larry extremely smart and deep person.

Perl was decent solution 8 years ago, before Python and Ruby (but fishy even back then - there were no popular Model-View-Controller frameworks back then!). Ruby on Rails started the revolution. 

I just don't think these days Perl is good language for big projects under weak management, based on my experience in it. Do **you** have experience in a non-trivial project in Python? And even if you do, it will not change my opinion about Perl one iota: Good for you it Perl works for you, but it did not worked for me, and I would feel obliged by professional ethic to warn anyone going into Perl projects about the inevitable problems. And as Perl gets less focus, and competitors grows stronger, it makes less sense to start new projects in Perl (unless you have strong Perl team - which is **not** the situation OP is in, IIUC.)

With very strong project manager, strong coding standards, constant code review, and excellent training of beginners by experts - maybe you can pull it through. Skip one of them, and get ready to face the mess. Been there, done that, so you won't scare me.

---

### Post by samjh on 2007-08-20
> **CostaRica said:**
> What about the GUI Designer?  Which one do you recommend?

Netbeans has the best free GUI designer so far.  There are commercial programs that do it too, but Netbeans is a very good free solution.

[www.netbeans.org](www.netbeans.org)

If you're already familiar with Java, I'd highly recommend you stick with it.  And yes, it is free and open source.  It is just not fully GPL'ed yet, but most parts (compiler, virtual machine, and majority of the standard API) are licensed under GPL.

---

### Post by CptPicard on 2007-08-20
If having a GUI designer is a requirement, you really need to consider Java and Netbeans. It has the best integrated GUI designer I have come across in Linuxland (but I may be biased, I am a Java guy).

That said, I do think that you really need to look at writing a web app. You'll be much more alone in with your project if you do it the desktop app way, it will be more difficult to do upgrades, as you'll have to distribute new versions, and a web interface is mostly good for anything you want to do, unless you are planning on coding your own weird widgets from scratch for the desktop app (which is going to be painful).

If you do go for a web app, forget Java and try something like TurboGears or Ruby on Rails. I am currently being totally disgusted at my attempts to integrate Hibernate+Spring+Wicket into producing reliable long transactions, and in order to get up to the Hello World stage, I've already written more infrastructure than will probably be of actual application code in the finished product.. :)

---

### Post by shawnhcorey on 2007-08-20
> **pmasiar said:**
> Not so: I have first hand experience with rather average web based app in Perl (not to big, not too simple, not too smart programmers doing it), and compared with my other projects, I participated (and it was quite a lot), that one is quite a disaster: for couple of reasons, one of them was the selection of the language. I was in love with Perl at the time, and I fought vigorously against switching to Java, but now I think Java was better solution and would be easier to maintain than the mess we have now.

So it is not only preferences, it is also battlescars :-)

And battlescars are not personal?

> > Python is just as esoteric as Perl.  

Not so. There is big difference in community attitude. Perl community is proud of is famous for its "TIMTOWDI" - There is more than one way to do it. Python motto is "there should **one** **obvious** way to do it **right**". Python has nothing like [Perl golf, yearly obfuscation contest, and poetry competitions](http://en.wikipedia.org/wiki/Perl_golf#Perl_golf). Having one good way - less chances to do it wrong.

What is a photon?  Is it a wave or a particle?  The answer is: it depends on how you look at it.  What is a "good" way depends on what you think is a good way.

> > What language do you want to learn: Perl, that is named after a semi-precious stone; 

Another concept you have 100% wrong: [pearl](http://en.wikipedia.org/wiki/Pearl) is organic by nature, it grows inside a mollusk, is closer to horns or claws than to stone. :-)

I didn't invent the nomenclature.  Pearls are called semi-precious stones; even if they are an oyster's concept of snot.

> > Python, that's named after a bunch of clowns?

But **what** a clowns! You Don't like having fun? Obviously, you do not expect inquisition. But then, nobody does :-)

Oh, "Perl golf, yearly obfuscation contest, and poetry competitions" are not fun.  Glad you cleared that up.

> > Besides, Python can't do arithmetic:

This is one of bad decisions for which Guido apologized, but it is still kept in for backward compatibility but will be eliminated in Python 3.0, coming to PC near you in 2008 (which BTW cannot be said about Perl 6). Until then, use "1.0/2" and you will get correct result.

Oh, I _have_ to excuse bad design decisions in Python but there is **no** excuse for bad design decisions in Perl.

> I have nothing against Perl hackers: I was lucke enought to be on one Perl conference, I enjoyed Damian Conway presentation (he is quite incredible: going for 2 hours, entertaining and fun talk about coding!), I enjoy reading "State of the Onion" and consider Larry extremely smart and deep person.

You have nothing against people who suffer under Perl.  You admire their fortitude and courage.  You just can stand those who like it.

> Perl was decent solution 8 years ago, before Python and Ruby (but fishy even back then - there were no popular Model-View-Controller frameworks back then!). Ruby on Rails started the revolution. 

There were no Model-View-Controller frameworks except in academic papers for the longest time.  But they were talked about since the introduction of structured programming.

> I just don't think these days Perl is good language for big projects under weak management, based on my experience in it.

No language is good under weak management.  Strong management knows about the weakness in a language and stresses it strengths.

> Do **you** have experience in a non-trivial project in Python? And even if you do, it will not change my opinion about Perl one iota: Good for you it Perl works for you, but it did not worked for me, and I would feel obliged by professional ethic to warn anyone going into Perl projects about the inevitable problems. And as Perl gets less focus, and competitors grows stronger, it makes less sense to start new projects in Perl (unless you have strong Perl team - which is **not** the situation OP is in, IIUC.)

Perl may not work for you.  But it's your personal choice.

> With very strong project manager, strong coding standards, constant code review, and excellent training of beginners by experts - maybe you can pull it through. Skip one of them, and get ready to face the mess. Been there, done that, so you won't scare me.

A strong project manager will always produces better code, regardless of language.

Coding standards are a crutch.  I have worked under MIL STD 2167 and ISO 9000.  All they did was generate paper.  They just made everyone think the code would work perfectly.

Constant Code Review means you failed to test.  Test is more important the code reviews.  The three best methods of successful code are: test, test, test.  (The ten best methods of successful code are: test, test, test, test, test, test, test, test, test, test.)

Excellent training is always desirable.  So isn't intimate understanding of programming and superior talent in logic.  But they are not always obtainable.

I never meant to scare you.  OK, you have had a bad experience with Perl and you never want to go there again.  And you think anyone who mentions Perl is J. Worthington Fowlfellow trying to lead everybody to Pleasure Island.

But that is your choice.  It's not the only choice.

---

### Post by pmasiar on 2007-08-20
I am glad that you let unopposed mention that Perl is becoming obsolete and Perl 6 may never happen. Hard to argue against that :-)

(/me runs for cover - I am not going to answer this discussion anymore - keep your Perl and be happy)

BTW I don't think OP was ever interested in doing it in Perl, so I am not sure why the commotion.

> **shawnhcorey said:**
> Oh, I _have_ to excuse bad design decisions in Python but there is **no** excuse for bad design decisions in Perl.


It is known bad decision, with known trivial workaround, which will be cleared up in known time. Perl 6 is in distant future, if ever, and it is **more** quirky, not less.

> You have nothing against people who suffer under Perl.  You admire their fortitude and courage.  You just can stand those who like it.

Either you or me are missing something in your paragraph - it does not make sense to me.

> There were no Model-View-Controller frameworks except in academic papers for the longest time.  But they were talked about since the introduction of structured programming.

[Smaltalk?](http://en.wikipedia.org/wiki/Smalltalk)  Public since 1980. 

> No language is good under weak management.  Strong management knows about the weakness in a language and stresses it strengths.

Some languages can survive under less than perfect conditions. Perl is not one of them.

BTW 1/3  of our "programmer" team was "wet lab" biologist with  little programming experience.

> Coding standards are a crutch.  I have worked under MIL STD 2167 and ISO 9000.  All they did was generate paper.  They just made everyone think the code would work perfectly.

Not **those** coding standards: like where to place braces, etc. How code looks like, so is more readable.

> OK, you have had a bad experience with Perl and you never want to go there again.  

Yup, that's right.

> And you think anyone who mentions Perl is J. Worthington Fowlfellow trying to lead everybody to Pleasure Island.

Not found in wikipedia, so it's wisdom lost on me :-)

I will warn anyone against Perl. If used, as we know Perl gives users enough rope to hang themselves, but we live in free country (or I wish for everyone to be so :-) ), do what you want with your projects.

---

### Post by shawnhcorey on 2007-08-20
> **pmasiar said:**
> I am glad that you let unopposed mention that Perl is becoming obsolete and Perl 6 may never happen. Hard to argue against that :-)

That's because the best ideas from Perl 6 have already been incorporated into Perl 5.  Perl is only becoming obsolete to those who don't like Perl.

> BTW I don't think OP was ever interested in doing it in Perl, so I am not sure why the commotion.

That's because nobody mentioned Perl to start with.

> It is known bad decision, with known trivial workaround, which will be cleared up in known time. Perl 6 is in distant future, if ever, and it is **more** quirky, not less.

No, the workaround is **not** trivial.  Every time you  do arithmetic, you have to decide if you're doing it as integers or as floats.  This is non-trivial.

> > You have nothing against people who suffer under Perl.  You admire their fortitude and courage.  You just can stand those who like it.

Either you or me are missing something in your paragraph - it does not make sense to me.

You have suffered.  You like people who have suffered.  You dislike people who say you have suffered in vain.

> > No language is good under weak management.  Strong management knows about the weakness in a language and stresses it strengths.

Some languages can survive under less than perfect conditions. Perl is not one of them.

BTW 1/3  of our "programmer" team was "wet lab" biologist with  little programming experience.

Meaning the project had little chance of success, regardless of language.  Why do you blame Perl and not management for this environment?

> > Coding standards are a crutch.  I have worked under MIL STD 2167 and ISO 9000.  All they did was generate paper.  They just made everyone think the code would work perfectly.

Not **those** coding standards: like where to place braces, etc. How code looks like, so is more readable.

And you think these coding standards did not dictate where to place braces or how much to indent?  They were far more exacting than that.

> > And you think anyone who mentions Perl is J. Worthington Fowlfellow trying to lead everybody to Pleasure Island.

Not found in wikipedia, so it's wisdom lost on me :-)

Try [http://www.bcdb.com/cartoon_synopsis/14-Pinocchio.html]("http://www.bcdb.com/cartoon_synopsis/14-Pinocchio.html")

> I will warn anyone against Perl. If used, as we know Perl gives users enough rope to hang themselves, but we live in free country (or I wish for everyone to be so :-) ), do what you want with your projects.

And I shall encourage everyone to use Perl.

BTW, every language gives users enough rope to hang themselves.  If you don't think Python does, then its a toy language.

---

### Post by CostaRica on 2007-08-21
I want to emphasize the great community we are (I am glad to say I am part of it now) because I admire:

- Your altruism in helping others.
- Your PASSION for coding.

I hope one day I will be as passionate about the language I finally chose.

Right now I am studying the Python-TurboGears-MySQL approach, even if I do not know what I will be finally using.

And (as someone was wondering), I indeed am alone doing this project.

Thanks for your advise! :)

---

