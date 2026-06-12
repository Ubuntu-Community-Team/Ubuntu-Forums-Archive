---
title: "Using Python and QT... or PyQT?"
date: 2009-12-26
forum: Programming Talk
---

### Post by redwoodguy on 2009-12-26
I've been trying to get PyQT configured with no luck. If anyone is using Python 2.6 and QT4 and could help me get it configured I'd appreciate it. 

1. I have downloaded and installed Python 2.6 and it works.
2. I have downloaded QT4 and QT Designer, and that works.
3. I downloaded "PyQT" from riverbank software, and this is what DOESN'T work. It wants me to run a configure.py script which fails. 
4. It seems like I don't have the PyQT files in the right directory, or that perhaps PyQT needs to work with very, VERY specific versions of QT and Python. I dunno.

---

### Post by CptPicard on 2009-12-26
Please, *please* tell me you aren't trying to set this up without using the package manager...

```

sudo aptitude install python-qt4 python-qt4-dev pyqt-tools

```

should pull everything you need and set them up.

---

### Post by redwoodguy on 2009-12-26
I hope you don't mind the stupid question here but.....I have successfully downloaded all the various elements. I can't get them to "play" together. 

[COLOR=Red]1, From the riverbank web site, they say to do this: 
[/COLOR][COLOR=Red]"After unpacking the source package (either a .tar.gz or a .zip file depending on your platform) you should then check for any README files that relate to your platform.[/COLOR]
 [COLOR=Red]Next you need to configure SIP by executing the configure.py script.  For example:[/COLOR]
 [COLOR=Red]python configure.py"[/COLOR]

Now, when I do that, I get an error from Python which says something like, "no such directory". And a few other error messages like that.

That's what is confusing me - this "configuration" business.

---

### Post by CptPicard on 2009-12-26
> **redwoodguy said:**
> I have successfully downloaded all the various elements.

Is there a real reason as to why you are downloading them... from... "websites"? :confused:

---

### Post by redwoodguy on 2009-12-26
Yes, I was trying to do it without the package manager, because the package manager did not seem to find all the pieces. So, I then went to Riverbank software and downloaded the tar.gz files, moved them into the Python directory and then tried to run that configure.py script.  Bad idea, I take it?

---

### Post by redwoodguy on 2009-12-26
Here's the longer story.
I used package manager to download PyQT. I then used QT Designer to make a small form - resulting in a *.ui file. I tried to run the *.ui file then into Python and that's when it told me I didn't have the right bits - the bit which generates Python code from the *.ui file. I think it is called "pyuic" or something similar.

---

### Post by OutOfReach on 2009-12-26
> **redwoodguy said:**
> Here's the longer story.
I used package manager to download PyQT. I then used QT Designer to make a small form - resulting in a *.ui file. I tried to run the *.ui file then into Python and that's when it told me I didn't have the right bits - the bit which generates Python code from the *.ui file. I think it is called "pyuic" or something similar.

The pyuic executable comes separate from the regular PyQt package, it comes in another package (along with some other handy tools) which is *pyqt4-dev-tools*
So, just install that and you're ready to go.

---

### Post by CptPicard on 2009-12-26
Ok, now I'm starting to see where you're at (giving enough context is always advisable... ;) ). I believe pyuic is in the pyqt-tools package, I spent some time looking for it too a while ago...

EDIT: What above said; it's **pyqt4-dev-tools** for Qt4.

Going out to the web and download and manually install stuff is always your last choice. You don't want to litter the system with self-installed, non-managed random versions of things...

---

### Post by ksa618 on 2009-12-26
I believe the pyqt-tools package is for Qt3. For Qt4, you'll want pyqt4-dev-tools.
Unless you have a specific reason for using Qt3, you shold stick to Qt4.

---

### Post by redwoodguy on 2009-12-26
OK. I think this is resolved. 

1. I installed  **pyqt4-dev-tools** and I notice it said "0 files installed" by which I assumed I already had it. 
2. I tried running "pyuic" again. Suddenly, it dawned on me that this should be run from the bash terminal window, not the Python interpreter window. D'oh. I am never surprised by how ignorant I can be. 
3. Pyuic runs now, but I will have to now get my options and switches set right to actually accomplish getting code out of it. 

Thanks to all for your patience. I only installed my first Linux system last week, and only started with Python kind of yesterday. And, I am old and decrepit too. The last program I wrote was in COBOL in 1972 on an NCR 615 Mainframe with 32k core memory and a 5MB HD.

---

### Post by CptPicard on 2009-12-26
Oh, in that case you'll be just fine, but welcome to the new millennium anyway; Python should be an excellent choice in this day and age ;)

---

### Post by wmcbrine on 2009-12-26
> **redwoodguy said:**
> The last program I wrote was in COBOL in 1972 on an NCR 615 Mainframe with 32k core memory and a 5MB HD.Luxury!

Etc. :)

---

### Post by redwoodguy on 2009-12-26
Thanks for the patience fellas. I'll do my best to limit stupid questions to one a day.:)

---

### Post by maximinus_uk on 2009-12-27
> **redwoodguy said:**
> The last program I wrote was in COBOL in 1972 on an NCR 615 Mainframe with 32k core memory and a 5MB HD.

You had 32k in 1972!?!?!?!?

I didn't get more than 1k until 1982, you lucky lucky man!!!

---

