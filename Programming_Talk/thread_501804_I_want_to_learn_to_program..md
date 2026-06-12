---
title: "I want to learn to program."
date: 2007-07-15
forum: Programming Talk
---

### Post by Jordan777 on 2007-07-15
I love video games and computers and I I'm pretty sure that's where I want to take my life.  I really want to try something like programming video games.  Also I think programming for the open source scene could be pretty cool too.  Can anyone recommend what programming language I should start with and how to best go about learning it?  I just really think I want to program or work with animations in the game industry.  Who knows things change right?:wink:  But or sure i want to learn how to code.

---

### Post by AlexenderReez on 2007-07-15
gaming..?i suggest python....search in google python tutorial.....

---

### Post by Paul820 on 2007-07-15
LOL, i can see this thread turning into a few pages. Seriously, have a look at a few languages and see what one you feel comfortable with. You will get many suggestions on trying python, it's easy, i have had a look at it and i am going to spend more time with it in the future. At the moment, i use C++. No one can really answer your question, it's up to you to decide. Get some recommendations for languages off some of the guys on here and have a look at them. Then decide. Hope you find what you are looking for. Good luck. :)

---

### Post by Jordan777 on 2007-07-15
There aren't languages like for certain tasks you want to complete?:confused:

---

### Post by Paul820 on 2007-07-15
If you want to start game programming and you have never programmed before you need to start at the beginning, learning the syntax etc. Diving head first into openGL or SDL or any other graphics library will put you against a brick wall very quickly. Take what reez0105 suggested and have a look at python first. You can make games in python aswell. Languages can do all sorts of different tasks, it's just some are designed to complete those task better and quicker than others.

---

### Post by Tomosaur on 2007-07-15
> **Jordan777 said:**
> There aren't languages like for certain tasks you want to complete?:confused:

Yes, but most of the popular ones will do pretty much anything you'd need to do. Python is generally recommended for beginners, since it eliminates much of the messy syntax of other languags. Don't take this to mean Python is 'watered down', it's pretty damn powerful.

---

### Post by samjh on 2007-07-15
> **Jordan777 said:**
> I love video games and computers and I I'm pretty sure that's where I want to take my life.  I really want to try something like programming video games.  Also I think programming for the open source scene could be pretty cool too.  Can anyone recommend what programming language I should start with and how to best go about learning it?  I just really think I want to program or work with animations in the game industry.  Who knows things change right?:wink:  But or sure i want to learn how to code.

If you want to make a career out of programming video games, you should aim to master C++.  It is the #1 language for video games at the moment, and for the foreseeable future too.

Furthermore, learning C++ early is a good thing.  It is a complex and powerful language that take at least a couple of years to get good at.  But as I said, it is complex and powerful, so the learning curve will be steep, but you will probably become a more well-rounded programmer than if you learn other languages.

To learn C++, start by installing the compiler and related tools:
```
sudo apt-get install build-essential
```

Then use one of the following books:
[Acclerated C++](http://www.amazon.com/Accelerated-C-Practical-Programming-Example/dp/020170353X)  (cheap price; starts from the abstract stuff and works towards details)
[How to Think Like a Computer Scientist - C++ version](http://greenteapress.com/thinkcpp/) (free download; covers basic programming concepts using C++)
[Teach Yourself C++ in 21 days](http://newdata.box.sk/bx/c/) (free online book; teaches C++ from details to more abstract stuff - opposite approach to the Accelerated C++ book)

This on-line reference will be useful for looking up C and C++ library functions and keywords:
[http://www.cppreference.com/](http://www.cppreference.com/)

How to use the GCC C++ compiler (ie. g++):
[http://www.cprogramming.com/g++.html](http://www.cprogramming.com/g++.html)

How to use Make and Makefiles (not needed until later on your learning):
[http://en.wikipedia.org/wiki/Makefile](http://en.wikipedia.org/wiki/Makefile)

Then after you have mastered the basics of C++, you can then acquire one of many programming books and other resources related to game development.  Linux has a lot of cross-platform libraries for game development, including SDL, OpenGL, OpenAL, Allegro, ClanLib, etc.

Good luck. :)

---

### Post by Jordan777 on 2007-07-15
So it looks like Python and C++ (probably python first haha).  I heard Ruby might be better to start on than Python.  Any truth to that?

---

### Post by pmasiar on 2007-07-15
> **Jordan777 said:**
> So it looks like Python and C++ (probably python first haha).  I heard Ruby might be better to start on than Python.  Any truth to that?

1) games: python has excellent game library: pygame. Even commercial games were made in it: galcon

2) C++ as "the only true way": There is no such a thing as "the only true way" in programming :-) It depends what you want. Ie for online game network delay will be bigger that difference in speed between C++ and Python. And with Python, you always can recode some deep bottleneck in C. So python first is good idea.

3) Ruby: Ruby was first in niche of "rapid app development" (Rails) and is scarcely used outside it. Compared to that, Python is widely used outside of web apps, for any scripting tasks, even scientific calculation - and with RPy, all power of R is accessible from Python. Python is older than Ruby, has more libraries (which might be important for games) and bas bigger community and big companies support (ie. Google and Ubuntu/Canonical use Python for internal development)

Ruby is rather popular with former Java enthusiasts, and they are rather easy prey to hype :-)

---

### Post by ButteBlues on 2007-07-15
> **pmasiar said:**
> 3) Ruby: Ruby was first in niche of "rapid app development" (Rails) and is scarcely used outside it. Compared to that, Python is widely used outside of web apps, for any scripting tasks, even scientific calculation - and with RPy, all power of R is accessible from Python. Python is older than Ruby, has more libraries (which might be important for games) and bas bigger community and big companies support (ie. Google and Ubuntu/Canonical use Python for internal development)

Ruby is rather popular with former Java enthusiasts, and they are rather easy prey to hype :-)

Considering Ruby is beginning to outpace Python, and even coming up on Perl in terms of number of programmers, I think your statements are for the most part uninformed and/or outdated.

Ruby's expanding rapidly - and while it doesn't yet have the vast number of libraries that Python does, it has all the major ones and is adding more daily - so much so, that the number of Rubyists is expected to grow by **50%** this year alone, as developers are leaving Python and Perl for it. In a few users, Ruby *will*, undoubtedly, be _the_ scripting language to use.

Combined with the fact that Rails is an absolutely phenomenal web development platform, it's only a matter of time.

---

### Post by Wybiral on 2007-07-16
C! C! C!

C... with SDL... and OpenGL.

But, you need to tell us what kind of games...

Text adventures... 2d... 3d... Graphically intense 3d... ?

This will make a difference.

---

### Post by pmasiar on 2007-07-16
> **ButteBlues said:**
> Considering Ruby is beginning to outpace Python, and even coming up on Perl in terms of number of programmers, I think your statements are for the most part uninformed and/or outdated.

not so - only biased for Python, exactly as yours is biased for Ruby :-)

> Ruby's expanding rapidly - ... number of Rubyists is expected to grow by **50%** this year alone,

It is easy to get 50% growth from low starting  base :-) . Python is more widely used, so 50% gain is hard if not impossible.

> Combined with the fact that Rails is an absolutely phenomenal web development platform, it's only a matter of time

Just FYI, Python has 3 web frameworks comparable to Rails (each optimized for different area): Django, TurboGears, and Pylons. 3 ORMs. So IMHO creativity is bigger in Python niche.

All this are my opinion against yours, only time will tell. OP can look at both languages and decide for herself.

and you did not disputed my claim that Ruby is used almost exclusively for Rails, so it stands :-)

---

### Post by Note360 on 2007-07-16
Oh god I forgot how fast these Ruby vs Python flame wars start. I remeber a time when Rubyists and Pythonists use to agree that their language was better than Perl. Now that time is gone *weeps*.

I am a Rubyist myself (finding myself at home in the weird subculture that lies underneath the hype (the origional rubyists and the non rails ones)). However, I dont think ruby has anything like PyGame which is nice and a bonus for python if you want to do game programming (I cant believe you people didnt mention this). Also C and C++ are used a lot in game programming (and I believe C# is coming into common use on the Windows side of things and Obj C for OS X). I am kinda hating on C++ at the moment so I am going to say go with (even though the lack of strings will piss you off at first, but if you dont know what strings are yet youll be fine.)

---

### Post by Paul820 on 2007-07-16
That's why i said i could see this turning into a several page thread. Everyone has their own idea on what others should learn first. :)

---

### Post by Note360 on 2007-07-16
> **Paul820 said:**
> That's why i said i could see this turning into a several page thread. Everyone has their own idea on what others should learn first. :)

Oh and message to the guy who made this thread. PLEEEEEEEEAAAAASE dont ask about what editor to use. That flame war is an age old fued my friend. most people here are vimmers however, those threads go to hell any way.

So basically I think you should pick a language after some research (I suggest python for you since it has teh tools for your task and they are simpleish, but remember one day you will have to learn C and C++ (two completely different languages btw)).

---

### Post by ankursethi on 2007-07-16
Game development == C++. Whatever anybody else says. Commercial games are mostly C++. Games have been made in Python, but that does not mean Python is best for game programming. It's a scripting language, and the "code the slower parts in C" argument falls to pieces when it comes to the complexity of computer games.

PS : I'm a Python guy myself, but I know the right too for the right job.

---

### Post by 7Priest7 on 2007-07-16
The first Programming Language I learned was Visual Basic...

Visual Basic is easy but propriatary

That means if you want to learn it first you could shell out some cash
or get [Envelop]("http://www.freebyte.com/programming/compilers/envelop.html")
Envelop is old and outdated
But It is still pretty easy

Visual Basic is pretty limited as far as games go but it is a fun first language (or was for me)

Visual Basic may be worth a try

Alex

---

### Post by cwaldbieser on 2007-07-16
> **Jordan777 said:**
> I love video games and computers and I I'm pretty sure that's where I want to take my life.  I really want to try something like programming video games.  Also I think programming for the open source scene could be pretty cool too.  Can anyone recommend what programming language I should start with and how to best go about learning it?  I just really think I want to program or work with animations in the game industry.  Who knows things change right?:wink:  But or sure i want to learn how to code.

What kind of games do you want to make?  If there are similar open-source games, you might look at the source to see what kind of language tools were used to make those games.  Try writing to game developers and get opinions from them.

---

### Post by Note360 on 2007-07-16
DO NOT LEARN VISUAL BASIC. Most people here have had a horrible time with it including me.

---

### Post by 7Priest7 on 2007-07-16
That is probably because Visual Basic is a windows specific thing...
You were probably trying to work it on Linux

Alex

---

### Post by djhworld on 2007-07-16
If you want to break into the games industry, C++ is your friend.

Any other language and you'll be laughed out of the boardroom.

Seriously.

EDIT: Java for mobile phone games though.....

---

### Post by pmasiar on 2007-07-16
> **Jordan777 said:**
>  I really want to try something like programming video games. 

I personally know guy who wanted just that, succeeded, and run away screaming. And read many stories about how games industry is the hardest on developers, pays less, and more stress that elsewhere (60 hrs a week is normal). Because of course there is permanent stream of newbies who think it is good idea and are willing to work for peanuts just ot get in and hoping it will be fun. So be warned, and do your research before jumping into gaming industry. It squeezes you like a lemon and throws you out.

> Also I think programming for the open source scene could be pretty cool too. 

This is better idea - doing it for fun.
There are many free software games, and engines to create games, like WorldForge.

> Can anyone recommend what programming language I should start with and how to best go about learning it?  

learn programming first, *then* think about learning cool graphics tools.

>  But for sure i want to learn how to code.

This is good goal. Start with Python (see my sig for links).

BTW there *are* games written in Python beyond pygame: [http://www.eve-online.com/](http://www.eve-online.com/) and [galcon](http://www.imitationpickles.org/galcon/index.html) are *commercial* games from top of my head, there are more, many free. Of course, many (but not all) commercial games are written in C/C++, you can go there later if you want to.

---

### Post by ButteBlues on 2007-07-16
> **pmasiar said:**
> not so - only biased for Python, exactly as yours is biased for Ruby :-)

Mine's based on numbers cited in a report. How about yours?

> > Ruby's expanding rapidly - ... number of Rubyists is expected to grow by **50%** this year alone,

It is easy to get 50% growth from low starting  base :-) . Python is more widely used, so 50% gain is hard if not impossible.

If Ruby had as "low [a] starting base" as you imply, then Ruby wouldn't be currently predicted to surpass Python in popularity within the next 2-3 years.

Or better yet, if Ruby were such a fringe language, how do you explain Mac OSX Leopard shipping Ruby and Rails (including Capistrano) and RubyGems by default?

> > Combined with the fact that Rails is an absolutely phenomenal web development platform, it's only a matter of time

Just FYI, Python has 3 web frameworks comparable to Rails (each optimized for different area): Django, TurboGears, and Pylons. 3 ORMs. So IMHO creativity is bigger in Python niche.

No offence, but none of those frameworks hold a dime to Rails for reasons cited far more times elsewhere than I can count.

> All this are my opinion against yours, only time will tell. OP can look at both languages and decide for herself.

The OP wouldn't want to learn either since they're interested in games. I only commented to correct your err and misinformation about Ruby.

> and you did not disputed my claim that Ruby is used almost exclusively for Rails, so it stands :-)

Ruby and Rails are simply two peas in a pod. Yes - right now Ruby is more popularly used with Rails than for stand-alone GTK/QT applications. Rails is a strong platform - why shouldn't it be expected that the number of Rubyists would predominantly use it? However, Ruby is also expanding elsewhere beyond simply Rails, and has been for a while.

---

### Post by Jordan777 on 2007-07-16
I'm still reading through all the posts haha.  Sorry I didnt get back to this sooner.  Um well ultimately i want to end up on graphically intense 3D games as I saw in one post here but 2D games such as Ragnarok and Gunbound are always great too.  Really I just want to get into programming to see if i even have what it takes.  I'm always sitting in front of the computer anyways so why not put my time to some creative use.  So so far it looks like start on Python or Ruby (still debating but it looks like Ruby's winning) and move to C/C++?

*Edit* 
I worked through all that.  It seems just from the two posters going at it haha that Ruby might be the better starting program... thingy.  Also someone said i should want to do this for fun.  Of course it would be for fun haha.  I have seen what is possible just using programming and paint and I have to say it was pretty darn cool.  I thought it looked really fun if not absolutely insane.  So the question still stands Python or Ruby then move onto C and C++. Oh and someone said I was a girl I'm a dude haha.  I'll drop by in a few hours because I need to do some homework for a while.

---

### Post by Jeremywilms on 2007-07-16
You cant become a programmer because you love games. You have to relize that it s work ro learn to programm. And just because you love games, does not mean you will love programming. Firt of all do you want to programm with.
Website
-HTML(Do not do this language!")
-php(Getting old)
-ruby
-python(For some games and Apps too)

Application, game developing
-VB6.0 & VB.net(You would never make games with this. this is for noob programmers & fast App Building)
-Python(More for Apps, you would'nt make a game with it.)
-C++ (Good for anything but webApps)
-Java (Good for online games, Apps. and Desktop Apps)
-C(Fast)

Those are just some popular levels.If you want to learn with a book, assure you have a good reading level. Or take classes.
You should learn java then C++. Java and C++ have similer syntax. Most people say C++ is easier then C, but they are the same thing basicly



> **djhworld said:**
> If you want to break into the games industry, C++ is your friend.

Any other language and you'll be laughed out of the boardroom.

Seriously.

EDIT: Java for mobile phone games though.....

No not at all.Java is used for way more then mobile phone games. Learning java will not make you a laughing stock. Seeing as you can learn C++ in a couple of days. Java is cross Platform. meaning it can be used on almost every OS. and is used for building many many popular games. It is also a vary flexible language, and open source, any functions that are not there you can make.

---

### Post by Note360 on 2007-07-16
> **Jordan777 said:**
> I'm still reading through all the posts haha.  Sorry I didnt get back to this sooner.  Um well ultimately i want to end up on graphically intense 3D games as I saw in one post here but 2D games such as Ragnarok and Gunbound are always great too.  Really I just want to get into programming to see if i even have what it takes.  I'm always sitting in front of the computer anyways so why not put my time to some creative use.  So so far it looks like start on Python or Ruby (still debating but it looks like Ruby's winning) and move to C/C++?

*Edit* 
I worked through all that.  It seems just from the two posters going at it haha that Ruby might be the better starting program... thingy.  Also someone said i should want to do this for fun.  Of course it would be for fun haha.  I have seen what is possible just using programming and paint and I have to say it was pretty darn cool.  I thought it looked really fun if not absolutely insane.  So the question still stands Python or Ruby then move onto C and C++. Oh and someone said I was a girl I'm a dude haha.  I'll drop by in a few hours because I need to do some homework for a while.

Ok. Ruby is nice and I love it, but if you really want to develop at this forumI would learn Python. Also truth be told if you want to learn C just learn C. It will take a while to wrap your head around it though.

---

### Post by pmasiar on 2007-07-16
> **ButteBlues said:**
> Mine's based on numbers cited in a report. How about yours?

I did not found any link in your post. But regardless, anyone can fake statistics. [TIOBE index](http://www.tiobe.com/tpci.htm), even as it is hopelessly biased to book sale numbers, still shows Python 50% ahead of Ruby (and because of many free online Python books, there is no need to buy paper books, hence the bias).

> If Ruby had as "low [a] starting base" as you imply, then Ruby wouldn't be currently predicted to surpass Python in popularity within the next 2-3 years.

Well, let's see in 3 years. I am not switching :-)

> Or better yet, if Ruby were such a fringe language, how do you explain Mac OSX Leopard shipping Ruby and Rails (including Capistrano) and RubyGems by default?

All linux distros have Python by default. OLPC picked Python as main implementation language (and not C or Ruby). Main language in Ubuntu, Google, Etc etc.

> No offence, but none of those frameworks hold a dime to Rails for reasons cited far more times elsewhere than I can count.

No offense, but you have no idea what are you talking about, but again - it is not important. 3 years from now, as you said. I admit that Ruby was first in niche of rapid web app development - it was Python's weak spot until 2005, but not any more.

> The OP wouldn't want to learn either since they're interested in games. I only commented to correct your err and misinformation about Ruby.

Well, he can easily program even commercial games in python as i mentioned before. This is exactly vote for Python, thanks for it! :-)

One argument I have against Ruby and for Python is, Ruby is not far enough from Perl. It is still a language where programmer is expected to learn tricks and quirks. Python is first language designed to be readable first - one of Guido's insight was that code is more ofter read than written, and so he optimized code for readability. Ruby, like Perl, is optimized for elegant shortcuts while writing code. So Ruby is definitely *NOT* optimized as easy first language for a beginner. IMHO. 

Just IMHO, I don't care about flamewars, it is personal opinion of me and couple my friends who use both and are fed up with Perl. YMMV.

---

### Post by pmasiar on 2007-07-16
> **Jeremywilms said:**
> 
-python(For some games and Apps too)
-Python(More for Apps, you would'nt make a game with it.)


So yes for Python games or no?

OLPC decided to develop in Python not only games - whole desktop is in Python! What these obviously very smart hackers know what you are missing?

---

### Post by Wybiral on 2007-07-17
> **Jordan777 said:**
> I'm still reading through all the posts haha.  Sorry I didnt get back to this sooner.  Um well ultimately i want to end up on graphically intense 3D games as I saw in one post here but 2D games such as Ragnarok and Gunbound are always great too.  Really I just want to get into programming to see if i even have what it takes.  I'm always sitting in front of the computer anyways so why not put my time to some creative use.  So so far it looks like start on Python or Ruby (still debating but it looks like Ruby's winning) and move to C/C++?

*Edit* 
I worked through all that.  It seems just from the two posters going at it haha that Ruby might be the better starting program... thingy.  Also someone said i should want to do this for fun.  Of course it would be for fun haha.  I have seen what is possible just using programming and paint and I have to say it was pretty darn cool.  I thought it looked really fun if not absolutely insane.  So the question still stands Python or Ruby then move onto C and C++. Oh and someone said I was a girl I'm a dude haha.  I'll drop by in a few hours because I need to do some homework for a while.

Wybirals Motto: "If it's 3d, use C!"

---

### Post by Jordan777 on 2007-07-17
I got it.  Oh and to the dude who sounded rather cynical I know programming is hard work I can see that when i look at code snippets.  I also understand it takes a lot of time and patience that is ok with me.  So Python, C, C++ sound like the winners.  Was there a difference between Python and python or is that just a mistake someone made on here?

---

### Post by Gremlinzzz on 2007-07-17
start here make a game 
[http://www.adventuregamestudio.co.uk/](http://www.adventuregamestudio.co.uk/)
:guitar:

---

### Post by ButteBlues on 2007-07-17
> **pmasiar said:**
> I did not found any link in your post. But regardless, anyone can fake statistics. [TIOBE index](http://www.tiobe.com/tpci.htm), even as it is hopelessly biased to book sale numbers, still shows Python 50% ahead of Ruby (and because of many free online Python books, there is no need to buy paper books, hence the bias).

Mine isn't based on book sales.

> Two years ago, the number of developers writing applications for the Microsoft Windows platform fell, while the opposite was true for Linux -- this has now become a trend.

Instead of the Web stealing away Windows Users, as people have predicted for years, it's Linux and handheld devices.

According to analysts at the Evans Data Corporation research house, 64.8 percent of North American developers are writing software for Windows, down from 74 percent only a year ago.

The decline in popularity of the world's most prevalent operating systems appears to coincide with the rise of Linux, as the number of developers targeting the open-source environment has gone up by three percentage points from 8.8 percent to 11.8 percent in the same year. The research group expects the number to drop another 2 percent in the coming year.

John Andrews, president of Evans Data, said this week that a shift away from Windows began about two years ago. "The data shows that this migration is now accelerating. Linux has benefited, but we also see corresponding growth in niche operating systems for non-traditional client devices," he said, adding that the development landscape was changing.

The popular notion among tech industry followers is that a more capable Web browser, able to run sophisticated applications either online or offline, will make the desktop operating system less important, if not irrelevant.

Many companies -- even Microsoft -- are taking up the idea of building a "Web, or cloud, operating system" for which developers can write online.

Even with more online applications, though, the Evans Data study notes that Windows desktop application development remains steady.

**The study also predicted that, although Javascript is by far the most widely used scripting language among North American developers, Ruby would see a 50 percent increase in popularity over the next year.**

In other findings, it seems that a third of developers are currently working with virtualisation, with more than 40 percent set to join them in the next year.

Microsoft was unable to comment by press time.

> > If Ruby had as "low [a] starting base" as you imply, then Ruby wouldn't be currently predicted to surpass Python in popularity within the next 2-3 years.

Well, let's see in 3 years. I am not switching :-)

Sucks to be you then. :P

> > Or better yet, if Ruby were such a fringe language, how do you explain Mac OSX Leopard shipping Ruby and Rails (including Capistrano) and RubyGems by default?

All linux distros have Python by default. OLPC picked Python as main implementation language (and not C or Ruby). Main language in Ubuntu, Google, Etc etc.

It is hardly the 'main' language at Google. It's a popular scripting language there, yes, but C is used far more (and naturally, so is Javascript due to all the AJAX things they implement).

As for Ubuntu, Python is used in a lot of things it does... but one has to understand that nearly everything you see in a release is upstream - only very few things are actually done by Ubuntu, so it's by and large, irrelevant.

> > No offence, but none of those frameworks hold a dime to Rails for reasons cited far more times elsewhere than I can count.

No offense, but you have no idea what are you talking about, but again - it is not important. 3 years from now, as you said. I admit that Ruby was first in niche of rapid web app development - it was Python's weak spot until 2005, but not any more.

I have yet to find a serious web developer making a living off of Python. I know plenty doing so with Ruby on Rails.

> > The OP wouldn't want to learn either since they're interested in games. I only commented to correct your err and misinformation about Ruby.

Well, he can easily program even commercial games in python as i mentioned before. This is exactly vote for Python, thanks for it! :-)

Python's usefulness in terms of game programming is pitiful compared to Java and C++.

> One argument I have against Ruby and for Python is, Ruby is not far enough from Perl. It is still a language where programmer is expected to learn tricks and quirks.

No, it's not.

Can tricks be learned to better improve code? Sure. But the same is true of Python, C, C++, and a long list of other languages.

> Python is first language designed to be readable first - one of Guido's insight was that code is more ofter read than written, and so he optimized code for readability. Ruby, like Perl, is optimized for elegant shortcuts while writing code. So Ruby is definitely *NOT* optimized as easy first language for a beginner. IMHO. 

Do you have any actual experience programming with Ruby? I picked up Perl, then Python, and then Ruby, and I find Ruby far better than the previous two in terms of teaching new users and re-using code.

But I guess things like:

```
5.times { print "foo" }
```

are just too complicated for the average person to figure out. :popcorn:

---

### Post by init1 on 2007-07-17
> **Jordan777 said:**
> So it looks like Python and C++ (probably python first haha).  I heard Ruby might be better to start on than Python.  Any truth to that?

I think Ruby uses OOP a bit more than Python.Try Ruby first, then Python.     
Once you know the basic concepts, go for C++ or C.

---

### Post by Jordan777 on 2007-07-17
OK I'm just gonna end this once and for all.  Thank you everyone for helping me.  There is even quite a few links that I will definitely be taking a look at.  I have to say (sorry terrible with remembering names) that the guy arguing for Ruby has won me over.  It's ok if it isn't for games it sounds like it'll be an interesting first experience anyways.  So Ruby, C, C++.  And most definitely more if I'm cut out for programming but for now I'll just set my goal to Ruby.  Thanks again guys you have all helped me out quite a bit :KS.

---

### Post by Note360 on 2007-07-17
Technically Python is tha name of the language, python is the name of the interpreter/runtime. However, most people ignore this fact as it really doesn't mean anything.

---

### Post by pmasiar on 2007-07-17
Language is called Python (proper name), compiler is python. Most peole don't care and see no difference :-)

---

### Post by djhworld on 2007-07-17
I'm over half way through my degree in games computing and the language of choice is C++, mainly because that's what the industry standard is. 

In the first year we did a bit of Java to get people onto a "programming playing field" as such. 

If you're just doing programming for a "bit of fun" sort of thing, I reccomend learning one of the languages stated in this thread. 

My programming experience went from 

Visual Basic (6 - 8 years ago...) -> C -> Java -> C++

Obviously combined with a hint of PHP/HTML etc. 

Personally I'd be reluctant to recommend Visual Basic (or any form of basic) as it rewards people for bad programming practise when they move further up the ladder.

---

### Post by pmasiar on 2007-07-17
> **ButteBlues said:**
> 
Python's usefulness in terms of game programming is pitiful compared to Java and C++.

still can beat Ruby! :-)

---

### Post by ButteBlues on 2007-07-17
> **pmasiar said:**
> still can beat Ruby! :-)
In terms of gaming, sure?

But what's the point in even trying to flout that about when any "scripting language" is absolutely awful for gaming to begin with?

---

### Post by AlexThomson_NZ on 2007-07-17
> **Wybiral said:**
> Wybirals Motto: "If it's 3d, use C!"

Wybiral's a smart guy.  I'll throw my 2c in and say C as well (for what it's worth)

---

### Post by pmasiar on 2007-07-17
> **ButteBlues said:**
> In terms of gaming, sure?

But what's the point in even trying to flout that about when any "scripting language" is absolutely awful for gaming to begin with?

I don't care about games much, but I know on top of my head  about 2 *commercial* games written in Python: Galcon and eve-online (I linked them in some other comment, use Google). So Python wins, Ruby loses, and I refuse to continue this useless discussion. Keep your Ruby, I have no problem with that, I keep my Python, and as you said before: it sucks to be you :-)

---

### Post by ButteBlues on 2007-07-17
> **pmasiar said:**
> I don't care about games much, but I know on top of my head  about 2 *commercial* games written in Python: Galcon and eve-online (I linked them in some other comment, use Google). So Python wins, Ruby loses, and I refuse to continue this useless discussion. Keep your Ruby, I have no problem with that, I keep my Python, and as you said before: it sucks to be you :-)
I've never heard of either of those games, so uh, case in point.

Until something on the level of Oblivion or even Half Life 2 is coded in Python and a major success, your entire point there is moot.

---

### Post by ub520 on 2007-07-17
civilization 4 used python so it was easy to mod.:)

---

### Post by AlexThomson_NZ on 2007-07-17
> **ub520 said:**
> civilization 4 used python so it was easy to mod.:)

I think that is a bit of a stretch.  I am pretty sure it uses boost.python to allow access to it's internals (for python scripting), but was written in C++ if I'm not mistaken (happy to be corrected here!)

---

### Post by AlexThomson_NZ on 2007-07-17
Well, I was mostly (not entirely) right!  From a dev who worked on Civ 4:

> 
We chose to use python because we wanted a well-supported scripting language that could extend our core code. Indeed, we wrote much more code in python than we were expecting, including all in-game screens and the main interface. It was a huge win for the project because writing code in a language with garbage collection simply goes faster than writing code in C++. The fact that users will be able to easily mod the interface is a nice plus as well. The downside of python was that it significantly increased our build times, mostly from linking with Boost.


---

### Post by Bob63 on 2007-07-18
Jordan777:
Although I myself am fairly new to Ubuntu/Linux, I do have some general programming experience in the MD-DOS/Windows environment on PCs. I agree that learning C++ will make you a better and more rounded programmer. I wrote my first programs in BASIC, and at the time, it was   probably the easiest language to learn because it had a lot in common with the way we tend to write and think. This was also a drawback, because you didn't need structure the way more modern languages do; you could literally write code that jumped all over the program, a technique that gave rise to the term "spaghetti code" [guilty look]. Having learned this language and style, it was more difficult for me to learn the more structured languages. So start off with a language like C++ that requires you to write structured programs.

I'd like to mention that I downloaded a copy of the 3-D drawing/animation program Blender, because:
a) I think 3-D is cool and wanted to learn how to do it.
b) Blender was free.
when I went to install it, I found out it required Python in order to run, at least on my Windows machine, so I had to fetch it as well.

Still and all, my initial outlay for software is $0, that's hard to beat!

Good Luck.
Bob

---

