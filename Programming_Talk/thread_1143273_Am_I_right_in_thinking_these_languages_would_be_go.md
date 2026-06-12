---
title: "Am I right in thinking these languages would be good to learn for my purposes?"
date: 2009-04-29
forum: Programming Talk
---

### Post by Last Tango on 2009-04-29
First off, I'll admit that the only programming I've ever done before is on a graphing calculator to make math class less of a hassle.  Primarily what I'm interested in doing is writing programs that can copy or create databases from websites (i.e. compiling high/low temperatures from weather websites in an automated fashion) and then being able to run this acquired data through various analyses to find patterns etc., (i.e. more complex best-fit line, curve, sinewave etc.,).  That's the main goal.  I also am interested in evolutionary algorithms, although my assumption is that delving into that field wouldn't be practical until I have a pretty good handle on less complex programming.

If that didn't make sense, I'll happily try to clarify what I mean.  Sometimes I don't seem to be able to communicate accurately what I attempted to saym and for that I apologize.

So basically what I've come up with is this:
Python for general programming
SQL for database stuff
Scheme for evolutionary programming
Does that sound about right?

Also, if anyone wants to link me to any helpful resources that won't come up quickly on google or the FAQ on this forum for learning this sort of stuff, I would appreciate it greatly.

---

### Post by soltanis on 2009-04-29
If you're pulling mass data from websites, Perl is an excellent language for parsing through human-readable text to rip out the pertinent data you are looking for. Python, though it has regular expressions, does not quite parallel Perl (which has tighter integration of regexps with its syntax, not to mention it invented Perl regular expressions anyway) in this regard.

MySQL sounds like a good call on the data storage (especially if you want that data to be related).

Scheme, Common Lisp, anything like that would probably suit you best for tracking patterns in data, yes.

Really its up to your own personal taste. Traditionally, a lot of the "glue" code for languages was hacked together from Perl, but Python has lately been stealing quite a lot of that thunder. For your particular task, though, Perl's syntax may yet serve you better.

---

### Post by jimi_hendrix on 2009-04-29
> **soltanis said:**
> If you're pulling mass data from websites, Perl is an excellent language for parsing through human-readable text to rip out the pertinent data you are looking for. Python, though it has regular expressions, does not quite parallel Perl (which has tighter integration of regexps with its syntax, not to mention it invented Perl regular expressions anyway) in this regard.

+1...perl you can just do if (/[a-z]*coolregex*/ =~ $string)...
in python you need to instantiate a class and compile the regex and stuff...
> 
MySQL sounds like a good call on the data storage (especially if you want that data to be related).

correct me if i am wrong, but i believe SQL is just a standard, and MySQL is an implementation of the standard...a very simple one that will suit your needs
> 
Scheme, Common Lisp, anything like that would probably suit you best for tracking patterns in data, yes.


i would recommend common lisp...scheme is very spartan, yet powerful, but common lisp already has stuff implemented for you to save you time

*runs from CptPicard*

---

### Post by ghostdog74 on 2009-04-29
> **soltanis said:**
> If you're pulling mass data from websites, Perl is an excellent language for parsing through human-readable text to rip out the pertinent data you are looking for. 

not true nowadays. Python(even PHP) are also on par.

> 
Python, though it has regular expressions, does not quite parallel Perl (which has tighter integration of regexps with its syntax, not to mention it invented Perl regular expressions anyway) in this regard.

regular expressions, although useful, is often not necessary. Makes code hard to read and debug when trouble comes. Not to mention the time taken to construct one. what works behind regex are just basic string manipulations and simple logic. Also Perl's internal string functions split() index(), etc can be faster than regex sometimes. Not to mention in the case of Python, string manipulations are always easy without regex.

---

### Post by ghostdog74 on 2009-04-29
> **jimi_hendrix said:**
> +1...perl you can just do if (/[a-z]*coolregex*/ =~ $string)...
in python you need to instantiate a class and compile the regex and stuff...

because in Python, there is no need to use regex most of the time. Also, there are advantages to compiling a regex. I am sure you have read up on that so i will not reiterate. With Perl, you can also compile your regex with the o modifier (qr//).

---

### Post by mkoehler on 2009-04-29
Personally, I'm only experienced in C, C++, PHP, MYSQL, and related languages, so I can't really comment on the best one to perform screen scrapes.  However, might I suggest connecting to XML data streams, such as [http://www.weather.gov/xml/?](http://www.weather.gov/xml/?)

On a side note, it could be interesting to apply various regressions to data that you obtain...however, I just wanted to make sure that you know that weather is governed by nonlinear differential equations that exhibit chaotic behavior, which is why forecasting conditions well into the future is so difficult to do accurately (you need very accurate initial conditions).

Whatever you end goal is, good luck and have fun! :P

---

### Post by Last Tango on 2009-04-29
> **mkoehler said:**
> however, I just wanted to make sure that you know that weather is governed by nonlinear differential equations that exhibit chaotic behavior, which is why forecasting conditions well into the future is so difficult to do accurately (you need very accurate initial conditions).

Whatever you end goal is, good luck and have fun! :P
Yeah, I wasn't expecting to be able to come anywhere near accurately predicting the weather purely based on numerical analysis or anything, I just think it would be interesting to see how close I can get, using correlation and stuff rather than hard science.

Thanks for the input so far!  As far as Perl, I'll look into it some more.  One question though, I know Ruby has been touted as the successor to Perl, any thoughts on this?  Particularly in relation to my goals right now?

---

### Post by CptPicard on 2009-04-30
If you're screen-scraping websites, Python has an excellent library called BeautifulSoup. SQLite is a more lightweight database than a full server like MySQL. Either way, you want to learn SQL the language...

While I am generally very fond of any Lisp, there is no particular reason to use one for your genetic-algorithm needs. Actually that sort of optimization can be heavy on the garbage collector, so you may want to be reusing your data representations and such... I have a feeling a straightforward Scheme implementation ends up being slow.

---

### Post by Kilon on 2009-04-30
> **CptPicard said:**
>  Either way, you want to learn SQL the language...

Very solid advice. Learning SQL should be your first priority. 

What you want to do can be done with any language out there. I would advice sticking with python first which easier and then if you wish you can explore other alternatives. 

I am using SQLITE at the moment , pySQLITE to be procise and I have a book on MYSQL which describes most of the feature of SQL langauge as well. Obvioulsy it is easy to jump around the two , but sqlite is more compact and easier to use. SQLITE comes with the new version fo python pre installed so I would advice giving SQLITE a chance first and then moving to MYSQL if you have to. 

I am making a database programm that I would love to see it evolve to use basic well should I say artificial intelligence. Of course it is easier saying than doing it.  Obviously you need to understand the complex maths behind it. But personally I am in no hurry to finish this project and surely is alot of fun to learn math as well. 

So If I was you I would say stick with python and sqlite as much I could and see how it goes from there. And If a problem arises well I am sure we could solve it together. Afterall the fun is the challenge. And when the challenge is big it is smart to start from the easy and then move to the more difficult part. Otherwise you may loose precious time. 

And as my father constantly reminds me "Time never comes back!"

---

