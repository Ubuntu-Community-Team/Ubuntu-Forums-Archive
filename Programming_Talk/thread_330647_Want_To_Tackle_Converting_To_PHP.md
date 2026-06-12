---
title: "Want To Tackle Converting To PHP?"
date: 2007-01-03
forum: Programming Talk
---

### Post by SuperMike on 2007-01-03
I wrote the first menu demo for UST (Ultimate System Tool), which is designed mostly for Ubuntu Server in console-only mode. It's a project to provide a kind of simplistic yast-like experience for managing Debian-based Linuxes only from the command line. I threw it together rapidly in Bash. Because I'm short on time with other projects, I need help to convert it to PHP and use extreme KISS principles. Why PHP? Because I know it best and because there's the largest number of developers available worldwide who can contribute to the project. Note I don't want to use ncurses on the project because I don't like the way it looks with its "shadow" effect. Plus, not everyone has compiled PHP with ncurses support.

[**[COLOR="Red"]Screenshot[/COLOR]**]("http://sourceforge.net/dbimage.php?id=83688")

[**[COLOR="Red"]Bash Script Download[/COLOR]**]("http://sourceforge.net/project/showfiles.php?group_id=173087&package_id=198197&release_id=435234")

Do you want to be the one to tackle converting this to PHP?

In general the goal of the code is to provide a menu system that loads dynamically based on a folder and script file structure -- providing an easy platform to extend it by merely copying in extra folders and files. The core part of the app draws the menus.

Part 2 of the project, which can come later, is a simple API to draw forms with checkboxes, popdown listboxes, text fields (and restrictions), a simple grid, etc.

---

### Post by pmasiar on 2007-01-03
I am going to be accused again promoting python too hard, but anyway:

Are you aware that [ubuntu prefers Python]("http://www.ubuntu.com/developers/bounties") solutions? Just FYI, please no flames.

---

### Post by SuperMike on 2007-01-03
Yeah, no problem. Knew I would get some flak on this. I put on a bullet proof flak jacket. It's just that there are probably more PHP developers out there than Python. Even 8 year old deserted islanders have PHP/MySQL web app talent these days as part of their tribal initiation. Besides, PHP is my language of choice and I'm the one who started the project. If someone wants to fork it, please, be my guest. :)

---

### Post by pmasiar on 2007-01-03
> **SuperMike said:**
>  Even 8 year old deserted islanders have PHP/MySQL web app talent these days as part of their tribal initiation.

LOL good one. :-) 

But situation is changing rapidly, $100 laptop  [http://www.laptop.org/](http://www.laptop.org/) from One Laptop per Child has python only - extra USB stick with PHP will be added to initiation I guess :-)

UPDATE: In case someone missed smiley, it was a joke based on SuperMike's "tribal initiation in PHP".

---

### Post by maddog39 on 2007-01-03
Okay well in my opinion, Python is in no way ready for full fledged web development as most of us do, its far to hard to use whith its CGI nonesense than PHP. I really like python for application development, but it just doenst work (for me anyway) with web development that well.

---

### Post by SuperMike on 2007-01-03
That's okay, guys. I'm rewriting the menu demo portion of the code now in PHP. Hope to have something up in a couple days.

---

### Post by gummibaerchen on 2007-01-03
> **SuperMike said:**
> That's okay, guys. I'm rewriting the menu demo portion of the code now in PHP. Hope to have something up in a couple days.

You really think, anyone is installing php for such a tool?

LOL ;) 


Canoncial is building some similiar app btw. I wonder, which app we will see in the next ubuntu release :D

---

### Post by SuperMike on 2007-01-04
Yeah, I'm used to the flak I'm hearing on this by now.

Well, think about this. You've heard of phpMyAdmin, and phpPGAdmin, etc., right? No one laughed then, right? Well, this is like a phpConsoleAdmin of sorts.

And think about this -- many people have Linux with no GUI in their server room and things are locked down by company policy such that they cannot bring up a web interface in certain tiers of their server room, such as the app tier. The only open port for them (without filling out a good bit of paperwork) is SSH. That's the way it is in my server room for the oppressive, multinational employer that I work for. A menu system like this can be useful when you start to think about the complexity of interfacing with an LDAP Server to add/remove users and groups to it -- it's a heck of a lot of command line switches to remember.

Last night and into this morning I stayed up until 4am and am almost done with the menu demo portion in PHP. It's working very similarly to the Bash demo for the UST project already up on SourceForge.net. The only thing I have to finish is the scrolling part where if the menu has to scroll off more items than can fit on the screen -- it needs a virtual scroll region and I'm working out the algorithm for that.

Once the menu demo is done, I can then start to build a console-based form generator API that uses the KISS principle. At that point, people could start to build modules quite easily for the thing by dropping a menu folder into a "plugins" directory for the project and to name their script page by a certain name like index.php. Their menus will automatically link in and the form API can provide them with a way to display and collect information to run against commands in the background. With this, people could write Ubuntu Server frontends to manage things like stopping/starting services, managing user/group administration on NIS, passwd, shadow, and LDAP, managing software through aptitude, managing Apache settings, managing mounted volumes, managing MySQL and PostgreSQL, and so on. The possibilities are endless once the PHP script kiddies find a simple platform that does the hard work for them regarding the TUI.

---

### Post by gummibaerchen on 2007-01-04
> **SuperMike said:**
> Yeah, I'm used to the flak I'm hearing on this by now.

Well, think about this. You've heard of phpMyAdmin, and phpPGAdmin, etc., right? No one laughed then, right? Well, this is like a phpConsoleAdmin of sorts.

Do you think it's the name?

Hey, phpMyAdmin and phpPgAdmin are WEBINTERFACES, not console applications.
These apps need a webserver anyway, and most times this includes PHP.

But not every server has PHP by default, and so I think you are wrong with your console tool in PHP.

If you want to, go ahead, I won't stop you, but I think that Canoncial or Ubuntu itself is actually building such an app (not in PHP of course), so I would use theirs for Ubuntu,

---

### Post by gummibaerchen on 2007-01-04
Is your project the official "Ubuntu System Tool"?

[http://www.golem.de/0607/46840.html](http://www.golem.de/0607/46840.html)

The screenshot in there looks exactly like you program, but the article is from August 2006.

---

### Post by gummibaerchen on 2007-01-04
Ok, just read that some with "great PHP experiences" is now the project leader.

Good bye UST, the idea was good, but not with PHP.

---

### Post by SuperMike on 2007-01-04
This is not "Ubuntu System Tool". It is "Ultimate System Tool", developed on Ubuntu, designed for Debian-based Linuxes, but especially for Ubuntu. It used to be called "Ubuntu System Tool" until the PM I brought onboard decided it was better to rename it and I agreed.

I'm building it because I'm hearing nothing about a console-based tool to help ease administration tasks for overworked IT operations staff. (Think of how many switches you need to mess with LDAP directory stuff at command line.)

Yast doesn't cut it for me -- it's reams and reams of code in order for you to add a new module to do something. It just doesn't have to be that way.

By tapping into the PHP populace with its mass of developers out there, it's got potential.

---

### Post by gummibaerchen on 2007-01-04
> **SuperMike said:**
> By tapping into the PHP populace with its mass of developers out there, it's got potential.

I think Python would have more potential, especially for Debian and Ubuntu,

---

### Post by pmasiar on 2007-01-04
> **gummibaerchen said:**
> I think Python would have more potential, especially for Debian and Ubuntu,

Just give up, even **I** gave up on switching SuperMike to python. :-)

Just imagine, making it in python/curses, so you can run it remotely over ssh and **still** have reasonable usability. Whou would use program like that? Only noob admins like me. And who cares for those?

---

### Post by MadMan2k on 2007-01-04
ROFL @ SuperMike, you have no f*cking idea what you are doing.
- reinventing the wheel by not using curses
- PHP is completly unsuitable console programming

good luck anyway

---

### Post by gummibaerchen on 2007-01-04
> **pmasiar said:**
> Just give up, even **I** gave up on switching SuperMike to python. :-)

Just imagine, making it in python/curses, so you can run it remotely over ssh and **still** have reasonable usability. Whou would use program like that? Only noob admins like me. And who cares for those?

Maybe bash would be good enought for that, as you would still use a lot os.system() or os.execl(). But this depends how pythonic you want the program.

Anyone interested in building such an application in Python or extending the bash script?

> **MadMan2k said:**
> ROFL @ SuperMike, you have no f*cking idea what you are doing.
- reinventing the wheel by not using curses
- PHP is completly unsuitable console programming

good luck anyway

same from here. would you please count the hours you spend developing? then i can have a better laugh :D

---

### Post by SuperMike on 2007-01-04
> **MadMan2k said:**
> ROFL @ SuperMike, you have no f*cking idea what you are doing.
- reinventing the wheel by not using curses
- PHP is completly unsuitable console programming

good luck anyway

[SIZE="2"]Now that's not a very nice way to put it. Wouldn't you agree? Try this one:

*Supermike, reinventing the wheel by not using curses, or using PHP which is not typically suitable for console programming, is, in my opinion, two poor choices.*

I'm glad you're adamant about your programming strategies, as am I. It's fair to criticize in this forum, but the profanity and the "don't know what you're doing" tone -- that's a bit off base.[/SIZE]

---

### Post by SuperMike on 2007-01-04
Again, for those who feel like it, when I turn this thing out, by all means be my guest and fork it into any language (or re-write it from scratch if you want).

---

### Post by Wybiral on 2007-01-04
Personally I think it's kind of neat... I write a lot of my stuff from scratch too and try to avoid external dependencies... Mostly because of the experience you gain from writing things yourself and as a kind of endurance test (not for REAL projects, mostly for my smaller experimental stuff). I like the BASH version... I don't really see a point in a PHP version, but it's his call. Python or C++ might be interesting choices... Even if you didn't want to use curses... Or using a combination of BASH and C++/python by calling them with command line arguments... But, once again, if you've made your mind on PHP, why not...

---

### Post by SuperMike on 2007-01-04
> **Wybiral said:**
> Personally I think it's kind of neat... I write a lot of my stuff from scratch too and try to avoid external dependencies... Mostly because of the experience you gain from writing things yourself and as a kind of endurance test (not for REAL projects, mostly for my smaller experimental stuff). I like the BASH version... I don't really see a point in a PHP version, but it's his call. Python or C++ might be interesting choices... Even if you didn't want to use curses... Or using a combination of BASH and C++/python by calling them with command line arguments... But, once again, if you've made your mind on PHP, why not...

Thanks for checking it out on SourceForge and downloading it. Glad you liked the Bash version.

With PHP, for me, it's all about making use of the mass of developers out there for it. However, it seems logical to me that if you want to make a console tool for sysadmin work, Perl is the language to go with. When you look at the history of why Perl was invented, it was primarily for sysadmin work. However, that kind of pushes a lot of good programmers out of the ring, and new ones. There is this mass of PHP programmers out there, and new ones at that. And from looks of the project sites on the web, there's a shortage of PHP programmers.

I like C and C++, and used to program on that with the Mac back in the 1980's, but darn if it doesn't need to be just a tad bit easier.

So I'm tetering on moving the whole thing to Perl, but I need to get a book on Perl -- I haven't used that language since '92. For now, however, I'll at least use the language I know best -- PHP -- and knock it out.

Actually, I know a little bit of Python. I'm no expert at it, but I wrote the pgst tool for PostgreSQL and this project is on SourceForge. I used the buggy Glade2 to draw the GUI, used the cumbersome PyGTK2 API to interact with it, used some small bit of actual Python code, and the rest was handled by piping a background process out to PostgreSQL and GNU command line tools and returning the result. My experience with Python was not very good. I had to ask a lot of questions, read some difficult online docs, and some PyGTK stuff didn't work as advertised. I can see it makes a so-so tool for making little GUI apps and control panels.

---

### Post by MadMan2k on 2007-01-05
> **SuperMike said:**
> There is this mass of PHP programmers out there, and new ones at that.
you probably know that PHP is mostly used as a Apache module for web-development.
So why should a web developet know about...
...Ubuntu?
...console programming?
...the tools UST will control?

Perl is not a choice either; the gnome-system-tools are being rewritten in python because noone is willing to maintain the perl version.

---

### Post by gummibaerchen on 2007-01-05
> **SuperMike said:**
> With PHP, for me, it's all about making use of the mass of developers out there for it. However, it seems logical to me that if you want to make a console tool for sysadmin work, Perl is the language to go with. When you look at the history of why Perl was invented, it was primarily for sysadmin work. However, that kind of pushes a lot of good programmers out of the ring, and new ones. There is this mass of PHP programmers out there, and new ones at that. And from looks of the project sites on the web, there's a shortage of PHP programmers.

Lol :) In which world do you live? Only because there may be more PHP programmers that does that not make your idea any better.
I don't think there a as many **good** PHP programmers as you might think.

And pls don't ignore the facts again here. Ubuntu prefers Python, and many developers here know Python very well. I was just wondering, when I read throught the "Programming Talk" forum, why noone said to the new ones who want to start programming: "learn PHP"...

> **SuperMike said:**
> Actually, I know a little bit of Python. I'm no expert at it, but I wrote the pgst tool for PostgreSQL and this project is on SourceForge. I used the buggy Glade2 to draw the GUI, used the cumbersome PyGTK2 API to interact with it, used some small bit of actual Python code, and the rest was handled by piping a background process out to PostgreSQL and GNU command line tools and returning the result. My experience with Python was not very good. I had to ask a lot of questions, read some difficult online docs, and some PyGTK stuff didn't work as advertised. I can see it makes a so-so tool for making little GUI apps and control panels.

When did you ( [-( ) do that? Don't know, every Glade I use is a little buggy, but hey, you could have also hardcoded the GUI. I think it still much easier than writing his own ncurses, just because of a shadow problem.

Maybe you should just dive in a little bit deeper? And there is not point in writing Python when you rely in "os.system()" the whole time. Maybe you should have tried bash + zenity then :-k

---

### Post by SuperMike on 2007-01-05
Well, I think I hear what's going on. I appear to be missing the boat. The new jobs at Google, for when they want someone to do sysadmin work, are going Python (although web stuff is remaining PHP in some cases). Ubuntu and Redhat appear to be wanting to use Python for all their admin tools and control panels. (Novell is going with C#, Mono, and GTK2, but I obviously don't stand behind that decision because it's like tipping the hat to Microsoft to say, 'yeah, great job there,' which I refuse to do.)

Since PHP is what I know, I'm going to at least knock out the menu demo in that and then migrate it to Python. I'm sure it will be a hair-pulling experience, however. I've got a guy I work with at my day job, and he's an old RTFMer who was one of the founding members of the Apache web server project, and he told me that he hates Python and between his comment and my experience, it has made me steer clear of it. However, I think the tide is turning.

Python can be some really funky, bizarre code to read sometimes. Some tasks are easy and quite readable -- some are not.

---

### Post by Verminox on 2007-01-05
> **SuperMike said:**
> Even 8 year old deserted islanders have PHP/MySQL web app talent these days as part of their tribal initiation.

:-D Time for a new sig... :p

---

### Post by amessina on 2007-01-05
Yeah, I've been in some offices where they only allow command line admin stuff on the servers. A tool like this would be useful to me. I'll have to bookmark the sf site to see when you get it usable so that people like me could build modules for it.

---

