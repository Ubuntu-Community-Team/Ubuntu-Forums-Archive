---
title: "Programming Language Dilemma"
date: 2007-05-19
forum: Programming Talk
---

### Post by ankursethi on 2007-05-19
I've been dabbling with various programming languages for the past few years(C/C++/Perl/PHP/Python), being most proficient in C and PHP, although I dislike PHP. All the programming I've ever done is small puzzles which keep floating around the Internet. I also haven't done any GUI programming. Now I want to get down to some serious development. The problem is that I don't want to use C because it's too basic, at least for a beginner like me and PHP works best for the web.

I want to build, say, a simple RSS reader, just to get the hang of the development process and the tools most often used (make, cvs/subversion etc.). Which language will be the best to do it in? I'd rather put up with the sluggishness of an interpreted language like Python than wrestle with C. I don't have any problems with learning a new language and/or toolkit.

Also, I want to learn C# (under Mono, of course), but I can't seem to find any good books that'd help. I do not have any problems with learning a new language, so I'd prefer a book or resource that's concise, not those "arrays are a collection of similar variables" type of books. GTK# has good documentation so I can learn that from the online docs.

GM

---

### Post by Mickeysofine1972 on 2007-05-19
check this out:

[http://ubuntu-gamedev.wikispaces.com/](http://ubuntu-gamedev.wikispaces.com/)

Mike

---

### Post by ankursethi on 2007-05-19
I don't really want to do game development. I just want books/tutorials on C# and some advice on which programming language to use for a simple desktop app.

---

### Post by Rab22 on 2007-05-19
> **ankursethi said:**
> I don't really want to do game development. I just want books/tutorials on C# and some advice on which programming language to use for a simple desktop app.

I would say it really depends on what you want to build.  C would probably be the best -- but it takes longer than some of the higher level languages.  

I have seen Python used to make some very great applications. 

Since GNOME now uses mono, C# would be another great language. I really like C# but I'm a bit skeptical since MS really created it.

 Java is another possibility.  Personally, I don't like it for a native desktop application.  But then, I haven't really tried developing on it in a while.


That's just my two cents and it really comes down to what you feel comfortable using and what you know well.

---

### Post by ankursethi on 2007-05-19
Thanks.

Anybody know of good resources to learn C#? I really want to look into it, but there are too many useless books out there.

---

### Post by WW on 2007-05-19
Sorry, I can't help you with C#.

On the other hand, Python and PyGTK are excellent tools for building a desktop app.  For an RSS reader, you can use [Feed Parser]("http://www.feedparser.org/"), which is available in the Ubuntu package **python-feedparser**.  This bit of interactive python shows an example of using feedparser to print the titles of the news entries from the Planet Ubuntu RSS feed.
```

~$ [color=blue]python[/color]
Python 2.4.3 (#2, Oct  6 2006, 07:52:30)
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> [color=blue]import feedparser[/color]
>>> [color=blue]f = feedparser.parse('http://planet.ubuntu.com/rss20.xml')[/color]
>>> [color=blue]for entry in f.entries:[/color]
...[color=blue]     print entry.title[/color]
...
Mark Shuttleworth: In defense of independent governance
Christer Edwards: Manually Install Thunderbird 2 : Ubuntu 7.04
Joey Stanford: Ubucon Boulder - June 2nd
Martin Albisetti: Dell announces the models (and date) for Ubuntu
<snip>
Mike Basinger: I’m So Blue
Ryan Kavanagh: Riddles anybody?
>>> [color=blue]print f.entries[2].description[/color]
<img class="face" src="http://planet.ubuntu.com/heads/joeyhg2.png" alt="" />
<p>The Colorado LoCo Team has done something amazing. They have gotten Google  to sponsor a stand-alone 
Ubucon in Boulder, dubbed <a href="https://wiki.ubuntu.com/Ubucon-Boulder" title="Wow!">Ubucon Boulder</a>. 
Thanks to Jim and Leslie for hosting and Neal, Mitch, David, and others for pulling this off.  I think we 
can expect more greatness from the Colorado folks in the future. The Gutsy release party plans call for 
renting a hotel. <img src="http://joey.ubuntu-rocks.org/blog/wp-includes/images/smilies/icon_smile.gif" alt=":-)" class="wp-smiley" /></p>
>>>

```
By combining feedparser with a PyGTK GUI interface, you could have a nifty little RSS reader up and running pretty quickly.

---

### Post by slavik on 2007-05-20
perl + gtk :)

---

### Post by barmazal on 2007-05-20
i don't know about mono but as asp.net development student i like asp.net website much, not sure the calls are the same but surely you can see what stuff can be done with MS version for web development.

As for all besides web dev i would advice learnvisualstudio.com, it's cheap and has great amount of videos.

As for mono, novell did great by copying MS language which probably taken from Java but i'm not sure they copied full functionality and online support MS keeps as websites i mentioned above.

C# is great language and .net platform probably the best, hopefully Novell will fully support stuff  in need so i will have less need to stay on windows but i'm afraid it will take much time and i barely can believe open source project can reach level of commercial project

---

### Post by ankursethi on 2007-05-20
> **slavik said:**
> perl + gtk :)

I like Perl, but I wouldn't like to use it for a desktop app. I like to keep it for web dev and small, write once scripts. Oh, and for practical extraction and reporting :p.

Okay, say I want to build a *large* app. Something the size of the GIMP. Which language out of Python and C# would then be better? I'd really like to see a speed comparison between these two languages.

---

### Post by slavik on 2007-05-20
python, C# doesn't have OGL (neither does java)  :)

---

### Post by barmazal on 2007-05-20
> **ankursethi said:**
> I like Perl, but I wouldn't like to use it for a desktop app. I like to keep it for web dev and small, write once scripts. Oh, and for practical extraction and reporting :p.

Okay, say I want to build a *large* app. Something the size of the GIMP. Which language out of Python and C# would then be better? I'd really like to see a speed comparison between these two languages.

Python is language for addons and C# for .net which means internet. You can do apps on both but large application won't be speed efficient using any of those. I think C# application would perform faster but on Windows rather Python's. Don't know how about Mono and Python on Linux.

---

### Post by pmasiar on 2007-05-20
> **barmazal said:**
>  i don't know about mono but as asp.net development student i like asp.net website much, (skip)
C# is great language and .net platform probably the best, (skip) but i'm afraid it will take much time 

translated: ASP is the only thing I know - but I am sure it is the best since warm water. 
LOL

> i barely can believe open source project can reach level of commercial project

lemme see ... say like open source Linux kernel, which is better than windoze?

LOL again. Always helps to know opinion of an ASP expert (or is it a student?) about why open source will never match commercial software.

---

### Post by slavik on 2007-05-20
> **pmasiar said:**
> translated: ASP is the only thing I know - but I am sure it is the best since warm water. 
LOL



lemme see ... say like open source Linux kernel, which is better than windoze?

LOL again. Always helps to know opinion of an ASP expert (or is it a student?) about why open source will never match commercial software.
not to mention that the likes of IBM, HP, and Sun are behind it. :)

even MS has BSD code in windows.

---

### Post by ankursethi on 2007-05-21
Looks like I'll stick with Python for now. I just hope Parrot makes things better (if it *ever* comes out).

---

