---
title: "clisp and ncurses"
date: 2009-05-26
forum: Programming Talk
---

### Post by sehku on 2009-05-26
I have recently discovered clisp, a wonderful and elegant implementation of the common lisp language, and have begun using lisp for just about everything I can.  

It is my intent to use clisp and ncurses to make a simple command line IRC client.  However, some stumbling blocks have been noticed.  

Firstly, the clisp ncurses library, while apparently able to be installed, is apparently very difficult to install, requiring compiling and packages from many different sources.  Does anyone have a good idea as to how to get ncurses to work in lisp under Ubuntu? 

Secondly, multithreading.  According to some sources I've found, clisp can't be multithreaded.  Being the widely acknowledged GNU port, I find it hard to believe there is not some way to at least mimic the function of multithreading.  (I need this so I have a thread for user input and a thread for socket-reading).  

Other implementations aren't gonna cut it either, I find clisp to be by far the best, and will find it very hard to use something else (I've tried sbcl, ecl, etc.).  Things like paren matching, history, and environmental variables like *args* make clisp my favorite.  

Also, I don't know emacs, and would very much like to not be dependent on slime or some other such interface.  Partially it's for portability concerns, partially it's just my preference.

---

### Post by soltanis on 2009-05-26
Oh dammit, you don't like sbcl. I was going to recommend that to you.

I used clisp, didn't like it because it was incompatible with the book I was using (it was written for CMU CL, I used sbcl).

I don't know enough about clisp to tell you how to install those libraries- strike that, use asdf. I'm sure clisp supports the "another system definition facility" (the cpan of common lisp, in other words), and that should install all the stuff for you with minimal hassle.

Other than that, for multithreading, there are probably libraries for supporting green threads in clisp, but to be honest with you, finding stuff for clisp is difficult (most of the common lisp community goes with CMUCL, in my experience). GNU's port of lisp, in my biased opinion, is suboptimal.

But good luck with Common Lisp, it's probably the best programming language choice you've ever made, you won't regret it. Happy hacking.

Oh, you might want to look here for libraries:
[http://cliki.net/](http://cliki.net/) - CL wiki

---

### Post by CptPicard on 2009-05-27
I hope you're not using something like a raw REPL and a text editor... I get that kind of impression. I mean, you really are supposed to use a proper environment/editor that are integrated with the REPL with all the associated niceties. This is why SLIME is great; I would never imagine *not* using SBCL simply because it's CLI side would be inferior, say, to something else :)

---

### Post by sehku on 2009-05-27
First of all, I am using nano to edit text files and basically piping them through the REPL by passing the file as an argument to clisp.  

Secondly, asdf-install seems to be a good utility, but I have never used it before.  I installed the cl-asdf package, but will require more instruction to get it working.  

I should mention that I don't like IDEs, they seem bloated and unnecessary.  And I certainly don't like features and support being IDE-specific, it encourages a lack of portability and a more difficult ground for testing software.  I've been fine with nano and CLI for C, C++, and php, and see no reason why lisp would be different.  

Also, as to clisp not being compatible with literature on lisp and such, I should mention that I have been learning everything as I go, and furthermore, I have no formal education in lisp, or programming at all, for that matter, so you'll have to forgive my lack of familiarity with the standard way of doing things.  

Emacs: I am not opposed to it, but it has a sharp learning curve and nano has been quite sufficient for everything I've needed thus far.  As a substitution to an IDE, it incurs the same issues that I've had with IDEs in general (see above)

So, the next logical step is some sort of syntax or way to install packages using asdf.  

(also, thank you for the prompt replies)

---

### Post by CptPicard on 2009-05-27
> **sehku said:**
> First of all, I am using nano to edit text files and basically piping them through the REPL by passing the file as an argument to clisp.

Yeah, I thought you were doing it wrong. You need to get into the lisp way of doing things more :)

Lisps are not meant to be used as the kind of interpreter or compiler most people are used to. You are supposed to work inside a live so-called lisp image, and for that, you need to be working at the same REPL instead of reconstituting the image at each pass. Trust me, it's a great way to build stuff to be editing things that are already there.

This of course requires some kind of external editor support, as the basic REPL essentially just provides the basic I/O and it really is not meant for actually any heavier work.

>  I've been fine with nano and CLI for C, C++, and php, and see no reason why lisp would be different.

You don't see it yet because you've been trying to use lisp like you could use C, C++... :) it has been meant to work differently from the start.

> 
Emacs: I am not opposed to it, but it has a sharp learning curve and nano has been quite sufficient for everything I've needed thus far.  As a substitution to an IDE, it incurs the same issues that I've had with IDEs in general (see above)


True, it has learning curve, that's the bad part. There is an Eclipse plugin called cusp for something more mainstream. I am not sure what you mean by the same issues... I get the feeling you're beginner enough not to really be able to judge. SLIME does not add anything to your project that shouldn't be there so in that sense the bloat argument is completely false. Instead it gives you a very powerful working environment to alter the lisp image you're in. 

In general I only agree with your IDE argument up to the point of coder understanding the project structure and how to use the tools manually if need be... otherwise, always make use of a tool if you've got one. But that's another discussion. :)

In any case, I would rather have nails pulled than do Lisp without SLIME the proper way, so... take it from a lisper.. ;)

---

### Post by sehku on 2009-05-27
the bloat is in reference to the IDE itself, it gives features that I will never use.  The slime thing is a portability and cross-compatibility concern.  

I have not used eclipse, and have heard almost nothing about it.  

However, I must point out that a development environment is the the focus of this thread.  I have been happy enough with what I'm using now, the reason it was brought up is because a number of tutorials, etc. that I've been searching through seem to take it as a give that slime is installed, and use those features.  I feel that I should be able to do everything I need to without required slime, and would prefer to avoid it if at all possible.  

I have been looking into asdf-install, and getting asdf-install itself installed seems the paramount concern.  I have got some information on it, but it seems out of sync.  My guess would be that they updated the download and not the tutorial, giving differences in filename, etc.  I cannot seem to get that to work.  

[http://common-lisp.net/project/asdf-install/tutorial/setup.html](http://common-lisp.net/project/asdf-install/tutorial/setup.html)

The ubuntu package alone does not seem to work.  Evidently "asdf" is different than "asdf-install," and there is no "cl-asdf-install" or similar package.  (I have installed common-lisp-controller, based on an apt-cache search, but it does not seem to work, either)

Any help is greatly appreciated.

---

### Post by jimi_hendrix on 2009-05-27
> **CptPicard said:**
> I hope you're not using something like a raw REPL and a text editor... I get that kind of impression. I mean, you really are supposed to use a proper environment/editor that are integrated with the REPL with all the associated niceties. This is why SLIME is great; I would never imagine *not* using SBCL simply because it's CLI side would be inferior, say, to something else :)

install emacs and slime, even if you are a vim user...it saves your life in lisp

then get sbcl, the slime environment will save you from the bad sbcl repl

i would look at bordeaux threads for threading and asdf-install for installing the libs (its a package manager in sbcl for this stuff)

if you wont use emacs, at least use eclipse and the cusp plugin, they are nice too

---

### Post by CptPicard on 2009-05-27
> **sehku said:**
> the bloat is in reference to the IDE itself, it gives features that I will never use.

You *never* intend to move beyond using nano to edit your code and piping to clisp? Nano is an awfully basic editor too, mind you, and if you're relying on the actual lisp implementation to give you stuff like parens matching and such, instead of editor... gawd.

> The slime thing is a portability and cross-compatibility concern.

How? Why? What sort of portability are you looking for? What kind of cross-compatibility? Are you going to work on the code on some other platform except Linux? Why would SLIME be an issue in deployment in any case?

You are having concerns that are not concerns, IMO.

> that I've been searching through seem to take it as a give that slime is installed, and use those features.  I feel that I should be able to do everything I need to without required slime, and would prefer to avoid it if at all possible.  

There is a very good reason why this is so. You may feel that you "should" be able to do stuff without slime, but I don't think that feeling is founded on much. A lot of other people have figured out that it is a very good way to do things, thus, they write their tutorials using that setup.

A quick comment from IRC from a Lisp god as to "why  lisp should not be different from C/C++...":

> 
<lnostdal> then why did the original, authentic hard-*** lisp gods create the lisp machines with built in custom IDEs tailored for doing the lisp thing?

> 
I have been looking into asdf-install, and getting asdf-install itself installed seems the paramount concern.  I have got some information on it, but it seems out of sync.

Sorry I can't help with this one. :) It's because I use the SBCL+SLIME combination myself, and it works a charm...

---

### Post by sehku on 2009-05-27
An editor is not the functionality of a language.  There is no reason for a language not to have its fullest ability pending a choice of editor.  

And yes, I intend to run this on any platform I can, as much as I'd like to, I don't live in an all-linux world, and there is no reason for a program not to be cross-compatible.  I intend to use lisp on any platform it will run on, and certainly don't want to impose an OS-based constraint when there is absolutely no reason to.  

And since you are attempting to sell me on emacs (an editor which seems very difficult, and provides no obvious advantage other than a lot of people already use it) and slime, perhaps instead of saying why I should use it and nothing more, you could direct me to another resource where I could learn it and try it.  It's not that I'm opposed to the idea inherently, so much as there's no reason for me to.  Yes, slime is supposedly very nice, but there is no reason to constrain myself to it, and certainly no reason to make the assumption that it is always the best idea.  I will give it a fair chance, but to be honest, if it won't run on all platforms, it is not useful to me at all.  

Other than the ncurses and multithreading libraries, what I have has been working very well for me.  I've written an IRC bot in it, and done a number of project euler projects, and until I needed ncurses, I have not had the slightest issue.  

> You never intend to move beyond using nano to edit your code and piping to clisp? Nano is an awfully basic editor too, mind you, and if you're relying on the actual lisp implementation to give you stuff like parens matching and such, instead of editor... gawd.

It's... an editor.  That's all it needs to be.  It's efficient and useful, and it has everything I need.  Paren matching is not an issue if you keep simple track of what you are doing.  It's no more confusing than semicolons in any other language.  Yeah, sure, every once in a while you forget one, but 99% it's not an issue, and even if you do forget one, you go back, add it, and it works fine (it's blatantly obvious where it was forgotten).  

I should at this point mention that the REPL is only manipulated for testing.  I bring it up when I want to make sure I get the arguments in the right order, or when I am unclear of the return values of functions in certain cases.  It's a simple, open it, see what happens, close it.  I don't do my editing in the REPL, but it's nice to be able to have, say, a history, so you can go back and try another set of arguments or another syntax.  This is why it's nice to have a functional REPL.  

No, I really don't see using anything other than nano.  It's a piece of software that does what it's supposed do, and nothing it doesn't need to.  It seems that a lot of people who hate it have just assumed it's too minimalist to be useful.  It's kind of like the mindset of people who use compiz and GNOME.  Is it kind of neat looking? sure.  Does it provide any real advantage over openbox?  Not in terms of work efficiency.  Does it provide disadvantages? yes, it kills my battery life.  

Now, the concerns may be less pronounced, but anything "more functional" than nano is bloat as far as I'm concerned.  

I really came here looking for help in one thing: installing some libraries with the ultimate goal of making an ncurses irc client.  The only helpful advice I've received on that front is to use asdf-install for the ncurses library, and no one seems to be able to help me with that, but are quite content criticizing my entire preference to how I work.  

To put this in perspective: it's as if I asked how to install wine, and you told me to boot windows.  Doesn't really solve the problem, does it?

---

### Post by soltanis on 2009-05-28
You don't NEED emacs/slime to do Lisp. What the lispers above do is suffer from an addiction to it.

Slime is a particularly good tool if you feel like putting up with it for a while, but it's just a tool for getting the Lisp job done. The Slime/SBCL combination is not a necessity to code Common Lisp at all.

Being of the same mind as you, i.e. I hate bloated editors/hard to install bull****, I have found that vim works pretty well with smart/autoindent/parens matching on and syntax highlighting turned off (though it does have a mode for CL); also GEdit with highlighting set to Scheme (close enough for me) and with parens matching on.

The most important thing to Lisp is the parens matching (it will save you) and proper indenting (again, vim manages it, GEdit doesn't, hooray for manual indents). It doesn't hurt your productivity at all if you want to use a light editor and mess around with the REPL in a Lisp image.

I mean, that all you're doing with slime anyway; it's just that the editor and REPL are put in one place with a bunch of bells and whistles.

One thing that you do need to be careful about, though, is treating Lisp like you treat other languages. Trust me, Lisp is not your father's programming language. It is a totally different beast; and the sooner you learn the Lisp way, the happier you will be (in Lisp and probably in other languages too).

EDIT.

Now back to your problem. CL-Ncurses is an asdf installable package. So what you want to do is this:

```

(require :asdf-install)
(asdf-install:install :cl-ncurses)

```

Woot.

---

### Post by sujoy on 2009-05-28
hey i totally understand you are enjoying nano. which is fine.

but regarding the cross-compatibility issue, both slime and emacs are available for win,*nix, and os x. so it is cross-compatible.

as for installing curses, well follow this link
[http://common-lisp.net/project/cl-ncurses/](http://common-lisp.net/project/cl-ncurses/)

as for asdf, for clisp you need to install asdf which ought to be there in your package manager itself, hence i had no problem installing it in my clisp days. and it comes bundled with sbcl, so i dont need to install it now anymore.

---

### Post by CptPicard on 2009-05-28
Hmmh. Not the first noob I meet here who "doesn't see" why things can be different because he hasn't tried anything else, and hence argues from a position of ignorance. It is a case of [blubness]("http://www.paulgraham.com/avg.html"). Only after exposure to new concepts you will appreciate enough to be able to actually "see" what they are good for.

For example, the cross-platformness argument regarding Emacs has no merit. I honestly don't understand why you would imagine that using Emacs for development would impose any constraints on on cross-platformness of your code. It is rather obvious you do not understand that you don't actually *run* lisp from Emacs, but what the heck...

There is no way for you to ever be able to develop anything, anywhere, if you set yourself this kind of goals.

The core point is here:

> **soltanis said:**
> One thing that you do need to be careful 
about, though, is treating Lisp like you treat other languages. Trust me, Lisp is not your father's programming language. It is a totally different beast; and the sooner you learn the Lisp way, the happier you will be (in Lisp and probably in other languages too).


This particular language is one that *should* have a good environment for development. Please read again the stuff about developing on a proper live REPL with proper inspection tools and benefits of integrated text editors and all that. Then you need to understand before you argue hard that you "see no need" for it but instead pipe your code from nano. *Please*. This is not just about editing convenience, it's about how to do things the way lisp does things.

And no, this is not an emacs-selling exercise at all. The fact just remains that it is the best tool at the moment. I'd love to hear of alternatives.

---

### Post by sehku on 2009-05-28
You don't have to code my way if you don't want to, mind you.  

```
[3]> (require :asdf-install)

*** - LOAD: A file with name ASDF-INSTALL does not exist
The following restarts are available:
ABORT          :R1      Abort main loop
Break 1 [4]> 

```

that doesn't look like the appropriate way, or I missed a pre-requisite somewhere.  Please explain anything you did beforehand (I'm sure I need a download or something to get this working).  Also, if there's a download, what directory would it go in so it's recognized by (require)?

---

### Post by CptPicard on 2009-05-28
> **sehku said:**
> You don't have to code my way if you don't want to, mind you.

Sure, and you will find in due time that nobody else does, either... and I am willing to make a bet that when time is ripe, neither will you. You will eventually find out that trying to force lisp being your regular edit-compile-run-debug style language makes you miss out on most of how it actually works and helps you build your stuff incrementally, and totally "live". :)  

I am not 100% certain of how the process you've built for yourself works, but I am assuming that you're just reloading the entire REPL all the time... if you're not, it may be more sane, but anyway, the incremental-construction model is a core Lisp concept, not some coding-style-preference I may have just picked up. If you don't do that, you quite simply are not understanding a lot of the ideas behind Lisp, and that is very objective.

---

### Post by soltanis on 2009-05-28
asdf-install supposedly does all the downloading and stuff for you. All you have to do is tell it what to install.

It looks like you don't have it installed for clisp, which means you need to install it first.

Take a look at cliki, it should have instructions there.

---

### Post by jimi_hendrix on 2009-05-28
for the record, it is installed by default in sbcl

---

### Post by nvteighen on 2009-05-29
Ok, a bit of common sense for the OP.

Lisp without a decent text editor is a pain. I don't know what kind of code you're writting, but if you, e.g., force yourself to use pure-functional Lisp (no setf's, to put it easy), you'll be easily nesting +9 levels of parens... Try to do that without paren matching and you'll lose a lot of time trying to debug what paren is unmatched.

And I wonder how you indent your Lisp code. Indentation in Lisp is radically different from ALGOL-like languages, where one tab means "one level below"... In Lisp you allign stuff vertically or you'll miss stuff very easily. A Lisp-aware editor will do this for you automatically.

I don't use SLIME, as I use Scheme not Common Lisp (so, plain emacs is all I need), but please migrate from nano. There are **several** alternatives: Gedit (surprised?), Kate, Eclipse, vim, emacs, etc.

Of course, you're free to choose your way to code, but at least consider this advice.

---

