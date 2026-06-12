---
title: "Choice of Programming language"
date: 2008-12-29
forum: Programming Talk
---

### Post by suncoolsu on 2008-12-29
Hi All,

This question is not related to ubuntu - but I thought I would find people on this forum who can answer this question effectively.

My area involves handling large amounts of data (of any kind) as my work is concentrated mainly in statistical computing. I know AWK, PERL, Python, RUBY etc can be very effective in handling large chunks of data (specially regular expressions)

here is my question - I am planning on learning ONE (due to lack of time) of these languages - Can anyone suggest me which would be the most suited for my needs(which include handling large data sets)? I know I am posing a wrong question (there can't be a best language - as it depends on one's need) - But can the experienced people out here comment based on what they have felt if they used all or any of these languages?

From my googling - Python would be good. 

Anyother opinions/suggestions?

---

### Post by Sorivenul on 2008-12-29
From the Programming Talk subforum:
[http://ubuntuforums.org/showthread.php?t=1006666]("http://ubuntuforums.org/showthread.php?t=1006666")
[http://ubuntuforums.org/showthread.php?t=1006662]("http://ubuntuforums.org/showthread.php?t=1006662")
Those Sticky threads should help.

As for my opinion, it depends on the ammount and type of data you plan on handling and what you want to do with it. Perl and Python are fine languages, and Python is, IMO, very easy to learn. The gurus of Programming Talk will probably have specific opinions and advice.

---

### Post by northern lights on 2008-12-29
The suitability of any language highly depends on the data and operations you want to do.

For statistical analysis, graphical representation, correlation and mathematical operations, I use [IDL]("http://www.ittvis.com/ProductServices/IDL.aspx"). Unfortunately, that's proprietary software. However unbeaten for handling very large data sets.

---

### Post by shankhs on 2008-12-29
There are lots of posts on this topic in the Programming sub-forum....
Still....
+1 for C/C++

---

### Post by moonoo on 2008-12-29
go python :D

[ducks]

---

### Post by Cracauer on 2008-12-29
> **suncoolsu said:**
> 
My area involves handling large amounts of data (of any kind) as my work is concentrated mainly in statistical computing. I know AWK, PERL, Python, RUBY etc can be very effective in handling large chunks of data (specially regular expressions)


Actually these are the least effective languages for large scale computation, with the exception of trying to do it in /bin/sh or something.

I really hope you mean that literally, that your regular expressions themselves are large ;)

If all you want is stream over lines ASCII data using regular expressions all the above are reasonably effective (because that's all C code working on C-format stored strings), but god forbids you need to break out of regex usage with a custom algorithm walking the string.

Anyway, if you have really large data you can't use regular expressions in the first place and then the above breaks down badly.  Likewise, handling binary data in scripting languages can be horribly slow, too.

I take the freedom of assuming that what you say is large data is just chunks of ASCII data that flow through a `perl -p -e 's/asd/asd/'` in a couple of seconds.  That's not large, but if that is what you do then any of the above will do except awk, which is really too limited and I wouldn't call it a "real" programming language.

Ease of adaption and available libraries would suggest Python, although Ruby is the more elegant language.

---

### Post by slavik on 2008-12-29
Large amount of text that needs to be processed ... Perl is the perfect tool for this, IMO.

---

### Post by tinny on 2008-12-29
> **shankhs said:**
> There are lots of posts on this topic in the Programming sub-forum....
Still....
+1 for C/C++

> **moonoo said:**
> go python :D

[ducks]

Why people, why?

Back it up please. Why are these languages a good choice?

---

### Post by tinny on 2008-12-29
Stats isnt my area, hence I dont have your answer. But perhaps you will find this resource interesting?

[http://www.astro.cornell.edu/staff/loredo/statpy/](http://www.astro.cornell.edu/staff/loredo/statpy/)

---

### Post by suncoolsu on 2008-12-29
thx guys for the input :-) I can find answer to any question on this forum .. thx for being so helpful

---

### Post by pmasiar on 2008-12-29
Free language fot statistics - it smells like R :-) And Python has R bindings - RPy - so you can parse files in Python and create R objects from them, using powerfull R functions on it.

R is written in C, so you have most of the C speed but with flexibility of shell language and all statistic functions you may ever need. So you  can program in high level, without worry about pushing bits in C in a wrong way.

rproject.org

---

### Post by ghostdog74 on 2008-12-29
> **Cracauer said:**
> 

I take the freedom of assuming that what you say is large data is just chunks of ASCII data that flow through a `perl -p -e 's/asd/asd/'` in a couple of seconds.  That's not large, but if that is what you do then any of the above will do except awk, which is really too limited and I wouldn't call it a "real" programming language.
why do you think awk can't do what that Perl one liner did ?

---

### Post by Cracauer on 2008-12-29
> **suncoolsu said:**
> thx guys for the input :-) I can find answer to any question on this forum .. thx for being so helpful

Errr. How about helping us help and answer the questions?

Is the data text format?

Will all processing take place on a per-line basis?

---

### Post by Cracauer on 2008-12-29
> **ghostdog74 said:**
> why do you think awk can't do what that Perl one liner did ?

Uh? I didn't say it can't place perl one-liners, also Perl's code compression will mean you might use more lines.

Awk is not a real programming language in my book namely because of difficulties making, reusing and distributing libraries.

---

### Post by Cracauer on 2008-12-29
[double post]

---

### Post by suncoolsu on 2008-12-29
I would need to used data which is definitely formatted .. i kknow what the entries are in some cases. The processing also is per line basis in most of the cases. What I might be interested in is to detect any obvious patterns. (I know graphs would help and a s/w like R is a plus). I wanted to approach the data analysis from a strict programming sense which inlvoves minimal R usage(when i say minimal i mean - I want to use the function already defined in R). I am just starting on my project - so I am not very sure what kind of data I might encounter in the future but for now - its mainly time-series data...and data from zillions of simulation from a Game theoretic problem

---

### Post by ghostdog74 on 2008-12-29
> **Cracauer said:**
> Uh? I didn't say it can't place perl one-liners, also Perl's code compression will mean you might use more lines.

I am not talking specifically about one-liners. This is your statement
> 
That's not large, but if that is what you do then any of the above will do except awk,

you mentioned "....except awk". Then I tell you that it can also be done with awk. Therefore your statement is not correct. 

> 
Awk is not a real programming language in my book namely because of difficulties making, reusing and distributing libraries.
If you are talking about more advanced programming capabilities like GUI, socket programming, numerical analysis, then maybe yes. But for trivial things like text processing as with OP's case, there's no reason to say awk cannot do the job.

---

### Post by Cracauer on 2008-12-30
I think you overanalyze my statement.

I can't recommend that a person who learns a new language starts learning awk. It is not that much easier than the others but severely limited for larger projects. Awk is good to through into sh scripts, but learning sh+awk+sed is definitely not the right approach here.

I use lots of libraries for non-GUI things. I collect things that I once consed up for many years, including for sh.  In awk this would be very difficult to do. And it's not that awk has a lot of stuff built in. Do they even have data parsing anywhere?

---

### Post by ghostdog74 on 2008-12-31
> **Cracauer said:**
> I think you overanalyze my statement.
then i think its always prudent to get facts right before giving a suggestion like that. I am only disagreeing on the part that awk cannot be used to do what that Perl one liner did, that's all. I do agree that for larger and complex projects, awk might not be the right tool to use.

> 
Awk is good to through into sh scripts, but learning sh+awk+sed is definitely not the right approach here.
if you have done sh and awk long enough, then you will understand that learning sed is redundant when awk is around. I have not used sed for centuries.

> 
I use lots of libraries for non-GUI things. I collect things that I once consed up for many years, including for sh.  In awk this would be very difficult to do. And it's not that awk has a lot of stuff built in.

where do you think [libraries](http://web.cecs.pdx.edu/~timm/dm/lib.html) come from? 

> 
 Do they even have data parsing anywhere?
If you are asking this, you seriously have to take more in depth look on awk. It is most suited for data parsing in sh. Or did you mean something else.?

---

### Post by nvteighen on 2008-12-31
Hell... what's this? A logico-philosophical forum? :D

---

### Post by Reiger on 2008-12-31
OK first off: I do not have much experience with statistics and the processing involved (beyond what little a highschool math course thaught me..) but from looking at your problem description:

If the problem is extracting little bits of info from a large context (essentially skimming a text programatically) then you'd want Perl or similar "Extracting & Reporting languages".
If, however, you have raw data which requires very much processing the key would be to identify chunks of work which can be calculated/performerd independently of each other. I'd say you either write a 'splitter' which identifies valid chunks of input data, sends that into a processor which writes it to an output file. Then you run a post-processor (written yourself) which collects the output and brews the final drought. Of course you could include more processor levels.

So at that point your program looks like this:

sh script to kickstart the process. Say:
#!/bin/sh
# splitter/'staff manager'
# post-processor
# final bits (say emitting a message like "go get it <here>"

Then we have a splitter which reads a chunk of data, sends it into a worker thread or process. If you go with threads then I'd suggest using a language like Java which shields you from a lot of management work that is required for making multiple threads run. Plus Java actually has in my experience a good IO speed -- you can abuse IO by echoing a line every other code statement and still have a decent speed.

Alternatively you can use a Math oriented language like Haskell to get the job done. It apparently has a nice foreign functions interface should you wish to delegate certain work (IO) to a custom C library (Python apparently has that too, btw), and apart from that it really does help if you understand Math but don't know programming that your Math formula's can be carried over without much modification...

---

### Post by pmasiar on 2008-12-31
> **ghostdog74 said:**
> then i think its always prudent to get facts right before giving a suggestion like that. [...] I have not used sed for centuries.

Oh really? :-) You must have started on one of those [amazing](http://www.geekologie.com/2006/10/08-week/) [steam](http://hackedgadgets.com/2007/10/05/steam-punk-computer/) [powered](http://ironwork.jp/monkey_farm/computer/pc2.html)  [laptops](http://www.geekologie.com/2007/11/steampunk_laptop_looks_old_wor.php)

It always helps when people stick to facts without exageration :-)

---

### Post by ghostdog74 on 2008-12-31
> **pmasiar said:**
> Oh really? :-) You must have started on one of those [amazing](http://www.geekologie.com/2006/10/08-week/) [steam](http://hackedgadgets.com/2007/10/05/steam-punk-computer/) [powered](http://ironwork.jp/monkey_farm/computer/pc2.html)  [laptops](http://www.geekologie.com/2007/11/steampunk_laptop_looks_old_wor.php)

sorry, i am not native english speaking, therefore, i don't get your little joke(i presume). If you are referring to whether i am old, yes, i am.  almost reaching 40 in a few years time.
> 
It always helps when people stick to facts without exageration :-)
Yes, but in this case, i don't think its exaggeration, but rather misinformation.

---

### Post by Cracauer on 2008-12-31
> **nvteighen said:**
> Hell... what's this? A logico-philosophical forum? :D

If I knew awk has so dedicated fans I'd... well, still say the same thing. Python, Perl and Ruby are better choices to learn for newcomes.

---

### Post by pmasiar on 2008-12-31
> **ghostdog74 said:**
> i don't get your little joke(i presume). 

You require exact statements from others but not from yourself. Ie how you "not used sed for centuries" if you are only 40 years old?

[Postel's law](http://en.wikipedia.org/wiki/Jon_Postel#Postel.27s_Law): "be conservative in what you send, be liberal in what you receive" is especially directed to programmers.

---

### Post by ghostdog74 on 2009-01-01
> **pmasiar said:**
> You require exact statements from others but not from yourself. Ie how you "not used sed for centuries" if you are only 40 years old?

Oh man, seriously, pmasiar, you are really is a joker.

---

### Post by suncoolsu on 2009-01-01
I agree :) ....

---

### Post by suncoolsu on 2009-01-01
@Reiger 
I think if i have done the data processing ( I mean extracting the "meaningful data" out of the big data set that I have) I would prefer to use a R (statistical package) than Java. 

Thx a lot for your detailed suggestion :-) i think you guys really helped me

---

### Post by P Minix on 2009-09-02
Which of these approaches requires the minimum amount of resources?  I am assuming AWK.

Do bindings or another method exist to post data from AWK to a database (SQLlite) or does AWK have to write out and then a separate process pick up the data?  or that point do I have to jump up to perl.

---

### Post by gtr32 on 2009-09-02
> **suncoolsu said:**
> 
My area involves handling large amounts of data (of any kind) as my work is concentrated mainly in statistical computing.

C# with LINQ would be well suited for that. I believe Mono now has LINQ support as well.

[http://www.java2s.com/Code/CSharp/LINQ/CatalogLINQ.htm](http://www.java2s.com/Code/CSharp/LINQ/CatalogLINQ.htm)

---

### Post by KIAaze on 2009-09-02
> **northern lights said:**
> The suitability of any language highly depends on the data and operations you want to do.

For statistical analysis, graphical representation, correlation and mathematical operations, I use [IDL]("http://www.ittvis.com/ProductServices/IDL.aspx"). Unfortunately, that's proprietary software. However unbeaten for handling very large data sets.

There's also ROOT for analyzing lots of numerical data:
[http://root.cern.ch/drupal/content/discovering-root](http://root.cern.ch/drupal/content/discovering-root)

It's open-source.
I don't know if it does exactly the same as IDL, but you can use it interactively (with cint), with C++ or with Python ([PyROOT]("http://root.cern.ch/root/HowtoPyROOT.html")).
It also offers a GUI toolkit.

Frankly, there are a lot of things I disliked about ROOT..., but it's probably still one of the best open-source frameworks for statistical stuff.
Just takes some time to get used to it.

Of course, if your data is text, perl, python, awk & co are probably better.
Python is the easiest to learn from what I know.

---

### Post by suncoolsu on 2009-09-09
Thx a lot guys!

I think I am comfortable with Python now - It was not hard to learn it. Lets see how hard is to do get my work done!

---

