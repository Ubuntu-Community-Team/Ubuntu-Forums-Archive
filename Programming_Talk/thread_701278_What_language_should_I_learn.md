---
title: "What language should I learn?"
date: 2008-02-19
forum: Programming Talk
---

### Post by LaRoza on 2008-02-19
As some of you know, I stay up late at night, and often do not sleep for longer than a day. I spend my time reading, listening to music, going out, on the forum, and programming when not actively job hunting.

During the late nights (this one included) and odd hours, I idly wrote a small web site thingy that will "help" someone chose a language to learn.

It is the first version (perhaps last, if it doesn't fly with y'all), and is likely not good. It is valid XHTML 1.1, for what it is worth :-)

Its usefulness is unknown to me, as I was focused on code and I already know how to program. 

Please take a look at it, and tell me what you think. (Keep it clean Wybiral ;))

It has my typical style for web sites that I write for function, i.e, default style.

[http://laroza.freehostia.com/home/apps/programming](http://laroza.freehostia.com/home/apps/programming)

I am interesting in learning how well/bad my assesments were, and what I can do to improve it.

(There is a feature with almost 0 discoverability, if you click on the "Purpose" and "Notes" headers, the lists will collapse to give you more room to read. I whipped that script up for my own purpose, so I could read it easier while testing. Improving the usability of the site will be next, after the tech details)

**Updates:**
* Fixed the math issue
* Added ability to exclude languages (The most code and thinking per time unit, as I did it immediately.)
* Fixed bug, that no one but me noticed...

---

### Post by pedro_orange on 2008-02-19
Lol, suggested "Forth" for me! I've never even heard of that before!


Very nice LaRoza, a well spent evening I dare say!

---

### Post by LaRoza on 2008-02-19
> **pedro_orange said:**
> Lol, suggested "Forth" for me! I've never even heard of that before!

Very nice LaRoza, a well spent evening I dare say!

You must have chosen that you know several languages and are looking for something new. 

If you do know more than a couple languages, and you are looking for something new, Forth is a good language to learn. 

(It should have given you Lisp and Assembly as well, at the very least)

It was spread out unevenly over several nights/mornings, I just did the most work this night/early morning.

---

### Post by pedro_orange on 2008-02-19
There was no place to put what languages you already knew, that would restrict the output somewhat.

Aye it gave me Forth, Assembly, Lisp. (Actually gave me lisp twice - zomg bug!!)

Along with Shell,Perl & Python.

(I have noticed the people on this forum LOVE python, so is it in their by default with every selection? :lolflag:)

---

### Post by LaRoza on 2008-02-19
> **pedro_orange said:**
> There was no place to put what languages you already knew, that would restrict the output somewhat.

Aye it gave me Forth, Assembly, Lisp. (Actually gave me lisp twice - zomg bug!!)

Along with Shell,Perl & Python.

(I have noticed the people on this forum LOVE python, so is it in their by default with every selection? :lolflag:)

It is primarily for new users, so that is why I chose not to restrict the output. I could easily write a menu that one can select the languages to exclude, which I may do now that I think about it.

Here is how it works:

* It takes a tally of the checkboxes ticked, and returns a result based on that.
* It takes note of the math skill, if it is above average, it recommended Lisp (no matter the skill), if it is below average, well, test that part.
* If there is a specific purpose, it calls up the page for that.

Perhaps I should move the Math question to a check box, and not have it do that. I was designing as I went, like a typical late night programming session.

No, it won't give Python for everything. It only gives Python for people with no experience, and for a couple of the specifc purpose options.

**Changes Planned so far:**
* Move the Math skill question to a checkbox, and not have it return a section for it.

---

### Post by Wybiral on 2008-02-19
> **pedro_orange said:**
> There was no place to put what languages you already knew, that would restrict the output somewhat.

Aye it gave me Forth, Assembly, Lisp. (Actually gave me lisp twice - zomg bug!!)

Along with Shell,Perl & Python.

(I have noticed the people on this forum LOVE python, so is it in their by default with every selection? :lolflag:)

Ironically I happen to LOVE Python, and it didn't show up for me, lol (well, it showed SciPy, probably because of the mathematics part). I got Forth, Assembly, and Lisp too (interestingly enough, I'm learning Lisp, and I know Forth and Assembly both pretty well). New for me probably would have been Haskell/Scheme/Erlang.

Maybe you should have a "languages I know" checkbox and remove the results that they already know?

---

### Post by xeth_delta on 2008-02-19
Nice page LaRoza! It suggested me to try Octave, Python/SciPy, Fortran, C/C++, Lisp. May I suggest an option to specify the languages one already knows? I can program in C/C++ and Fortran.

Even though Fortran is indeed an old language, but the standard has been updated several times over time. The latest revision being 2003. It might be worth mentioning this. One thing I really disliked in F77 and earlier was the fixed syntax. Luckily (at least from my point of view) it was deprecated.

Good luck!

---

### Post by LaRoza on 2008-02-19
> **Wybiral said:**
> Ironically I happen to LOVE Python, and it didn't show up for me, lol (well, it showed SciPy, probably because of the mathematics part). I got Forth, Assembly, and Lisp too (interestingly enough, I'm learning Lisp, and I know Forth and Assembly both pretty well). New for me probably would have been Haskell/Scheme/Erlang.

Maybe you should have a "languages I know" checkbox and remove the results that they already know?

If you know it, it is redundant to recommend it. 

It is simple in its operation.

I don't know Haskell or Erlang, where are they most used? 

Scheme is a Lisp, and I do focus on Common Lisp because that is what I know the most about. If you click on "See all languages" you will see all but one of the languages listed.

(There is a hidden feature for those that think they are clever)

Yes, I will add something like that, along with moving the math skills to checkbox.

---

### Post by LaRoza on 2008-02-19
> **xeth_delta said:**
> Nice page LaRoza! It suggested me to try Octave, Python/SciPy, Fortran, C/C++, Lisp. May I suggest an option to specify the languages one already knows? I can program in C/C++ and Fortran.

Even though Fortran is indeed an old language, but the standard has been updated several times over time. The latest revision being 2003. It might be wiorth mentioning this. One thing I really disliked in F77 and earlier was the fixed syntax. Luckily (at least from my point of view) it was deprecated.

Good luck!

I use Fortran 77...

Fortran 2008 may be out soon, keep your ears (eyes) open.

Thanks for the feedback everyone, could I ask you all do pretend you are someone else and check on the usefulness of the results? It is aimed at beginners and those wanting to learn, not those that are more experienced than I am.

---

### Post by xeth_delta on 2008-02-19
> **LaRoza said:**
> I use Fortran 77...

Fortran 2008 may be out soon, keep your ears (eyes) open.


Hehe, I guess the syntax type is a matter of preference.
You're right about the 2008 update, I just read it over the internet. Any idea when the specification will be released?

---

### Post by LaRoza on 2008-02-19
> **xeth_delta said:**
> Hehe, I guess the syntax type is a matter of preference.
You're right about the 2008 update, I just read it over the internet. Any idea when the specification will be released?

No, it doesn't add much though. Like the 90 to 95 versions.

---

### Post by pedro_orange on 2008-02-19
When you're happy with this page you should put it within the Sticky at the top. 

Very good resource.

---

### Post by LaRoza on 2008-02-19
> **pedro_orange said:**
> When you're happy with this page you should put it within the Sticky at the top. 

Very good resource.

I am not going to sticky my own thread most likely.

I am working on it now, see it again everyone. Ok, I know, the exlude option doesn't actually exclude anything yet.

---

### Post by Brendan Hart on 2008-02-19
:O thanks man... Way to turn me off programming games, I was going to be a games programming until your Language Selector told me "Programming games is a common goal. Games are often underestimated."


Nah just kidding thanks for that. Was good python for me starting language

---

### Post by pedro_orange on 2008-02-19
> **LaRoza said:**
> I am not going to sticky my own thread most likely.

I am working on it now, see it again everyone. Ok, I know, the exlude option doesn't actually exclude anything yet.

Not the thread. Add the link to [http://laroza.freehostia.com/home/apps/programming](http://laroza.freehostia.com/home/apps/programming) in the Programming FAQ :)

---

### Post by LaRoza on 2008-02-19
Thanks for the feedback everyone. The exclude option is now implemented. Hows that for fast programming?

---

### Post by pedro_orange on 2008-02-19
> **LaRoza said:**
> Thanks for the feedback everyone. The exclude option is now implemented. Hows that for fast programming?

Thats agile development for you!

---

### Post by LaRoza on 2008-02-19
> **pedro_orange said:**
> Thats agile development for you!

It involved designing a form, which I scrapped and redid (like I always do), then doing some repetative boring stuff and rewriting all the language functions, writing a client side script to make it less obtrusive, by hiding it.

Luckily, my coding style and habits make it easy to read and alter my code. Because everything is kept nice and organized (structured), it is easy to change.

Who says you can't write clean code in PHP...?

---

### Post by Siph0n on 2008-02-19
Nice website! It will probably help out a lot of new people... Especially the ones who post threads about which language to learn... I was half expecting it to return Python for anything I chose, but it didn't! ;) Good work!

---

### Post by LaRoza on 2008-02-19
> **Siph0n said:**
> Nice website! It will probably help out a lot of new people... Especially the ones who post threads about which language to learn... I was half expecting it to return Python for anything I chose, but it didn't! ;) Good work!

Thanks. I am thinking about its development (which was quick and unplanned, like most things I do in the middle of the night), and I realized the code is surprisingly lucid. I don't have any comments, as usual. That is something I need to work on.

Python isn't the answer to everything. I do recommend it as a first language (for all of the common reasons), but not for everything.

---

### Post by pmasiar on 2008-02-19
It is nice and I like it, but I was thinking somethink closer to "choose your own adventure" style, so you can comment of what decision is at every fork.

Yeah I know I need to shut up and put up the page. Not going to happen any time soon... :-(

---

### Post by LaRoza on 2008-02-19
> **pmasiar said:**
> It is nice and I like it, but I was thinking somethink closer to "choose your own adventure" style, so you can comment of what decision is at every fork.

Yeah I know I need to shut up and put up the page. Not going to happen any time soon... :-(

You like it? Good (I was waiting for you, you often see issues that others ignore)

If you can give me a better idea of what you are thinking of, I am sure I can whip something up. As you know, I have no job (no school, no friends, no responsibilities) and have a lot of spare time.

---

### Post by pmasiar on 2008-02-19
> **LaRoza said:**
>  you often see issues that others ignore)... I have no job (no school, no friends, no responsibilities) and have a lot of spare time.

So, you need to get a life, find friends, get a job! :-)

I guess your parents support you now, and I understand how addictive it can be to hang all day long on forums and spread help right and left to  people from all parts of the world. But it is not a life. 

Searching for a job should be full-time effort, you need to keep doing it 8 hours a day, every day, not including checking email, and it should be your highest priority. Really. Go to your local library, ask librarian about books for job-hunting. Most likely [What Color Is Your Parachute?](http://www.jobhuntersbible.com/articles/wciyp.php) will be available, translated. It is excellent book. You need to read it in some time in your life (one of "25 Books That Have Shaped Readers' Lives, like Saint Exupery's "The Little Prince,"), so you may as well start now. Trust me.

Regarding my idea of implementing "Language Chooser", I would do something closer to [http://en.wikipedia.org/wiki/Choose_your_own_adventure](http://en.wikipedia.org/wiki/Choose_your_own_adventure)  wiki-based game, because you can do more comments in each fork, and is easier to backtrack one step and see where the other choice will lead.

---

### Post by Acapulco on 2008-02-19
The host is down for me :(

---

### Post by LaRoza on 2008-02-19
> **pmasiar said:**
> So, you need to get a life, find friends, get a job! :-)

I guess your parents support you now, and I understand how addictive it can be to hang all day long on forums and spread help right and left to  people from all parts of the world. But it is not a life. 

Regarding my idea of implementing "Language Chooser", I would do something closer to [http://en.wikipedia.org/wiki/Choose_your_own_adventure](http://en.wikipedia.org/wiki/Choose_your_own_adventure)  wiki-based game, because you can do more comments in each fork, and is easier to backtrack one step and see where the other choice will lead.
I am working on it, the job part. I am enjoying my time, and I will enjoy my job when I get one. (I am easy to please, and accept what is)

Don't underestimate me, my parent (I only have one) is just providing house. I pay for all my stuff, including food sometimes. My mother doesn't like me paying for food though.

I will consider that type of page. When I was a kid, I found those types of books to be stupid. (I am a very fast reader, a page in a couple of seconds, and I do not always read things in order.) I do not like multi layered choices like that, and prefer things to be staight forward. In the page, you can get recommendations, or view everything, nothing in between.

However, if others would like that...

The client is the boss. (I don't have clients, or a boss, but like to be useful, so that is my "boss")

---

### Post by LaRoza on 2008-02-19
> **Acapulco said:**
> The host is down for me :(

[http://laroza.freehostia.com/home/apps/programming/index.php](http://laroza.freehostia.com/home/apps/programming/index.php)

Try again. It is almost always up.

---

### Post by Acapulco on 2008-02-19
> **LaRoza said:**
> [http://laroza.freehostia.com/home/apps/programming/index.php](http://laroza.freehostia.com/home/apps/programming/index.php)

Try again. It is almost always up.

Strange....I can't even resolve freehostia.com.

I guess I'll wait some more time... Uhmmm, maybe the cat pulled the plug of the servers? >: )

---

### Post by LaRoza on 2008-02-19
> **Acapulco said:**
> Strange....I can't even resolve freehostia.com.

I guess I'll wait some more time... Uhmmm, maybe the cat pulled the plug of the servers? >: )

It loads in a second for me. Where are you? I am in the USA.

---

### Post by pedro_orange on 2008-02-19
Is the source for this available? :)

---

### Post by LaRoza on 2008-02-19
> **pedro_orange said:**
> Is the source for this available? :)

For the site? Sure, I will tar it up.

**Note: I want comments on the site, not my late night coding style.**

[http://www.box.net/shared/brbl6yr8cs](http://www.box.net/shared/brbl6yr8cs)

---

### Post by Acapulco on 2008-02-19
> **LaRoza said:**
> It loads in a second for me. Where are you? I am in the USA.

Ok. I'm sorry to keep bothering you, but, this is strange.

I used a free traceroute web page and resolved [www.freehostia.com](www.freehostia.com) to 64.72.112.12, is this correct?

If so, I can traceroute fine but only if I use the IP. Do you know what could be wrong? I'm in Mexico BTW.

Reverse DNS seems fine. (Sorry, but I'm working with Windows at the moment :/ )

```

C:\Users\Acapulco>tracert 64.72.112.12

Traza a la dirección dns1.freehostia.com [64.72.112.12]
sobre un máximo de 30 saltos:

  1     1 ms     2 ms     1 ms  home [172.16.0.1]
  2    21 ms    19 ms    19 ms  dsl-servicio-l200.uninet.net.mx [200.38.193.226]

  3    23 ms    21 ms    20 ms  customer-201-125-75-6.uninet.net.mx [201.125.75.
6]
  4    57 ms    51 ms    54 ms  bb-dallas-stemmons-2-pos13-0-0.uninet.net.mx [20
0.38.193.29]
  5    62 ms    62 ms    64 ms  so-9-1.car1.Houston1.Level3.net [4.78.8.1]
  6    66 ms    70 ms    71 ms  ae-5-5.ebr1.Dallas1.Level3.net [4.69.132.230]
  7    61 ms    72 ms    71 ms  ae-61-61.csw1.Dallas1.Level3.net [4.69.136.122]

  8    61 ms    62 ms    62 ms  ae-1-69.edge2.Dallas1.Level3.net [4.68.19.11]
  9   189 ms   197 ms   200 ms  Alphared.edge3.Dallas1.Level3.net [4.71.220.6]
 10    69 ms    65 ms    65 ms  dns1.freehostia.com [64.72.112.12]
```

If I put in Firefox "http://64.72.112.12" i get a "cp.freehostia.com not found" error.

:confused: I have no idea whatsoever about why is this happening.

Thanks though for your time.

---

### Post by LaRoza on 2008-02-19
> **Acapulco said:**
> Ok. I'm sorry to keep bothering you, but, this is strange.

I used a free traceroute web page and resolved [www.freehostia.com](www.freehostia.com) to 64.72.112.12, is this correct?

If so, I can traceroute fine but only if I use the IP. Do you know what could be wrong? I'm in Mexico BTW.

Reverse DNS seems fine. (Sorry, but I'm working with Windows at the moment :/ )


You can't use the IP address to get to the site, that only leads to the host. (I am not a network expert, don't know the technical reasons).

Is it possible that this domain is blocked?

---

### Post by Acapulco on 2008-02-19
> **LaRoza said:**
> You can't use the IP address to get to the site, that only leads to the host. (I am not a network expert, don't know the technical reasons).

Is it possible that this domain is blocked?

I don't think so. My ISP wouldn't ban a complete domain just for the kicks of it. I'm gonna try elsewhere and see what happens.

Thanks again. :)

---

### Post by LaRoza on 2008-02-19
> **Acapulco said:**
> I don't think so. My ISP wouldn't ban a complete domain just for the kicks of it. I'm gonna try elsewhere and see what happens.

Thanks again. :)

Wait, I am setting it up on another server. Give me a couple seconds.

[http://laroza.awardspace.com/home/index.php?p=programming](http://laroza.awardspace.com/home/index.php?p=programming)

---

### Post by xeth_delta on 2008-02-19
I have a short question. There are two options: "I prefer to solve problems from the top down and want to be able to start programming from the beginning." and "I like to solve problems from the bottom up, and don't mind not making visibile progress while learning concepts."
What would make it preferrable to choose one programming language over another in those two cases?

---

### Post by LaRoza on 2008-02-19
> **xeth_delta said:**
> I have a short question. There are two options: "I prefer to solve problems from the top down and want to be able to start programming from the beginning." and "I like to solve problems from the bottom up, and don't mind not making visibile progress while learning concepts."
What would make it preferrable to choose one programming language over another in those two cases?

The first one refers to getting started immediately. In Python (for example) one can start programming and understanding (for the most part) what is happening immediately. With C, it isn't so obvious. One has to think about what is happening. Python, you have to know one keyword, and how to make a statement. In C, you have to deal with headers, defining functions, and calling functions.

Beyond hello world, one has to learn about memory address, the stack v the heap, and memory allocation. In Python, and other dynamically typed HLL's, you just focus on the logic. 

I really don't know if the test takes those questions into account in that manner. I would have to look at the code again.

---

### Post by happysmileman on 2008-02-19
Told me to learn Lisp

---

### Post by LaRoza on 2008-02-19
> **happysmileman said:**
> Told me to learn Lisp

Obey it, the almighty server side script has spoken.

---

### Post by happysmileman on 2008-02-19
> **LaRoza said:**
> Obey it, the almighty server side script has spoken.

Cool, so I have no idea what the difference between Common LISP and Scheme is, which one is more widely used and/or which one would be better in any of the readers opinions, and why?

It also said Fortran so opinions on that as well if you have any?

---

### Post by LaRoza on 2008-02-19
> **happysmileman said:**
> Cool, so I have no idea what the difference between Common LISP and Scheme is, which one is more widely used and/or which one would be better in any of the readers opinions, and why?

I am studying Common Lisp, but if you want to know more about the differences between Scheme and Lisp, you can check the wikipedia articles. When I read about them when I started learning a Lisp, I found Common Lisp to be my cup of tea.

Either will work, it doesn't matter really.

---

### Post by xeth_delta on 2008-02-19
> **happysmileman said:**
> Told me to learn Lisp

Vader voice: "Join the Lisp side, it is your destiny!"

Sorry for the bad joke, but I couldn't resist posting it :)

---

### Post by CptPicard on 2008-02-19
> **happysmileman said:**
> Cool, so I have no idea what the difference between Common LISP and Scheme is, which one is more widely used and/or which one would be better in any of the readers opinions, and why?

That's a whole subject for a holy war.. :)

Scheme is a minimalist Lisp. It stresses tail recursion for looping structures and tries to keep the language as small and clean as possible. Therefore it is often used in academia for language research and education.

CL is supposedly the more real-world Lisp. It's got more syntactic sugar to the language, and is more "multi-paradigm" (it has a pretty powerful object system for example) whereas Scheme is more apparently functional in approach.

Now... personally I tend to be partial to Scheme but it's a matter of preference. Scheme has a couple of fundamental language features that CL simply lacks -- re-entrant continuations and the yield/force lazy evaluation mechanism. CL on the other hand has dynamic-scoped variables whereas Scheme's scoping is strictly lexical. CL also has a bit of a strange way of referring to functions, in Scheme your variable can just simply be a reference to a function and that's it...

The point is that you can implement in Scheme everything CL has when it comes to the syntactic sugar such as higher-level looping constructs, and you can build your own objects with closures, but CL is not going to get proper call/cc anytime soon. If I'm going to code in a Lisp, I might just as well make use of the goodies or move back to Python.. :p

---

### Post by LaRoza on 2008-02-19
> **xeth_delta said:**
> Vader voice: "Join the Lisp side, it is your destiny!"


[img]http://imgs.xkcd.com/comics/lisp_cycles.png[/img]

---

### Post by sryth on 2008-02-19
> **LaRoza said:**
> I am studying Common Lisp, but if you want to know more about the differences between Scheme and Lisp, you can check the wikipedia articles. When I read about them when I started learning a Lisp, I found Common Lisp to be my cup of tea.

Either will work, it doesn't matter really.


Here's another link for your lisp wiki pages.

[http://www.plt-scheme.org/](http://www.plt-scheme.org/)

Home page of PLT scheme and the Dr Scheme IDE.  Dr Scheme and the help desk/tutorials/beginning languages/teach packs that come with it, and the free online books on that site, are one of the best things to happen to scheme/lisp in quite a while.

It also has Swindle integrated for a nice object system as an advanced dialect.

---

### Post by y-lee on 2008-02-19
This is a cool idea LaRoza :)

It is kind of funny it recommended I study Assembly, Forth, or Lisp.

Assembly falls under the OMG i already know more than I need to know about it, I think I'd rather be beat than try to do any real programming in it. 

Forth, hmmm, well at least I know what it is.

Lisp, yep been playing around some with common Lisp. I like the idea of it.

Btw most of my programming experience is with C in the MS dos world, aside from the stuff i learned in college a long time ago in the punched card days.

I think i need to learn python tho really as it seems so popular these days or Haskell as I read a math blog on category theory and he uses it alot to explain his ideas  and it seems pretty cool.

---

### Post by xeth_delta on 2008-02-19
> **LaRoza said:**
> [img]http://imgs.xkcd.com/comics/lisp_cycles.png[/img]

Funny comic! :D Where did you find it?

---

### Post by LaRoza on 2008-02-19
> **xeth_delta said:**
> Funny comic! :D Where did you find it?

What?! You don't recognize it? You couldn't think of it at the very mention of Lisp + Star Wars?

I will take you had a sheltered life :-).

xkcd.com

---

### Post by happysmileman on 2008-02-19
> **xeth_delta said:**
> Funny comic! :D Where did you find it?

[http://www.xkcd.com]("http://www.xkcd.com")

---

### Post by xeth_delta on 2008-02-19
> **LaRoza said:**
> What?! You don't recognize it? You couldn't think of it at the very mention of Lisp + Star Wars?

I will take you had a sheltered life :-).

xkcd.com

Haha, as a matter of fact the drawing style seemed familiar. Once you mentioned the site I remembered where I saw it. ;)

---

### Post by LaRoza on 2008-02-19
> **xeth_delta said:**
> Haha, as a matter of fact the drawing style seemed familiar. Once you mentioned the site I remembered where I saw it. ;)

Ah, good. I thought you never heard of it...

---

### Post by LaRoza on 2008-02-19
> **sryth said:**
> Here's another link for your lisp wiki pages.

[http://www.plt-scheme.org/](http://www.plt-scheme.org/)

Home page of PLT scheme and the Dr Scheme IDE.  Dr Scheme and the help desk/tutorials/beginning languages/teach packs that come with it, and the free online books on that site, are one of the best things to happen to scheme/lisp in quite a while.

It also has Swindle integrated for a nice object system as an advanced dialect.

Thanks, I will have to add some Scheme stuff soon. Just have to use it first.

---

### Post by Joeb454 on 2008-02-19
Told me to learn Assembly, then Forth, then Lisp...

The weird thing?

I've done a bit of Assembly, and I hate it with an immense passion :p

---

### Post by xeth_delta on 2008-02-19
Back to the topic, I just noticed something, you get the same results if you choose either "I have no programming experience." or "I know one language well.". Same result if you choose both (Ok, one shouldn't, the two possibilities exclude each other).

---

### Post by LaRoza on 2008-02-19
> **xeth_delta said:**
> Back to the topic, I just noticed something, you get the same results if you choose either "I have no programming experience." or "I know one language well.". Same result if you choose both (Ok, one shouldn't, the two possibilities exclude each other).

If you know no language, I recommend Python, with a see also for C. If you know one language well, it can't be both Python and C. As I recommend Python for the first language, with C as the second, giving the same result makes sense.

Naturally, as was suggested (by a bunch of people), you can exclude languages. If one know either one, the other will come up. 

My general advice is to learn Python, C, then Lisp.

Natually, the next level is Lisp (with others thrown in, that may be interesting).

The last one is for Assembly, Forth, and Lisp.

If one has a specific purpose, it gives different results.

---

### Post by Fbot1 on 2008-02-19
> **LaRoza said:**
> For the site? Sure, I will tar it up.

**Note: I want comments on the site, not my late night coding style.**

[http://www.box.net/shared/brbl6yr8cs](http://www.box.net/shared/brbl6yr8cs)

I think you should use this sort of approach rather than weighting it:

```

bool Do_you_want_to_access_the_hardware_directly;
bool Should_it_work_on_Macs;
bool Should_it_be_popular;
.....

if (Do_you_want_to_access_the_hardware_directly == true)
	 {java=csharp=python=ruby=perl=pascal= false;}

else 	{c=cpp=d=asm=hla= false;}

if (Should_it_work_on_Macs == true)  {pascal= false;}

if ( Should_it_be_popular == true) {d=asm=hla=pascal= false;}
.....

```

---

### Post by xeth_delta on 2008-02-19
> **LaRoza said:**
> If you know no language, I recommend Python, with a see also for C. If you know one language well, it can't be both Python and C. As I recommend Python for the first language, with C as the second, giving the same result makes sense.

Naturally, as was suggested (by a bunch of people), you can exclude languages. If one know either one, the other will come up. 

My general advice is to learn Python, C, then Lisp.

Natually, the next level is Lisp (with others thrown in, that may be interesting).

The last one is for Assembly, Forth, and Lisp.

If one has a specific purpose, it gives different results.

Ok, I see now. Thanks

---

### Post by Fbot1 on 2008-02-19
> **LaRoza said:**
> If you know no language, I recommend Python, with a see also for C. If you know one language well, it can't be both Python and C. As I recommend Python for the first language, with C as the second, giving the same result makes sense.
Actually, it wouldn't considering that case would never happen.

---

### Post by slavik on 2008-02-19
> **Fbot1 said:**
> I think you should use this sort of approach rather than weighting it:

```

bool Do_you_want_to_access_the_hardware_directly;
bool Should_it_work_on_Macs;
bool Should_it_be_popular;
.....

if (Do_you_want_to_access_the_hardware_directly == true)
	 {java=csharp=python=ruby=perl=pascal= false;}

else 	{c=cpp=d=asm=hla= false;}

if (Should_it_work_on_Macs == true)  {pascal= false;}

if ( Should_it_be_popular == true) {d=asm=hla=pascal= false;}
.....

```
afaik, it is possible to write device drivers in Perl :)

---

### Post by LaRoza on 2008-02-19
> **Fbot1 said:**
> I think you should use this sort of approach rather than weighting it:


The site is intended for beginners mostly, and general advice.

I am going to do the more specific and interactive site later, sort of the way pmasiar described it.

That will like take a little more planning, but will take less code.

---

### Post by Fbot1 on 2008-02-19
> **slavik said:**
> afaik, it is possible to write device drivers in Perl :)

directly?

---

### Post by LaRoza on 2008-02-19
> **slavik said:**
> afaik, it is possible to write device drivers in Perl :)

I have seen a device driver in Python, so it wouldn't be a stretch to be able to make one in Perl.

---

### Post by slavik on 2008-02-19
> **Fbot1 said:**
> directly?
that, I am not sure about ... Perl isn't exactly the language I would want to use to write device drivers, unless I really go nuts ;)

---

### Post by amingv on 2008-02-19
It gave me Assembler, Forth and Lisp (which I kind of agree with). I took it again, with the mindset I had about four months ago when I started to learn to program. It gave me Lisp, C and Java.

They are not bad suggestions, of course, and I eventually plan to learn all of them. But for the beginner me I would have suggested Python instead of Java (I suppose that came prompted by the cross-platform question). That is, I feel that for someone that has never programmed before, a language that enforces OOP is not very functional. When you are starting you want to make little "hacks" and quick fixes and scripts are perfect for that.

Of course I'm in no position to hold my statement, because I do not know Java (yet). But that was one of the reasons I didn't pick it at the beginning. I like the C suggestion though and the Lisp less so, but still better than Java.

By the way, you seem to be enjoying Lisp, LaRoza, and your program too ^_^.

---

### Post by slavik on 2008-02-19
how about a simple table of language features (of course, being beginner friendly cannot be one of them because it is not quantifiable) ...

edit: I mean a 2d table, like a matrix :)

---

### Post by HermanAB on 2008-02-19
"What language should I learn?

English.

---

### Post by CptPicard on 2008-02-19
Hmm. Your bottom-up and top-down points are slightly strange I think... I always felt like bottom-up programming yields much better to "coding from the start", as you're building your program by first writing small blocks and then combining them into bigger blocks... and top-down forces you to design more before you start seeing actual progress?

---

### Post by Fbot1 on 2008-02-19
> **slavik said:**
> how about a simple table of language features (of course, being beginner friendly cannot be one of them because it is not quantifiable) ...

edit: I mean a 2d table, like a matrix :)

[http://en.wikipedia.org/wiki/Comparison_of_programming_languages](http://en.wikipedia.org/wiki/Comparison_of_programming_languages)

?

---

### Post by Presto123 on 2008-02-19
Should I be concerned if it tells me I should learn Spanish? :lolflag:

I like it LaRoza, it tells me I should learn Python, which I was already interested in doing. :)

---

### Post by LaRoza on 2008-02-20
> **amingv said:**
> It gave me Assembler, Forth and Lisp (which I kind of agree with). I took it again, with the mindset I had about four months ago when I started to learn to program. It gave me Lisp, C and Java.

They are not bad suggestions, of course, and I eventually plan to learn all of them. But for the beginner me I would have suggested Python instead of Java (I suppose that came prompted by the cross-platform question). That is, I feel that for someone that has never programmed before, a language that enforces OOP is not very functional. When you are starting you want to make little "hacks" and quick fixes and scripts are perfect for that.

Of course I'm in no position to hold my statement, because I do not know Java (yet). But that was one of the reasons I didn't pick it at the beginning. I like the C suggestion though and the Lisp less so, but still better than Java.

By the way, you seem to be enjoying Lisp, LaRoza, and your program too ^_^.
The cross platform suggestion didn't cause you to get Java. 

It is most likely because you chose the second option, and one of the last three.

I will refine the suggestions. For those that do not see the pattern, it only has three recommendations (based on the check boxes), and the specific purpose option adds more.

---

### Post by LaRoza on 2008-02-20
> **CptPicard said:**
> Hmm. Your bottom-up and top-down points are slightly strange I think... I always felt like bottom-up programming yields much better to "coding from the start", as you're building your program by first writing small blocks and then combining them into bigger blocks... and top-down forces you to design more before you start seeing actual progress?

I wll rephrase that, thanks.

I coded the form first, and then forgot about it.

---

### Post by Acapulco on 2008-02-20
> **LaRoza said:**
> Wait, I am setting it up on another server. Give me a couple seconds.

[http://laroza.awardspace.com/home/index.php?p=programming](http://laroza.awardspace.com/home/index.php?p=programming)

Yeey. It works for me, thanks!.I got Assembly, Forth and Lisp without excluding any language. 

I guess I would take Forth, as I know nothing about. The other two I had to learn for college classes, although I must admit I'm not proficient in neither. 

Pretty good guess.

Have you looked into Processing ([http://www.processing.org]("http://www.processing.org")? I know it's not a language per se, as it is actually Java, but I believe it would qualify as a subcategory, because it has many different things, specially since it's focused on visual arts and design.

Can't seem to get C++ for a reason, and I only got Ruby and Pearl after ticking off  "I like being creative and finding new ways of doing things, even if it isn't the most obvious way.".. I wonder what that means : )

It's very nice though. How does it work? Is it based on a decision tree or something? 

Maybe someone with experience in neural networks can train a net for this. That would be awesome.

---

### Post by LaRoza on 2008-02-20
> **Acapulco said:**
> 
Can't seem to get C++ for a reason, and I only got Ruby and Pearl after ticking off  "I like being creative and finding new ways of doing things, even if it isn't the most obvious way.".. I wonder what that means : )

It's very nice though. How does it work? Is it based on a decision tree or something? 

Maybe someone with experience in neural networks can train a net for this. That would be awesome.

It is very simple in its operation. It is quite "stupid".

You can get the source for it through a link earlier in this thread.

---

### Post by LaRoza on 2008-02-22
I rewrote it. It follows the general use of the original, but this one is better in my opinion. But I am just the person who wrote it, what do you all think of it now?

(Both servers have the updated version, if you can view my page from the link to my home page in my sig, then use the "IE" one. Next time, get a real browser that can handle the correct MIME type for XHTML docs.)

---

### Post by Zwack on 2008-02-24
Interesting... 

For me it suggests Assembler, Forth and LISP...

What other languages might be usefully added?

Pascal, Ada, SML/NJ?...

Z.

---

