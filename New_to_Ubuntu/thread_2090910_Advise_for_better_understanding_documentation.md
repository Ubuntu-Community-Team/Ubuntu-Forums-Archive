---
title: "Advise for better understanding documentation"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by starstreams on 2012-12-03
The last few months I've been doing an extensive amount of searching on the net with the idea of trying to get a better understanding of the more critical concepts that a Linux user needs to know to be effective with the OS (for any distro) I'm asking for advise from someone who was in my shoes at one time and could recommend how to get over some of these obstacles. I don’t' want to keep asking people how to do things, but rather how to better comprehend what I'm trying to learn on my own.

 The problem I'm facing often is that I'm having a difficult time understanding the help pages and read-me files. They tend to use symbols <  and the syntex examples are never consistent among the various help pages on the net. I'm always confused, when I just want to understand what most of you understand. [U]I'm not referring to the actual commands, as I know there is no quick way to learn that. 
I'm referring to comprehending the way in which people explain how things works[/U]. For example, At the SpaceFM site, there's a confusing section. I'll highlight in red the so called symbols I'm referring to as an example.
 
```
http://ignorantguru.github.com/spacefm/
```[INDENT]> [COLOR=Blue]
[/COLOR]
[COLOR=Blue][COLOR=Black]**The installer requires the build dependencies listed in the [README]("https://github.com/IgnorantGuru/spacefm/blob/master/README") file. Build dependencies include: (package names may vary on your distro)**[/COLOR]
autotools-dev bash build-essential dbus desktop-file-utils libc6 libcairo2 libdbus-1-3 libglib2.0-0 libgtk2.0-0[/COLOR] (**[COLOR=Red]>=2.18[/COLOR]**) [COLOR=Blue]libgtk2.0-bin libpango1.0-0 libstartup-notification0 libx11-6 shared-mime-info intltool pkg-config libgtk2.0-dev libglib2.0-dev fakeroot libstartup-notification0-dev libdbus-1-dev libudev0[/COLOR] ([COLOR=Red]**>=143**[/COLOR]) [COLOR=Blue]libudev-dev[/COLOR][/INDENT][INDENT]And the other thing about this example above is, what is all this text in blue? It runs on and on without any breaks. Are they all dependencies I need, or just some.. how does a new user know what they're talking about? 
I'm not lazy, and I've learned so much from my Linux book the last 6 months, but I just feel like I'm getting to a point where I'm not progressing because every time I think I understand an error and fix it, there's a new error. Like the other day for example, I uninstalled my PcmanFM because I wanted to install another FM. Well, I used the Synaptics just because I didn't want to take a chance on braking my file manger since I'm still using the OS to learn basics. I thought the package manger would take care of installing everything correctly but ended up braking something and now I'm not able to boot the OS.. To make a long story short, It seems like it's one thing after another, can't seem to make heads or tails. What am I missing other than my brain? Do I need to learn scripting before I can even ask these questions? Or is this learning process normally a long journey in complete darkness. I'm so hungry to get away from windows. I don't trust Microsoft anymore.  [/INDENT][INDENT]I'm sure some of you've had to have been where I am, is there **any** advise you can give to better understand the documentation examples and help pages?

Advanced Thank you
[/INDENT]

---

### Post by Bashing-om on 2012-12-03
I regret you feel so frustrated. To really comprehend this operating system is a very steep learning curve, and there are no short cuts once beyond the point and click stage. Read study think and read some more ! ... I realize this is not what you wanted to hear so let me back up a bit. Like anything else an understanding of fundamentals is required. As in system processes, how the system works from what perspective. How individual modules relate to a objective, Booting? Grub, plymouth, system V, upstart. drivers, buss polling ???

The list goes on and on .. and what can make it even more confusing, this is a constantly evolving system and growing by leaps and bounds to meet the innovations of technology ! Simple beginning was a kernel, a few modules compiled into it or made available to the kernel and a simple bootloader (lilo). Now the kernel is massive, we have progressed from lilo to grub to grub2 to grub2.2; The advent of plymouth and changing from system v to upstart for all system processes... Change change change.. it is often difficult to determine what is germain and still relevant from documentation that you do not know how old it is! The point I want to make is one just has to keep reading and studying. You will get to a point where it starts to make sense and you will be able to determine the relevancy.

Now to the point of your direct questions: (>=) means, just as you may imagine -greater than or equal. The list in blue is a list of possible dependencies, in linux a space is a delimiter, thus the space is a  separator between names of packages/files. Bear in mind computers are logical, and logic always prevails ! But syntax can vary, depending on how the programmer programs, and there are many programmers!

As a first step in comprehension, one must understand the terminology; I suggest you look up some glossaries; study the terms and how they interrelate. Then take a look at a couple of bash scripting tutorials (you will not learn it all in a hundred settings !), get a gist of how the system operates - learning little by little. Soon you can craft good search terms, google is your friend! Then just follow your curiosity.  

Now my conclusion: In my humble opinion this is the greatest operating system the world has ever known. Can do anything that one has the imagination to conceive and the skill to implement ! Thanks to open source.

[INDENT]off my soap box now <== BDQ

[/INDENT]

---

### Post by bab1 on 2012-12-03
> **starstreams said:**
> The last few months I've been doing an extensive amount of searching on the net with the idea of trying to get a better understanding of the more critical concepts that a Linux user needs to know to be effective with the OS (for any distro) I'm asking for advise from someone who was in my shoes at one time and could recommend how to get over some of these obstacles. I don’t' want to keep asking people how to do things, but rather how to better comprehend what I'm trying to learn on my own.

 The problem I'm facing often is that I'm having a difficult time understanding the help pages and read-me files. They tend to use symbols <  and the syntex examples are never consistent among the various help pages on the net. I'm always confused, when I just want to understand what most of you understand. [U]I'm not referring to the actual commands, as I know there is no quick way to learn that. 
I'm referring to comprehending the way in which people explain how things works[/U]. For example, At the SpaceFM site, there's a confusing section. I'll highlight in red the so called symbols I'm referring to as an example.
 
```
http://ignorantguru.github.com/spacefm/
```[INDENT][/INDENT][INDENT]And the other thing about this example above is, what is all this text in blue? It runs on and on without any breaks. Are they all dependencies I need, or just some.. how does a new user know what they're talking about? 
I'm not lazy, and I've learned so much from my Linux book the last 6 months, but I just feel like I'm getting to a point where I'm not progressing because every time I think I understand an error and fix it, there's a new error. Like the other day for example, I uninstalled my PcmanFM because I wanted to install another FM. Well, I used the Synaptics just because I didn't want to take a chance on braking my file manger since I'm still using the OS to learn basics. I thought the package manger would take care of installing everything correctly but ended up braking something and now I'm not able to boot the OS.. To make a long story short, It seems like it's one thing after another, can't seem to make heads or tails. What am I missing other than my brain? Do I need to learn scripting before I can even ask these questions? Or is this learning process normally a long journey in complete darkness. I'm so hungry to get away from windows. I don't trust Microsoft anymore.  [/INDENT][INDENT]I'm sure some of you've had to have been where I am, is there **any** advise you can give to better understand the documentation examples and help pages?

Advanced Thank you
[/INDENT]

The items in blue are package numbers and the numbers in red are version numbers of the package.  A search on [COLOR="Blue"]libgtk2.0-0[/COLOR] and Ubuntu returns [**_[COLOR="DarkSlateGray"]this[/COLOR]_**]("http://packages.ubuntu.com/search?keywords=libgtk2.0-0").  Note the difference in the listing of lucid vs oneric and later (> = means greater or equal to).

All I can say is read read read, and then read some more.  You don't have to buy books, most of the information is available for free on the Internet.  Start with the basics.  Documentation assumes you know the subject.  It is reference material.  You need more along the lines of *how it works.*  It's worth noting that the general subject is more than any one person can absorb.  Folks tend to specialize areas of expertise.  Do you have an area the you are interested in (i.e. system admin, network admin, programming, etc.)?

I would say start with system admin.  You will learn how to maintain the installation.  here is a  Google search of [**_[COLOR="Blue"]*Linux system Administration *[/COLOR]_**]("https://www.google.com/search?q=linux+system+administration&btnG=Go!").

---

### Post by bfmetcalf on 2012-12-03
In my opinion one of the greatest ways to learn is to cruise the forums.  Sit and hit the "New Posts" tab for a while and read through posts with people having issues.  This will show you what the issue is and how it was fixed, in many cases giving you insight into what different commands do, what some of the syntax you come across means and not to mention a head start on any issues that may arise.  I cruise these forums and the archlinux forums very often and not surprisingly learn something new almost everytime I'm on them.  

The archlinux forums especially give me a great learning experience as many of the issues over there are a little more involved as the user base is generally more experienced and less people just getting into Linux.  

The more you read the more you will learn, that is what Linux is, there is no manual per say, just forums and wikis scattered all over the place with their own brand of wonderful knowledge.

---

### Post by starstreams on 2012-12-04
Thank you all.  
 *Bashing-om*, *bab1*, and *bfmetcalf*. You're suggestions were priceless.
 It's funny because all these little suggestions, they give some direction.  
 

 > **Bashing-om said:**
>  it is often difficult to determine what is germain and still relevant from documentation that you do not know how old it is! The point I want to make is one just has to keep reading and studying. 
 That's a darn good point *bashing-om* and one I can relate to. I guess there's no easy answer because you have to know the past to understand the future. But it just keeps expanding. (For a nitch focus, I would say network and system security) to limit the endless see of possibility's. When I got into PCs / windows over 10 years ago, even got A+ certified, everything was simple, but today I see people who are just getting into computers and there is so much terminology they're overwhelmed. But with linux it seems more critical to know what your suppose to be looking for and using. But I get the point, I'll just take it one day at a time, and like you said, I think eventually with enough reading all this should start absorbing into my brain. If not, that's another issue.  :biggrin:
 I sort of panicked when I made this post because I'm so anti windows 8 now that I found out MS wants to spy on everyone, and I didn't even like windows 7 for various reasons. And the fact that NTFS puts the header information at the center of the drive kind of limits things you can do with Truecrypt. Not an issue with ext3, and 4. I like the fact that Linux is trustworthy, and there are plenty of good watchdogs who know whats going on because they can see the source. I can't say that about windows. I guess I also panicked because I didn't think you could cause your OS to not load by using the built in installers. But what ever I did the other night broke something and the package recovery didn't fix it. Thankfully this is just a test system, and I've got another virtual machine of the OS to play with until I figure out why the system won't boot. I don't want to just reinstall it either as I know I won't learn anything doing that.
 > **bab1 said:**
> You don't have to buy books, most of the information is available for free on the Internet. 
I would say start with system admin. You will learn how to maintain the installation. here is a Google search of [[COLOR=#0000ff]*_**Linux system Administration **_*[/COLOR]]("https://www.google.com/search?q=linux+system+administration&btnG=Go%21").
 Very true bab1, and thank you for that link! I didn't even think of using that search term. note, I did buy a book a few months back called: *Visual Quickstart Guide Unix/Linux 4th Edition Deborah S. Ray*. Often business is slow at my work place so I sit around for hours and take notes  in the book, then go home and practice what I read. It's been an amazing book as far as beginners is concerned, but not enough info on installing, and compiling. But I also realize most knowledge does come from one source. So far all the commands in the book have worked well with this Lubuntu, but it's really just basics: *Setting-permissions*, *moving-files*, using *su*, *sudo*, ..ect. The administration books should be a good follow up. I know the net is good source also, just Had to ask because too many people out there don't format consistently and it can really throw off a new user. I'm just being impatient I guess. hehe. I'll take it slow.

 I think the most difficult thing for me about linux, (and is what also makes linux versatile) is how everything you install has different packages associated. Coming from windows it's strange because most applications in windows come pre compiled with all this stuff and most the libraries are in windows. But on their other hand, it's nice having the control that Linux gives you.  I guess I should hammer on understand packages so I can backup all these packages in case something is missing from a repository at a later future date.  
 In any case,   Please don't misunderstand. The experience has been great, sorry if I sounded disappointed. I'm not at all. Just trying to learn too much too quickly.

 I really appreciate you're guys insight! Huge thank you!

---

### Post by squakie on 2012-12-04
Don't feel bad at all - I'm an ex systems programmer and systems administrator and ran into the same thing with Unix many, many years ago now.  our company had some things it was doing on the programming side which our mainframe really didn't support with the proprietary operating system.  So, under a non-disclosure agreement back then we installed a co-processor just to run Unix and get access to things like TCP/IP, etc..  The first time I was looking at the documentation I couldn't follow what the heck they were talking about - the same command appears in more than 1 of the books - it had different context depending on how you use it.  So, I called up the national techinical support center and asked for guidance.  Their reply:

" You know where it came from, don't you?  Some guys at Bell labs, MIT, etc., sitting around in the middle of the night with their tie-died t-shirts, shorts, sandles, a head of lettuce and a tomato going 'WOW! Look what I made it do!' ".

I've laughed my butt off ever since!

---

### Post by DuckHook on 2012-12-05
I suspect that all of us feel your pain. My own experience coming to grips with the damn thing was awful. I started trying out Linux in 1997. Back then, it was only fit for extraterrestrials and masochists. It was impossible to get anything done sans the command line because the desktop experience was positively foul. First distro tried was Red Hat, back before they even used RPM. As a newbie, you just settled for what came with the distro, thanked whichever demon you sacrificed to that some of it actually managed to run on your hardware and didn't dream of adding or asking for anything else. There were no forums to speak of and the mailing lists (remember those?) were full of angry frustrated users every bit as clueless as I was. I had another life back then, so I dropped Linux for two years as a potentially good idea that was not even quarter-baked.

Two years later, curiosity got the better of me and I installed another Red Hat distro (can't even recall the versions anymore -- if someone said 007, I'd probably nod like a bobble-head and mindlessly agree). Almost the same results. A little further this time, but ultimately, capitulation, followed by the humiliating crawl back to Windows.

Couple(?) of years after that, it was Mandrake. The first distro that I could run with anything even remotely resembling a clue. I gave up on that one when a Windows install wiped out my whole partition and I couldn't face the pain of reconstructing all of my lost configs, settings and data. Sometimes, it's just easier to take the cowardly way out and walk.

All in all, with life happening and the such, I didn't look at Linux again until '05. Ubuntu was a whole 'nuther world. Feature rich, slick, worked right out of the box (at least for me) and required minimal use of the command line. I do remember wrestling with *sudo* the first time though. "...what *is* this *&%$##!! command? Why can't I get root? I want root!" It was the cry of the frightened child impossible to reason with because he's so scared and intimidated that he's just blindly striking out from sheer terror.

But this time, I stuck with it. If I broke an install by doing something stupid (I once *rm*-ed my / directory as root--and finally figured out why you use *sudo*), I didn't give up. I would reinstall. This happened more times than I can remember. Many a night my wife would get awfully suspicious about what I as doing at 3:00 in the morning. Did I have a little number a continent away whom I was flirting with on the side? Well, the sordid truth was that I did, and her name was Ubuntu.

Anyhows, by relentlessly sticking with it, through sheer cussed bloody-mindedness, I managed to learn the most significant commands, what the obscure symbols and square brackets and switches and arguments do, and how to parse some of the truly awful explanations in the *man* pages that read like they've been written by drunken Martians translating Chinese and who think it positively wuss to provide actual *examples*. <sigh>

The message in all of this otherwise pointless autobiography is that there is no easy way. And it's alright to feel angry and frustrated and lost. You've got to wander in the desert to get to the promised land. But when you get there, you will be amazed at what you find and you'll have the quiet pride of knowing that it was your own two feet that got you there.

Having said all of that, there are a few things that make the journey a tad easier, like water bottles and even the odd camel. I wish someone had pointed them out to me:

1. Install a virtual machine just as soon as you feel comfortable enough setting one up. Install all of your experimental systems on that. Then go to town fiddling with it, tuning it, and inevitably breaking it. Life is much happier when you know that even the stupidest thing you do has limited consequences.

2. Do a minimal install on one of those virtual machines. Minimal installs come with no Xwindows, no desktop, nada. Just that bare, scary, intimidating, nasty cursor waiting for you--daring you--to type something. If you force yourself to use this environment, with no recourse to the comfort of a GUI, setting up your network, mounting and unmounting disks, connecting to NASes, even surfing the web and retrieving e-mail (it can be done), the command line quickly loses its fear factor. In fact, you will be surprised at how quickly it recedes into the background.

3. Most of all, just relax. It's not life or death. It's not your boss. It's not your sig-other. It's just a jumble of electrons at your beck and call. If they don't always do what we want, screw-em, and go enjoy a good beer.

---

### Post by squakie on 2012-12-05
Yeah - Slackware in the 1995-1996 range was a lot of fun to install.  In those days I was still working so it wasn't so bad.  If I had to do that now, not sure how I would do, but hey - why try?  Educational?  Perhaps.  Needed by some?  Glad I'm not one of those.

OP - have you tried one of the free to download books that are an introduction to Linux in general and cover the command line?

---

### Post by Zill on 2012-12-05
> **starstreams said:**
> ...I guess I also panicked because I didn't think you could cause your OS to not load by using the built in installers. But what ever I did the other night broke something and the package recovery didn't fix it...
On this particular point I would only offer the following advice...  
[LIST=1]
[*]Use a stable release of Ubuntu, not a development release.  For maximum stability I recommend the LTS releases, rather than the interim releases.
[*]Only install software packages intended for your particular release - do not try to mix-n-match packages intended for different releases.
[*]Try to stick to the standard repository sources - do not install PPA packages unless absolutely essential.
[*]Don't try to install software manually (i.e. compiled from source) until you have *considerable* Linux experience.
[/LIST]
If you follow this guidance you should find that software can be installed with no risk of breaking your system. ;-)

---

### Post by Noor1101 on 2012-12-05
Hi Starstreams and others 

Interesting questions here in this thread. I've been trying Linux (xUbuntu 12.04 & Debian 7) since last August, and I run into the same issues: I learn a lot from this forum and the internet in general (and the free download "Linux in a Nutshell"), but I feel I want to learn some kind of 'over-all Linux reasoning skill'. The small issues I've run into have been solved (thanks to this forum and some Linux-experts in the city I live in), but I crave for some kind of 'bigger-picture'-understanding, to understand the logic. And I guess that patience and taking it one step at the time is the key to this - however frustrating that sometimes might be.

In my experience, face-to-face communication with someone who is skilled, helps a lot with learning this omnibus insight. I guess it's mostly the advantage of being able to directly ask for simpler language, clarification when needed. (Plus the fact that the communication is in my mother-tongue, also helps.)
I found out that three people in my circle of friends and acquaintances are very good with Linux (one works for Google, another manages Linux servers for multiple clients, and to the third one it's just a hobby). Talking to them helps a lot. 
Also I found a Linux users' group in the city I live in, who get together once a month. (All free of charge; no obligations; "open source" as it should be.) 
I can recommend that to everyone! And maybe if such a group doesn't exist yet in your neighbourhood, setting one up can't be too difficult.


Well, those are my thoughts. I'll be following this thread to see what others think.

Good luck with all the learning, starstreams!

Regards
Noor

---

### Post by JKyleOKC on 2012-12-05
> **starstreams said:**
> I'm sure some of you've had to have been where I am, is there any advise you can give to better understand the documentation examples and help pages?It's been a few years (like nearly 50) but when I first set out to learn about computer languages, I was in an excellent location to do so: I worked for G-E at a plant with most of their top software folk as well. As I studied about ALGOL-60 I came across the term "string" and could not figure out its meaning, from context, so I went to these brilliant software folk and began asking questions. Turned out that none of them were familiar with the term either!

I finally had to order a book from Elsevier and wait a month for it to arrive, to learn that a "string" was a group of text characters strung together.

Now, of course, we all take the meaning for granted. But back in 1965, those mainframe days when we were developing the first practical video terminal, nobody had any idea.

In the course of my self-education, I developed a strategy that has worked quite well over the years: When I take up a new subject, I grab the most recent professional-level book on it that I can find, and begin reading. When I inevitably come across something that mystifies me, I then go back to the oldest publications I can find on the subject and study them.

The reason is simple: the first people working on the subject had to explain things to their peers in language and analogies those peers could comprehend. To begin understanding relativity, I read Einstein's writings from the 1920s. To get a start on wave and field theory, I went to Clark-Maxwell's papers. And so on ad nauseum. This got me started and let me read ever more detailed works until I found what I had been looking for!

If you want to understand the Unix philosophy that has carried through into Linux, I'd recommend as a starting point the book "Software Tools" by Brian Kernighan and P. J. Plauger, in the original edition if you can find it. It was written at a time before Unix itself was widely known, and used a language called RATFOR (RATional FORtran) for all of its examples -- but RATFOR was a total analog of C, and the tools described were in fact the basic Unix toolkit! It's actually possible to compile all of their samples, and learn the philosophy by doing just what they did in the early development of Unix.

---

### Post by squakie on 2012-12-05
> **JKyleOKC said:**
> It's been a few years (like nearly 50) but when I first set out to learn about computer languages, I was in an excellent location to do so: I worked for G-E at a plant with most of their top software folk as well. As I studied about ALGOL-60 I came across the term "string" and could not figure out its meaning, from context, so I went to these brilliant software folk and began asking questions. Turned out that none of them were familiar with the term either!

I finally had to order a book from Elsevier and wait a month for it to arrive, to learn that a "string" was a group of text characters strung together.

Now, of course, we all take the meaning for granted. But back in 1965, those mainframe days when we were developing the first practical video terminal, nobody had any idea.

In the course of my self-education, I developed a strategy that has worked quite well over the years: When I take up a new subject, I grab the most recent professional-level book on it that I can find, and begin reading. When I inevitably come across something that mystifies me, I then go back to the oldest publications I can find on the subject and study them.

The reason is simple: the first people working on the subject had to explain things to their peers in language and analogies those peers could comprehend. To begin understanding relativity, I read Einstein's writings from the 1920s. To get a start on wave and field theory, I went to Clark-Maxwell's papers. And so on ad nauseum. This got me started and let me read ever more detailed works until I found what I had been looking for!

If you want to understand the Unix philosophy that has carried through into Linux, I'd recommend as a starting point the book "Software Tools" by Brian Kernighan and P. J. Plauger, in the original edition if you can find it. It was written at a time before Unix itself was widely known, and used a language called RATFOR (RATional FORtran) for all of its examples -- but RATFOR was a total analog of C, and the tools described were in fact the basic Unix toolkit! It's actually possible to compile all of their samples, and learn the philosophy by doing just what they did in the early development of Unix.

GE - like in GECOS?  Like in some pieces bought by Honeywell (which became Honeywell Bull, then just Bull)?  Like in GECOS being renamed GCOS?  Or was it more if the bigger iron?

---

### Post by JKyleOKC on 2012-12-05
Sounds like you might have lived that roller-coaster ride too! Yep; GECOS was the General Electric Comprehensive Operating System for the GE-600 series machines that controlled all launches from the Cape in the days of Mercury and Apollo. Honeywell bought the Computer Division in 1970 and awarded me my 5-year G-E pin. Then Honeywell turned the reins over to Control Data, which renamed my area as Magnetic Peripherals Inc. in 1875, and I got my 10-year Honeywell pin from MPI. Five years later, my area was split off from MPI to become BTI Systems, a subsidiary of BancTec (which made check readers for banks). And BTI Systems finally vanished from the scene.

Honeywell deleted the word "Electric" from the name of the o/s and GECOS became GCOS. They also changed the hardware system's name to Level 6000.

I was in the Oklahoma City plant, which made the first removable-platter disk drives in the G-E line (by copying the IBM 2311 design), and also tape equipment. It eventually became the main disk production facility, and MPI finally got bought up by Seagate not long before Control Data went belly-up. The local plant is now just an engineering office, still part of Seagate but actual manufacturing went to Malaysia years ago.

---

### Post by DuckHook on 2012-12-05
> **Noor1101 said:**
> ...I want to learn some kind of 'over-all Linux reasoning skill'.

The problem is: there is no such thing as an 'over-all Linux reasoning skill'. @squakie's hilarious comment is spot on:

> " You know where it came from, don't you? Some guys at Bell labs, MIT, etc., sitting around in the middle of the night with their tie-died t-shirts, shorts, sandles, a head of lettuce and a tomato going 'WOW! Look what I made it do!' "Sometimes, the funniest things are the absolutely truest things too. The follow-up to that story would be that the "amazing thing" that Mr/Ms tie-die "made it do" then wormed its way into the kernel and and never found its way out. There's no rhyme or reason to any of it. It was cool, it worked, and it's been there ever since.

Take the PS command. This one drives me nuts. You can use the BSD arguments that don't start with a hyphen (the classical one is *aux*) or you can use the UNIX arguments, but these must have a hyphen (*-ef*), or you can just give up on the whole thing like I do and use a pseudo-graphical tool like *htop*. If you ask the bearded ones why this ridiculous hotch-potch of behaviours continue to be allowed, they will sonorously intone that PS is one of the oldest command tools in creation, was inherited from BSD, and that we must properly bow to tradition by indulging in obscurity, confusion and sacrificial rites. But how is a new user going to make sense of any of this? There's no 'over-all Linux reasoning' in any of it. You do it *this* way... well... just *because*.

I'm not complaining. The absence of an imperial authority dictating that "thou shalt only do things *my* way", is one of the biggest reasons that Linux continues to grow, improve and draw the sort of tie-die geniuses that make it all possible. In exchange, the rest of us have to learn how to work with the fact that it's messy, organic, anarchic and lacks the unified architectonic structure that is one of the few but key strengths of the proprietary vendors.

As per the spirit of the open source movement, there are many free and open resources available to inquiring minds. This link is invaluable:

[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

One of the recommendations therein is a book that I've personally found very useful and which can be downloaded from here:

[http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf](http://www.rigacci.org/docs/biblio/offline/TLCL-09.12.pdf)

In summary. None of these resources will teach you 'over-all Linux reasoning skill' because there is no such animal. But we can slowly learn its idiosyncrasies, its loopy syntax, its maddening obscurities, and instead of thinking of these things as irredeemably awful, we can take the attitude that they leave us new things to explore and discover all the time.

---

### Post by Noor1101 on 2012-12-05
Thanks DuckHook, I understand what you're saying. I guess without an overall reasoning skill we're back to acquiring an overall experience - one step at a time. 

Patience and enthusiasm! 

>  we can slowly learn its idiosyncrasies, its loopy syntax, its maddening  obscurities, and instead of thinking of these things as irredeemably  awful, we can take the attitude that they leave us new things to explore  and discover all the time. 	
Very well said, DuckHook :)


I'm enjoying the ride, anyway. Can't imagine I'll ever go back to Windows.

---

### Post by picaflor on 2012-12-05
Hi,

  Sometimes it helps to append "tutorial" or "howto" to your google searches. This tends to get you information geared more for the less experienced. I'v been using linux exclusively since around 1997, and I still find that this often helps me out a lot.

Happy Hunting!!!

---

### Post by starstreams on 2012-12-05
You guys all bring interesting ideas to the table, and again. I really have enjoyed reading the responses.
 Man, there were so many responses, I think I’m just going to try to absorb everything so I don't make this post excessively long. And I'll admit, some of what you guys talked about Is over my head, but at least I can look back at the terminology and utilize it as a point of direction.  I feel like a piece of toast. you guys toasted me. :tongue:
 

 I do realize the potential of the kernel and eventually  would like to utilize some of it's flexibility. But I need be very honest with regard to what I'm after, not only with Linux but any system. They are:
 
[LIST]
[*]Keeping the system running.
[*]Backward compatibility
[*]Security
[/LIST]
*Keeping the system running* and problem free is really the root of why I want to learn the inner workings of the OS. I became pretty proficient in securing a windows system. The issue I have with windows is that you never know what Microsoft is up to with their code being closed and all their background services that run without most users knowing. Linux seems more transparent and the fact that it's open source is assuring. With Linux I feel like the developers have a pure and honest agenda to make something great for the people, and not just for their pockets. But like many of you have already pointed out, I guess it all takes times to absorb. I've been fixing windows systems for over 10 years, I've only been into Linux for a few months. What a difference. I do like what I'm seeing.   
 

 The other point was, *Backward compatibility*. For me this means always having the ability to run an application even when a new release comes out 10, 15 year later. From my perspective, "today" it seems Linux respects backward compatibility more so then Microsoft. The fact that MS forces people to adopt to a new operating system leaving out drivers, and also gives no option to install newer drivers like directX 11 on older platforms, makes them rotten. 

Last, Linux *security* seems to speak for itself, it's more transparent.


 > **Zill said:**
> On this particular point I would only offer the following advice...  
 
[LIST=1]
[*]Use a stable release of Ubuntu,     not a development release. For maximum stability I recommend the LTS     releases, rather than the interim releases.
[*][COLOR=Red]Only install software packages     intended for your particular release - do not try to mix-n-match     packages intended for different releases.[/COLOR]
[*][COLOR=Red]Try to stick to the standard     repository sources - do not install PPA packages unless absolutely     essential.[/COLOR]
[*]Don't try to install software manually (i.e. compiled from     source) until you have *considerable* Linux experience.
[/LIST]
 If you follow this guidance you should find that software can be installed with no risk of breaking your system.  



Those are great points, Thanks Zill
One of the issues for me right now is what you said in the [COLOR=Red]2nd [COLOR=Black]and[/COLOR] 3rd[/COLOR] lines of advice.  I guess I don't really know how to look for and verify what the proper packages would be for my release. note: I had removed my default File manger because it didn't work well with Truecrypt. After removing it,  I looked in synaptic install options for Nautilus FM which works with Truecrypt. There were dozens of things called Nautilus FM and I just assumed they were addons to give Nautilus more functionality. But I choose to play it safe and only installed the one called Nautilus FM since i have no idea what all the other choices were. As far as the issue with the system now, I can't give the error message at the moment because after running the package-repair-option from grub recovery, now I just get a black screen with a blinking cursor at the top left. I'm going to try to keep searching this on the net, If I can't figure it out, I might make a new post and see if anyone can guide me along. I don't want to just reinstall. That' s for wimps. hehe :biggrin:



At this point, I'm thinking a need to take a hard crash course on installing packages. There's something fundamental about the operating system I'm missing. And even though I'm feeling more proficient in using basic terminal commands, the root concept of how applications and updates are applied is challenging because I don't think I've learned how to identify and find proper package versions. I mean when you run apt-get, I have no idea what it's installing. All I know is someone told me to type ..Apt-get.. ect into the terminal. I've never setup my repository source links either if thats even someone I'm suppose to touch? maybe I need to look into these things in more depth.

---

### Post by squakie on 2012-12-05
> **JKyleOKC said:**
> Sounds like you might have lived that roller-coaster ride too! Yep; GECOS was the General Electric Comprehensive Operating System for the GE-600 series machines that controlled all launches from the Cape in the days of Mercury and Apollo. Honeywell bought the Computer Division in 1970 and awarded me my 5-year G-E pin. Then Honeywell turned the reins over to Control Data, which renamed my area as Magnetic Peripherals Inc. in 1875, and I got my 10-year Honeywell pin from MPI. Five years later, my area was split off from MPI to become BTI Systems, a subsidiary of BancTec (which made check readers for banks). And BTI Systems finally vanished from the scene.

Honeywell deleted the word "Electric" from the name of the o/s and GECOS became GCOS. They also changed the hardware system's name to Level 6000.

I was in the Oklahoma City plant, which made the first removable-platter disk drives in the G-E line (by copying the IBM 2311 design), and also tape equipment. It eventually became the main disk production facility, and MPI finally got bought up by Seagate not long before Control Data went belly-up. The local plant is now just an engineering office, still part of Seagate but actual manufacturing went to Malaysia years ago.

Yep!! Way back when I worked on the level 64 systems, then the DPS/7 systems and then the DPS/7000 systems, also Level 6, DPS/6 and the adapted version that was the communications front end.  Worked as a systems programmer and systems admin on those boxes for a long, long time.  finally in the 90's when Bull pulled all of that out of the U.S. we moved on to DEC.  A completely different animal - even reminiscent of Unix!  We also had a symmetrical processor Unix box and a couple of Bull Unix boxes for some data communications tasks.

Brings back a lot of memories - fun work, hard work, long hours!

---

### Post by DuckHook on 2012-12-05
> **squakie said:**
> Yep!! Way back when I worked on the level 64 systems, then the DPS/7 systems and then the DPS/7000 systems, also Level 6, DPS/6...

Erhm... you guys realize that this makes you walking museum pieces, right?):P

---

### Post by DuckHook on 2012-12-05
Let's address your difficulties one-by-one:

Keeping the system running

You came to the right OS. Linux may be obscure and complex and ornery, but it is rock solid. Most of the issues in these forums having to do with a "broken" Linux system are actually breakages of high-level tasks, like a desktop environment or a graphics-based application (like a word processor). The operating system itself continues to purr along quite nicely, thank you very much. Of course, it doesn't matter to the end user whether it's Linux that has broken or their word processor because either way they can't get their work done, but from a technical perspective, there is all the difference in the world. An app failure loses only the app data and does not compromise anything else whereas a system failure loses data universally and often corrupts the whole OS.

Backward compatibility

I used to think of Linux as incredibly backward compatible until the latest version of Ubuntu using the latest kernel dropped support for old 32-bit only processors. But, by-and-large, backward compatibility is still okay. However, I have recently had to find/install modules for wireless cards that are no longer supported by the kernel, then pin an old 3.2 kernel to my laptop so it wouldn't be upgraded to v3.5, etc. I would say that backward compatibility (at least on the HW side) is starting to become a problem. But I realize what the kernel developers are up against: just how big do you allow the kernel to get supporting all of this old hardware?

Security

Another area where Linux shines. However, here, I must urge patience. As a user new to Linux, the tendency is to carry over all of the old Windows assumptions/prejudices/practices. Many of them aren't needed in Linux and those that are needed suffer from the infamous Linux obscurity. Whole pages could be devoted to security in general, so I will just direct you here:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

The author of this thread (it's actually more of a guide) is an amazing chap who has written scads of guides and howtos. It's humbling how knowledgeable some people get to be, and you wonder how they do it. At any rate, in this guide, he outlines the basics of Ubuntu security for the curious. However (and this is where all gurus stumble), he has no idea how intimidating his guide is for the absolutely new user. My advice: provided that you don't install things you don't know and provided that you stick to a pretty generic system running nothing but repository software, Linux is awfully secure right out of the box. There is no pressing need to harden it any further until you are more comfortable with Linux and have a better understanding of things. At some point, you will want to learn *snort*, *apparmor*, SSL, encrypted directories, VPNs and yada-yada-yada, but these are unnecessary for the absolute beginner and will just make your head explode. Time enough to learn them later.

> now I just get a black screen with a blinking cursor at the top leftWill let you start that as a separate thread should you need it.

> At this point, I'm thinking a need to take a hard crash course on installing packages... when you run apt-get, I have no idea what it's installing...Here is a link to a great site called *psychocats*, one of the best sites for absolute beginners to Linux. I've zeroed in on her explanation for installing, but the rest of her site is definitely worth a read. She also links to further sites that deal with various aspects of installing in greater detail.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by squakie on 2012-12-06
> **DuckHook said:**
> Erhm... you guys realize that this makes you walking museum pieces, right?):P

Heck, I worked on the old 2000 series as well (can anyone say mod1?).  I knew where I stood in the world when and ex-girlfriend and I were in Boston for a long weekend and went to the computer museum.  There in the museum were pieces of equipment I worked on.  That does make you feel old!  ;)

---

### Post by Zill on 2012-12-06
> **starstreams said:**
> ...Those are great points, Thanks Zill
One of the issues for me right now is what you said in the [COLOR=Red]2nd [COLOR=Black]and[/COLOR] 3rd[/COLOR] lines of advice.  I guess I don't really know how to look for and verify what the proper packages would be for my release. note: I had removed my default File manger because it didn't work well with Truecrypt. After removing it,  I looked in synaptic install options for Nautilus FM which works with Truecrypt. There were dozens of things called Nautilus FM and I just assumed they were addons to give Nautilus more functionality. But I choose to play it safe and only installed the one called Nautilus FM since i have no idea what all the other choices were...

...At this point, I'm thinking a need to take a hard crash course on installing packages. There's something fundamental about the operating system I'm missing. And even though I'm feeling more proficient in using basic terminal commands, the root concept of how applications and updates are applied is challenging because I don't think I've learned how to identify and find proper package versions. I mean when you run apt-get, I have no idea what it's installing. All I know is someone told me to type ..Apt-get.. ect into the terminal. I've never setup my repository source links either if thats even someone I'm suppose to touch? maybe I need to look into these things in more depth.

If you stick to the default repositories for your installed release then these will *automatically* point to the correct versions of software for your release.  These repos are listed in the file /etc/apt/sources.list and can be viewed with the following command:
```
cat /etc/apt/sources.list
```
Note that a "#" sign in front of a line indicates that this particular line will be ignored by the package management system.  Only the lines without a "#" will be read.

The various GUI package managers (such as "Software Center" and "Synaptic") should also show this same list of repos, but presented in a slightly different way.

When you install a package this will install *both* your required application and, if necessary, *all* the associated dependencies.  These will all have the correct versions for your release.

My point was that you will create many problems if you add repos for other releases to your sources.list as this will confuse the package manager and cause system breakage.  Similar problems *can* arise if you add PPA sources as these can sometimes bring in dependencies with the "wrong" version(s) for your release.

If you don't change the default sources.list until you totally understand how the system works then you should have a reliable and stable system.  I strongly recommend that you *only* install apps from the repos using the package management system (apt-get, "Software Center" or "Synaptic") as this will ensure reliability.  If you obtain packages from any other source, or try to compile and install software from source, then you are quite likely to end up in "dependency hell" and break your system!

---

### Post by JKyleOKC on 2012-12-06
> **DuckHook said:**
> Erhm... you guys realize that this makes you walking museum pieces, right?):PSure thing. G-E hired me originally to write the service manuals for that first video terminal, the Datanet-750, which actually used a small consumer TV as its monitor in the prototype version. Memory was a sonic delay line, and the device was the first one G-E built that used integrated circuits instead of discrete transistors. Most of the crew I worked with are gone now, and I myself am a bit creaky around the edges, but hanging in here with you young whippersnappers keeps me alive!

---

### Post by starstreams on 2012-12-07
> **Zill said:**
> If you stick to the default repositories for your installed release then these will *automatically* point to the correct versions of software for your release.  These repos are listed in the file /etc/apt/sources.list and can be viewed with the following command:

The various GUI package managers (such as "Software Center" and "Synaptic") should also show this same list of repos, but presented in a slightly different way.
But that's just it, I did use Synaptic to uninstall my Filemanger and then installed Nautilus FM using Synaptic for that as well, I had tons of Nautilus FM install choices listed in the Synaptic "*Not Installed*" section just waiting to be installed. I didn't know what any of it was and just assumed they were safe extensions to the Nautilus FM since they all had the name Nautilus. I thought they were safe because the were in the synaptic list.
That's why I'm not sure why something got broke. I've never touched my repositories *sources.list*. All I did was uninstall PCmanFM file manager and then installed a few of the Nautilus FM options that were in the list.
By the way, thanks for the info on the sources.list location, I was not aware of that file.

Now is it possible that Nautilus FM library's might not be compatible with my version of LXDE Lubuntu? I thought you could install any file manger you wanted. I kind of need Nautilus for Truecrypt to mount as it needs certain library's that Nautilus uses. Or else I think I could get a script to force truectypt to work with PCmanFM.

> **Zill said:**
> 
My point was that you will create many problems if you add repos for other releases to your sources.list as this will confuse the package manager and cause system breakage.  Similar problems *can* arise if you add PPA sources as these can sometimes bring in dependencies with the "wrong" version(s) for your release. I didn't touch the sources.list, but I'm glad you mentioned that. I wasn't aware that there were specific repository's for each distribution. I thought everything ran on any distro. Good info, thank you.

I wonder if I should try to troubleshoot this blank screen issue or if I'm pressing my luck too soon with regard to my lack of knowledge. Maybe I should reinstall the OS? Then again, after reading what DuckHook said about the fact that Linux usually retains it's stability even though the users sometimes hack their account.. (as I obviously have done), Maybe my issue is a matter of just uninstalling something. I'm not sure why the recovery didn't fix it. I also tried to boot a previous date presented by the recovery boot list. Looks like this is going to take some manual labor. :p

---

### Post by squakie on 2012-12-07
> **JKyleOKC said:**
> Sure thing. G-E hired me originally to write the service manuals for that first video terminal, the Datanet-750, which actually used a small consumer TV as its monitor in the prototype version. Memory was a sonic delay line, and the device was the first one G-E built that used integrated circuits instead of discrete transistors. Most of the crew I worked with are gone now, and I myself am a bit creaky around the edges, but hanging in here with you young whippersnappers keeps me alive!

Fantastic work Jim!  On one hand I know some would say "thank goodness", but me - I miss those days.  To me those were the days of really working on a computer.  When the Level/6 was made into the communications front-end for the 6000 series on up, it was named Datanet, and the adapter(s) continued with that name until the day Bull pulled out of the U.S..  It's an honor to meet someone who did all that work!

---

### Post by DuckHook on 2012-12-07
> **starstreams said:**
> I wonder if I should try to troubleshoot this blank screen issue or if I'm pressing my luck too soon with regard to my lack of knowledge. Maybe I should reinstall the OS?

If you have little significant data on the system, then I would suggest a reinstall. You will likely be spending more time trying to figure out the problem than reinstalling. Do you have recent/good backups of your important data?

If you want to try hunting this problem down, then I would suggest that you start a new thread, as the forum admins don't like it when we conflate unrelated problems, especially on threads where the title does not accurately reflect the problem.

If so, please mark this thread solved (it is sorta solved:|, isn't it?) and open a new one.

---

### Post by DuckHook on 2012-12-07
I don't go back quite that far. Sonic delay line memory puts you back there in the Late Triassic. But I do remember the first computer our little firm ever bought to do payroll. It was a massive console thing with magnetic core memory and built-in line printer. I remember watching as a technician opened it up one time, marvelling at all the tiny exquisite little cores, all strung together by Scandinavian seamstresses. It probably weighed over a ton. I remember someone accidentally backing into it with a forklift. It didn't budge. Not one inch.

About three months after it was installed, we started getting wonky results. Tech after tech couldn't figure it out until an old shaggy Hungarian guy who had escaped after the '56 uprising thought he could fix it. He went out to his car, walked back in with a 24 lb sledgehammer and, over the literal screams of his boss, promptly proceeded to give it a whack on the backside. Well, damned if it didn't do the trick. A rolling memory test confirmed that the thing was back to true. When we asked him what he'd done, he explained that in London where he'd trained, seasonal temperature fluctuations would sometimes twist some of the cores out of alignment. The cure was to impart a sharp vibration to them and they would naturally realign. I'll never forget the look on his boss's face as he gave his explanation.

Gawd, I'm going to miss this thread.

---

### Post by Noor1101 on 2012-12-07
> **DuckHook said:**
> 
Gawd, I'm going to miss this thread.

Maybe a "Computer History" subforum within the "Specialized Discussions" section would be a good idea?

---

### Post by JKyleOKC on 2012-12-07
I'd go for that special forum section idea! Personally I'd love to get my memories of those days into an archive or two; it was a rare opportunity and there are all too few of us who lived those days left to tell what it was like!

---

### Post by Bashing-om on 2012-12-07
Ok, I also would like to continue this discussion - nostalgic ? who me ??--
how bout spector 440 , neax machines, or rex and lex prologs ??

How may know that Verizon was initially the communications systems for Southern Pacific RailRoad ?(Southern Pacific Communications) -> GTE -> sprint -> sprint/GTE -> US Telcom/sprint -> GTE/US telcom -> Verizon.
I was around in the days prior to satellites ! Or fiber optics ! Now, getting those infrastructures up and WORKING with hundred year old technologies was daunting to say the least. Back in those days --- What is a cell phone ? We developed it all and the networks to support to all. Could not have been done with out also developing the computer systems and programming to make it all happen !

---

### Post by DuckHook on 2012-12-07
If any of the forum admins are following--how about it, guys?

And what would we call it? I propose: "Geezers and Wheezers"

P.S. This thread has now been completely, thoroughly, absolutely and positively hijacked.

---

### Post by Zill on 2012-12-07
> **starstreams said:**
> ...Now is it possible that Nautilus FM library's might not be compatible with my version of LXDE Lubuntu?...
Nautilus *is* a file manager but is generally referred to as simply "nautilus" rather than "Nautilus FM". This might seem pedantic but when you want to install software it is generally best to use the core package name.  All the other suffixes relate to "add-ons" for the core package.  You generally start with the core package and then add any others you find you *need* later as you go along.

I am not sure what the cause of your problem is but it *may* be attributable to adding Gnome applications to a LXDE desktop environment.  While it is *sometimes* possible to mix applications intended for different DE's, this can cause problems and will certainly add "bloat".

Nautilus is a Gnome application and therefore works best in a Gnome system.  If you add it to an LXDE system then installing nautilus will drag in loads of other Gnome applications as dependencies.  All these extra packages, intended for a different DE, *may* potentially interact adversely and cause problems.

Until you have more Linux experience I do recommend that you only use applications intended for your (LXDE) system.

---

### Post by squakie on 2012-12-07
> **DuckHook said:**
> I don't go back quite that far. Sonic delay line memory puts you back there in the Late Triassic. But I do remember the first computer our little firm ever bought to do payroll. It was a massive console thing with magnetic core memory and built-in line printer. I remember watching as a technician opened it up one time, marvelling at all the tiny exquisite little cores, all strung together by Scandinavian seamstresses. It probably weighed over a ton. I remember someone accidentally backing into it with a forklift. It didn't budge. Not one inch.

About three months after it was installed, we started getting wonky results. Tech after tech couldn't figure it out until an old shaggy Hungarian guy who had escaped after the '56 uprising thought he could fix it. He went out to his car, walked back in with a 24 lb sledgehammer and, over the literal screams of his boss, promptly proceeded to give it a whack on the backside. Well, damned if it didn't do the trick. A rolling memory test confirmed that the thing was back to true. When we asked him what he'd done, he explained that in London where he'd trained, seasonal temperature fluctuations would sometimes twist some of the cores out of alignment. The cure was to impart a sharp vibration to them and they would naturally realign. I'll never forget the look on his boss's face as he gave his explanation.

Gawd, I'm going to miss this thread.

I remember the first time I actually to see core as well - most people for the last God knows how many years have no idea what that really was.  They have no idea of cards and backplanes that were literally wire-wrapped like they used to do on their beginning electronics kits until breadboards came out.

I remember having a problem on one of the Level/64's from Honeywell - I think it was a 64/40  - and just couldn't figure it out.  We had a very well respected service engineer in those days, and he even got stumped and just kicked the skin on the service processor and bingo!  everything was fine from then on.  You just never knew!

Jim - I remember a lot of those old removable disks from Homeywell/CDC, etc..  I think back to when several kilobytes was a lot on a mainframe, when a couple of 10-meg disks was all you needed, yet they did a lot of computing!  I remember spinning down one of those dudes (specifically the system drive I built the OS from) and when I spun on the top and lifted it off the spindle, the damn thing fell apart and I had platters and balance weights all of the floor, and this sinking feeling of "well, I've got a lot of hours of work to do now!".  I firmly believe that if the "kids" now had to go back to that, learning the idea of finding every byte or nibble you could shave off a program, learning to do your own overlays before the OS could do it for you, etc., that they'd be a lot better off.  But then again, I don't understand much of this "new-fangled stuff" they are doing now yet - not sure I'll ever take the time again to learn things like that.  Those days being a programmer really meant something - now, with all respect to those who do the fantastic programming we see - it just isn't the same.  I guess in some ways it's magnitudes above what we used to do just in a different way.  But with some of the case tools that have been around, not to mention programs that basically write the OS for you, it's a really different, and I'm sure very spectacular and just as exciting world as we had.

+1 on the "old farts" forum.  I don't go into the engineering side as far as you seem to, but it was so much fun work I think.

---

### Post by starstreams on 2012-12-07
> **DuckHook said:**
> If you have little significant data on the system, then I would suggest a reinstall. 

Yep, I'll probably reinstall and and worry about troubleshooting down the road if the issue ever comes up again. 
At least I'll be more experienced. I have no data on the system anyway.

[COLOR=Blue][B]
Thanks again to everyone! I've marked this thread at solved. [/B][/COLOR]

@ Zill 
Thank you for that last follow up post #32, Much appreciated. 
If I didn't name anyone, please pat yourself on the back for me..hehe. You guys were gold!
I don't know what this popcorn means, but it sounds good right about now. :popcorn:

---

### Post by JKyleOKC on 2012-12-08
> **DuckHook said:**
> If any of the forum admins are following--how about it, guys?

And what would we call it? I propose: "Geezers and Wheezers"

P.S. This thread has now been completely, thoroughly, absolutely and positively hijacked.I gotta apologize to starstreams and to forum staff for introducing the historical element. During the 15 years that I ran CLMFOR (later renamed SDFOR) on CompuServe, thread drift was a constant there. We all took it for granted.

I do hope that Forum Staff go for the suggestion. It might even help in the support mission of the forums as an entity, by giving a place to collect background information that can help newcomers put everything into perspective.

---

### Post by oldos2er on 2012-12-08
You could always start a thread in the Community Cafe. Or a google+ circle if there isn't one already.

---

### Post by squakie on 2012-12-08
Anybody else remember the old Singer (yep, the sewing machine company!) computers?  I had a chance to work as a programmer on one of those sometime back in the very early '70's and I'm sure glad I didn't make that mistake!

---

### Post by starstreams on 2012-12-09
> **JKyleOKC said:**
> I gotta apologize to starstreams and to forum staff for introducing the historical element.

It's me that needs to apologize for not emphasizing  how much I truly appreciate veteran-computer guys like you JKyleOKC showing up in my thread. Thumbs up! 

So much of the important rudiments get lost as software and technology like calculators teach us how to move backwards and forget. 
I think the historical conversation "was" very relevant to the post because it brings ..even new users like me back to the fundamental roots (terminology). 

When I got into computer repair in 2001, I could call almost any support number or go into a store like Best Buy and people know what they were talking about at the hardware level. Not the case anymore because so many have forgotten the basic foundation, or just never knew it. I actually only started using computers in 1998 so I'm a baby, but I hit it really hard and never stopped. 
Long story short, I think it's healthy to read historical posts because it exposes users like me to older terminology which I think are critical foundations to learning and is why I insist on learning Linux terminal commands and scripting very soon. 

No need to apologize, we can only benift from historical concepts especially in this context. 

Please carry on...

---

### Post by squakie on 2012-12-10
Much more thanks should go to Jim - he was in on the ground floor of some very exciting engineering things.  He was one of the true engineers and pioneers.  I relied on people like him for tech support!  I was just a programmer/analyst turned systems programmer and systems administrator way back in the early 70's and on up.  Although I must say that did involve a lot in those days - you had to know the hardware, the various communications protocols(the most common were sync, bisync and async), terminals, terminal "servers", multiplexers - well, the list goes on and on.  We did have some exciting times, and I remember so fondly making our own computers - not like today with compatible motherboards, etc., but rather with buy a bare board, populate it (solder all the components on, solder the through-board connections, etc., make you own cables, etc.) and then trying to figure out how to make anything run on it, writing your own floppy disk drivers, etc..  When the first IBM PC's came on the market we were amazed - and 64 KB of memory!  Hard disks?  My first hard disk for my personal PC was a whopping 10meg (and that was BIG in those days) and sounded like a dang airplane when it spun up.  At work we had to plug scopes in to trap the data (hexadecimal mind you - our second language along with binary and some actual English!) on the communications lines so we could see what was happening when we had an error.  Doubt anyone but the true engineers do that now.  Did you know that in those days (yes, there were punched cards) you could punch up a deck of cards, turn on a radio, and actually listen to the computer play songs?  We used to do that at Christmas.  Graphical printers?  We had plotters, we had the early dot-matrix, but mainly big old line printers (over 1200 lines a minute).  Put in the right program, get ready to eat about 10 very expensive ink rolls (they weren't only $40 or $50 each - they were more), then set aside 5 or 6 hours and you could overprint using just the characters on a print belt.  Print several long pages, join several of these long lists side to side, and you got a 6' by 4' (or larger) image that when you stood back about 8 feet or so looked like a black and white picture of a skier on a mountain.

Don't ask me how we did any of that back in those days - I don't remember any of it!  There was a lot of hard work, long hours (isn't that just the nature of IT?) but it was fun.

The only thing I didn't like was being on-call 24/7/365 and needing to be either 15 minutes or less away from the computers or a terminal of some sort I could use.  Most of the time for the types of things we did required being on site and being pressured about how much time they can't afford to lose.  These also usually happened about 2 in the morning.

I am far from alone - there are thousands upon thousands of us out there.  Add to that the programmers who knew every byte of their code, knew how to read a dump to debug, and there are probably millions.

But we're antiques now.  Things have changed so much over the last 10-20 years it's almost not recognizable.  I know todays group of tech heavys have to know an entirely different skill set, do some entirely different things, accomplish some amazing things, all with a background that goes back a long way - curiosity, logic, getting a kick out of "making it do that", and even enjoying the long and often strange hours.  It's just a completely different game from when I was out there.

Jim is someone to be admired - he wasn't one of the common folk like me.  He was truely working on some amazing things.  Things he did laid the ground work for where things have come to today.  I got to use some of the things he worked on but from a user standpoint, not the engineering side like he.  I noticed that duckhook, bashing-om, etc., appear to be more in Jim's realm as well.  I was a "user" in the sense I used what they developed, not a maker and engineer as they were.  My hats off to all of them!

So much has changed now, and I never kept up.  I guess once I was done working I just thought "seems too much like work" ;)

---

### Post by Bashing-om on 2012-12-10
There was an adage back in that day "out for two years and never get caught back up" That is an indication of how rapidly technology was developing ! Me I dropped out to go to college, I had an intense desire to know why, and after the quiet academic episode choose not to go back to the rat race. Even though I did miss those adrenalin rushes !



[INDENT][INDENT]It was fun ! <== BDQ
 
[/INDENT][/INDENT]

---

### Post by JKyleOKC on 2012-12-10
> **squakie said:**
> Jim is someone to be admired - he wasn't one of the common folk like me.  He was truely working on some amazing things.  Things he did laid the ground work for where things have come to today.  I got to use some of the things he worked on but from a user standpoint, not the engineering side like he.  I noticed that duckhook, bashing-om, etc., appear to be more in Jim's realm as well.  I was a "user" in the sense I used what they developed, not a maker and engineer as they were.  My hats off to all of them!I disagree with that first sentence. I was just a tech writer, translating engineeringese into the language of the real heroes: the working stiffs in the field like Squakie who kept the tape reels turning and cleaned up ground loops.

Yes, I wrote the service manuals for the first raster-based video terminal, but the real genius there was a fellow named Al Cuccio, the project leader, and later the head of technical operations for Seagate. The only real innovation I did was a skunk-works project to teach computers to do my job for me; that led to something I called ADEPT (Automated Document Editing and Production Technique) which let four of us in Oklahoma City outperform 52 people in Minneapolis in the production of service manuals. It was a sort of precursor to what we know now as Desktop Publishing but it ran on a mainframe. Creating that over a two-year period is what got me into software and turned me into a user of Multics, the pappy of Unix and grandpappy of Linux. I still have a few Multics manuals; anyone who's read "man pages" would feel quite at home with them.

Along the way I had to teach myself the rudiments of system administration and learn assembly language programming. I wound up writing my own assembler program for a "communications controller" that I managed to get the use of for a year or so and turn into a time-shared CPU with its own hard disk -- a mammoth half-megabyte or so device that was larger than a walk-in refrigerator. I had to write the disk driver for it to make it work at all. Yep, those were fun times! But all the details I had to discover for myself in those days made it much easier to keep up with the industry as it progressed over the quarter-century I was part of that plant, and later as it exploded to take over the world.

The most important thing I learned, though, was the concept of "paying forward" for all the help I got from others along the way. That's what I try to do today in whatever time remains to me, and something I sincerely hope all who read this thread will take up to make sure that the hard-earned knowledge over the years doesn't get lost, buried under all the new developments that continue to pour out of the labs!

---

### Post by DuckHook on 2012-12-10
> **squakie said:**
> ...I noticed that duckhook,...appear to be more in Jim's realm as well.

Whoa! I'm not even in the same league as you guys... just an Ordinary Joe who has accumulated an eclectic body of knowledge nowhere close to being complete, organized or systematic. As noted earlier in the thread, I was a clueless muggle starting out in '97 who gave up numerous times before finally finding a wand that worked. I wouldn't know where to begin when it comes to coding or scripting, and as to syadmin, would likely fall on my sword before taking on something that complicated. Quite frankly, and without any hint of false modesty, I'm a considerable sad-a$$ when it comes to things technical.

Best description of me, as I suspect it is for many on these forums is: "enthusiast". I like the philosophy behind Linux. It's the world's largest and most sophisticated community garden. We put in what we can, we plant and water and till and cultivate and weed to the best of our ability, we help newcomers with a smile, a kind word and some advice, and then almost magically, we get produce of the most wonderful variety, colours and flavours. What's not to like?

It doesn't always work out. Occasionally, the fruit is sour or the vegetables have worms, but this is only to be expected and a small price to pay for the bounty of the land.

Geez. Now look what you guys have done to me. Gone all maudlin, I have.

Request to the forum gods/goddesses, if any are listening in...

Somehow, this thread seems to have struck a nice chord. Might we mortals prevail upon you lords and ladies to move it to the Community Cafe forum, and to change it's name to something that you deem appropriate? I know that it is a drifted thread, but would hate to try starting another just to lose the tone and texture already here.

---

### Post by squakie on 2012-12-11
+1 on playing it forward, Jim.  I try to do that, but this linux "stuff" is still a little cryptic to me - because I just haven't taken the time to dig in and learn what's happening under the hood.  I'm getting a little old for some of it, but maybe it's about time I wake up the old mind, get a couple of linux tech books, set up an old system just for play, and just get in and learn it for once.  There was a time with Unix where I was ok, but that's been like 18 years ago.  My memory filled up, some failed, and I don't have swap to hold some of it.  So, a lot of things have been "flushed" from my head and unfortunately left all kinds of little pieces of useless information that just don't add up to much anymore.  ;)  Sometimes I think it would be fun to get into the kernel, device drivers, etc.  Other times I think "I paid my dues long and hard a long time ago!".  The end result is increasing unfamiliarity with so much!

BTW - you'd like something that happened to me years ago.  I was having problems with one of the communications front-ends (Datanet) and finally gave up and looked in the manual.  Well, the left page showed the error, while the left side, still in FRENCH, explained it!  I called national tech support out in Boston, they checked their manual, and said "the damn page is in FRENCH!".  I had to laugh! ;)

---

### Post by Noor1101 on 2012-12-11
I agree with DuckHook: if there's no chance of creating a special subforum for these historical discussions, a good alternative would be to move the posts/thread to another, new, thread in the Community Cafe.

I'm not an expert at all, but I am really interested in all that's being told here.
My experience with these historical backgrounds lies solely in my being a granddaughter of two IT "pioneers" who worked in computing since the 40's/50's. 
I'm still proud of one of my grandfathers for becoming 3rd in a (national, I think) computer chess programming competition in the 70's (though I wasn't around yet) :KS

[SIZE=1]Here I can't go on without saying [SIZE=1]"rest in pe[SIZE=1]ace,[/SIZE][/SIZE] father's father ". His funeral is tomorrow.

[/SIZE] I have fond memories of an amazingly realistic flight simulator in the 80's, and the still-intriguing workings of a plotter.

I guess I'm an interested baby noob compared to you all :)

I would LOVE to read more, even though I don't have the knowledge to talk along.

---

### Post by Noor1101 on 2013-04-23
I'd like to propose the same question again, even though a couple of months have passed.. Could a special area of this forum be designated for historical discussions (/ personal stories / (general) computer anecdotes)?

I am very interested in (reading about) this area of computing "sociology" (:D) and I also think it can have a function by keeping the level of interest / motivation up for frustrated users (like me, sometimes) :)

---

### Post by coldraven on 2013-04-23
Apart from tinkering with Linux there are also some good productivity tools to be had.
Install Artha 
```
sudo apt-get install artha
```

Then highlight any word and press Ctrl-Alt-W to get a definition. See the screenshot :)
You can use wildcards to solve crossword puzzles. So searching for "ad???e" gives the following results.
adduce 
adelie 
adhere 
adjure 
admire 
adnate 
advice 
advise

Sorry to be a bit cheeky :)

---

