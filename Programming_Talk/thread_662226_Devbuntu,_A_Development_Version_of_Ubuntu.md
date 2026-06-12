---
title: "Devbuntu, A Development Version of Ubuntu"
date: 2008-01-08
forum: Programming Talk
---

### Post by snickers295 on 2008-01-08
Hello, Me and  [Cheater]("http://ubuntuforums.org/member.php?u=148906") are working on a development version of ubuntu and want to know what tools and stuff you want in it.
this isn't just for c++, its for web, java, and others too.
we want stuff for those like editors, IDEs/APIs, compilers, etc.
this is the list of stuff we have planned to do so far:

> [INDENT] [COLOR=#000000]Remove all games (We need to figure out the exact packages name(s))[/COLOR]
[COLOR=#000000]> > > Remove ekiga softphone[/COLOR]
[COLOR=#000000]> > > Install eclipse[/COLOR]
[COLOR=#000000]> > > Install vlc (it plays nearly everything)[/COLOR]
[COLOR=#000000]> > > Install build-essential[/COLOR]
[COLOR=#000000]> > > Install vim-full,vim-gtk[/COLOR]
[COLOR=#000000]> > > Install emacs[/COLOR]
> > > Install build-essential [/INDENT]and we will be making a new repo too so if the package doesn't get in by default, you can find it there.

---

### Post by Wybiral on 2008-01-08
Priority #1, make it come with "build-essential" built in!

Personally, I use Gedit (the default text editor) for most of my development, though it would be handy to have the "gedit-plugins" package installed by default for developing.

Some other handy packages for developers would be SVN, CVS, and autotools.

---

### Post by lamalex on 2008-01-08
Geany!

---

### Post by CptPicard on 2008-01-08
Uh, why?

If someone is a developer, surely they will be able to apt-get whatever they prefer and need, and not need anything shoved down their throats.

Besides, there are so many development packages there that this could theoretically be huge.

---

### Post by johnwillis on 2008-01-08
Hiya :)

I would personally like to see MonoDevelop in it, along with Eclipse. 

And if you feel like dropping in NVU for web development that'd be helpful.

One more thing, please don't forget a nice FTP client, I use filezilla, but gFTP would be fine :)

Keep us all updated with your progress...

:)

---

### Post by Wybiral on 2008-01-08
> **CptPicard said:**
> Uh, why?

If someone is a developer, surely they will be able to apt-get whatever they prefer and need, and not need anything shoved down their throats.

Besides, there are so many development packages there that this could theoretically be huge.

Excellent point. Not to rain on any parades or anything, but someone seriously interested in a "developer" Linux would probably go for Gentoo or something. Perhaps instead an application to walk-through and install all of the common developer packages would be a good idea.

---

### Post by zveroboy on 2008-01-08
I had tried to install Eclipes with c/c++ plug-in and could only run it as admin (sudo).  Obviously, I did something wrong during installation.  However, I couldn't find any clear instructions.  So, having said that it would be nice to have Eclipse installed and configured.
Other handy multipurpose editor is gVim with Ruby plug-in.

Glade Interface Designer is very useful, as well.  



Just out of curiosity, why Gentoo is better for development?  What makes it so different from Ubuntu, as far as development is concerned?

---

### Post by CptPicard on 2008-01-08
> **Wybiral said:**
> someone seriously interested in a "developer" Linux would probably go for Gentoo or something.

Gentoo is just way too high-maintenance a distro for a work box... that's why I came over to Ubuntu. On your coding machine you want to get work done, so the distribution must be a reliable workhorse... but still, trying to predict whatever the user is going to be doing on it is a step too far; development boxen can be highly customised, and in this case, you mostly want a plain vanilla Linux to start with, *most importantly so that you're developing against something that you know is least common denominator, and that deviances from the norm are introduced intentionally*.

---

### Post by Acglaphotis on 2008-01-08
I've got an app that might be useful to you, look at my sig.

---

### Post by slavik on 2008-01-08
no need for a separate distro ... just make a meta-package :)

---

### Post by nhandler on 2008-01-08
> **slavik said:**
> no need for a separate distro ... just make a meta-package :)

We are also creating a custom repository. That repo will contain all of the apps included in Devbuntu. It will also include a a meta package. But no matter what form we distribute Devbuntu in, we still need a good selection of packages. So keep the suggestions coming.

---

### Post by CptPicard on 2008-01-08
> **Cheater said:**
> We are also creating a custom repository. That repo will contain all of the apps included in Devbuntu.

Even more duplicated work, that I doubt you guys will have the resilience to keep following through... and people will have to hack their sources.lists as first thing when they figure out that they need full Ubuntu anyway, when they can't find something they need in the custom repo. Where is the gain in this again then?

---

### Post by slavik on 2008-01-09
or you add both of them :)

apt has a dir called list.d which stores extra list files. :)

EDIT: for my suggestion (if libraries are allowed)
editor/IDE stuff (sorry to repeat myself):
-geany
-Anjuta
-Eclipse
-Glade

libraries (not just the C versions, but also for Python, Perl, etc):
-All openGL stuff (glut, glu, mesagl)
-GTK dev libraries
-SDL
-any extra GNU libraries

that's all I can up with right now. :)

---

### Post by Vox754 on 2008-01-09
> **snickers295 said:**
> Hello, Me and  [Cheater]("http://ubuntuforums.org/member.php?u=148906") are working on a development version of ubuntu and want to know what tools and stuff you want in it.

I just want to point out that this thread was started by the same guy who, a few days ago, [couldn't explain the meaning of "indentation" to save his life.](http://ubuntuforums.org/showthread.php?t=661086)

---

### Post by snickers295 on 2008-01-09
> **Vox754 said:**
> I just want to point out that this thread was started by the same guy who, a few days ago, [couldn't explain the meaning of "indentation" to save his life.]("http://ubuntuforums.org/showthread.php?t=661086")
that why cheater is help:)

---

### Post by Scarath on 2008-01-09
> **snickers295 said:**
> that why cheater is help:)

cheater == help 
nice 

so is devbuntu going to come with EVERY dev package pre-installed? 

will it come with prolog? thats only tiny u could squeeze that in lol

If not i can see why people are suggesting just getting normal ubuntu and getting the packages you want from it. 

Maybe just a devubuntu website would be helpful? a webo devoted to telling people about whats available for developing on ubuntu.

---

### Post by snickers295 on 2008-01-09
> **Scarath said:**
> cheater == help 
nice 

so is devbuntu going to come with EVERY dev package pre-installed? 

will it come with prolog? thats only tiny u could squeeze that in lol

If not i can see why people are suggesting just getting normal ubuntu and getting the packages you want from it. 

Maybe just a devubuntu website would be helpful? a webo devoted to telling people about whats available for developing on ubuntu.
Devbuntu is going to have many packages and to get a package in you have to suggest it here so we know what everyone wants.

---

### Post by Wybiral on 2008-01-09
I think the problem is that I would want the Python/C/C++/Assembly stuff, but I wouldn't want: eclipse, 1000 PHP and Perl modules, Qt development files, etc... Each developer is going to have packages that they want, and some they don't. The only universal one would probably be "build-essential".

This is why I think a developers "installer" might be interesting. Like easyubuntu / automatix for development files (where you have a nice collection and an easy walkthrough that you can select/deselect from), but a full-on distribution seems excessive.

---

### Post by achron on 2008-01-09
I vote for a full Ruby on Rails setup also...

ruby
gems
mysql
etc...

---

### Post by CptPicard on 2008-01-09
> **snickers295 said:**
> Devbuntu is going to have many packages and to get a package in you have to suggest it here so we know what everyone wants.

Why would I go through the trouble of getting your "approval" for whtatever I need, if I can just simply apt-get install anything I want using a single command? The *first* part of the education of a programmer is to get to know the platform, and even more so in Linux where apps tend to "hug the OS" a bit more than somewhere else.

Again, this one sums it up quite well for me...

[IMG]http://icanhascheezburger.files.wordpress.com/2007/08/skeptical-cat-is-fraught-with-skepticism.jpg[/IMG]

---

### Post by LaRoza on 2008-01-09
I usually just install things separately, but a live cd with all the tools would be pretty cool.

Some of what I install, that wasn't mentioned already:

* gcl (GNU Common Lisp)
* ghc (Haskell)
* hugs (Haskell)
* nasm 
* gfortran, g77
* sun-java6-jdk
* dmc 
* tcl

---

### Post by snickers295 on 2008-01-09
> **CptPicard said:**
> Why would I go through the trouble of getting your "approval" for whtatever I need, if I can just simply apt-get install anything I want using a single command? The *first* part of the education of a programmer is to get to know the platform, and even more so in Linux where apps tend to "hug the OS" a bit more than somewhere else.

Again, this one sums it up quite well for me...


we will add as many things as we can so if you want something why don't you stop complaining and say what you want to go in it?

---

### Post by nhandler on 2008-01-09
I think some people aren't quite understanding the full reason for creating devbuntu. Devbuntu is being designed to be used as a live cd. Like most people have already said, a true developer would customize their computer the way they want. However, what happens when the dev isn't at their computer? Maybe they are at a friend's house, library, or internet cafe. They obviously aren't going to install Ubuntu. They also probably don't want to use Windows. That is where Devbuntu comes in. Most people don't like spending time installing packages. Also, a lot of dev related packages are somewhat large. By putting them on a cd, the developer will be able to work on their projects from any computer only having to install a minimal amount (if any) of packages.

@CptPicard: This project is by no means meant to replace installing a normal Ubuntu installation on the computer and getting familiar with it. In fact, I would almost advise beginners not to run Devbuntu until they learn more about Ubuntu. Devbuntu is more of a "tool" than a replacement for Ubuntu (at least for now). We are also not "approving" packages. We are simply asking for suggestions for packages to include. This is to make it easier for you. You are more than welcome to apt-get every package you use. You are also free to not use Devbuntu. But if you do use a dev related package, please submit it to this thread. That way, other people can benefit from the package as well.

@Wybiral: When running a live cd, most people won't care if there are extra packages included. They will either use them or not use them. Since it is a live cd, the packages won't be taking up room on the hard drive. As a result, there is no reason that anyone should care about having them (unless they are obsessed about having a clean Applications menu). The automatix-like program also sounds interesting. I'll keep that in mind for later. But no matter what form we release Debuntu in, it still needs a large package list.

@Vox754: Bringing up that thread was totally uncalled for. The only way to learn is to practice and make mistakes. I'm sure you weren't born writing perfect code. Also, every script serves as practice. These forums were designed as a friendly community. Your post was neither friendly or serving any true purpose. Posts like that deserve to be deleted.

I have been compiling a list of all packages that have currently been submitted. Currently, we have over 20 unique suggestions. Keep them coming. Also, there is no harm in recommending a package that has already been suggested (it tells us that more people want it), but also try to make unique suggestions so we can include more packages.

---

### Post by snickers295 on 2008-01-09
> **Cheater said:**
> 
@Vox754: Bringing up that thread was totally uncalled for. The only way to learn is to practice and make mistakes. I'm sure you weren't born writing perfect code. Also, every script serves as practice. These forums were designed as a friendly community. Your post was neither friendly or serving any true purpose. Posts like that deserve to be deleted.

i thought that that was funny him bringing that up.

---

### Post by CptPicard on 2008-01-09
> **Cheater said:**
> Maybe they are at a friend's house, library, or internet cafe.

At my friend's house I socialize with my friend, at the library I read or borrow or return books, and at a cafe I drink coffee.

I develop at home in my home office on my workstation which is specifically adapted for purpose :) An alternative is getting a laptop, but coding on them sucks most of the time.

---

### Post by LaRoza on 2008-01-09
> **Cheater said:**
> 
@Vox754: Bringing up that thread was totally uncalled for. The only way to learn is to practice and make mistakes. I'm sure you weren't born writing perfect code. Also, every script serves as practice. These forums were designed as a friendly community. Your post was neither friendly or serving any true purpose. Posts like that deserve to be deleted.


If you feel that way about a post, report it.

---

### Post by Wybiral on 2008-01-09
> **Cheater said:**
> @Wybiral: When running a live cd, most people won't care if there are extra packages included. They will either use them or not use them. Since it is a live cd, the packages won't be taking up room on the hard drive. As a result, there is no reason that anyone should care about having them (unless they are obsessed about having a clean Applications menu). The automatix-like program also sounds interesting. I'll keep that in mind for later. But no matter what form we release Debuntu in, it still needs a large package list.

OK, makes sense. I guess my only problem then is that I don't get most of my development files from a repository. I've never been able to rely on the repositories to have the most updated release (they almost never do), so I typically end up having to build a large portion of my development requirements.

But, to help you with your list anyway: svn, cvs, autotools, gedit-plugins, nasm, swig, pyrex (the current package is crap, I would need the most recent build), numpy, simpy, scipy, pyode, pyopengl, pygame, python-feedparser (universal feed parser), python-lxml, SDL dev files (including all of the extensions: ttf, image, gfx, etc), OpenGL dev files (GL and GLU headers), ghex (gnome hex editor), boost library (everything), cherrypy, turbogears, python-beautifulsoup, python-goopy

Those are the ones I use (that I can think of) that aren't preinstalled. There may be more...

---

### Post by nhandler on 2008-01-09
> **CptPicard said:**
> At my friend's house I socialize with my friend, at the library I read or borrow or return books, and at a cafe I drink coffee.

I develop at home in my home office on my workstation which is specifically adapted for purpose :) An alternative is getting a laptop, but coding on them sucks most of the time.

Well, think about other people besides yourself. At my library, there are always people on the computers. This could be because they don't have one at home (or one with internet), they like the quiet environment, or a handful of other reasons. On vacation, many people go to an internet cafe or a similar place to get on a computer. And I'm sure you have used a computer at your friend's house at least once. If none of these things apply to you, then don't use Devbuntu. However, I'm sure these apply to at least 1 person on these forums. And for that person, Devbuntu will help them out.

@LaRoza: I thought about reporting it, but I think I'll let it stay. That way, everyone can see the post he made.

@Wybiral: I know the repos aren't always up-to-date. That is one reason we will be creating a custom repo. Hopefully, this repo will contain more recent versions of dev related packages. Otherwise, I could always add the most recent version of the package from the developer's site to the live cd (but this wouldn't allow it to get updates from the repo).

---

### Post by Wybiral on 2008-01-09
> **Cheater said:**
> @Wybiral: I know the repos aren't always up-to-date. That is one reason we will be creating a custom repo. Hopefully, this repo will contain more recent versions of dev related packages. Otherwise, I could always add the most recent version of the package from the developer's site to the live cd (but this wouldn't allow it to get updates from the repo).

It's not just that the repositories don't have updated packages, most of the project owners don't build a debian package for every change they make. I personally find myself using SVN to update my development tools more than the repository updates. They're just way too far behind for some things. I'm not trying to down your project, just explaining why it's not very applicable to me.

---

### Post by nhandler on 2008-01-09
> **Wybiral said:**
> It's not just that the repositories don't have updated packages, most of the project owners don't build a debian package for every change they make. I personally find myself using SVN to update my development tools more than the repository updates. They're just way too far behind for some things. I'm not trying to down your project, just explaining why it's not very applicable to me.

Well, I think you are right. If you MUST have the latest version of packages that come from sites without debs, then Debuntu may not be for you. Just keep in mind, if you are at a computer other than your own that is running Windows (like most are), you (most likely) won't be able to install the newest version. If you have a normal Ubuntu live cd, you could download the package and compile it. You could also do the same with Debuntu. The only difference is, Debuntu will have a lot of other tools you might need (Take SVN for instance). So even if it does not provide the exact thing you need, it still can help.

---

### Post by CptPicard on 2008-01-09
How is one supposed to be able to do that kind of package hacking on a LiveCD? After all, LiveCD filesystems are read-only -- are you suggesting we compile and make all the necessary changes into some sort of a ramdisk?

I can understand a LiveCD for your general browsing etc needs, but development... hmmm. Just setting up your environment is going to take more time than you usually spend coding on your friend's/library's/cafe's computer...

---

### Post by Acglaphotis on 2008-01-09
Actually, they can be edited by mounting them in a squashfs loop partition, you must of course copy the livecd on the computer.

---

### Post by pmasiar on 2008-01-09
If you guys want to learn something about packaging a distro, why you don't join MOTU team instead of creating distro without real business reason, as a training exercise?

In MOTU, your effort be guided to something useful. Devbuntu looks like rather contrived idea - developing from a liveCD, when away from my main computer makes little sense to me.

Of course do as you wish, you are not hurting anyone and wasting only your own time, but you asked about opinion/feedback, so don't be upset if someone gives you one :-)

---

### Post by Wybiral on 2008-01-09
> **Cheater said:**
> Well, I think you are right. If you MUST have the latest version of packages that come from sites without debs, then Debuntu may not be for you. Just keep in mind, if you are at a computer other than your own that is running Windows (like most are), you (most likely) won't be able to install the newest version. If you have a normal Ubuntu live cd, you could download the package and compile it. You could also do the same with Debuntu. The only difference is, Debuntu will have a lot of other tools you might need (Take SVN for instance). So even if it does not provide the exact thing you need, it still can help.

In a number of situations, I MUST have them (PyRex is a great example, but there are others) There are SVN clients for Windows too, so for most projects I could build them on Windows too. But I don't use Windows, and as others have mentioned, I don't develop while I'm traveling. Developing isn't like checking your email, it's something you sit down and do. I'm not going to be visiting family for some holiday and say "let me just implement that enhancement real quick", it would take too much time.

---

### Post by Vox754 on 2008-01-09
> **Cheater said:**
> I think some people aren't quite understanding the full reason for creating devbuntu.

...[explanation]...

@Vox754: Bringing up that thread was totally uncalled for. The only way to learn is to practice and make mistakes. I'm sure you weren't born writing perfect code. Also, every script serves as practice. These forums were designed as a friendly community. **Your post was neither friendly or serving any true purpose.** Posts like that deserve to be deleted.


My post was not friendly, but it had a purpose.

If you read this section of the forums during the past year you know that sometimes guys who have no programming knowledge want to create the next big application out of thin air.
(CptPicard: no more jokes on He-who-must-not-be-named, please.)

Yes, this forum is meant to be friendly, but programmers (or should I say, scientists) implicitly live by another code of conduct which is "show us the code or shut up", meaning that you need to prove you can pull off your project before you can get others' attention.

Our criticism is meant only to help you realize the limitations of your ideas.

Actually, I now have faith in this project since you have shown that you have a plan by answering different questions.

And you know what, it is a good idea. In the past year I did exactly this.
I did some programming in my home, then carried my source files and documentation references with me in a USB stick to school and coded happily for a few hours in Kate with a Knoppix Live CD.
Knoppix can be loaded entirely to RAM, so I did just that (it makes everything faster).
[LIST=1]
[*]Load the full CD to RAM (1 GB)
[*]Work with your sources in your external media
[*]When you are done, turn off the PC
[*]The entire Linux environment disappears without leaving a trace in the precious newly acquired hardware with Vista(TM).
[/LIST]

This may sound a little too complicated but it worked okay for me.
Some programming environments or distributions like ActivePython from ActiveState can be installed anywhere in two minutes. So you can just install it every time, on RAM of course. (Mmm... maybe this works best for dynamic scripting languages rather than static compiled ones.)

Hopefully, this has shown you that I'm not a bad person.
And I liked snickers295 attitude. Always take things with a little humor.

Programmers always need to have sense of humor. So, although I wasn't born writing perfect code, I recently revisited some of my old C programs written for Windows and realized I used a pretty weird indent style; kind of like indenting the braces but unindenting the block of code inside them! Ha ha! The ironic part is that I cannot prove this since I deleted the sources.

---

### Post by pmasiar on 2008-01-09
What will be way cooler than liveCD will be a distro running from Flash USB stick. I bet there are guides all over the net how to put it together, you just need to collect them and make sure it works for everyone. 

And you heard it here first: USBuntu :-)

---

### Post by nhandler on 2008-01-09
@pmasiar: There are guides to install Ubuntu onto a flash drive. However, those drives aren't designed to handle the strain of an operating system, so you end up killing the drive. But once we release an iso, you can install it on a cd or follow one of those guides to install it on a flash drive.

@Vox754: Thanks for clarifying. I now see where you are coming from. It just is different seeing one of those posts directed at someone you are working with vs. directed at an unknown person. I'm sorry I reacted the way I did. And thanks for having faith in the project.

@pmasiar: I have tried packaging debs (and fixing bugs). Look up my launchpad account (Linked to in my profile). The main reason I stopped was that I wasn't enjoying it. I would much rather contribute to the community in a way that I enjoy.

@CptPicard: I'm having a little difficulty understanding your question. Are you asking how they will make changes (Like installing programs and saving files) to the disk while running it? If so, then the answer is simple. They can either attach a flash drive to the computer, ssh/ftp/upload through apache server the files. They can also mount one of the computer's internal hds.
If you are asking how we are planning to make changes to the normal Ubuntu iso, then look up a program called Reconstructor.

---

### Post by pmasiar on 2008-01-10
> I have tried packaging debs (and fixing bugs). 
If you started thread with this, you would get completely different response.

Every week a wannabe comes and claims something audacious (last time one guy claimed to buy out Novel :-) ), so we are cautious about that. Obvously you do have skills to succeed.

Bon voyage, and have fun trying!

---

### Post by nhandler on 2008-01-10
> **pmasiar said:**
> If you started thread with this, you would get completely different response.

Every week a wannabe comes and claims something audacious (last time one guy claimed to buy out Novel :-) ), so we are cautious about that. Obvously you do have skills to succeed.

Bon voyage, and have fun trying!

Thank you. But learn from this experience, never underestimate anyone. They might just turn out surprising you. :)

---

### Post by ThinkBuntu on 2008-01-10
Note that I haven't read other posts; these are just my own suggestions:

[LIST=1]
[*]~/Sites/ working with Apache. Mac OS has this, so [http://localhost/~myusername/](http://localhost/~myusername/) points to that folder in my home directory. Nice to not have to track down /var/www
[*]I'd recommend not going with any sort of Eclipse...try to use native tools as much as possible, but include an Ubuntu Eclipse guide on your project's homepage
[*]RubyGems installed with Rails and dependencies
[*]Make sure that there's some editor for every language, and all major compilers. Granted, Vim and Emacs work with all languages, but I'm referring to GUI editors. Maybe GEdit covers all? But I doubt that.
[*]CVS, SVN, with Desktop integration and graphical clients for each
[*]Find a good FTP program, or write your own. My experience was that FTP (except from the Terminal) was horrendous in Linux when moving more than a handful of files, which was a deal-breaker for deployments. I love Transmit on my Mac :^)
[/LIST]

That should get you started.

---

### Post by ThinkBuntu on 2008-01-10
Also, one thing that would be great is a lightweight "Help" style app, or integration of GNOME's Help browser, with programming tutorials. I'd recommend including solid documentation and some good tutorials for these languages:

Web Design (JS is programming, I guess)
[LIST]
[*]XHTML
[*]XML, XSLT
[*]CSS
[*]JavaScript
[/LIST]
Programming
[LIST]
[*]C
[*]C++
[*]MySQL
[*]PHP, maybe CakePHP too
[*]Perl
[*]Ruby, maybe Rails too
[*]Python, maybe Django too
[*]Common Lisp and/or Scheme
[*]Java
[/LIST]

---

### Post by ThinkBuntu on 2008-01-10
Oh, and include MySQL, PostgreSQL, and phpMyAdmin at the very least. These services (user chooses which DB), as well as Apache, should start on boot.

---

### Post by nhandler on 2008-01-10
> **ThinkBuntu said:**
> Also, one thing that would be great is a lightweight "Help" style app, or integration of GNOME's Help browser, with programming tutorials. I'd recommend including solid documentation and some good tutorials for these languages:
[SNIP]


This is an interesting idea. Do you know if there is any documentation on editing the help app? If not, I think we will have to stick to html docs.

As for your ideas, I will look into them. They sound very interesting. Thank you for contributing.

---

### Post by ThinkBuntu on 2008-01-10
I imagine there's some API for providing Help for your application that the browser understands, and I'd expect it to be flexible enough to be used as a code reference or guide if it's designed to afford developers customization of their Help docs.

---

### Post by pmasiar on 2008-01-10
> **Cheater said:**
> Thank you. But learn from this experience, never underestimate anyone. They might just turn out surprising you. :)

Nah. Main law of universe says that 90% of **everything** is crap, it is up to you to prove you have the goods and are in top  10% :-)

---

### Post by ThinkBuntu on 2008-01-10
> **pmasiar said:**
> Nah. Main law of universe says that 90% of **everything** is crap, it is up to you to prove you have the goods and are in top  10% :-)
A bit cynical, although I'm not saying you're wrong. Just curious though, what's your professional experience? As general or specific as you like.

---

### Post by CptPicard on 2008-01-11
> **ThinkBuntu said:**
> Just curious though, what's your professional experience?

:lolflag:  (considering who you're asking...)

---

### Post by pmasiar on 2008-01-11
> **ThinkBuntu said:**
> A bit cynical, although I'm not saying you're wrong.

Of course I am not. Universal laws are valid regardless if you like them or not :-)

[http://en.wikipedia.org/wiki/Sturgeons_law](http://en.wikipedia.org/wiki/Sturgeons_law)

>  Just curious though, what's your professional experience? As general or specific as you like.

I was trying to create a consistent way for forum regulars to present experience (so readers can see if it is relevant to their questions), but "powers that be" disliked it, at it earned me permanent infraction points. [thread](http://ubuntuforums.org/showpost.php?p=3669414&postcount=2)

Given that the same question is popping back again and again, if someone else (who can afford possible infractions) reformulates it and starts it, I will support it, but I cannot afford the risk of starting it myself. :-/

BTW I do like current "thanks" karma, it did not existed when I started mentioned thread.

---

