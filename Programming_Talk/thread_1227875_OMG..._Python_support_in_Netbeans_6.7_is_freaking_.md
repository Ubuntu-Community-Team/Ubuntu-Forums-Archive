---
title: "OMG... Python support in Netbeans 6.7 is freaking awesome"
date: 2009-07-31
forum: Programming Talk
---

### Post by kpkeerthi on 2009-07-31
I've been experimenting with the new Python plugin in Netbeans 6.7 for a couple of weeks. All I can say is Wow! It has everything I expect from a Python IDE. 

Check out the wiki [http://wiki.netbeans.org/Python]("http://wiki.netbeans.org/Python") for a list of currently available and planned features of the plugin.

I've been using Eclipse for more than 7 years and I always prefer Eclipse + JDE/JEE plugins for Java/J2EE development over Netbeans. But for Python, I seem to like Netbeans. 

There is PyDev for Eclipse but I find it very buggy, feature less and it doesn't 'feel' quite right. PyDev extensions is a joke IMO. Why pay for it when you you get more (& better) for free? 

Netbeans + Python + jVi (for Vi editing capabilities) = Rocks!!!

---

### Post by Tony Flury on 2009-07-31
Will Netbeans 6.7 python support run on Hardy Heron ?

not been brave enough to try Intrepid or Jaunty yet - well the last time i tried Intrepid it failed to recognise either my wireless card or video - something that Hardy did out of the box.

---

### Post by kpkeerthi on 2009-07-31
It should. Ensure that you have Java 6 SDK installed. Java 5 SDK should also work but the font rendering will be as good as GNOME's only if you use Java 6. Download the [linux installer]("http://download.netbeans.org/netbeans/6.7/python/ea2/start.html?platform=linux&lang=en&option=python") and install it. Its a .sh file (netbeans-6.7-python-linux.sh) and you may want to grant execute persmission before you launch it. 

Note: You don't have to launch the installer as a **root**. **sudo** not required and it can be installed in you $HOME folder itself.

---

### Post by Tony Flury on 2009-07-31
Have you managed to get 6.7 with Python EA working with gtk applications - see [http://ubuntuforums.org/showthread.php?t=1228157&highlight=netbeans+python](http://ubuntuforums.org/showthread.php?t=1228157&highlight=netbeans+python) for the problems I am having ?

---

### Post by kpkeerthi on 2009-07-31
Yes. It works fine for me. From Tools -> Python Platforms ensure that your Python is configured for GTK properly (You can see mine in the screenshot attached)

---

### Post by Tony Flury on 2009-07-31
I have the paths set right ... the error message is odd - as it is finding both pygtk module (and all its dependents) and the gtk module (and at least some of its dependents and the gobject module (and its dependents), and it is failing on the name _gobject- which sounds like a name space scope issue - and not a path issue.

from the terminal : 
[CODE]
$ python
Python 2.5.2 (r252:60911, Jul 22 2009, 15:35:03) 
[GCC 4.2.4 (Ubuntu 4.2.4-1ubuntu3)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import sys
>>> for x in sys.path :
...    print x

/usr/lib/python2.5/site-packages/flickrapi-1.2-py2.5.egg
/usr/lib/python25.zip
/usr/lib/python2.5
/usr/lib/python2.5/plat-linux2
/usr/lib/python2.5/lib-tk
/usr/lib/python2.5/lib-dynload
/usr/local/lib/python2.5/site-packages
/usr/lib/python2.5/site-packages
/usr/lib/python2.5/site-packages/Numeric
/usr/lib/python2.5/site-packages/PIL
/usr/lib/python2.5/site-packages/gst-0.10
/var/lib/python-support/python2.5
/usr/lib/python2.5/site-packages/gtk-2.0
/var/lib/python-support/python2.5/gtk-2.0
[CODE]

from the net beans Python Paths tool the directory list is the same with the exception of 
/home/tony/netbeans-6.7/python1
which is at the top of the list


Edit : Right - ignore that lot - turns out that the Project was bound to the netbeans python platform (which did not have gtk in the path) but for some reason it was finding some but not all of the libraries - how very very very odd.

---

### Post by Greyed on 2009-08-02
> **kpkeerthi said:**
> For those who can differentiate between a Python editor and a Python **IDE**, check this out: [http://www.netbeans.org/features/python/](http://www.netbeans.org/features/python/)

Not seeing any features there that hasn't already been present in WingIDE and Komodo for years.  In fact it looks comparable to the free versions of those products.  Certainly nothing that would compel me to want to subject myself to Java just to edit Python.  :/

---

### Post by Tony Flury on 2009-08-02
if wingide or Komodo were free i would agree with you Greyed, but as Netbeans is free, then it gets my vote.

It does have some wrinkles to iron out, but I am sure they will sort that out. BTW java is not visible at all when you are using the IDE, so you don't have to subject yourself to java in order to create, edit, save or run python applications.

---

### Post by Greyed on 2009-08-02
WingIDE and Komodo *are* free.  All versions?  No.  Versions which compare to the feature list of Neatbeans' Python support?  Yes.

---

### Post by JordyD on 2009-08-02
> **Greyed said:**
> WingIDE and Komodo *are* free.  All versions?  No.  Versions which compare to the feature list of Neatbeans' Python support?  Yes.

Looking at the sites, it seems Komodo Edit is Free and WingIDE 101 is free. Notice the capitalization.

---

### Post by kpkeerthi on 2009-08-03
Java is perfectly fine with me. Netbean's Python plugin does have some rough edges to iron out. Considering it still in EA, its acceptable and its got tremendous potential. I'm looking forward to it. I favor FOSS.

EDIT:
I checked the feature list of Komodo Edit. It appears to be just an 'editor' and not an 'IDE'. Doesn't even have a debugger. Its not fair to compare it with Netbeans & its Python Plugin.

EDIT(2):
Checked out WingIDE (free version). Netbeans offers more features than WingIDE 'Pro' as part of its 'core' platform and supports more languages. Python is just one aspect of it. It doesn't even come closer to the capabilities of Netbeans.

---

### Post by Greyed on 2009-08-03
> **kpkeerthi said:**
> EDIT:
I checked the feature list of Komodo Edit. It appears to be just an 'editor' and not an 'IDE'. Doesn't even have a debugger. Its not fair to compare it with Netbeans & its Python Plugin.

Just me but Python is hardly a language that requires an integrated debugger.  That's pretty low on my list of priorities.

> EDIT(2):
Checked out WingIDE (free version). Netbeans offers more features than WingIDE 'Pro' as part of its 'core' platform and supports more languages. Python is just one aspect of it. It doesn't even come closer to the capabilities of Netbeans.And yet Pro has the source assistant and Netbeans doesn't, which is pretty high on my list.  So, no, it doesn't offer more.  It offers less.

---

### Post by kpkeerthi on 2009-08-03
> **Greyed said:**
> 
And yet Pro has the source assistant and Netbeans doesn't, which is pretty high on my list.  So, no, it doesn't offer more.  It offers less.
This one is the context specific function signatures and its doc string, right?

---

### Post by Copernicus1234 on 2009-08-03
Thanks for the heads up. I will try it out. Currently using Aptana with Pydev which I like very much, but I enjoy trying new alternatives as well.

---

### Post by Greyed on 2009-08-03
> **kpkeerthi said:**
> This one is the context specific function signatures and its doc string, right?

Yes.  This isn't listed in the features of the plugin.  In fact I have not seen it outside of WingIDE and I consider it one of the must-have features for coding because the other fuctions of most IDEs can be easily replicated by just opening another window.  Having an on-the-fly reference into not only the language's functions/methods but your own program's functions/methods is not something that can be easily replicated by just opening another window.

---

### Post by kpkeerthi on 2009-08-03
Screenshot of Netbean's context-specific source assist and documentation viewer for Python. I find a debugger is inevitable in large projects.

---

### Post by kpkeerthi on 2009-08-03
I have added the link to the plugin's wiki for those you may be interested in the list of currently supported and planned features. 
[http://wiki.netbeans.org/Python](http://wiki.netbeans.org/Python)

---

### Post by Greyed on 2009-08-03
> **kpkeerthi said:**
> Screenshot of Netbean's context-specific source assist and documentation viewer for Python. I find a debugger is inevitable in large projects.

Those are calltips.  Calltips = evil and not the same thing.

---

### Post by kpkeerthi on 2009-08-03
> **Greyed said:**
> Those are calltips.  Calltips = evil and not the same thing.

What is source assistant and what makes it not evil? 
EDIT: OK. I get the picture now. Netbean's Navigator does the job and is much cleaner. It provides a nicer graphical representation of the source, attributes and methods as against text description in Source Assistant. Nothing radical in source assistant IMO.

---

### Post by Greyed on 2009-08-03
> **kpkeerthi said:**
> What is source assistant and what makes it not evil? 
EDIT: OK. I get the picture now. Netbean's Navigator does the job and is much cleaner.

If by cleaner you mean hides the code underneath your current line, sure!  I'll agree it's "cleaner".  SA sits down in the corner, and **doesn't obscure your code** nor does it require you to hit a button to get it to do its magic.  All you have to do is flick your eyes down and left when you need to.  No obscuring relevant code.

---

### Post by kpkeerthi on 2009-08-03
> **Greyed said:**
>  SA sits down in the corner, and **doesn't obscure your code** nor does it require you to hit a button to get it to do its magic.  All you have to do is flick your eyes down and left when you need to.  No obscuring relevant code.
Agreed. I would use if WingIDE was free/open source. $180 for single OS / single developer license? :frown:

---

### Post by Bodsda on 2009-08-03
> **Greyed said:**
> In fact I have not seen it outside of WingIDE and I consider it one of the must-have features

There is not really such a thing as a must have feature... If you take the definition of 'must' literally. The only thing you 'must' have to code python is an editor.

@OP
this looks pretty sweet, you may have swayed a vim lover here. As long as it has all of the vim niceness (including :vsp and :sp) and the features can be turned on/off on an 'as needed' basis, then I might consider trying it :)

---

### Post by Greyed on 2009-08-04
> **Bodsda said:**
> There is not really such a thing as a must have feature... If you take the definition of 'must' literally. The only thing you 'must' have to code python is an editor.

Must have... to consider using it over a plain editor...  Nitpick much?  :P

---

