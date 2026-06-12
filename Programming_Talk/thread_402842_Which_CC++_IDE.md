---
title: "Which C/C++ IDE?"
date: 2007-04-06
forum: Programming Talk
---

### Post by Tyscorp on 2007-04-06
I have recently switched to Ubuntu from Windows. I want to know which C/C++ IDE I should get and how to install it. Please bare with me as I am quite new at Linux. I have tried Anjuta but I don't like it. Its not very good in my opinion. I cant even work out how to compile.

---

### Post by lawentzel on 2007-04-06
Most people compile their programs at the command line.  In Anjuta there is a "Terminal" tab that allows you to do so.  I have clicked on Build in Anjuta, but I am still pretty new myself and haven't figured out why that isn't working or how to configure it so it will.

Next, a lot of people have already asked this question.  If you click up on search area, and type in IDE you will find a number of posts which answer this question.  I think Anjuta will do everything I need, I just haven't spent enough time figuring out how to do so.

The general consensus is Windows does seem to have things well integrated so you never have to leave your IDE to compile or debug.  Is Linux there?  Probably after some configuring.  Maybe a lot of configuring.  But you tend to have a lot more flexibility with it.

Lee

---

### Post by smokey edgy on 2007-04-06
Personally, I would suggest using Eclipse with the CDT plugin. You get a good chunk of the benefits that Java developers get (the obvious syntax highlighting, auto-completion, refactoring aids, etc). I've used it in Linux for a bunch of projects and its pretty good.

However, there's nothing like the feel of writing C/C++ code in VI with the command line make and compiler. ;)

---

### Post by trucutu31 on 2007-04-06
> **smokey edgy said:**
> 
However, there's nothing like the feel of writing C/C++ code in VI with the command line make and compiler. ;)


Yes, or writing it in Emacs .... :)
More seriously, in general, a good text editor with the command line gcc is often as convenient as an IDE. That's only my opinion...

---

### Post by maxamillion on 2007-04-06
[Geany]("http://geany.uvena.de/") .... its in the repos under universe iirc

---

### Post by j_g on 2007-04-06
Aha. Yet another example of _the_ question of the week, as described in my other posts. This weekend, I'll try to put together a FAQ for Windows programmers moving to Linux, so if you can wait until then, I'll give you a lot more detailed information about this.

---

### Post by trucutu31 on 2007-04-06
Sometimes, you can heard of Kdevelop on other threads.


> **maxamillion said:**
> [Geany]("http://geany.uvena.de/") .... its in the repos under universe iirc

Hey, it's looks interesting ! Did you test/use it ?

---

### Post by twentytortures on 2007-04-06
I also switched from using windows to ubuntu so I know how it feels when you want to have the same environment for both. I use Code::Blocks as my IDE because it runs on both Windows and Linux so I have the same interface no matter what platform I am using!

You can get Code::Blocks from [http://www.codeblocks.org](http://www.codeblocks.org) in an easy to install .deb. Just make sure that if you do decide to use this IDE to get a nightly build, just go into the forums and click the nightly build link. Or even better, I'll get you one. 

[http://forums.codeblocks.org/index.php?PHPSESSID=60ded4c476865fc053928a977e7f95ff&board=20.0](http://forums.codeblocks.org/index.php?PHPSESSID=60ded4c476865fc053928a977e7f95ff&board=20.0)

I've used the MSVC IDE, Ajunta, Kdevelop, dev-c++, and clodeblocks. So far codeblocks is my favorite :) .

---

### Post by DC@DR on 2007-04-06
I would definitely recommend [CodeBlocks](http://www.codeblocks.org), it's such a great C/C++ IDE, open-source, mature and full of features (and use the nightly builds, since it has the latest fixes and features of all)

---

### Post by GeneralZod on 2007-04-06
[KDevelop](http://etotheipiplusone.com/kdevelop-debugging.png) has grown on me quite a lot, especially since I upgraded to 3.4.0 (and threw out most of the toolbar buttons :))

---

### Post by russell.h on 2007-04-06
I used KDevelop, but it seemed bloated.

I used Code::Blocks in windows, and loved it, but the linux version seemed to have troubles. Just general bugginess accross several nightly builds.

I tried Eclipse which seemed very nice, but installing the plugin was a pain (or rather, figuring out how to install it was a pain), and it still seemed more java oriented (btw, is Eclipse written in Java? It "felt" like it).

I used Geany under Edgy and found it quite usable, pleasantly minimal. Great for smaller projects.

However recently I have been using Anjuta (1.2.4a, the one in the Feisty repos) and have found it to be the best IDE I have used in Linux. It isn't as minimal as Geany, but nor is it as bloated as KDevelop (and probably a bit less so than Code::Blocks). It has all the features I need, and really nothing more. That being said it could use a bit of finish around the edges, something that the developers seem to have skipped in favor of a whole new version (2.x is out for testing).

---

### Post by twentytortures on 2007-04-07
You've had problems with bugs in code::blocks? I've only ever experienced one, and it does drive me nuts, never click on some selected text and drag. You'll have to do a ctrl-alt-backspace.

---

### Post by etola on 2007-04-07
I've passed to kubuntu from windows ~1 year ago. I also looked for a good IDE at first 
and tried several. At last I settled on emacs + konsole. I needed to access my office computer thru ssh and trying to work with an IDE to change even a small part of the code becomes really tedious. The advantage of emacs is that you can always use it whenever you want without the need for an IDE interface. Also, it is wonderful. Now, I'm reading my mails, listen to mp3, prepare documents in latex and code a lot using emacs. Just be a little patient in the begining until you get used to shortcuts; then you'll love it.

---

### Post by samjh on 2007-04-08
I use Code::Blocks.  There are some bugs, but no show-stoppers.  It works well in 90% of situations, and the other 10% have work-arounds or have no real impact.

But I use Geany as my general-purpose code editor.  Simple but functional.

---

