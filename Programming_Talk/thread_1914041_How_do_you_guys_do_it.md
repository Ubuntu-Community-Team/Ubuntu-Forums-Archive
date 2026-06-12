---
title: "How do you guys do it?"
date: 2012-01-23
forum: Programming Talk
---

### Post by Arbiter on 2012-01-23
Hi all,

At this risk of making this sound like a whiny rant thread, here it goes...

I've been trying to learn one language (just one!) for a long time now.  Honestly, I'm ready to throw in the towel and give up.

I started playing around with programming back in college, oh say about 7 or 8 years ago.  To date, I have yet to figure out how to do anything practical.  Sure, I can get C or PHP to display "Hello, world!" until I'm blue in the face, but I'll be damned if I can figure out how to do anything useful, like write an application.

I mean, at what point is it supposed to click and all come together and make sense, because I sure can't make heads or tails out of it.

Does anyone else here have problems with programming?  If so, how did you overcome it?

Best regards,

Arbiter

---

### Post by memilanuk on 2012-01-23
Not an answer per se, but another person with similar issues - you are not alone ;)

I've been thru god-only-knows-how-many tutorials and books and whatnot, mostly in one language, but a little bit in a couple others.  I understand (or think I do) most of the concepts, but I seem to hit a wall when it comes to making anything really functional on my own.  OOP and MVC seem to be the sticking points, really.  How to get over/around that, I have no idea.  Luckily, I don't have any aspirations of being a professional coder ;)  Unfortunately, I have a few projects that I want to tackle mainly because they would fill a niche in other hobbies that I have that no one else seems to be taking on... so I either have to give it up and live without these niche apps until someone else decides they want to make 'em... or keep grinding away at it until something 'clicks'.

---

### Post by amauk on 2012-01-23
Sounds like you're throwing yourself in at the deep end ...... and sinking

First up, different languages are catered toward different things
The right language to use for a task depends on what that task is

You wouldn't use C to write a web-application
You wouldn't use PHP to write a desktop application

You need a reason to program- a goal to achieve
What that goal is will determine which language to use

There's plenty of online tutorials and reference guides for both C and PHP
Hunt some of those down, and use them to get familiar with the languages

I'd completely ignore any graphical bits for now
While it's easy to get graphical quickly with PHP (as you can get a web browser to display stuff)
GUI stuff in C is much more involved

Start with the basics, and build up
Learn how to accept user input, display stuff back to the user, read a file, write to a file, etc.
All the basic stuff needed to make something that's useful

Then you need a project
Pick something small and easy to start with
If you wanted to try and do something in both C and PHP, pick a task that could be a desktop application or equally a web-app - Say, a diary
An application where you input a date and save some text associated with that date
and display any associated text back when provided with a date

Once you've got the basics of user input and output, move onto other more complicated things

---

### Post by Arbiter on 2012-01-23
> **amauk said:**
> Sounds like you're throwing yourself in at the deep end ...... and sinking

First up, different languages are catered toward different things
The right language to use for a task depends on what that task is

You wouldn't use C to write a web-application
You wouldn't use PHP to write a desktop application

You need a reason to program- a goal to achieve
What that goal is will determine which language to use

There's plenty of online tutorials and reference guides for both C and PHP
Hunt some of those down, and use them to get familiar with the languages

I'd completely ignore any graphical bits for now
While it's easy to get graphical quickly with PHP (as you can get a web browser to display stuff)
GUI stuff in C is much more involved

Start with the basics, and build up
Learn how to accept user input, display stuff back to the user, read a file, write to a file, etc.
All the basic stuff needed to make something that's useful

Then you need a project
Pick something small and easy to start with
If you wanted to try and do something in both C and PHP, pick a task that could be a desktop application or equally a web-app - Say, a diary
An application where you input a date and save some text associated with that date
and display any associated text back when provided with a date

Once you've got the basics of user input and output, move onto other more complicated things

Well just to illustrate more of where I am, I'm mostly doing PHP because I want to develop PHP/MySQL web applications.  My ultimate goal is to develop a serialized inventory system for work and several other private endeavors.  So far I can do procedural stuff okay.  So far I haven't been successful in getting PHP to take user input from an HTML form or anything like that.

---

### Post by Arbiter on 2012-01-23
> **memilanuk said:**
> Not an answer per se, but another person with similar issues - you are not alone ;)

I've been thru god-only-knows-how-many tutorials and books and whatnot, mostly in one language, but a little bit in a couple others.  I understand (or think I do) most of the concepts, but I seem to hit a wall when it comes to making anything really functional on my own.  OOP and MVC seem to be the sticking points, really.  How to get over/around that, I have no idea.  Luckily, I don't have any aspirations of being a professional coder ;)  Unfortunately, I have a few projects that I want to tackle mainly because they would fill a niche in other hobbies that I have that no one else seems to be taking on... so I either have to give it up and live without these niche apps until someone else decides they want to make 'em... or keep grinding away at it until something 'clicks'.

Pretty much same here, man.  It's good to know that I'm not the only one having issues with this stuff :)

---

### Post by simeon87 on 2012-01-23
> **Arbiter said:**
> Well just to illustrate more of where I am, I'm mostly doing PHP because I want to develop PHP/MySQL web applications.  My ultimate goal is to develop a serialized inventory system for work and several other private endeavors.  So far I can do procedural stuff okay.  So far I haven't been successful in getting PHP to take user input from an HTML form or anything like that.

So how do you study? There should be plenty tutorials that explain how to create a form and how to get user input. You need to do every step of the way:

- Create a page with HTML / PHP that contains a form.
- The user enters content in various input fields.
- When the user submits the form, you get the values in PHP and you process them if needed.
- You can then store them in a database using SQL
- Later, when you need the data, you can get it using SQL again to display it on other page.

---

### Post by stefangr1 on 2012-01-23
I think reading books, tutorials, and examples is a good way to learn some basics. However, to really learn it you have to use the programming language. When you're new to it, you'll have to do a lot of problem solving, and then when you found these solutions you will hopefully remember them.

The only programming language I know so well that I can write a program without doing any research is C. Many other programming languages (like the object oriented languages) have functions that are far less generic, my impression is always that there's a different function for everything and therefore I can't remember them all...

---

### Post by hockey97 on 2012-01-23
> **Arbiter said:**
> Hi all,

At this risk of making this sound like a whiny rant thread, here it goes...

I've been trying to learn one language (just one!) for a long time now.  Honestly, I'm ready to throw in the towel and give up.

I started playing around with programming back in college, oh say about 7 or 8 years ago.  To date, I have yet to figure out how to do anything practical.  Sure, I can get C or PHP to display "Hello, world!" until I'm blue in the face, but I'll be damned if I can figure out how to do anything useful, like write an application.

I mean, at what point is it supposed to click and all come together and make sense, because I sure can't make heads or tails out of it.

Does anyone else here have problems with programming?  If so, how did you overcome it?

Best regards,

Arbiter

Your not alone, everyone including me and even college students going for computer science classes have the same problem.

I had to help about 8 students and get this never took a computer science class and I was able to do college students homework. 

The problem is the resources your using and even professors can't explain things properly.

they mostly never mastered the concept since in american schools your taught to memorize everything. Which is wrong... 

if you want to be good at anything you need to understand the logic behind what your being taught and why it works that way.

to understand math one much understand who created math to be able to master math.

same goes with computer science. I learned binary but I asked the question why are computer systems using just binary 2 based values.

it's because electronics only can use 2 values. the circuit is either on or off.

when you understand that you can understand the binary system much better with a better understanding.

If your new to programming the instructor/ professor or an author of the book needs to dumb down the concepts into words that can describe the concept clearly. Otherwise you won't understand anything from a programming class or book or any of the programming concepts.

it's a huge problem in colleges right now in the U.S where students have to use other resources in order to get an a.

I been programming for 5 years and still have a ways to learn more advance concepts like graphics programmming and much more.

got a hang on networking programming and making applications.

the more advance applications you want to crate the more knowledge you need
to understand concepts and problems you will face and need to solve.

so, just have fun and enjoy reading tutorials and doing some basic things.

Trust me you won't understand the programming language fully to make a application until you done some probjects. like make a basic console calculator when that is done then the next step is to how to make a GUI for this calculator. make small projects that will allow you to gain experience programming making apps in console and have a GUI for your app.

overall you won't get to an advance level quickly it takes time to learn many concepts and trust me the more you learn the more you will understand why arrays are needed or useful and why classes are useful. 

once you do all small labs and ready for the big appliaction build. Then that first task will be the hardest thing you would ever do.

why because you will need to use arrays and classes... for your first app I bet you 100% you won't use arrays or classes. When you do this after looking at your first finish application you will study it. You would be like oh I could done this or that there.

You will eventually understand why your need arrays and classes and when to use them.

you can make applications without them but once you start making some hard-core programs that actually do something very neat and cool... you will understand that such programs needs lots and lots of code. In such casses  classes help orgainze your functions and variables and arrays allow variables to store more then 1 piece of data. It again helps you organize your code. It also allows you to execute your code faster and requires less code to do such tasks.


Programming is kinda like getting into a cold pool.  you can't just jump right in and expect your body to get used to the lower temperatures. 

You mostly use the steps and slowly adjust to the water temps.

what I am saying is that you need to learn programming small chunks at a time and don't keep thinking I am going to make this best application that people will pay millions to me to use.

you need to jump in with the interest in making computer applications not always about money or how much you will make.

the money will follow you. If you do good programming work and create apps people need then the money will follow you.

you can't follow the money.

which almost everyone here including me we always start off thinking we can make the next big video game or application or OS.
yet, we think this when we have no understanding how computers work.

once we start learning and understand how much math and work that goes into these babies.. we will then retink that and be like oh.. I am just happy that I can make a user click an ok button or show some simple animation.

trust me, I bet everyone here got very excited when they were able to create a GUI interface to their software and was able to make people click the ok and cancel buttons... well at least I was.

I showed my dad, sisters etc... I was like this is cool.. they were like what?? so what many programs can do that..Most weren't impressed but I sure was since I actually knew how the system works.

I guess the more you learn about any subject the more excited you will be about the subject.

math, I never liked it.. the schools didn't taught it right and we were always in a rush or hurry to learn the concepts. Which is impossible to do.

yet, after actually learning programming I got more respect for math. I can now understand why we had to learn slope formula and many other formulas.

while people in college most I talked to always say why would I need this.. I am not going to ever use this math. Yet, I am pretty sure the college never explain fully how and why you need to use this math to solve real world problems. 

I blame the teachers and schools. 

well anyways now I get e-books online from my local library.
I can read lots of educational books. They are very helpful.

If your not understanding it, try and read some tutorials online.

or go to google and try and search some simple free code.

you can then download that code and study it and play around with it.

play with the values and you will be amazed at how much you learn by actually playing and tinkering with things.

---

### Post by 1clue on 2012-01-23
One common thread here is to have a project.  A real project.  Sounds like the inventory system is a great starter project, and as anyone who has ever done it professionally can attest it is one that you could modify to your heart's content without ever getting everything in there.

About GUIs and windows, I strongly disagree.  Nearly every language has a library with a prefabricated set of dialog boxes for standard concepts.  If you're making a 'normal' non-web application, then open a file and print it out.  You generally need to supply a title, text for the box, and where to start from.  Maybe some extensions to allow.

As for web applications, consider trying a framework instead of whittling everything from a stick.  I use groovy/grails for that, but you could stay a bit closer to the metal with ruby/rails.  You have the framework make the basic page and wire it in, and you just tweak it to show what you want.

It really helps to understand what every single character does, because the framework rarely gets by without tweaking, but over 90% of any app is what is called boilerplate.  It's the same thing everywhere, it's stuff that needs to be there but it's the same thing on every other page.  A framework does the boilerplate for you, you just tweak the interesting stuff.

---

### Post by ofnuts on 2012-01-23
> **Arbiter said:**
> Hi all,

At this risk of making this sound like a whiny rant thread, here it goes...

I've been trying to learn one language (just one!) for a long time now.  Honestly, I'm ready to throw in the towel and give up.

I started playing around with programming back in college, oh say about 7 or 8 years ago.  To date, I have yet to figure out how to do anything practical.  Sure, I can get C or PHP to display "Hello, world!" until I'm blue in the face, but I'll be damned if I can figure out how to do anything useful, like write an application.

I mean, at what point is it supposed to click and all come together and make sense, because I sure can't make heads or tails out of it.

Does anyone else here have problems with programming?  If so, how did you overcome it?

Best regards,

Arbiter

Several thoughts:

1) There is programming, and there is writing code. Writing the code is almost a side issue. The real tough part is transforming an idea into something that can easily be explained to the computer. Learning C or PHP isn't enough. It's like learning how to use a saw, this won't tell you how to build furniture, even if it's an important part of it. The science/art of program design comes slowly and you can't expect to read the K&R end to end, close it, and go write a full-sized application. Either you start small and find gradually bigger applications to write, or you write small add-ons for your favorite software.

2) There are computer languages, and there are APIs and libraries. Knowing only languages won't get you very far because you'll spend a lot of time reinventing the wheel if you go past the "Hello world" stage. One of your first task is trying to figure out which libraries are relevant for what you want to do. This may have a deep influence on your design. What you code is very often only the "glue" between library calls.

3) Read code. Lots of it. Especially the parts that you don't understand. Try to figure out why it does things in some ways you didn't expect.

---

### Post by r-senior on 2012-01-23
How about having a go at some problems on Project Euler? The early ones aren't too heavy on the mathematics and give you a bite-sized project and a sense of achievement as you complete problems. Perhaps best of all, when you complete a problem, you get to see how other people solved it and you can learn a lot.

It won't teach architecture, but you can use things like this as a step up to your own project ideas. The trick with those is to be realistic about what you can achieve in a reasonable timeframe. Not completing things gets frustrating.

---

### Post by CoffeeRain on 2012-01-23
I have had the same problem in the countless times I have tried to learn C. I enjoy PHP, but that may be because I started out with an idea of what I wanted to do, and then coded it. Try reading through reference guides. This may spark an idea of what you want to do. You could try just for fun making a chat box like website, or something similar. Maybe learning C or PHP isn't right. You might try looking at Python. Python can work with GUI through many libraries. TK, WX, and QT are all available.

---

### Post by HotCupOfJava on 2012-01-24
Sometimes it takes having an actual problem to solve for things to finally "click". As others here have pointed out, knowing some programming concepts and language basics is akin to having tools and building materials, but you have to then create something unique with them. It is one thing to follow tutorials with step-by-step instructions, and quite another to figure out what your steps will be to solve a real-world task.

Even on my smallest projects, it takes much more time figuring out how the application should be designed than it does to actually write code.

My earliest practical, non-tutorial programs were rather small, modest applications. I would suggest you think smaller to start with. An inventory system can be a daunting task for one person, even if it is for a small shop. You would be dealing with data storage and retrieval (which may or may not involve a database engine, the use of which is a whole other ball of wax), user interfaces, sorting, table structures, etc.

We've all been frustrated by programming before (AARG all I want is for it to do X!! Why is this so hard??!!). I suspect you need something you can feel a sense of accomplishment with a little more quickly :D

---

### Post by juancarlospaco on 2012-01-24
Try something like Python !,
doesnt matter what fanboys say PHP and JS syntax are fugly.

---

### Post by 1clue on 2012-01-24
> **juancarlospaco said:**
> Try something like Python !,
doesnt matter what fanboys say PHP and JS syntax are fugly.

+1.

This sort of thing assumes you understand event models and know about system states during the event.

Unfortunately for beginners, that sort of thing is pretty much a given for any sort of dynamic web framework.

---

### Post by sanderd17 on 2012-01-24
I have had the feeling for a long time, and I still kinda have it.

But a while ago, I made a Gnome-Shell extension. It wasn't easy, as it's not documented so well, but I had in mind what it would be, and I started from an existing extension that used almost the same UI elements, so I only had to change the backend. And the total code is only one little file, so nothing too impressive.

Here on the forums, there was mentioned that there is an international clock missing in GS, so maybe I'm gonna try to do that next.

---

### Post by karlson on 2012-01-25
> **hockey97 said:**
> Your not alone, everyone including me and even college students going for computer science classes have the same problem.
I had to help about 8 students and get this never took a computer science class and I was able to do college students homework. 
The problem is the resources your using and even professors can't explain things properly.
they mostly never mastered the concept since in american schools your taught to memorize everything. Which is wrong... 


Huh???????  If you are talking about second rate colleges sure the better schools don't do that.  If you don't believe me watch Stanford's CS106 lectures on YouTube.

> 
to understand math one much understand who created math to be able to master math.


Not who but why.

> 
Programming is kinda like getting into a cold pool.  you can't just jump right in and expect your body to get used to the lower temperatures.  You mostly use the steps and slowly adjust to the water temps.


Bad analogy.

> 
the money will follow you. If you do good programming work and create apps people need then the money will follow you.


Not necessarily true.  You can be a mediocre programmer earning loads of money and be a great programmer earning peanuts for the simple reason of self marketing (and yes I am speaking from experience).

> 
I guess the more you learn about any subject the more excited you will be about the subject.


Depends...

> 
while people in college most I talked to always say why would I need this.. I am not going to ever use this math. Yet, I am pretty sure the college never explain fully how and why you need to use this math to solve real world problems.  I blame the teachers and schools.


The american system of education is based on survival of the fittest so the teachers and schools will explain this to you in some cases if you know to ask the question.  Most of us in our school years are lazy enough to skip this part simply because our parents either didn't explain how we would need to achieve our goals in life or we were too stubborn to listen.  So in either case blame the person you see in the mirror every morning.

---

### Post by SeijiSensei on 2012-01-25
> **Arbiter said:**
> Well just to illustrate more of where I am, I'm mostly doing PHP because I want to develop PHP/MySQL web applications.  My ultimate goal is to develop a serialized inventory system for work and several other private endeavors.  So far I can do procedural stuff okay.  So far I haven't been successful in getting PHP to take user input from an HTML form or anything like that.

Google can help you find answers to most PHP questions.  For instance, searching for "php forms processing" brings up [this page]("http://www.html-form-guide.com/php-form/php-form-processing.html") among others which gives a simple example.  The PHP manual itself often has basic introductions to major topics like [this one](http://php.net/manual/en/language.variables.external.php).

---

### Post by cprofitt on 2012-01-25
> **Arbiter said:**
> Hi all,

At this risk of making this sound like a whiny rant thread, here it goes...

I've been trying to learn one language (just one!) for a long time now.  Honestly, I'm ready to throw in the towel and give up.

I started playing around with programming back in college, oh say about 7 or 8 years ago.  To date, I have yet to figure out how to do anything practical.  Sure, I can get C or PHP to display "Hello, world!" until I'm blue in the face, but I'll be damned if I can figure out how to do anything useful, like write an application.

I mean, at what point is it supposed to click and all come together and make sense, because I sure can't make heads or tails out of it.

Does anyone else here have problems with programming?  If so, how did you overcome it?

Best regards,

Arbiter

I finally broke through that barrier when I found something I wanted to write. Then I had the direction and motivation. That was with C#.

I am still trying to learn Python, but lack the "what do I want to write".

---

