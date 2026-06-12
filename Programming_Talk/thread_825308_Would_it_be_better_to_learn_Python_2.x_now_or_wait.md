---
title: "Would it be better to learn Python 2.x now or wait for Python 3.0?"
date: 2008-06-10
forum: Programming Talk
---

### Post by laptoplinux on 2008-06-10
I have never gotten around to learning python, but I have done programming in the past in C++, Perl, and Fortran 90.  I'd like to start learning Python soon, but I've heard that the 3.0 release (due out around September 2008, I think) will break some things from the 2.x line.  That being the case, do you think it would be wiser to start learning Python 2.x now, or to wait until 3.0 hits and then pick it up?  Either way, I'll be going in as a fresh learner with no prior Python experience.

Also, I do a lot of heavy numerical programming, so I'd like to also learn how to mix Fortran libraries (such as lapack) and Fortran 90 code into Python to do the heavy-duty number crunching when necessary.  Would it be reasonable to expect any tools necessary for that to be ported to Python 3.0 not too long after its release?

My own inclination is to wait for 3.0 so that I won't have to waste time learning things from the 2.x line that I will have to unlearn later.  But what are your thoughts?

---

### Post by danbuter on 2008-06-10
If you're not in a hurry, I'd wait. I don't think there will be a ton of differences, but I find it's easier to learn it one way, then have to re-learn it 6 months later with minor changes. Those minor changes lead to "gotchas" for me. Of course, Perl and Ruby, the other 2 major scripting languages, are also going through major upgrades right now.

---

### Post by amingv on 2008-06-10
In my opinion (and my opinion alone): don't wait one second. What will you do if Python 4 comes next? Wait for another release?
Some things will change, but they will not make 2.5 knowledge useless, in fact if you don't have to maintain a large code based on deprecated functions I doubt you (as a learner) will even notice it much.

What you could learn from here to the release is priceless.

---

### Post by LoneWolfJack on 2008-06-10
> Of course, Perl and Ruby, the other 2 major scripting languages

Out of curiosity... if Python, Perl and Ruby are the three major scripting languages for you, where would PHP come in? something like uber-scripting-language? ;)

As for Python 2 or 3, doesn't really matter... Python 2 will live on several years even after the release of Python 3.

Yet if you already have knowledge in Perl, I'd stick with that. There's nothing that Python can do that Perl can't. If you want to do web programming, learn PHP.

---

### Post by elithrar on 2008-06-10
The differences between 2.x & 3.0 are quite minor - you can also just: ```
from __future__ import <method>
``` ...which will give you much of the behaviour of 3.0 in 2.4 and above.

---

### Post by pmasiar on 2008-06-10
Don't wait. Only person who hates Python will suggest waiting :-)

Most concepts will not change, many features you can import now from __future__, 80% of translating of 2.6->3.0 is done automatically, and many packages will stay in 2.6/2.7 form. Whole point is, development will be done in parallel, and translation mostly automatically (with warning and guide to fully automatic translation), waiting will gain you nothing.

---

### Post by pmasiar on 2008-06-10
> **LoneWolfJack said:**
> Out of curiosity... if Python, Perl and Ruby are the three major scripting languages for you, where would PHP come in? something like uber-scripting-language? ;)

[snip]

Yet if you already have knowledge in Perl, I'd stick with that. There's nothing that Python can do that Perl can't. If you want to do web programming, learn PHP.

Yet with Python, you can do anything you can in Perl or PHP, but in much cleaner way. Check [http://en.wikipedia.org/wiki/Model_View_Controller](http://en.wikipedia.org/wiki/Model_View_Controller) to see what are you missing in PHP. :-)

---

### Post by slavik on 2008-06-10
> **pmasiar said:**
> Yet with Python, you can do anything you can in Perl or PHP, but in much cleaner way. Check [http://en.wikipedia.org/wiki/Model_View_Controller](http://en.wikipedia.org/wiki/Model_View_Controller) to see what are you missing in PHP. :-)
You started it, I will finish it:

Perl: Multiple kernel threads, Python: GIL. Perl 1, Python 0
Perl: easily capture output of a command ($output=`command`;), Python: import os, os.popen. Perl 2, Python 0
Perl: regex is part of the language, Python: regex just like in Java. Perl 3, Python 0
Perl: print "$1\n" while($large_text =~ /((?:[:xdigit:]{2}[:-]){5}[:xdigit:]{2})/); Python: sorry, I am not typing out 5 lines to extract a MAC addresses from a large text (not counting actually opening the file). Perl 4, Python 0
Perl: one line to create an inet socket, Python: all the tutorials I've seen, the code looks too much like C. Perl 5, Python 0.

pmasiar, do you really want me to add more?

Is MVC the only thing you got? I don't see large ticket request systems being written in Python (or PHP for that matter). RT and OTRS are both written in Perl and trust you me, the code is very readable (if you were going to bring that up). Please don't bring up Google supporting Python, because the app server is probably not Python and MapReduce is written in C++. Not only that, but Hadoop (open source version/competitor of MapReduce) is written in Java. Not to mention all the apps that financial companies use to keep track of the market are written in C++ and Java (please tell them that they are wrong).

to get back on topic, OP, you should read the articles on what 3.0 will introduce and start learning now. The most important part of learning a language (specifically language, not programming) is getting accustomed to the syntax and how it does things (and what is considered good practice in the language).

---

### Post by Wybiral on 2008-06-10
> **slavik said:**
> You started it, I will finish it:

Perl: Multiple kernel threads, Python: GIL. Perl 1, Python 0


Don't forget about stackless Python and Jython!


> **slavik said:**
> Perl: easily capture output of a command ($output=`command`;), Python: import os, os.popen. Perl 2, Python 0

This doesn't evaluate to a win, considering you accept that Python can do it...


> **slavik said:**
> Perl: regex is part of the language, Python: regex just like in Java. Perl 3, Python 0

Why does it have to be part of the syntax? Regex use is infrequent in most applications when you have access to all the parsing libraries Python has.

> **slavik said:**
> Perl: one line to create an inet socket, Python: all the tutorials I've seen, the code looks too much like C. Perl 5, Python 0.

Python loses because it doesn't look like Perl? :)

---

### Post by pmasiar on 2008-06-10
> **slavik said:**
> pmasiar, do you really want me to add more?
Is MVC the only thing you got?

I admit I kinda started it (by responding to even less substantiated comment), but I think we should better discuss details in "Why I love/hate Perl/Python", in context, to avoid repeating.

Do you want to move your argumentation there? I have **no** intention to continue it here, sorry.

And I admit you know and love your Perl, slavik, and also know how to do it right. Will it make you more happy that just today, hours ago, I got really excited by possibility to move out of my current Java project back to Perl? :-)

---

### Post by Can+~ on 2008-06-11
> **slavik said:**
> You started it, I will finish it:

Perl: Multiple kernel threads, Python: GIL. Perl 1, Python 0
Perl: easily capture output of a command ($output=`command`;), Python: import os, os.popen. Perl 2, Python 0
Perl: regex is part of the language, Python: regex just like in Java. Perl 3, Python 0
Perl: print "$1\n" while($large_text =~ /((?:[:xdigit:]{2}[:-]){5}[:xdigit:]{2})/); Python: sorry, I am not typing out 5 lines to extract a MAC addresses from a large text (not counting actually opening the file). Perl 4, Python 0
Perl: one line to create an inet socket, Python: all the tutorials I've seen, the code looks too much like C. Perl 5, Python 0.

Weird, none of those things seem like a deal breaker. Like "oh my god, I can type a horrible command in perl to get the mac address in one line! AWESOME, I could save tons of lines, f**k readability, I want space!".

There's is a loooot of bias here (also goes to pmasiar). And no, no one of you is gonna come up with objective differences, it will all look like that "Oh it looks like C, I don't like it", "It has this but it has this other thing", just STOP.

pmasiar: I like python, I even promote some people since it's easy, but I don't carry a pybible (pyble?) and bash everyone around because it has more features, if you like it, use it, if you don't, good for you. I also like C, even C++! (although, not often).

---

### Post by GammaPoint on 2008-06-11
I would start immediately. Don't postpone the fun.  You'll be able to figure out any changes when they come around, just like we'll all have to.  As for interfacing Python with Fortran, might want to look at f2py.  I've never actually used it, but I probably will soon (I'm in computational physics).

---

### Post by Wybiral on 2008-06-11
> **slavik said:**
> print "$1\n" while($large_text =~ /((?:[:xdigit:]{2}[:-]){5}[:xdigit:]{2})/);

Your code makes angry faces at me

---

### Post by babacan on 2008-06-11
> **Wybiral said:**
> Your code makes angry faces at me
omg run ! Pearl is pissed off!

---

### Post by LoneWolfJack on 2008-06-11
There shouldn't be a discussion about why this or that language is better. Diversity is a good thing. Even Python certainly has its place.

Yet if someone calls Python, Perl and Ruby the three major scripting languages he doesn't have an idea what he is talking about.

> Yet with Python, you can do anything you can in Perl or PHP, but in much cleaner way.

You will never ever convince the millions of C programmers (yes, there are FAR more of them than there are Python programmers) of this world to agree to that so don't keep indicating Python is better because of its weird syntax. If it works for you, that's great. Personally, I can't take a language serious that's trying enforce structuring the code by whitespace.

I will have to agree that Perl programmers tend to produce "show off"-code like "look, I can squeeze half a zillion commands in one line. I'm so leet!". But you can also find people who structure their code very well.

Btw, did you ever wonder why Perl got pushed aside by PHP for web development? It's because you could say "Perl can do many things, but none of them really good". This is even more true for Python.

As a professional, it is your job to choose the language best suited for the job. If your customer comes along and wants changes to his Python website, he'll get that, no problem. Yet if he comes along and says he needs a relaunch, we'll offer PHP. For any other task there are languages that are better suited than Perl or Python.

---

### Post by Luke has no name on 2008-06-11
I see you are all Blub programmers.

---

### Post by pmasiar on 2008-06-11
> **LoneWolfJack said:**
> You will never ever convince the millions of C programmers ... Python is better because of its weird syntax.

I never said that Python can replace C. All I said was that Python can replace Perl and PHP in their prime area (scripting and web development), and also Python is better first language for beginner than C/C++/Java. C is excellent complementary language for Python - their strengths and weaknesses are in different places, and C is excellent for libraries (driven from Python, of course).

And I like many other languages, too. I happens to prefer Python as my first choice for most tasks, because I am more productive that way. You may have different preferences, good for you.

Weird syntax? Every other language has weird syntax! :-)

---

### Post by Wybiral on 2008-06-11
> **pmasiar said:**
> Weird syntax? Every other language has weird syntax! :-)

Yes, I will take whitespace over braces and semicolons any day.

---

### Post by slavik on 2008-06-11
> **pmasiar said:**
> I never said that Python can replace C. All I said was that Python can replace Perl and PHP in their prime area (scripting and web development), and also Python is better first language for beginner than C/C++/Java. C is excellent complementary language for Python - their strengths and weaknesses are in different places, and C is excellent for libraries (driven from Python, of course).

And I like many other languages, too. I happens to prefer Python as my first choice for most tasks, because I am more productive that way. You may have different preferences, good for you.

Weird syntax? Every other language has weird syntax! :-)
Perl's prime area is NOT web dev. Perl only did web dev because nothing else could in the late 90's

EDIT: well, you could do it with C, but that's beside the point.
Perl's prime area is parsing text and generating reports based on that.

---

### Post by LaRoza on 2008-06-11
> **slavik said:**
> Perl's prime area is NOT web dev. Perl only did web dev because nothing else could in the late 90's


Perl was the language for server side scripting at one point. Perl dominated in that area until PHP and now it seems Ruby and Python are butting in (my money is on Python)

> **Wybiral said:**
> Yes, I will take whitespace over braces and semicolons any day.

Now we need the parentheses brigade to come in...

Should this be moved to Why To Love/Hate?

---

### Post by LoneWolfJack on 2008-06-11
> I never said that Python can replace C.

I was just referring to C-style notation.

> 
All I said was that Python can replace Perl and PHP in their prime area (scripting and web development), and also Python is better first language for beginner than C/C++/Java. C is excellent complementary language for Python - their strengths and weaknesses are in different places, and C is excellent for libraries (driven from Python, of course).


Python may be able to replace Perl or Python, but there's no market for it so to speak. PHP has grown into a very efficient and powerful web programming language and holds its place as the primary webdev language for good reasons. As for Perl... well... there's nothing in Python that Perl can't do and Perl has the bigger community (assumed), so still no reason to  prefer Python.

C is a class of it's own. Real programmers don't just use something like PHP's array_search() function, real programmers do that on 5 pages of code with hashes all over the place! :)

> Weird syntax? Every other language has weird syntax!

You probably feel that way because the BSD style notation madness has infected the brains of many programmers. At my company, we strictly enforce whitesmith style notation, which results in code that is very easy to read.

See here for different Indent styles:
[http://en.wikipedia.org/wiki/Indent_style]("http://en.wikipedia.org/wiki/Indent_style")

Bottom line, if you like Python, thats ok. Like I said, diversity is a good thing. Still, be aware that multi-purpose is not the same as general purpose (as in C) or special purpose (as in PHP). We will have to see if Python has a future or if it will remain a niche product.

That being said... at my company we're currently looking for an experienced freelance Python programmer. If anyone is interested -> PM.

---

### Post by LaRoza on 2008-06-11
> **LoneWolfJack said:**
> 
As for Perl... well... there's nothing in Python that Perl can't do and Perl has the bigger community (assumed), so still no reason to  prefer Python.

C is a class of it's own. Real programmers don't just use something like PHP's array_search() function, real programmers do that on 5 pages of code with hashes all over the place! :)

Bottom line, if you like Python, thats ok. Like I said, diversity is a good thing. Still, be aware that multi-purpose is not the same as general purpose (as in C) or special purpose (as in PHP). We will have to see if Python has a future or if it will remain a niche product.


[http://www.pbm.com/~lindahl/real.programmers.html](http://www.pbm.com/~lindahl/real.programmers.html)

> 
Real Programmers do List Processing in Fortran.

Real Programmers do String Manipulation in Fortran.

Real Programmers do Accounting (if they do it at all) in Fortran.

Real Programmers do Artificial Intelligence programs in Fortran. 

If you can't do it in Fortran, do it in assembly language. If you can't do it in assembly language, it isn't worth doing.

PHP can be used on the desktop to create GUI and CLI applications, one can use GTK with it and TK. 

I am not sure what you are arguing though, so I am not going to try to make counters.

---

### Post by LoneWolfJack on 2008-06-11
And how many different desktop programs written in PHP have you used the last month? ;)

Other than that, lighten up - so far just tongue in cheek hostility here.

---

### Post by LaRoza on 2008-06-11
> **LoneWolfJack said:**
> And how many different desktop programs written in PHP have you used the last month? ;)


What does it matter? Programming languages are tools. Use the most efficient tool for the job.

---

### Post by nvteighen on 2008-06-11
History repeating...

(*sighs*)

Thread forecast: Python increases your development speed, but C/C++ gives you more processor speed... (insert 80-20 rule). Then, why don't you code everything in Assembly? Someone will by the way defend Java or C#, meanwhile a (mostly very interesting) discussion on Turing completeness will enter. After that, links to the definition of what's a Blub programmer and why you need 10 years to be an expert... The experiment on kids learning Python before Java and those that didn't... After aprox. 7 pages of insulting each other, LaRoza will close the thread and everything will be forgotten until an unaware newbie asks for help with Mono or what language (s)he should learn next.

---

### Post by LoneWolfJack on 2008-06-11
> What does it matter? Programming languages are tools. Use the most efficient tool for the job.

Which is exactly what I wrote in an earlier post in this thread that you apparently did not read. ;)

---

### Post by LaRoza on 2008-06-11
> **nvteighen said:**
> History repeating...

(*sighs*)

Thread forecast: Python increases your development speed, but C/C++ gives you more processor speed... (insert 80-20 rule). Then, why don't you code everything in Assembly? Someone will by the way defend Java or C#, meanwhile a (mostly very interesting) discussion on Turing completeness will enter. After that, links to the definition of what's a Blub programmer and why you need 10 years to be an expert... The experiment on kids learning Python before Java and those that didn't... After aprox. 7 pages of insulting each other, LaRoza will close the thread and everything will be forgotten until an unaware newbie asks for help with Mono or what language (s)he should learn next.

Hey! You gave away the ending...

This thread was supposed to be on whether it is best to wait or not wait to learn Python. The answer is: not wait.

To cut a long story shorter, see all the articles in the link in my sig.

---

### Post by nvteighen on 2008-06-11
> **LaRoza said:**
> 
This thread was supposed to be on whether it is best to wait or not wait to learn Python. The answer is: not wait.

It was **supposed** to be on that, as you say.

Where's the OP, by the way?

---

### Post by pmasiar on 2008-06-11
> **LoneWolfJack said:**
> Python ... there's no market for it so to speak. PHP has grown into a very efficient and powerful web programming language and holds its place as the primary webdev language for good reasons. As for Perl... well... there's nothing in Python that Perl can't do and Perl has the bigger community (assumed), so still no reason to  prefer Python.

PHP is popular with web hosting companies, and with young hacker wannabes who have no idea what MVC is and why **not** using MVC is not an option in in production system (do you? :-) ). PHP was after all **designed** for web apps -- but quick and dirty apps, creating scalable and maintainable PHP apps requires serious project management skills. As Python web deployment improves (and with emergence of Google App Engine), python becomes premier language to rapid web app development - just ask YouTube :-)

Perl for serious big applications is slowly dying - Perl6 is 6 years or so in making, and still no results.

---

### Post by LaRoza on 2008-06-11
> **nvteighen said:**
> 
Where's the OP, by the way?

Probably learning Python.

---

### Post by nvteighen on 2008-06-11
> **LaRoza said:**
> Probably learning Python.
So I hope :)

---

### Post by Can+~ on 2008-06-11
> **nvteighen said:**
> History repeating...

(*sighs*)

Thread forecast: Python increases your development speed, but C/C++ gives you more processor speed... (insert 80-20 rule). Then, why don't you code everything in Assembly? Someone will by the way defend Java or C#, meanwhile a (mostly very interesting) discussion on Turing completeness will enter. After that, links to the definition of what's a Blub programmer and why you need 10 years to be an expert... The experiment on kids learning Python before Java and those that didn't... After aprox. 7 pages of insulting each other, LaRoza will close the thread and everything will be forgotten until an unaware newbie asks for help with Mono or what language (s)he should learn next.

Time traveller spotted, arrest him!

---

### Post by nvteighen on 2008-06-11
> **Can+~ said:**
> Time traveller spotted, arrest him!

Why, did I do something illegal? Ha, but I know my rights! I'm gonna call my lawyer.

---

### Post by laptoplinux on 2008-06-11
Actually, the OP has spent the day learning some Quantum Field Theory while hacking away on some Fortran 90 code to do physics calculations. Python has been a bit of a side interest for me since I first heard about it a few years ago.  My interest is to try to learn it on the side and eventually see if writing code in Python with Fortran bindings for the numerical heavy lifting works better than just writing the whole thing in Fortran to begin with.

(Say what you will about Fortran, but it seems to be the lingua franca for numerical physics calculations, and with good reason.  It can't be beat for pure speed, which is important for grinding out math that can choke a supercomputer cluster.)

---

### Post by laptoplinux on 2008-06-11
Not to mention that F90 has some good built-in stuff for working with complex numbers and dealing with matrices and vectors.  

By the way, nice thread hijack there.=D>;)

---

### Post by LaRoza on 2008-06-11
> **laptoplinux said:**
> Actually, the OP has spent the day learning some Quantum Field Theory while hacking away on some Fortran 90 code to do physics calculations. Python has been a bit of a side interest for me since I first heard about it a few years ago.  My interest is to try to learn it on the side and eventually see if writing code in Python with Fortran bindings for the numerical heavy lifting works better than just writing the whole thing in Fortran to begin with.

(Say what you will about Fortran, but it seems to be the lingua franca for numerical physics calculations, and with good reason.  It can't be beat for pure speed, which is important for grinding out math that can choke a supercomputer cluster.)

Fortran 90? Bah. I use Fortran 77.

As long as you are having fun.

---

### Post by days_of_ruin on 2008-06-11
Learn now.The differences aren't going to be big.
And slavik this thread was *supposed* to be about python.SHUT UP ABOUT PERL!!

---

### Post by LaRoza on 2008-06-12
> **days_of_ruin said:**
> SHUT UP ABOUT PERL!!

Java is better.

(In fairness to slavik, a Perl thread would probably have Python mentioned at least once)

---

### Post by nvteighen on 2008-06-12
> **LaRoza said:**
> Java is better.

(In fairness to slavik, a Perl thread would probably have Python mentioned at least once)
Once? Are you sure?

(and in any C/C++/C# thread, Python will also be mentined at least three times... And you forget the IDE discussions too)

---

### Post by Wybiral on 2008-06-12
> **nvteighen said:**
> Once? Are you sure?

(and in any C/C++/C# thread, Python will also be mentined at least three times... And you forget the IDE discussions too)

And the obligatory member pointing out the redundancy on the forum :)

---

### Post by nvteighen on 2008-06-12
> **Wybiral said:**
> And the obligatory member pointing out the redundancy on the forum :)
You got me :p

---

