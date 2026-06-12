---
title: "Ubuntu 13.04 Files 3.6.3"
date: 2013-08-28
forum: New to Ubuntu
---

### Post by cosname on 2013-08-28
I used some time ago Ubuntu 12.04 and there was a behavior, windows and mac now has: when i simply type in window it will make a fast select in current folder.

But now on ubuntu 13.04 with current default file browser, when i type it does full search in current folder. How to make a fast select on typing, and search only on Ctrl+F? I don`t want to change current file browser. 

Thank you!

---

### Post by eternal243 on 2013-08-28
Which file browser are you using? I don't have nautilus since I'm using Kubuntu, so I can't check, but in the Dolphin browser it works fine.

---

### Post by dhunt84971 on 2013-08-28
I did find this on the askubuntu forums:

[http://askubuntu.com/questions/275883/traditional-search-as-you-type-on-newer-nautilus-versions](http://askubuntu.com/questions/275883/traditional-search-as-you-type-on-newer-nautilus-versions)

The answer recommends using [SolusOS patched Nautilus]("http://www.webupd8.org/2012/08/install-solusos-patched-nautilus-in-ubuntu-1204.html") which reverts your nautilus back to 3.4.2 which has the type-search feature you are used to.  I have not tried this, so be careful to read other responses and successful installations before trashing your current installation.

Just an opinion, I am rather fond of the full search only because it does a recursive search into the subfolders and I have become very used to only needing to remember the filename and not much else.  It is also very very fast.

Good luck.

---

### Post by cosname on 2013-08-30
I like the fast search, but it would be pretty nice if i could make a fast navigation here right here:
[IMG]http://img.ctrlv.in/img/522081606c056.png[/IMG]

So when i watch the "About files"

:[IMG]http://img.ctrlv.in/img/522082cba457d.png[/IMG]

And in options there is no way to remove fast search on type (using Ctrl+F or search button also does, so here would be a great thing if fast search by typing).

Also "Fast Search" by typing is bad when you are in folder with huge structure, that is bad. Bin in other way i like the current file browser...

So i can`t do fast folder/file select by typing?

---

### Post by vanadium on 2013-08-30
After six months of trying to get used to the thing, I installed the SolusOS patched version (went very well).

On the one hand, the current search in nautilus has vastly improved over that in previous versions: it is a lot faster and actually finds your files. I would have preferred, however, that the recursive search would only work on demand, i.e. after pressing Ctrl+f. Now, it also kicks in when you want to highlight a specific file, disrupting the display and eventually displaying a bunch of other files from deeper directories that are not relevant.

The current recursive search in addition is not quite suited for professional work. If one has multiple projects, each with a "Reports" folder in it, trying to locate that folder will yield a window full of "Report" folders with no hint of which is which. Recursive search would be much more usefull if it searched the entire pathname. In that case, "project x reports" would only pop up the reports folder(s) living under the "Project x" folder.

Apparently, no-one ever tested the feature for real useability.

---

### Post by cosname on 2013-09-01
[COLOR=#000000]So the SolusOS patched version has that ability?
Fast select on type and fast search on demand (Ctrl+F)?
How to install it?[/COLOR]

---

### Post by cosname on 2013-09-01
[COLOR=#000000]So the SolusOS patched version has that ability?[/COLOR]
[COLOR=#000000]Fast select on type and fast search on demand (Ctrl+F)?[/COLOR]
[COLOR=#000000]How to install it?[/COLOR]

---

### Post by vanadium on 2013-09-02
SolusOS patched version is a forked version of nautilus 3.4, and features the classical typeahead search within one folder, along with the slow and bad working recursive search (Ctrl+f).

I find myself relying more and more on unity launcher to find and open a folder: it matches items based on keywords in the entire pathname. "report project x" thus only shows the "report" folder of project x, rather than a number of different "report" folders from all over your directory tree.

To install: [http://www.webupd8.org/2012/08/install-solusos-patched-nautilus-in-ubuntu-1204.html](http://www.webupd8.org/2012/08/install-solusos-patched-nautilus-in-ubuntu-1204.html)
This also works in 12.10 and 13.04.

---

