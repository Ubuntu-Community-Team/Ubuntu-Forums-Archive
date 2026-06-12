---
title: "[SOLVED] See my first program!"
date: 2008-01-09
forum: Programming Talk
---

### Post by Amazona aestiva on 2008-01-09
This thread is dead.

*[SIZE="3"]Hi Everyone![/SIZE]*
**I've been learning programming for about six month, and I made something:**

I've made my special math toolkit!
Tools:
 - a simple calculator
 - a thing called "Analizator" which can count out: **(((pi^9)*pi)/3)*(pi^5)^(1/2)**
 - a prime finder
 - a greatest common factor & lowest common multiple finder

It's name is "KisNAGY" which means that something little matches with something bigger than itself. (do you know a word in English instead of Kisnagy? dictionaries don't)
[COLOR="RoyalBlue"][B]
If You would like to try it:[/B][/COLOR]

EDIT1* Pascal source codes are attached too, so you can compile it if you want.
[B][I]
EDIT2* I attached an older one without the graphical library and sudo.[/I][/B]

[COLOR="Red"]**I WARN You that this is a beta and It uses a graphical library which can't be interrupted by shortcuts, so close all your programs and save your works before start it!!! AND I have only tested under Gutsy!**[/COLOR]

Install the graphical library:
```
sudo apt-get install libsvga1 libsvga-dev
```

Download the attached archive and unpack it.

The SVGA library needs sudo permission, so start with terminal.

[B]
[COLOR="RoyalBlue"]If You have any kind of idea how to improve it, PLEASE let me know![/COLOR][/B]
[COLOR="DarkOrange"][B]
Best regards, Nándor[/B][/COLOR]

---

### Post by Wybiral on 2008-01-09
I'm not running anything "sudo" without seeing the source first :)

---

### Post by Lster on 2008-01-09
Yes this sounds a little dodgy!

---

### Post by bernied on 2008-01-09
> **Wybiral said:**
> I'm not running anything "sudo" without seeing the source first :)
+1

This should be a warning for everyone.

Maybe Amazona aestiva is innocent, but if so, then why not publish the source?

---

### Post by LaRoza on 2008-01-09
How are we going to make recommendations for improvement if we can't see the source?

This is the programming talk forum, not blind testers forum.

---

### Post by Kadrus on 2008-01-09
I downloaded your program..it doesn't work...nothing happens when I open it..and let us see the source code..
Wrap your code around PHP tags..or code tags
[php]source code[/php]
```
source code
```

---

### Post by Amazona aestiva on 2008-01-09
> **Wybiral said:**
> I'm not running anything "sudo" without seeing the source first :)

You are right

Source is attached
I don't want to fool you!

---

### Post by Lster on 2008-01-09
Wrap it in some PHP or CODE tags...

---

### Post by Kadrus on 2008-01-09
Am I the only one that can't see the program..it's not running...anyone else having the same problem?

---

### Post by Amazona aestiva on 2008-01-09
> **Lster said:**
> Wrap it in some PHP or CODE tags...

what do you mean?

---

### Post by Kadrus on 2008-01-09
> **Amazona aestiva said:**
> what do you mean?
He was talking about the source code..he probably posted that before you attached the sources..

---

### Post by Amazona aestiva on 2008-01-09
> **Kadrus said:**
> Am I the only one that can't see the program..it's not running...anyone else having the same problem?

what does it say?

---

### Post by bernied on 2008-01-09
> **Kadrus said:**
> Am I the only one that can't see the program..it's not running...anyone else having the same problem?
So did you really run the binary (program) as root (using sudo)?
This was perhaps not a good idea.

[Read this](http://en.wikipedia.org/wiki/Rootkit).

---

### Post by Amazona aestiva on 2008-01-09
> **bernied said:**
> So did you really run the binary (program) as root (using sudo)?
This was perhaps not a good idea.

[Read this](http://en.wikipedia.org/wiki/Rootkit).

I don't like that idea too, but what should I do?

It doesn't start without sudo! Can I emulate that permission or something?

---

### Post by Lster on 2008-01-09
Could you use another library that doesn't require root privileges?

---

### Post by Amazona aestiva on 2008-01-09
> **Lster said:**
> Could you use another library that doesn't require root privileges?

I attached an older version that doesn't need sudo.

However,The graphical much nicer.

---

### Post by bernied on 2008-01-09
> **Amazona aestiva said:**
> I don't like that idea too, but what should I do?

It doesn't start without sudo! Can I emulate that permission or something?
Publish only the source. Anyone who wants to try it can compile it and run it with sudo if they like. If they know how to do that, then they probably understand the dangers (hopefully). If they don't know, or can't work it out, then they probably wouldn't be able to help you anyway.

Why are you writing in Pascal?

---

### Post by Amazona aestiva on 2008-01-09
> **bernied said:**
> ...

Why are you writing in Pascal?

I learn programming at secondary school, currently Pascal, next year Delphi and C/C++.

---

### Post by Wybiral on 2008-01-09
> **Amazona aestiva said:**
> You are right

Source is attached
I don't want to fool you!

It's just a general rule that you don't execute anything "sudo" unless you can see the code. I might suggest using a library like SDL instead of VGA (since it doesn't require being root to run). VGA uses direct access to the video device which seems a bit unnatural in modern operating systems.

EDIT:

I just ran it. Looks very nice for a first program. The use of SVG makes it slightly videogame-esque though. You might want to look into using a GUI toolkit so it wont have to go into any special video modes (will run in window).

---

### Post by Amazona aestiva on 2008-01-09
> **Wybiral said:**
> It's just a general rule that you don't execute anything "sudo" unless you can see the code. I might suggest using a library like SDL instead of VGA (since it doesn't require being root to run). VGA uses direct access to he video device which seems a bit unnatural in modern operating systems.

Right, If I were you I'd not run an unknown program with sudo too.

So I attached an older without that library. I hope it'll run. However the graphical is much nicer.

Currently the Pascal compiler only knows VGA.

---

### Post by Amazona aestiva on 2008-01-09
> **Wybiral said:**
> ...
EDIT:

I just ran it. Looks very nice for a first program. The use of SVG makes it slightly videogame-esque though. You might want to look into using a GUI toolkit so it wont have to go into any special video modes (will run in window).

Thanks, now I know It works for other people too.:)

EDIT1* Would you recommend a GUI toolkit? (for pascal perhaps)

---

### Post by LaRoza on 2008-01-09
> **Amazona aestiva said:**
> Thanks, now I know It works for other people too.:)

EDIT1* Would you recommend a GUI toolkit? (for pascal perhaps)

For GUI's:

* GTK
* QT
* TK
* wxWidgets

You are not only restricted to using Pascal, you could easily learn another language. You might be interested in C, C++, Python or Perl. All of them have the above libraries available in some form.

---

### Post by monkeyking on 2008-01-09
> **Wybiral said:**
> 
I just ran it. Looks very nice for a first program. The use of SVG makes it slightly videogame-esque though. You might want to look into using a GUI toolkit so it wont have to go into any special video modes (will run in window).

Could you post a screenshot?

---

### Post by Amazona aestiva on 2008-01-09
> **monkeyking said:**
> Could you post a screenshot?

No I can't. Screen-shot doesn't work in that VGA mode. It captures black a screen.:(

---

### Post by CptPicard on 2008-01-09
> **Amazona aestiva said:**
> 
It's name is "KisNAGY" which means that something little matches with something bigger than itself. (do you know a word in English instead of Kisnagy? dictionaries don't)

Sounds like the "self-similarity" we see in fractals.

---

### Post by LaRoza on 2008-01-09
> **Amazona aestiva said:**
> No I can't. Screen-shot doesn't work in that VGA mode. It captures black a screen.:(

It seems that VGA isn't a really good thing to use...

I think you will like using another language, perhaps Python and wxWidgets or Perl and wxWidgets. If you want to compile and such, you can use C.

My wiki might help you in your quest.

(I didn't run the program because I am on Windows at the moment. In school at the moment)

---

### Post by Amazona aestiva on 2008-01-09
> **LaRoza said:**
> It seems that VGA isn't a really good thing to use...

I think you will like using another language, perhaps Python and wxWidgets or Perl and wxWidgets. If you want to compile and such, you can use C.

My wiki might help you in your quest.

(I didn't run the program because I am on Windows at the moment. In school at the moment)

Yeah, but may I ask is there a big difference between c and c++? Which do you advise?

EDIT1* Do you know how to cross compile C under Ubuntu (linux) to Windows?

---

### Post by bernied on 2008-01-09
I apologise for my earlier post. There are some nasty folk about, but you do not seem to be one of them. Happy coding!

---

### Post by Amazona aestiva on 2008-01-09
> **bernied said:**
> I apologise for my earlier post. There are some nasty folk about, but you do not seem to be one of them. Happy coding!
No trouble at all:)

---

### Post by Lster on 2008-01-09
I must also. Sorry for earlier doubts and happy coding. :)

---

### Post by LaRoza on 2008-01-09
> **Amazona aestiva said:**
> Yeah, but may I ask is there a big difference between c and c++? Which do you advise?

EDIT1* Do you know how to cross compile C under Ubuntu (linux) to Windows?

A big difference? Yes, a very big difference. You design and write programs differently in each language, especially those two.

I prefer C, but really doesn't mean anything. If you used OO design in your program, use C++ as it would be easier to rewrite. 

If you really want an easier time, use Python, which can be compiled if desired.

---

