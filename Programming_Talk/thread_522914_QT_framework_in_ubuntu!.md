---
title: "QT framework in ubuntu!"
date: 2007-08-11
forum: Programming Talk
---

### Post by n.aggel on 2007-08-11
hi, i 've been using qt in windows, and i was hoping that i could also use it in ubuntu.... 

-->How can i install it in ubuntu
-->is there any IDE suitable for QT.....
-->should i use Kubuntu?
--->any other framework that i can use for cross-platform development?


thanks in advance for your help!

NA

---

### Post by Steveway on 2007-08-11
oO Such ignorance...something in me just died while reading your post....

---

### Post by xtacocorex on 2007-08-11
Kdevelop is the main IDE for KDE, which uses QT.  

No, you don't need to use Kubuntu.  You just need to install the QT libraries which are in the repos; don't know which ones you will need though.

wxWidgets is cross-platform, as is Tkinter within python.

---

### Post by Jessehk on 2007-08-11
Install qt-dev-tools, or qt4-dev-tools depending on which version of Qt you want to install. 

To build a Qt project, either use an IDE like KDevelop or put all the sources in their own directory and 

```

qmake -project
qmake
make

```

---

### Post by n.aggel on 2007-08-11
> **Steveway said:**
> oO Such ignorance...something in me just died while reading your post....
ohh, now i see, now i can understand you are the all-knowing *** of the forum...You are the biggest computer scientist ever existed, so you got disturbed by my question.... Share a paper {or at least a post } you all-knowing god...so that we can see how smart you are....

***Person {or what ever word fits there :lol:}

[\sarcasm]

Thanks to everyone else....

My question was basically oriented towards the availiable IDEs.. 
I guess Kdevelop should work pretty well with QT.. i will check it out:)

---

### Post by CptPicard on 2007-08-11
Well, the reason he felt like that is that KDE has been a Qt-based environment from the beginning, and Qt was originally developed for Linux, and cross-platform compatibility for Windows came later...

So... yeah, pretty much any Linux distribution is *the* place to develop on Qt really. :)

---

### Post by Steveway on 2007-08-11
No, I don't intend you to know what IDE's there are on Linux for what.
But I intend you to know that QT comes from the Linuxworld if you, like you allready said, you use qt in windows.
And by adding 1 to 1 or by visiting trolltechs side, you should know that there are tons of good programs for making QT apps and of course tons of cool apps using QT, even a full blown Desktopenvironment using...qt (KDE, like you allready mentioned).
And to be productive:

-->How can i install it in ubuntu | like you install all other things in ubuntu
-->is there any IDE suitable for QT..... | there are many good ones
-->should i use Kubuntu? |you don't need to but you can
--->any other framework that i can use for cross-platform development? |many, gtk, wxwidgets, tkinter...
EDIT: Picard beat me by 9 minutes, damn warpspeed.
EDIT2: It's like asking if there is something in Linux for making a server.

---

### Post by n.aggel on 2007-08-11
> **Steveway said:**
> No, I don't intend you to know what IDE's there are on Linux for what.
But I intend you to know that QT comes from the Linuxworld if you, like you allready said, you use qt in windows.

Who said that i didn't know that.... i said:

> hi, i 've been using qt in windows, and i was hoping that i could also use it in ubuntu....


Sorry for my english {not my native language}, but the hoping part refered to being to use in efficient way....cause to took me  a while to do this on windoze{i could do it only throgh the command line}, not even close to the productivity of Visual Studio.... Also i wan't sure if i could use it on ubuntu since it is gnome based.....


> **Steveway said:**
> 
And by adding 1 to 1 or by visiting trolltechs side, you should know that there are tons of good programs for making QT apps and of course tons of cool apps using QT, even a full blown Desktopenvironment using...qt (KDE, like you allready mentioned).


Yes there are tons of good programs for making QT apps but {at least in windows} i couldn't manage to use not even one! So, i was hoping that since linux is the natural environment for QT there would IDEs working out of the box {that's why i asked...if anyone has some experience to guide me, not moque me }


> **Steveway said:**
> 
And to be productive:

-->How can i install it in ubuntu | like you install all other things in ubuntu

i had to install: 
libqt4-core
libqt4-debug
libqt4-gui
libqt4-qt3support
libqt4-sql
qt4-designer
qt4-dev-tools
qt4-doc
qt4-qtconfig

+build essential, that i didn't know it wasn't installed by default.... I think that installing any other app like gvim is ALOT simpler.... + as i said above i was hoping for some directions to install it with some kind of an IDE like netbeans for java....

> **Steveway said:**
> 
-->is there any IDE suitable for QT..... | there are many good ones


so list some, if they 've worked for you. Any guide so the can work for me will do!

> **Steveway said:**
> 
-->should i use Kubuntu? |you don't need to but you can


Again hoping QT would work out of the box...with minimal setup effort....

> **Steveway said:**
> 
--->any other framework that i can use for cross-platform development? 
|many, gtk, wxwidgets, tkinter...


Again hoping that since GTK is native for gnome {i am not sure...Don't flame me} maybe there would be something out of the box...so i could work on it....

PS: i hope for some help, next time you post Steveway :P { no hard fillings :) }

---

### Post by the_unforgiven on 2007-08-11
You can also use [Code::Blocks]("http://www.codeblocks.org") IDE.
It has native project template for QT4.
The downloads of .deb are available from their site - you just have to install it with 
**# dpkg -i <downloaded.deb>**

HTH ;)

---

### Post by pmasiar on 2007-08-11
> **n.aggel said:**
> Sorry for my english {not my native language}, but the hoping part refered to being to use in efficient way.

It is not about your english. Ever heard of Google? JFGI: if you claim you know Qt on windows, look it up before asking trivial questions: [http://en.wikipedia.org/wiki/Trolltech](http://en.wikipedia.org/wiki/Trolltech)

---

### Post by n.aggel on 2007-08-11
Another polite guy.... why are you posting the link....how can it help me... JFGI yourself...

---

### Post by pmasiar on 2007-08-11
If you've bothered to click, you would learn that: "The popular free Unix desktop environment KDE uses Trolltech's Qt library. Trolltech also employs several KDE developers." Then you might search for [http://www.google.com/search?q=kde+ubuntu](http://www.google.com/search?q=kde+ubuntu) - but it would be too hard I guess for window user?

Now, do you know all the letters? Or you need more help with that </sarcasm>

---

### Post by n.aggel on 2007-08-12
And the fun goes on.....:popcorn:

> **pmasiar said:**
> If you've bothered to click, you would learn that: "The popular free Unix desktop environment KDE uses Trolltech's Qt library. Trolltech also employs several KDE developers." 


Who said i didn't know  that, or that this thing was my question...

> **pmasiar said:**
> 
Then you might search for [http://www.google.com/search?q=kde+ubuntu](http://www.google.com/search?q=kde+ubuntu) - but it would be **[SIZE="4"]too hard I guess for window user?[/SIZE]**

Now, do you know all the letters? Or you need more help with that </sarcasm>

And might search another billion things....but i wanted to hear some experienes...

PS: who named you a linux user?** So you consider me{and i guess all the others like me} inferior **cause i 've been using windows? As i 've said before i you think you 've done so much in computer science share it with us.....

PS2: JFGI computer science and i think the results will shock you </sarcasm>

PS3: i know this is a serious forum, so i will stop posting unrelevant things, unless i get insulted again...

---

### Post by n.aggel on 2007-08-12
I found something that may help some guys:

[http://www.clivecooper.co.uk/tutorial/index.html](http://www.clivecooper.co.uk/tutorial/index.html)

Basically it is a guide of how to setup qdevelop for ubuntu!

---

### Post by EtniesBMX on 2007-08-31
> **n.aggel said:**
> I found something that may help some guys:

[http://www.clivecooper.co.uk/tutorial/index.html](http://www.clivecooper.co.uk/tutorial/index.html)

Basically it is a guide of how to setup qdevelop for ubuntu!

this is what i was looking for. thanks. 
these guys are pretty harsh. :confused:

makes me want to not try and help out or discuss on here

edit: using qdevelop, i got an error regarding qt3 vs. qt4. if someone else is having this problem and doesnt know how to fix it, enter

sudo update-alternatives --config qmake

and choose qt3 or qt4

---

### Post by ryno519 on 2007-08-31
And the "Programmers are all anti-social douchebags" stereotype lives on. Bravo, fellows. Let me post a basic breakdown of this thread.

Person A: I would like a simple question answered so I will be able to develop applications for the GNU/Linux community.

Person B: **** YOU, ARSEHOLE!

Classy.

---

### Post by pmasiar on 2007-08-31
> **ryno519 said:**
> And the "Programmers are all anti-social douchebags" stereotype lives on. 

It is not about stereotypes, it is about not wasting everyone's time by asking trivial questions: do your homework and ask smart question instead, see my sig.

---

### Post by n.aggel on 2007-08-31
> **pmasiar said:**
> It is not about stereotypes, it is about not wasting everyone's time by asking trivial questions: do your homework and ask smart question instead, see my sig.
It seems that you can't understand that sometimes, someone may not know where to search{to do hishomwork}! To consider something trivial you must have the same bagckground {on the subject} with the other one....

Also if you think the question is trivial or useless then don't ansewr it! why make a post condemning the question....i can't understand that...You want to show to everyone else that this thread is stupid, and that the person writing it is clueless?You want to force the average reader to continue reading a "useless" post?

---

### Post by tseliot on 2007-08-31
@Please, everybody stop posting unless you really want to help n.aggel.

@n.aggel
of course the "Search" function of this forum is your friend.

> **n.aggel said:**
> hi, i 've been using qt in windows, and i was hoping that i could also use it in ubuntu.... 

-->How can i install it in ubuntu
If you use either Adept or Synaptic and search qt you will see that you can install the designer, etc.

> **n.aggel said:**
> -->is there any IDE suitable for QT.....
Kdevelop for C++ and Eric3 for Python (Py-QT)

> **n.aggel said:**
> -->should i use Kubuntu?
you can use either Kubuntu or Ubuntu (or Xubuntu). 

> **n.aggel said:**
> --->any other framework that i can use for cross-platform development?
GTK+ (with Python, Ruby, C, C++, C#, Java)
wxWidgets

---

### Post by pmasiar on 2007-08-31
When I don't know anything about the issue, I start learning trivial stuff from wikipedia, and follow the links. This gives me good idea for keywords to farther google search.

You may also read up [http://uncyclopedia.org/wiki/Smart](http://uncyclopedia.org/wiki/Smart) :-)

Edit: OK, sorry I apologize. I was maybe too harsh, and you might be too young to just let it skip over. But promise me to read "how to ask smart questions" in my sig - you may not believe it right now, but there **are** forums out there **much harsher** to newbies like this one :-) Uncyclopedia link above is bonus link for fun, not for real of course.

---

### Post by Note360 on 2007-08-31
ok. Every one step back from the computer. No reaso n to go insulting people.

Their are times when we can be abit rude to windows people (and I appologize for us as a whole), but honestly every one gets the "Hey google it arsehole" thing when they start out. I got it alot every oen does. Its just the way it works.

Oha nd for qt. You have it installed right? If you do all you need is an editor (and QtDesigner) and you should be fine. Its not to hard. I suggest getting used to the terminal, but thats just me.

---

### Post by Erunno on 2007-08-31
Here's a (beta) plugin to integrate Qt into Eclipse:

[http://trolltech.com/developer/downloads/qt/eclipse-integration-download]("http://trolltech.com/developer/downloads/qt/eclipse-integration-download")

---

### Post by n.aggel on 2007-08-31
> **pmasiar said:**
>  But promise me to read "how to ask smart questions" in my sig - you may not believe it right now, but there **are** forums out there **much harsher** to newbies like this one :-) Uncyclopedia link above is bonus link for fun, not for real of course.

I 'll definetally read the link in your sig!{i will also check out about python....} :)

---

### Post by Note360 on 2007-08-31
haha... The one time pmasiar doesnt mention python he gets some one into it.

PyQt is great I have been using it for the past day and I liek ti better than wxpython, but thats kinda obvious.

---

### Post by happysmileman on 2007-08-31
For the "Should I use Kubuntu", I think it'd be helpful, KDE is built with QT anyway, so QT programs would look better and stuff on it (though GNOME is making a lot of progress in integrating QT apps), you also have access to the KDE libraries.

I think if you want to program for Ubuntu instead it might be best to use GTK, though since you already started with QT this is probably not a good choice

---

### Post by Note360 on 2007-08-31
> **happysmileman said:**
> For the "Should I use Kubuntu", I think it'd be helpful, KDE is built with QT anyway, so QT programs would look better and stuff on it (though GNOME is making a lot of progress in integrating QT apps), you also have access to the KDE libraries.

I think if you want to program for Ubuntu instead it might be best to use GTK, though since you already started with QT this is probably not a good choice

I am a day in day out gnome user and I like using qt myself. Their are ways to integrate it better, but not completely (yet).

---

