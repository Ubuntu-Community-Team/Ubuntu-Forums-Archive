---
title: "Learning Wx"
date: 2006-12-17
forum: Programming Talk
---

### Post by studiesrule on 2006-12-17
I'm really interested in learning wxWidgets or wxPython (I know c++ and python pretty well). This is the first time I've tried programming GUI's, and I thought that wx would be ideal. However, I haven't been able to find any indepth tutorials, and the example given on the site isn't at all useful. Can somebody please post some links to good tutorials or give me some pointers. Since I haven't gotten very far yet, is there any better/easier alternative to wx? Thanks for the help

---

### Post by Game_Ender on 2006-12-17
I would stick with wxWidgets.  I think wxPython will be the best route you can take for learning.  The current latest version of wxPython is 2.8, but Ubuntu 6.10 only has 2.6.  Which is really fine for learning.  If you want to go cutting edge there are instructions for getting 2.8 installed on Ubuntu [here]("http://www.wxpython.org/download.php#binaries").   Also don't forget to install the python-wxtools package.  It comes with some great apps, like a good python shell called PyCrust.

The one thing missing from the Ubuntu wxPython packages is the great demo that wxPython has.   The website has links to the 2.8.x.x releases, but here is the [demo]("http://downloads.sourceforge.net/wxpython/wxPython-demo-2.6.3.3.tar.bz2") for 2.6.x.x release and here are [the docs]("http://downloads.sourceforge.net/wxpython/wxPython-docs-2.6.3.3.tar.bz2").  To see all the fully interactive demos run the demo.py script from the demo tar ball.  It lets you update the demos and see the results in real time.

If you can't find the links in that text here they are:
[http://downloads.sourceforge.net/wxpython/wxPython-docs-2.6.3.3.tar.bz2](http://downloads.sourceforge.net/wxpython/wxPython-docs-2.6.3.3.tar.bz2)
[http://downloads.sourceforge.net/wxpython/wxPython-demo-2.6.3.3.tar.bz2](http://downloads.sourceforge.net/wxpython/wxPython-demo-2.6.3.3.tar.bz2)

---

### Post by DavidBell on 2006-12-18
I've just started using wx with C++ lately and it seems pretty good. No problems if you've used MFC, WTL or the like - it's basically the same where you create your ui objects and set up event tables that call functions of your choice. I'm still using Visual Studio as my ide because I prefer it's debugger, when my program is working in windows I just copy and recompile for linux either in Code::Blocks or wxHatch, usually with no change to the cpp for my simple stuff.

In windows I downloaded wxPack which got all my source libraries set up nicely and added wxwidgets to MCVS help and intellisense (not completely). It also included a large number of samples - I just had a look at the first 3-4 chapters of the included book, then had a look at the 'Minimal' sample project to see how it works, now I just look at relevant samples when I get stumped with some of the widgets.

This get's you up and running for basic guis, to start making your own widgets, owner draw etc obviously needs a deeper understanding, probably best to ask at the wxwidgets forums.

DB

---

### Post by DavidBell on 2006-12-18
BTW if anyone can tell me how to set code::blocks or wxhatch to do a static link with wxwidgets, ie so I can just copy a binary to other systems without wx libs, I'd be grateful. DB

---

### Post by studiesrule on 2006-12-18
thanks a lot. The new tutorial has come out as an ebook, and I've downloaded that. It seems to be pretty helpful. I've never had any experience with MFC, or anything. This is my first try. But I'm starting to understand it vaguely, by just reading the code.

---

### Post by DavidBell on 2006-12-18
> **studiesrule said:**
> I've never had any experience with MFC, or anything. This is my first try. But I'm starting to understand it vaguely, by just reading the code.

Just to start you off this is the basic method (in C++)

1. If you look at minimal.h/cpp you will find something like a new class

```

class myFrame : public wxFrame {...

```

by deriving from wxFrame like this you automatically suck in all the windowing code ... all you need to do is call (base member function) Show() and you have a hello world application up and running.

2. In the constructor you add all your widgets, the only thing that takes getting used to is the use of 'sizers' instead of abolute co-ords for widget positions and dimensions. If you want to respond to user interaction with specific controls, give them a unique (long)ID instead of ID_ANY

(PS. Code::Blocks and wxPack both come with graphical widget editors that generate skeleton code for creating the widgets in the constructor)

3. In the same class you add functions for interacting with specific (or groups of) widgets

4. Finally there is the event table, which is a series of macros ... if you dig around the source they are something like the following (based on what I've seen in other libraries)

```

#define BEGIN_EVT_TABLE(...) \
     virtual bool EventFunction(ID, event)\
            {switch (ID)\
                   {

#define EVT_?????? (eID, function) case eID : 
                                   {function(event); \
                                     break; \
                                   }

#define END_EVT_TABLE() \
                     }\
            }

```

What this does is set up a function that basically consists of a big **switch** statement, and each **EVT_????() **line adds an extra **case:**. All ui events relating to the frame get fed into this function which distributes them out to the functions you defined in 3. 

That's pretty much it. HTH. DB

---

### Post by evilidler on 2006-12-18
The best tutorial is the wxBook:
[http://wxwidgets.org/docs/book/](http://wxwidgets.org/docs/book/)

I bought it, and I'm happy with it. Also readable on Safari, as linked from that page.

I recommend using the custom repository to get wxWidgets 2.8.x, as the first thing
people on the forums respond with when people have problems, is "use the latest
version" ;)

---

### Post by David Haas on 2006-12-18
wxPython in Action was published in 2006. It's written by Robin Dunn, the guy who wrote wxPython, and Noel Rappin, and published by Manning. I bought a like-new used copy at Amazon for ~$34. It looks well-done.

From this site, I got the instructions for updating the packages for Ubuntu 6.06:
<http://www.wxpython.org/download.php#prerequisites>

"There is a set of packages maintained by the wxPython team for Ubuntu 6.06 (Dapper Drake) for i386 based systems, which are also known to work well on Ubuntu 6.10 (Edgy Eft). You can get them by adding the following to your /etc/apt/sources.list file:

    # wxPython APT repository at wxcommunity.com
    deb [http://wxpython.wxcommunity.com/apt/ubuntu/dapper](http://wxpython.wxcommunity.com/apt/ubuntu/dapper) /
    deb-src [http://wxpython.wxcommunity.com/apt/ubuntu/dapper](http://wxpython.wxcommunity.com/apt/ubuntu/dapper) /

After the repository info has been added to /etc/apt/sources.list you can fetch and install the packages using one of the GUI package manager tools such as Synaptic or Adept, or by running the following commands from a terminal window:

    sudo apt-get update
    sudo apt-get install python-wxgtk2.8 python-wxtools wx2.8-i18n

These packages (and their dependencies) will replace earlier versions of wxPython and wxGTK in the same release series that may have been installed previously."

David Haas

---

### Post by studiesrule on 2006-12-19
actually, I believe the wx programming book evilider was referring to is free to download, and distribute. There's even a link to it from wikipedia. 

thanks a LOT david. the class definition is basically an example of inheritence right? I guess now that I have the book, I'll be off fine, but I have some compiler errors which I'll post in a seperate thread (as it isn't too related with this one).

---

