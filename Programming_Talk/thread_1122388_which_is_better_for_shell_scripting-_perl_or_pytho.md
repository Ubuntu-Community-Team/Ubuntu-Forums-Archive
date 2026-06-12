---
title: "which is better for shell scripting- perl or python ?"
date: 2009-04-11
forum: Programming Talk
---

### Post by shivam89 on 2009-04-11
which is better for shell scripting- perl or python ?
suggest some good sources to learn

---

### Post by Sinkingships7 on 2009-04-11
Hope you brought your sunglasses.

I've never used perl, so I can't make a fair comparison, but I can tell you that Python has a library for just about anything you could possibly want to do. However, I've heard that Perl is great at manipulating text.

---

### Post by ghostdog74 on 2009-04-11
> **Sinkingships7 said:**
> Hope you brought your sunglasses.

I've never used perl, so I can't make a fair comparison, but I can tell you that Python has a library for just about anything you could possibly want to do.
and so has Perl. 
> 
 However, I've heard that Perl is great at manipulating text.
Both Python and Perl can do similar things. 

@OP, please your question will lead to a flame war. in any case, the only real solution for you is to start to learn both. then find out for yourself which one is better.

---

### Post by Greyed on 2009-04-11
Also do a search on the forums.  This is a FAQ so often brought up the horse it beats ceased having parts larger than a few atoms years ago.  I believe there are even mentions of them in the stickies.

---

### Post by iponeverything on 2009-04-11
I don't think that it will lead to flame war! so there ;)

I know perl, so perl is what I use.  If I find a tool that is in python that comes close to what I need, it is usually not big deal to modify it to do what I need. I for me its not the means, but the ends.  

I love perl because I can kick out script that will do some fairly complex text processing on directory full of files in a hour or two.. I couldn't do the same thing in python, because I don't know it well enough. IMO both are pretty amazing tools --

---

### Post by nvteighen on 2009-04-11
Knowing both languages and loving both, IMO, Perl is much more suited for shell scripting than Python. The issue is this: Perl has a lot of natively built-in facilities to handle text streams (regexp, specially), which is what you're going to do most of the time. Also, it has direct access to some useful environment variables ($!, @ARGV, %ENV, etc.) which you can access in Python only through the sys module.

Of course, there's some bias: Perl was born as a succesor for awk, sed and similar shell scripting languages... so it is nearer to those than Python is, which was designed more as a general purpose language. Perl became a general purpose one... And because of concurrent evolution, we have now the funny issue that both Perl and Python are, in fact, very similar.

Best solution: try both and see which suits better for you.

---

### Post by Greyed on 2009-04-11
> **nvteighen said:**
> Knowing both languages and loving both, IMO, Perl is much more suited for shell scripting than Python. The issue is this: Perl has a lot of natively built-in facilities to handle text streams (regexp, specially), which is what you're going to do most of the time.

Bah.  The day I gave up Perl for sysadmin work on 'nix boxes was the day I found os.path.walk().  Superseded these days by os.walk(), of course.  The rest is just sugar but not having to custom code a recursive directory walk in every dang script I had to touch (which, when I worked professionally in perl, was every one) was more than enough in and of itself.  :p

---

### Post by chrisjsmith on 2009-04-11
IMHO, Perl is write only (once you've written it you'll wonder what the hell it does for an eternity).  Python is readable too :)

---

### Post by Sprut1 on 2009-04-11
I don't know Perl well so I'm really not the right person to speak, but learning Python is so easy to learn that I'd suggest learning both.

---

### Post by ghostdog74 on 2009-04-11
> **Sprut1 said:**
> but learning Python is so easy to learn that I'd suggest learning both.

*confused*

---

### Post by nvteighen on 2009-04-11
> **Greyed said:**
> Bah.  The day I gave up Perl for sysadmin work on 'nix boxes was the day I found os.path.walk().  Superseded these days by os.walk(), of course.  The rest is just sugar but not having to custom code a recursive directory walk in every dang script I had to touch (which, when I worked professionally in perl, was every one) was more than enough in and of itself.  :p

Hm... File::Find wasn't enough?

> **chrisjsmith said:**
> IMHO, Perl is write only (once you've written it you'll wonder what the hell it does for an eternity).  Python is readable too :)

Perl code can be write-only if you want it to be so... and not only Perl, but any other programming language.

---

### Post by Sprut1 on 2009-04-11
> **ghostdog74 said:**
> *confused*

Maybe I expressed myself poorly, the point is that Python could be learned parallell to any other language, imo.

---

### Post by Greyed on 2009-04-11
> **ghostdog74 said:**
> *confused*

IE, Python was so easy to learn one could reasonably learn it and have brainpower left over for that Perl thingy.  ;)

As opposed to learning, uhm... uhm...  something a lot harder and being so brain frazzled you'd not want to learn anything else.

---

### Post by Greyed on 2009-04-11
> **nvteighen said:**
> Hm... File::Find wasn't enough?

Nope.  First because I never dabbled in Perl's bolted on OO.  The syntax made me break on in hives and that was when I was a Perl programmer! 

Second, I moved over to Python circa 1.5.2.  Which was, 1999-2000.  Back then it was Perl 5.4 aaaand 5.4.  

Third.  5.4, as far as I recall, had no File::Find.  I can't Book::Find my Camel book but a quick search of "perl 5.4 file::find" on the ol' Google yielded nada.  s/5.4/5.6/ and there are hits galore.

For those keeping score, yes, that means I have loathed Perl for 10 years.  Either I hold a grudge or the language has scarred me for life.  Which you think will give you an indication of my views on the suitability of Perl's uses in any venture.  ;)

---

### Post by nvteighen on 2009-04-11
> **Greyed said:**
> Nope.  First because I never dabbled in Perl's bolted on OO.  The syntax made me break on in hives and that was when I was a Perl programmer! 

Second, I moved over to Python circa 1.5.2.  Which was, 1999-2000.  Back then it was Perl 5.4 aaaand 5.4.  

Third.  5.4, as far as I recall, had no File::Find.  I can't Book::Find my Camel book but a quick search of "perl 5.4 file::find" on the ol' Google yielded nada.  s/5.4/5.6/ and there are hits galore.

For those keeping score, yes, that means I have loathed Perl for 10 years.  Either I hold a grudge or the language has scarred me for life.  Which you think will give you an indication of my views on the suitability of Perl's uses in any venture.  ;)
I see. All the perldoc says is that Perl 5.8's File::Find was broken... So, maybe it's a new module or whatever.

Bah, I don't think Perl is a swiss army knife and it does have weird things that make it harder than it should be, but I really like it for shell scripting stuff. Python, being a pure-OOP language (even when you don't implement your own classes) forces you in much situations to an OOP paradigm only because of how the language works in general (of course, Python is not as OOP-idiotic as Java).

But maybe here, being both Python and Perl almost equally functional for the task, we may say that here you can choose whatever you like more.

---

### Post by Greyed on 2009-04-11
> **nvteighen said:**
> But maybe here, being both Python and Perl almost equally functional for the task, we may say that here you can choose whatever you like more.

Yupyup, hence my initial response pointing them to the stickies as this has all been hashed out before.  Since then I've just been having a wee bit o' fun.  Been a while since there's been a topic on this sub that I could just give a few good natured raspberries.  :D

---

### Post by pmasiar on 2009-04-11
I am not sure if asking OP to read FAQ is too much - there are exact topics "Why I love/hate Perl" and "... Python" to get all the language bashing one can stand.

And answer is, as always: it depends. :-)

It depends what other goals you have in life and in programming.

- Do you want to learn just one language and be done with it? Python
- Do you want to maintain old systems, or be able to write hundreds of 5 line scripts for any task, quickly? Perl.

Knowledge of Perl is expected from any widely learned programmer, but Perl has many many quirks - it's mascot is Camel for a reason. Perl is friendly, it's just picky about the friends. It is (unlike Python) not a language to use just couple hours a month. Perl is a bag of many sharp tools, and requires real dedication and constant practice, or you can get hurt. Perl is not "swiss army knife" - it is swiss army chainsaw. 

I loved Perl (and still maintain Perl projects), but would choose Python over Perl for any new project (and Perl over most other languages).

---

### Post by slavik on 2009-04-11
As this thread is starting to de-evolve into yet another "Python is better than anything else" thread. This thread is closed.

OP, here's a tutorial on Perl that I've found through google: [http://www.comp.leeds.ac.uk/Perl/start.html](http://www.comp.leeds.ac.uk/Perl/start.html)

Other members have Python tutorial links in their signatures.

You may also want to check out the stickies at the top of this forum.

---

