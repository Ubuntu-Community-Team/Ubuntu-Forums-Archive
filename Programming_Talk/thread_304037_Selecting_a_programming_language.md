---
title: "Selecting a programming language"
date: 2006-11-21
forum: Programming Talk
---

### Post by kinson on 2006-11-21
Hi Guys :)

I'm currently working as a programmer(windows), admittedly I'm not very good(fresh grad, ugh). Done some programming in C++, Java, VB6. Currently doing some maintenence of C++ and VB6 programs at work. I'm struggling with some parts of the MFC in C++.

Anyways, I think I might be moving to C# in the office soon, due to requirements. But I don't suppose that anything using the .NET framework will work in linux? :S

What I realli wanted to ask was:
If I were to pick up a language to code some simple stuff in Linux(at least to get me started on linux programming), any suggestions on what would be a good language? I'm not very good at coding interface :s

Btw, I'm not intending for this to turn into a "X language is better than Y language" poll, hehehe. Just some push in the correct direction :p

Cheers,
Kinson :)

---

### Post by Kieranties on 2006-11-21
A good idea would be to diveinto some scripting language.

I too am a software developer, mainly in c#.net stuff.  Although o-o and iterative programming techniques can of course be applied in linux you will find that it is often easier and better to build an application in a scripting language and if it needs an interface, then build it after.  After all, the interface will only call things that you have already scripted.

I highly recommend python, not only for its scripting capabilities but for its huge backing community, flexibility for almost any programming style and also its ability to be coupled with almost any other kind of application you think you may make in the future.  It is a language that once learnt you will find it hard to think "perhaps I should have programmed it in X instead of python"

You may also want to look into "generic" scripting useing bash scripts.  Of course, python can be integrated within any shell scripts you create!

---

### Post by sweemeng on 2006-11-21
actually you can run c# program on linux. you can code it too. but certain thing don't work yet. like wysiwyg asp.net and windows form designer don't work. but the c# program work very well on linux. 

you just need mono. thats for c#.

simple, language, no recommendation, just wanted to say, python is fun to code. by then i'm having fun with ruby too.

---

### Post by kinson on 2006-11-21
Lol, amazing how fast the replies come in in this forum 0_0!!!

I'll do a quick read up on Phython and see how it is in a sec (God bless wikipedia :p ). Not too familiar on how you would build a script, then later onli write the interface, but thats why I'm here, lol ! :)

Thanks for the quick replies, and will welcome more comments :)

Cheers,
Kinson

---

### Post by Kieranties on 2006-11-21
[QUOTE=kinson]Not too familiar on how you would build a script, then later onli write the interface, but thats why I'm here, lol ! [/QUOTE]

It is surprisingly easy.  
Say you write a method which at the command line looks like
```
mymethodname -someinput
```
a simple gui would be to have a textbox which the user types in  "someinput".  Then have a button which when clicked calls "mymethodname" with the parameter "someinput" passed in.  Quite a large majority of programs written for linux are simply graphical wrappers around exisiting command line applications!

I am gonna be getting back on track with my python programming soon.  There are a few things with my linux setup that I really like, so it is my intention to create a script to set it up for me.  Of course, once it is working well, it would be nice to have a gui for it to make it easier for other people to utilise and customise its options after

---

### Post by kinson on 2006-11-21
Ok. I get what you mean. But it sounds a lot like a DLL to me.

I suppose you saying:
> Quite a large majority of programs written for linux are simply graphical wrappers around exisiting command line applications!
is probably why we can work with the programs directly from the shell..?

```

xmms -q

```

Cheers,
Kinson

---

### Post by Robbjedi on 2006-11-22
C is always a good choice, from there you can easily branch out, and the power is unrivaled.

If you are looking for something a bit more light consider Perl Ruby or Python.

---

### Post by kinson on 2006-11-22
> **Robbjedi said:**
> C is always a good choice, from there you can easily branch out, and the power is unrivaled.

If you are looking for something a bit more light consider Perl Ruby or Python.

I hear very often that C/C++ is very powerful etc. But I've been struggling with C++ a bit. And I'm not a big fan of coding interface :s I'm not sure how it works in Linux, but its a pain the a$$ to code that in Windows(MFC) :s

Cheers,
Kinson

---

### Post by Kieranties on 2006-11-22
> **kinson said:**
> Ok. I get what you mean. But it sounds a lot like a DLL to me.

Not completly, just think of the gui as a program calling a program. Ok, I suppose in that sense your initial prog is a dll. Grip is a great example of this, as all of it's config within the gui uses commands which you would usually type at a command line.

Remember that linux is a drivative of unix.  GUIs came a lot later

---

### Post by kinson on 2006-11-22
> **Kieranties said:**
> Not completly, just think of the gui as a program calling a program. Ok, I suppose in that sense your initial prog is a dll. Grip is a great example of this, as all of it's config within the gui uses commands which you would usually type at a command line.

Remember that linux is a drivative of unix.  GUIs came a lot later


You mean Grip Audio Ripper? [http://en.wikipedia.org/wiki/Grip_audio_ripper](http://en.wikipedia.org/wiki/Grip_audio_ripper)
Is that coded in python?(the source looks laike C/C++ to me)

Either way, it sounds interesting :) I'll look into python programming over the weekend if I can find the time.

I found some nice online guides for python, and I'll download an ebook or 2 :)

Cheers,
Kinson

---

### Post by Kieranties on 2006-11-22
As far as i know grip is done in C.

Oh I also forgot, if your a fan of Monty Pthon, then you will probably find many of the python tutorials and exercises quite comedic!

---

### Post by kinson on 2006-11-22
> **Kieranties said:**
> As far as i know grip is done in C.

Oh I also forgot, if your a fan of Monty Pthon, then you will probably find many of the python tutorials and exercises quite comedic!

Dunno what monty pthon is :P It rings a bell, but I don't know what it is :p

If its written in C, then it wont be much help to me right? :p After all, I'm trying to learn Python :p(To be honest, used any code I've downloaded from Open source stuff before, I've downloaded and unzipped, but no idea where to start looking :s, I feel damn blur+stupid )

Cheers,
Kinson

---

### Post by Kieranties on 2006-11-22
> **kinson said:**
> Dunno what monty pthon is :P It rings a bell, but I don't know what it is :p

!!!!!1!!!!1111111!!11!!
oh dear oh dear oh dear.  Go down to your local dvd store and by Holy grail and Life of Brian NOW.  Screw the programming, get a life lesson in some of the greatest comdey ever first!

> **kinson said:**
> 
If its written in C, then it wont be much help to me right? :p After all, I'm trying to learn Python :p(To be honest, used any code I've downloaded from Open source stuff before, I've downloaded and unzipped, but no idea where to start looking :s, I feel damn blur+stupid )

Hehh, I was just using it as an example.  I highly recommend the o'reilly python book.  I am not too sure what version they are up to now, but they are very explicit for newbies, and and great way to satrt.  They are probably going pretty cheap on amazon

---

### Post by kinson on 2006-11-22
> **Kieranties said:**
> !!!!!1!!!!1111111!!11!!
oh dear oh dear oh dear.  Go down to your local dvd store and by Holy grail and Life of Brian NOW.  Screw the programming, get a life lesson in some of the greatest comdey ever first!

Lols, I see a couple of torrents for those, I'll go download it sometime next week. I like comedies :D (Weekened at Bernie's rules :) )


> 
Hehh, I was just using it as an example.  I highly recommend the o'reilly python book.  I am not too sure what version they are up to now, but they are very explicit for newbies, and and great way to satrt.  They are probably going pretty cheap on amazon

*Cough...softcopy is its on way*cough cough...Thanks ;) *koff koff
I'd love to have my own hard copies, programming books are realli nice to read(hardcopies that is), I personally can't realli stand reading ebooks. But books here(Malaysia, but I'm Chinese, if anybody asks) are rather expensive(at least a hundred bucks for computer books). The official Ubuntu book is RM109 here, which I was thinking of getting to show me support, but then again, I've got the forums and O'reilly's Ubuntu book(softcopy), so I was wondering whether I should just donate that money to Ubuntu(if they accept donations), lol.

Either way, python training should start soon for me...I'm excited !!!:D

Cheers,
Kinson

---

### Post by kinson on 2006-11-23
On a side note, I'm curious why nobody mentions Delphi when talking about Linux? Is there some special reason for it? lol :p

Cheers,
Kinson

---

### Post by Kieranties on 2006-11-23
> **kinson said:**
> On a side note, I'm curious why nobody mentions Delphi when talking about Linux? Is there some special reason for it?

Dear God!  Delphi should be destroyed.  For every aspect that Delphi can be applied to, it would be far better if people used c++, Java, or these days c#.

Delphi was built on Pascal, which was designed as a *teaching* language.  No professional work should be developed in one of the worse structured languages of all time.

Maybe I am biased, I am meant to be using Delphi at work.  I hate it so much I am using c# instead and telling people to complain once I am done!

---

### Post by kinson on 2006-11-23
> **Kieranties said:**
> Dear God!  Delphi should be destroyed.  For every aspect that Delphi can be applied to, it would be far better if people used c++, Java, or these days c#.

Delphi was built on Pascal, which was designed as a *teaching* language.  No professional work should be developed in one of the worse structured languages of all time.

Maybe I am biased, I am meant to be using Delphi at work.  I hate it so much I am using c# instead and telling people to complain once I am done!


Lol, I was trying to copy/paste your quote to my collegue sitting next to me :p, but damn MSN messenger wouldn't allow me to paste that much text.(she's uses Delphi7 to work :p )

Actualli quite a few people in my workplace use Delphi, I don't know head or tails(or body) about delphi, lols. So I suppose thats your reason for not using Delphi, hahaha :p

Good luck on converting people, hahah :)

Cheers,
Kinson

---

### Post by Kieranties on 2006-11-23
> **kinson said:**
> Lol, I was trying to copy/paste your quote to my collegue sitting next to me :p, but damn MSN messenger wouldn't allow me to paste that much text.(she's uses Delphi7 to work :p )

Actualli quite a few people in my workplace use Delphi, I don't know head or tails(or body) about delphi, lols. So I suppose thats your reason for not using Delphi, hahaha :p


Yeah, a lot of companies still do.  Technically I was employed as Delphi developer, but when I saw that the company I work for are still using Delphi **4** I almost cried.

Of course now, the majority of "bigwigs" are complaining that it takes too long to convert code for the bigger programs.  HAH!  Serves them right for not upgrading their apps and working environments for the last ten years!

---

### Post by kinson on 2006-11-23
Heh. I had some free time after sorting out a bug a couple of months ago. And the project manager said since I had some free time I could read up on Delphi(to help maintain the other software you see :P ). I still haven't :p

When I got outta college a couple of months back, me first assignment was maintaining a c++ program. The problem for me was it was a little complicated, and the author wasn't working in the company anymore, and nobody in my dept knew c++ (wth?). So till now I'm still worried that any issue crops up with that c++ program(cause that means me).

Currently working on mainting a VB6(bleh..) DLL, but they say they're moving to C# for newer stuff, so I hope I get involved. Too bad they didn't say python or anything, then I could learn and apply, hahah.

---

