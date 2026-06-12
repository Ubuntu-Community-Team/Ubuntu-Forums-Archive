---
title: "Windows VB User wanting to develop apps for Ubuntu"
date: 2005-09-21
forum: Programming Talk
---

### Post by Lem on 2005-09-21
Ok.. Relative Linux newb - Been running a few weeks on a couple of epia boxes - have a nice funky desktop, and am happy doing shell scripts etc. So far, so good.

For the final transition from windows, I'd like to start developing apps for Linux. I used to do most of my apps in VB - mainly because I tend to link into other apps, generally Excel and AutoCAD as well as firing SQL at various databases.

Assuming I want to do something similar in Linux (although levering QCad and OOffice instead) - what would be the best way to go?

More than happy to learn a new language, but the easier the better please!  ;-)

---

### Post by toojays on 2005-09-21
If you specifically want to deal with those applications, it might be best to find out first what languages they recommend for interfacing.

Otherwise, the general consensus in Ubuntu-land is that Python is the most versatile language to start with.

---

### Post by davmac on 2005-09-21
There's part one of a good article at [http://www.linuxjournal.com/article/8550](http://www.linuxjournal.com/article/8550) about writing applications to control OpenOffice.

Given your VB background I would have thought the RealBasic ([http://www.realbasic.com/](http://www.realbasic.com/)) would be worth a look too.

HTH,

Dave Mac

---

### Post by Lem on 2005-09-21
Realbasic looks superb as I'm actually trying to port a number of windows vb apps to linux in order to improve stability (that old windows chestnut!) and lower costs.

Cheers  :smile:

---

### Post by David Marrs on 2005-09-21
Also keep an eye on the Mono project; they're writing a VB.NET compiler. Even now you *should* be able to run VB.NET apps under Mono that have been pre-compiled in Windows for the .NET Framework.

---

### Post by Lem on 2005-09-21
I've been watching the mono project with interest. As you state, it stills requires applications to be compiled on a windows machine - so you're not 100% certain it going to run on linux until you fire it up.

However, if I don;t get on with realbasic (I have it running here and it's looking good), then I'll proabably return the idea of running my apps via mono.

---

### Post by RagingFuryBlack on 2005-09-22
Gambas is very similar to visual basic.  Give that a shot.

---

### Post by Zonkle on 2006-01-17
[QUOTE=Lem]I've been watching the mono project with interest. As you state, it stills requires applications to be compiled on a windows machine - so you're not 100% certain it going to run on linux until you fire it up.[/QUOTE]

It doesn't require applications to be compiled on a windows machine ! You can compile and run everything from Linux .... but what he meant is even programs you compiled in Windows can run on Linux .. but I dunno about that since I didn't try it ... but of course you can compile in Linux.

---

### Post by John Dooley on 2006-01-18
I used and liked VB when I was programming in windows. When I moved to Linux/Unixed I missed the neat way to quickly construct GUI.

I have recently learned Python which  reminds me a lot of VB. Within the last week I am triying out wxPython and boa-constructor.

boa-constructor is an IDE like the Visual Basic IDE. It lets you do menus, status bars, dialog boxes, etc. wxPython is a wrapper on top of the wxWidgets which is the Linux "MFC". When using boa-constructor and wxPython you don't have to worry about wxWidgets. 

The nice think about wxPython and Python is that it will run under Linux, Windows, and MAC X OS.

Ubuntu has very good Python support. I was able to use Synaptic to install everything I needed- wxPython and boa-constructor. Python is installed by default when ubuntu is installed.

Manning is coming out with a wxPython book this month. For the Python language, I like the Apress book Beginning Python by Magnus Lie Hetland. Of course, there is lots of good stuff on line if you don't want to buy the books.

I heard there was about 3 milion VB programmers world wide. MS is probably pushing C# more than VB nowadays. Python has between 1 milion and 500,000 but is growing in popularity.

---

