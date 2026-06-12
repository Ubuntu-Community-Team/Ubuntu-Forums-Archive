---
title: "Good OS for hobbyist?"
date: 2007-11-22
forum: Programming Talk
---

### Post by nightlith on 2007-11-22
Probably posting in the wrong forum, but hey, first post! It is programming related though, so this seems like the best place.

I used to program a lot. Just dabbled mostly, and all of it self taught. All of it was done making "games". I started young, 7 or 8, making goofy BASIC apps on my mother's Vic20. Went on to DOS and it's QBASIC interpreter, discovered C/C++ (djgpp), took some classes in high school, and read a couple books. Nothing ever panned out in terms of a programming career mostly because this was all when computers were geeky ****, and none of the schools I went to offered anything resembling Computer Science. Whatever, just trying to give a little of my background experience.

I've gotten the itch to try my hand at it again, as I greatly enjoyed coding out different ideas, and I'm a sucker for fun little 2d games. I've had a lot of things I've always wanted to try, but at some point, probably between job, marriage, children and houses, I've never had time to keep up with my passion. Getting back into C++ seems very impossible at this point because, obviously technology didn't wait for me ;)

Personal life story aside, is a Linux OS going to better suit me for 2d hobbyist-esque programming? I've dabbled with the DirectX APIs but I completely lost. I don't mind OpenGL, but finding windows specific resources was....difficult. Also, I'd appreciate book ideas. Though I seem to learn a lot faster by doing than reading.

And, not to cause an argument, but I really enjoyed using MSFT's VisualStudio IDE. I loved the interface and the "Ease of use" features it had. Are there similar development platforms for Ubuntu? Or does everyone just use vi? ;)

---

### Post by CptPicard on 2007-11-22
Linux is *the* "hobbyist OS" and has been that for over a decade. Welcome on board. :)

You'll find everything you need to code pretty much anything you want on any language of your choice... the best IDEs you'll find for Java and C++, but for the most part, you'll be better off learning your editor of choice well.

---

### Post by LaRoza on 2007-11-22
Python + PyGame, see my wiki. Any distro of Linux will do, also, Windows and the Mac OSX will work also, without changing the code.

You can use any editor you want, I usually use Gedit, Kwrite or Kate and Vim. Geany seems to be a nice lightweight, but feature rich IDE, although I don't use IDE's.

---

### Post by seetho on 2007-11-22
> **nightlith said:**
>  I started young, 7 or 8, making goofy BASIC apps on my mother's Vic20. 

Hey!  I started off with the VIC-20 too!  Those were the good old days of personal computing...

> Personal life story aside, is a Linux OS going to better suit me for 2d hobbyist-esque programming?

It's one of the best - after all it was built by hobbyists and is largely still worked on by hobbyists.  You basically have all the tools you need to build pretty much anything.  Can't ask for more can you?

> And, not to cause an argument, but I really enjoyed using MSFT's VisualStudio IDE. I loved the interface and the "Ease of use" features it had. Are there similar development platforms for Ubuntu? Or does everyone just use vi? ;)

The 'best IDE' is the one you are most used to!  Personally I just use 'Gedit' and sometimes 'VIM' for my editing needs.  Everything else I do in commandline.  Of course it take a while to be efficient at it but it's a liberating feeling when you are not really tied to any kind of single 'do-it-all' IDE.  I have some proffesional C/C++/ASM developer friends still hanging on to their text mode QEdit (from MSDOS days) and running their MSVisual C++ compilers from commandline - and they are comfortably developing huge apps for WinVista.

So keep an open mind and welcome to Linux.

---

### Post by khnle on 2007-11-22
Microsoft Visual IDEs are good, but by no means, not the only ones and certainly not the best.  You can't use that tool to solve every problem on every platform.  Same thing with Linux, same with Java, same with <fill in the blank>.  Don't pick your tool before your problem.

---

### Post by nightlith on 2007-11-22
Haha, yeah, kind of a stupid question about it being a good choice :p I've tried various distros in the past with mixed results. Ubuntu looks fantastic though, and my experience with it has been good. I've not 'needed' to use linux though so I've never fully switched. It certainly does look like the best choice.

LaRoza, that wiki is great! Consider it bookmarked. Following your recommendation for Geany, I've also discovered Code::Blocks. Anyone with experience with it can recommend it? Both look like what I'm more accustomed to with Windows based pc's, but I'm wondering if they'll be easy to configure?

It's not so much that I'm afraid to text edit code, certainly not since it's what I grew up on. I'm just unfamiliar with The Linux Way of doing things in terms of 'make' and creating gcc compiler scripts or whatnot. It seems a bit more than complicated for what I'd like to do.

One of the greatest API's I've used in the past in my old DOS days was something called Allegro. Is there something similar around these days?

Thanks again for the help! Looking forward to making some more posts from inside Ubuntu ;)

---

### Post by smartbei on 2007-11-22
Allegro still exists, though I have no idea how commonly used it is. I recommend taking LaRoza's suggestion and using Python and PyGame to create what you had in mind - since it will take far less time to get to a decent degree of efficiency in Python as compared to C++. I believe pyGame includes everything you need to make a simple (2D)game.

If you still want C++ though, I believe SDL is commonly used. As a plus, IIRC it is platform indpendant.

---

### Post by glok_twen on 2007-11-22
similar vintage here. i learned on apple II, trs-80 and commodore 64.

let the opinions continue...

my $0.02 would be to give Java a whirl. the book Head First Java, of which i have absolutely no affiliation, will both re-ground you in object concepts and also introduce the language.

what i found in experimenting with code::blocks, kdeveloper, vi, etc is that all are great tools in their own right. with Head First Java plus Netbeans you will get a ubiquitous language, user friendly IDE that's managed through the ubuntu repos, and insulation from needing to do work with how specifically to link in libraries and config outside your code. of course there is a very extensive and tested libraries for all sorts of work you'd want to do. altho i haven't done much graphics work myself.

---

### Post by nightlith on 2007-11-22
I'm not at all familiar with Python. My knowledge is comprised mainly of BASIC, C/C++, some (very limited) Pascal, and various web stuff (HTML, PHP, etc). Would it be easy to pick up and go, like syntax wise?

I think Civilization 4 uses Python for it's modability...but I've not fiddled too much with that. Perhaps I should have!

---

### Post by sn0n on 2007-11-22
may i recommend RealBASIC? its free for personal use on linux. 
you can find it at [http://realsoftware.com/download/](http://realsoftware.com/download/)
after downloading and "installing" at first run it will ask you to "register" which is free and automatic.

---

### Post by jespdj on 2007-11-22
Many Ubuntu desktop applications are written in Python.

The two major IDEs for Java are [Eclipse]("http://www.eclipse.org") and [NetBeans]("http://www.netbeans.org"). These two are both mainly made for Java, but not limited to Java; they can also be used for C, C++ and other programming languages.

---

### Post by ankursethi on 2007-11-22
All right, here goes :

1. Code::Blocks is great.

2. Allegro still exists at Allegro.cc and is actively developed. I've used it in the past with C++ and IMHO it's easier to use than SDL for simple 2D games.

3. With Python+PyGame you will have an environment which is easy to code in, like QBasic, but can be taken to a much higher level than QBasic could be and follows all good principles of programming. For starters, Python is a language heavily used in the computing industry by giants such as Google. [http://www.python.org](http://www.python.org) and [http://www.diveintopython.org](http://www.diveintopython.org) and [http://www.pygame.org](http://www.pygame.org)

4. If Python doesn't click with you, you can always learn Ruby. Python and Ruby have different syntaxes, vastly different philisophies yet in terms of productivity (and fun :)) they virtually stand on the same ground. [http://www.poignantguide.net](http://www.poignantguide.net) and [http://ruby-lang.org](http://ruby-lang.org)

5. C/C++ is still around, and they still rock. It's pretty much impossible to phaze these two languages out.

6. Microsoft's C# is not all that bad, really. It runs under Linux with Mono and MonoDevelop is a very nice development environment to program in.

Programming in Windows == design effective solutions for clients to boost profitability.
Programming in Linux == have fun, kick ***, FTW!

---

### Post by LaRoza on 2007-11-22
> **nightlith said:**
> I'm not at all familiar with Python. My knowledge is comprised mainly of BASIC, C/C++, some (very limited) Pascal, and various web stuff (HTML, PHP, etc). Would it be easy to pick up and go, like syntax wise?


Python is extremely easy to learn, in fact, with prior programming experience, however slight, you should be able to write functional code as you learn.

I'm glad you liked the wiki, I do not spend enough time working on it, but I try.

---

### Post by Ichido on 2009-05-23
Thinking about trying REALbasic but I read a lot here about Python.
So I Synaptic-ed Python, but where is it?
How do I get Python?
Why is it 'Better' than REALbasic, if it is?
Any help would be appreciated.

---

### Post by Krupski on 2009-05-24
> **nightlith said:**
> I used to program a lot. Just dabbled mostly, and all of it self taught. All of it was done making "games". I started young, 7 or 8, making goofy BASIC apps on my mother's Vic20. Went on to DOS and it's QBASIC interpreter, discovered C/C++ ....

You sound a lot like me.

The ULTIMATE fun OS was Microware OS-9 Level 2 running on a TRS-80 Color Computer 3 and writing programs in assembler.

Next best thing is Linux and C / C++.

By the way, if you like BASIC (as I do), look into BWBASIC and BLASSIC.

BWBASIC is a very nice interpreter and BLASSIC is virtually a clone of GWBASIC (as far as how it works, syntax compatibility, etc..)

Programming in C, under Linux, is lots of fun... and these forums are an EXCELLENT place to get quick and VERY knowledgeable help.

Have fun! I know I am!  :)

-- Roger

---

### Post by cl333r on 2009-05-24
You revived a 2 years old thread.

---

### Post by Krupski on 2009-05-25
> **cl333r said:**
> You revived a 2 years old thread.

Not me. :)

The post above mine was 1 day ago. I admit though I didn't look at the dates.

---

### Post by jespdj on 2009-05-25
> **Ichido said:**
> Thinking about trying REALbasic but I read a lot here about Python.
So I Synaptic-ed Python, but where is it?
How do I get Python?
You already have Python. Open a terminal (Applications > Accessories > Terminal) and type in "python" <enter>. Voilà...

And please do not re-open two year old forum topics; just start your own, new topic.

---

### Post by Ichido on 2009-05-25
> **jespdj said:**
> You already have Python. Open a terminal (Applications > Accessories > Terminal) and type in "python" <enter>. Voilà...

And please do not re-open two year old forum topics; just start your own, new topic.

My apologies.
Just wanted some advice.
I'll post a new topic.

---

### Post by asbuntu on 2009-05-25
Note: I am attempting to delete this posting.  It was inappropriate due to age of the thread.  Can any moderator do this and/or explain how do do this?  Thank you.

> **CptPicard said:**
> ...the best IDEs you'll find for Java and C++...

Funny you should say that - I have not been successful getting a C++ IDE running in Ubuntu.  Tried Anjuta - could not get that going.  Tried Eclipse with CDT - still no go.

In all fairness, I'm sure there is a learning curve, and I do recall how much time I took to become a master on the MS side of the house.

It just seems that there is not a lot of truly useful starting information available for us C/C++ programmers.  Its as if you need knowledge to get knowledge, but if you don't have the knowledge, well, lets not go there quite yet.  :-)

I have spent what I thought was a reasonable effort to find out how to install Anjuta or Eclipse/CDT, so I don't think I can be accused of wanting to be spoon fed.

That said, does anyone have any recommendations for documentation, installation and use, alternative IDE's, etc.?  Thanks.

---

