---
title: "OpenCL a good idea?"
date: 2007-08-07
forum: Programming Talk
---

### Post by Tripmonkey_uk on 2007-08-07
I've spent the last couple of days thinking up new projects that could be useful to Linux and other open source software. This idea is the one that I think could be the most useful, but I've never programmed anything to do with Jabber myself, so I thought I'd post here to see if you guys think it's possible.

Communication is one of the most important things for any piece of software. Giving users the ability to report bugs, find help easier and to work more as a team, brings big benefits for both developers and users alike.

We have OpenGL for developers to implement graphics & OpenAL for the sound. We also have SDL to take care of audio, 2D video, controls etc. but what about communication? A cross platform Open Communications Library could make it a lot easier for developers to implement communication features into programs & games.

The technology to make up the library is (mostly) already here in the form of the Jabber protocol (for text messaging & chat), the Speex codecs (for VOIP) & IRC (for continues text chat). All have proven themselves to be very good at what they were made to do & deserve to be used a hell of a lot more than they currently are.


[CENTER]**BASIC USAGE**[/CENTER]

A user starts a program which automatically notifies the Open Communications Library (if it's installed) that it's developers have Jabber/VOIP/IRC services available for use and gives OpenCL the address of the server that they are hosted on. OpenCL then connects the user to the services when the program issues it the correct commands.


[CENTER]**EXAMPLE**[/CENTER]

Bob's downloaded a new program for testing..
[LIST=1]
[*]He gets stuck on how to use a certain feature of the program, so he clicks on the programs Help menu and selects the menu option called CHAT. This automatically connects him to the programs Jabber server & main chat room for text chatting with the software's user community.

[*]Bob finds out Joe can help him, but he's having trouble typing at the same time as trying to sort the problem out. He clicks on the next link called VOIP that automatically connects him to the programs VOIP server, where he can now have a live conversation with Joe (who joins too) and gets step by step instructions on sorting the problem out.

[*]They sort the problem but encounter a bug along the way. Bob clicks onto the next option in the Help menu called IRC and is automatically connected to the developers IRC server. He submits a bug report to one of the programs developers and gets back to testing  the new software.
[/LIST]
That's an example of how a normal program could use OpenCL. The software that would probably benefit the most though is games. 

I've put together a quick PDF for the Gamers Example which contains quite a few mock up pictures that I made to try & get my idea across easier. You can download it by clicking [here]("http://gp2x.projectinfinity.org.uk/downloads/GamersExample.pdf")!


[CENTER]**BENEFITS OF USE**[/CENTER]

A lot of the benefits of using something like OpenCL should be quite clear to most people, just by reading the examples provided. There are some less obvious benefits too though..

[LIST=2]
[*]One of the reasons that Ogg Vorbis has been so successful, is that it has two main uses and not just the one. It can be used as a straight replacement for MP3 & other codecs for use within hardware/software audio players, and the lack of restrictions also makes it ideal for implementing  directly into software itself.
Unfortunately Jabber only has the one use at the moment. It might be the best messaging protocol currently out there, but that alone doesn't seem to be enough for a lot of users to swap from the protocols that they're already using. A project like OpenCL could boost Jabbers uptake.
If a Jabber ID's used for in game messaging, desktop messaging and the user can also use it as an OpenID for web pages, then people will be more inclined to use it. One Jabber ID would cover pretty much all the bases.

[*]It wouldn't just be software itself that could take advantage of OpenCL. It could handle link management from web pages too. This would give users an easy way of joining a VOIP server from a gaming clans website etc.

[*]So far VOIP, messaging and IRC have been primary tied to peoples desktops. With the release of devices like Nokia's N800 though, more people than ever are starting to use them on the move. An Open Communications Library would give these devices a stable & convenient platform to work from that ensures compatibility across different devices.
[/LIST]

This has been a fairly quick post but I hope I've managed to convey the idea clearly enough. I can see it in my head fine, but found it very hard to put it to paper (erm.. forum). If anyone can think of a reason why something like this wouldn't work or has anything else at all to add, then please submit it to the comments :)

---

### Post by nicolas2b on 2007-08-07
It exist and it's called DBus, no ?
For the voip and co, it's empathy/telepathy.
Tell if I'm wrong

---

### Post by mostwanted on 2007-08-07
> **nicolas2b said:**
> It exist and it's called DBus, no ?
For the voip and co, it's empathy/telepathy.
Tell if I'm wrong

You're quite right.

Telepathy is the text/audio/video chat API scheduled for some future version of Gnome. The Gnome developers are always raving on about it and it's already available in select apps. This is the site:

[http://telepathy.freedesktop.org/wiki/](http://telepathy.freedesktop.org/wiki/)

Empathy provides Gtk+ widgets for use with Telepathy and DBus provides inter-program communication (so program X knows what program Y is doing).

---

### Post by pmasiar on 2007-08-07
> **Tripmonkey_uk said:**
> I've spent the last couple of days thinking up new projects that could be useful to Linux ..., but I'm not a programmer myself so I thought I'd post here to see what you guys think about it.


I have bad news for you: good ideas are a dime a dozen! :-) Whole point is to create half-usable prototype, so other people can use it, and start adding features. If you cannot start coding, and you hope other people will do it for your idea, you are likely get disappointed. Smart people capable coding it are too busy on their own projects, and people not busy are just learning and not capable to code it. So there. 

I suggest you to learn programming, it is real fun. Then, join existing project to "learn the ropes". Then, chances are you will see real need for something which will have immediately use, and you will hack prototype over weekend or summer, and new project is born. Having solution and looking for a problem to solve is not gonna work.

I might be wrong (honestly I did not spent much time reading details of your idea), but chances are I am not. Every week someone comes with another brilliant idea waiting for others to implement it, and I do not see it happening.

Open source is build on "scratching your own itch". Designing good solution for something you foresee but it does not itch you yet has even own name as [antipattern](http://en.wikipedia.org/wiki/Antipattern) - [YAGNI](http://en.wikipedia.org/wiki/YAGNI) - You Ain't Gonna Need It. So don't worry, many people (including me, couple times :-) ) did exactly the same thing. Just remember YAGNI, and let it go. :-)

Another rule of thumb is, don't try to generalize solution until you have 3 special cases, you ain't gonna guess it right.

Really, learn programming. Python is easy and fun.

---

### Post by Tripmonkey_uk on 2007-08-08
Sorry.. I shouldn't have written that I'm not a programmer. I know well enough that anyone who writes that in a programmers forum will instantly be ignored & repeatedly told to learn programming themselves. I do code in C++ & Python, just never felt the need to write a complete programme myself yet.

It's a shame that you didn't read all of it. If you had you would have noticed that I never once asked for somebody else to do the work for me. I was just wondering if anyone who's coded Jabber servers etc. before could see any reason why this wouldn't work, that's all.
It's called feedback on an idea.


@ nicolas2b
It seems to me that Telepathy & OpenCL are completely different ideas.

Telepathy is a project to stop programmers wasting their time by separately codeing the exact same features into messaging/VOIP software & to all work on these features within a single framework.
It's also not fully cross platform compatible.

OpenCL is about giving the average computer user a way to use these programs & to be able to connect to the servers in a hassle free way, no matter what operating system they use.
OpenCL can be written to take advantage of the presence of Telepathy & to work with it, but it's a completely different thing all together.

---

### Post by pmasiar on 2007-08-08
> **Tripmonkey_uk said:**
> Sorry.. I shouldn't have written that I'm not a programmer. I know well enough that anyone who writes that in a programmers forum will instantly be ignored & repeatedly told to learn programming themselves. 

Wrong. You don't appreciate it, but you are not ignored. I am trying to help you. I am showing you bugs in your thinking. :-)

It is not about "posting in this forum". You cannot lead programming project if you cannot code - the only leadership pattern people recognize is, is "to follow a leader". If you cannot lead, you have to follow. :-)

> I do code in C++ & Python, just never felt the need to write a complete programme myself yet.

You need to produce half-usable alpha version, which people can try and customize to own needs. Until then, it's vaporware. And nobody will do it for you.

> It's a shame that you didn't read all of it. 

I spend all this time to write to you how free software projects work. Not like you would like them to work, but how they work in real life. If I thought you have no merit, I would not bother answering at all (like I did not bothered with another hare-brained project posted today).

> If you had you would have noticed that I never once asked for somebody else to do the work for me.

Sorry for missing something. 
You said you are not programmer, and yet don't expect anyone to code it for you, and don't expect learn programming? How do we get the code?

> It's called feedback on an idea.

You got as much feedback as my time allowed me. I have couple projects of myself :-)

> OpenCL is about giving the average computer user a way to use these programs & to be able to connect to the servers in a hassle free way, no matter what operating system they use.

before you can automate something, you need to *fully* understand it. Don't assume people hacking telepathy are not as smart as you - what you want to do is probably harder that you expect. If you think your project improves on telepathy, learn telepathy first, and think if you can add your features to it, or in next version, or in fork, or reuse some code of it.

As Linus says: "talk is cheap, where is the code?"

---

### Post by pmasiar on 2007-08-08
Just fount on Ubuntu Planet: [How to start your own project](http://www.somethingsimilar.com/wordpress/2007/08/06/how-to-get-your-project-moving-or-my-ego-is-massive-and-you-should-listen-to-me/)

Money para: "The nerds will come to you but you&#8217;ve got to work your *** off first. No one, absolutely no one, who is any ... good will come near your project if its nothing more than a few airy ideas."

---

### Post by Tripmonkey_uk on 2007-08-08
> **pmasiar said:**
> Wrong. You don't appreciate it, but you are not ignored. I am trying to help you. I am showing you bugs in your thinking. :-)


Please don't quote other peoples work & try to fob it off as your own. I've read that programming article too you know :)

> **pmasiar said:**
> 
It is not about "posting in this forum". You cannot lead programming project if you cannot code


Thats funny.. My last project was [**GP2X Standards**]("http://gp2x.projectinfinity.org.uk/news.php").
I had a lot of programmers (over 15) working under/with me & the project was a complete success.
Most (if not all) of the finished work is currently being implemented into the [**Open2X project**]("http://www.distant-earth.com/open2x/"). Hence the reason that I'm looking for new project to work on.

> **pmasiar said:**
> 
You need to produce half-usable alpha version, which people can try and customize to own needs. Until then, it's vaporware. And nobody will do it for you.


When did I ever ask anyone to do it for me?
I asked for feedback on an idea & _that is all!_

> **pmasiar said:**
> 
I spend all this time to write to you how free software projects work. Not like you would like them to work, but how they work in real life.


I've already completed the standards project, as well as successfully creating & running the [Ubuntu-FS]("http://ubuntufs.wordpress.com/") site.
How do I not have real world knowledge??

> **pmasiar said:**
> 
You said you are not programmer, and yet don't expect anyone to code it for you, and don't expect learn programming? How do we get the code?


I never said that I don't expect to learn programming. Where did you get that from?
I've never fully learned programming because I've never needed to. I learn new things as I need them & I'm more than happy to learn programming, _if_ I think that a projects worth it.
I have the books on my shelf to prove it :)

> **pmasiar said:**
> 
Don't assume people hacking telepathy are not as smart as you - what you want to do is probably harder that you expect. If you think your project improves on telepathy, learn telepathy first, and think if you can add your features to it, or in next version, or in fork, or reuse some code of it.


Have you not read anything that I've written??

My project has nothing to do with Telepathy & I certainly don't think I'm as smart as the people hacking that project. In fact I'm pretty damn certain that I'm not.
What I said was that OpenCL could be written to take advantage of Telepathy if it's found to be installed on a system.

I always appreciate it when people take the time out of their busy schedules to reply to my forum posts, but please don't misquote me or simply make stuff up just to try & make yourself look smarter. Trust me it doesn't work.

---

### Post by pmasiar on 2007-08-09
> **Tripmonkey_uk said:**
> 
Thats funny.. My last project was [**GP2X Standards**]("http://gp2x.projectinfinity.org.uk/news.php").
I had a lot of programmers (over 15) working under/with me & the project was a complete success.
Most (if not all) of the finished work is currently being implemented into the [**Open2X project**]("http://www.distant-earth.com/open2x/"). Hence the reason that I'm looking for new project to work on.


You could start with this info in your original post, and I would not associate you with other joker wannabes who are "starting" open source project every week here. Sorry for wasted time - yours, and even more - mine :-(

---

### Post by slavik on 2007-08-09
basically, you want an expanded "help menu"

I guess my question is, when the user involkes that help 'thing', who is on the other end, a support person like what hp/dell/others have on their websites, or like an irc channel?

because 1 would be much easier to do than another, imo. (with irc, you could tell pidgin to join the appropriate channel on the appropriate network, with the former, you'd need the support people :))

---

### Post by Tripmonkey_uk on 2007-08-09
Ok well it looks like I didn't do a very good job of explaining the project. What I might be best off doing is leading you all through my train of thought leading up to me posting in the forum. Maybe people will understand what I'm on about & be able to think up a better way of going about it than I can :)

I was looking for open source versions of programmes for gamers to use. I was hoping to replace [Xfire]("http://www.xfire.com/") & [Teamspeak]("http://www.goteamspeak.com/") with open source software like Jabber that could do the same job, or an even better job if possible?

I found [GOIM]("http://goim.sphene.net/wiki/show/About") as a replacement for Xfire & [Mumble]("http://mumble.sourceforge.net/Main_Page") as a replacement for Teamspeak.

After reading up on these two programs I started to think that instead of programmers having to write basic chat services to put into their games, they could just as well use Jabber chat rooms to do the exact same thing.. but better.

Using jabber chat rooms within games would give users & developers some advantages over normal gaming message systems:
[LIST]
[*]It would allow gamers to add people who are on the same game server as them, directly into their desktop messenger contact list.

[*]It would save developers the hassle of writing an in-game messaging service from scratch.

[*]Jabber is open source, therefore always being improved upon.

[*]Gamers would also gain the usual advantages of using Jabber vs proprietary formats on their desktop, including using it as their [OpenID]("http://openid.net/") for logging onto gaming sites (when OpenID gains in popularity).
[/LIST]

That's basically how I started with this idea. I then expanded it onto including VOIP with the Speex codecs, but using the gamers Jabber ID as the VOIP user name instead of having two separate ones.
So far we have one Jabber ID being used for desktop messaging, in-game messaging, VOIP & as an OpenID for logging into websites.

Of course the hardest part is to actually get the gamers connected to the Jabber chat rooms in game without any intervention on their part. It would need to be instantaneous & invisible to the user.

Example:
Joe chooses to join the Blue team on a multi-player game server, and is automatically connected to the blue teams Jabber chat room without manually having to enter the chat rooms address his self.

What I meant by OpenCL, was either a library or API that would handle these connections.

That's the basics of the idea anyway. So as not to confuse everyone again, I'll leave it at that for now & let you guys share your thoughts :)

---

### Post by slavik on 2007-08-09
> **Tripmonkey_uk said:**
> Ok well it looks like I didn't do a very good job of explaining the project. What I might be best off doing is leading you all through my train of thought leading up to me posting in the forum. Maybe people will understand what I'm on about & be able to think up a better way of going about it than I can :)

I was looking for open source versions of programmes for gamers to use. I was hoping to replace [Xfire]("http://www.xfire.com/") & [Teamspeak]("http://www.goteamspeak.com/") with open source software like Jabber that could do the same job, or an even better job if possible?

I found [GOIM]("http://goim.sphene.net/wiki/show/About") as a replacement for Xfire & [Mumble]("http://mumble.sourceforge.net/Main_Page") as a replacement for Teamspeak.

After reading up on these two programs I started to think that instead of programmers having to write basic chat services to put into their games, they could just as well use Jabber chat rooms to do the exact same thing.. but better.

Using jabber chat rooms within games would give users & developers some advantages over normal gaming message systems:
[LIST]
[*]It would allow gamers to add people who are on the same game server as them, directly into their desktop messenger contact list.

[*]It would save developers the hassle of writing an in-game messaging service from scratch.

[*]Jabber is open source, therefore always being improved upon.

[*]Gamers would also gain the usual advantages of using Jabber vs proprietary formats on their desktop, including using it as their [OpenID]("http://openid.net/") for logging onto gaming sites (when OpenID gains in popularity).
[/LIST]

That's basically how I started with this idea. I then expanded it onto including VOIP with the Speex codecs, but using the gamers Jabber ID as the VOIP user name instead of having two separate ones.
So far we have one Jabber ID being used for desktop messaging, in-game messaging, VOIP & as an OpenID for logging into websites.

Of course the hardest part is to actually get the gamers connected to the Jabber chat rooms in game without any intervention on their part. It would need to be instantaneous & invisible to the user.

Example:
Joe chooses to join the Blue team on a multi-player game server, and is automatically connected to the blue teams Jabber chat room without manually having to enter the chat rooms address his self.

What I meant by OpenCL, was either a library or API that would handle these connections.

That's the basics of the idea anyway. So as not to confuse everyone again, I'll leave it at that for now & let you guys share your thoughts :)
to be honest, you're not the first to come up with such an idea ;)

Uplink uses IRC. :)

---

### Post by AlexThomson_NZ on 2007-08-10
I think I see what you're driving at, but sockets programming (IMHO) is fairly trivial (at least as far as I got), and wrapping this in libraries I think might take away some of the flexibiliy, and add complexity for those who might only need to implement a simple protocol.

// Disclaimer: My personal bias is toward one tool per job (ie. I'd prefer a good, efficient browser than one that lets leave VoIP messages on another users bittorrent client, etc.) :)

---

### Post by slavik on 2007-08-10
also, libpurple is a nice library :) no need for a new one.

---

