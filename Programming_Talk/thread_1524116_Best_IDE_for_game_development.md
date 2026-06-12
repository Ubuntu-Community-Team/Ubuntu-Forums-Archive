---
title: "Best IDE for game development?"
date: 2010-07-04
forum: Programming Talk
---

### Post by pato wlmc on 2010-07-04
Well, 4 months ago, i used to dual-BOOT windows and Ubuntu, but like a month ago i decided to finally change to Ubuntu.

Everything is really perfect by now, it's really all I've been dreaming for, and maybe more.  

But i'm ready to continue working on c++ game developing. In MS, i used to use wxDevc++ but, seems like there's isn't a Linux version.

So all i want to know, is if someone could tell me a great IDE for game development on Linux.

What i'm looking for?

[LIST]
[*]Ease of access to game development libraries ( Like allegro )
[*]IF POSSIBLE, an IDE specially designed for game development 
[*]No compatibility problems if i ever wanna move my project to WIndows
[*]....Well that's pretty much it =p

[/LIST]

Thanks. and sorry for my bad english jeje. =p

EDIT #1; NOTE: I'm really a newbie to game development so i don't really know that much about IDE'S an considering that i'm new to Ubuntu =S....  So please talk to me like if i were a 5 year old kid xD....

---

### Post by WRDN on 2010-07-04
I've always found CodeBlocks to be a decent IDE. Netbeans is also very nice.

I don't know of any IDEs designed for game development, but all can be used to add the required libraries for a particular engine/API etc.

The most important thing I've found for fast development is the Code Completion support. Out of the options noted above, Netbeans has the best code completion I've found.

As for cross platform goodness, you could use something like CMake: [http://www.cmake.org/](http://www.cmake.org/)


On a slightly different topic, which I hope you know already, if you're doing any work you don't want to lose, get it under VERSION CONTROL (!!!), such as [Subversion]("http://subversion.tigris.org/") or, better yet, [git]("http://git-scm.com/"). The former is a centralised version control system (CVCS), while the latter is a distributed VCS. Pick which ever you would prefer, both are in the repositories.

---

### Post by Admiral Yi on 2010-07-05
If you really liked DevC++, you can run that under wine. I used to use it myself when I did C++ developing, and it ran fine.

If you don't know what wine is, its a program that can run some windows only programs on Linux. See [http://www.winehq.org/](http://www.winehq.org/) for more info.

---

### Post by Simian Man on 2010-07-05
Games are really not that different from other software, so there's really no point in having an IDE designed specifically for gamedev.  Also the ability to link to external libraries is a necessity for virtually any project, so any decent IDE will support linking to Allegro.

As for actual IDEs, I use Eclipse for my game, but Netbeans and Code::Blocks are also good.

Also definitely heed WRDN's suggestion of using source control.

---

