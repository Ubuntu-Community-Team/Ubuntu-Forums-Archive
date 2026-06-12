---
title: "ANN: SPE 0.8.4.c Python IDE editor released (in Hardy)"
date: 2008-02-14
forum: Programming Talk
---

### Post by stani on 2008-02-14
As SPE was being developed for more than a year in subversion, I thought it is time for a release again. Even better I contacted MOTU land and thanks to Pochu the new SPE got packaged for Ubuntu Hardy!

SPE 0.8.4.c is a major bugfix release. It ships updated plugins and also some new features, especially if you use Linux or Blender, for which Witold did a great job. I would also like to thank in particular the webhost Zindep.com for their support and patience.

New features:

    * new versions of WinPdb debugger, PyChecker, wxGlade & XRCed gui designer
    * clear output pane
    * support for wxPython 2.8
    * linux support for nautilus, gnome-terminal, konqueror, konsole, thunar
    * improved blender support up to 2.45 (by Witold)

Fixes:

    * sidebar sash more tolerant
    * show path in title (linux)
    * run with filename with spaces
    * nicer debug dialog box
    * kill process fix
    * notebook
    * insert signature
    * numpad keys (by isolationism)
    * find tab with nonexisting files
    * add environment to SPE.py (linux)
    * better warning for documentation for unsaved files
    * better handling of new empty files
    * many more...

Installing on Debian(unstable) and Ubuntu Hardy:

    sudo apt-get install spe

Installing on all other platforms:

   1. Download either the zip or tar ball from here
   2. Unzip it where you want and do NOT rename the _spe folder
   3. Start SPE from within the _spe folder with "python SPE.py"

About SPE:
SPE is a python IDE with auto-indentation, auto completion, call tips,
syntax coloring, uml viewer, syntax highlighting, class explorer,
source index, auto todo list, sticky notes, integrated pycrust shell,
python file browser, recent file browser, drag&drop, context help, ...
Special is its blender support with a blender 3d object browser and its
ability to run interactively inside blender. Spe integrates with XRCed
(gui designer) and ships with wxGlade (gui designer), PyChecker (source
code doctor), Kiki (regular expression console) and WinPdb (remote,
multi-threaded debugger).

The development of SPE is driven by its donations. Anyone who donates, gets a nice pdf version of the manual without ads (74 pages). 

For more info go to [http://pythonide.stani.be](http://pythonide.stani.be)

---

### Post by snlake on 2008-02-23
Unfortunately I cannot install spe 0.8.4c-1~hardy1 in hardy. It depends on pychecker >=0.8.17-5, but in the hardy repositories there is only version 0.8.17-3.

---

### Post by stani on 2008-02-26
> **snlake said:**
> Unfortunately I cannot install spe 0.8.4c-1~hardy1 in hardy. It depends on pychecker >=0.8.17-5, but in the hardy repositories there is only version 0.8.17-3.
Pychecker should now be available. Can you try again and see if pychecker works? Please report here (success or fial):
[https://bugs.launchpad.net/ubuntu/+source/spe/+bug/195459](https://bugs.launchpad.net/ubuntu/+source/spe/+bug/195459)

---

### Post by snlake on 2008-02-26
> **stani said:**
> Pychecker should now be available. Can you try again and see if pychecker works? Please report here (success or fial):
[https://bugs.launchpad.net/ubuntu/+source/spe/+bug/195459](https://bugs.launchpad.net/ubuntu/+source/spe/+bug/195459)

Thank you for the hint.

Both the installation of SPE and checking python source code with pychecker via SPE works fine. I've added a confirmation to bug #195459 accordingly.

---

