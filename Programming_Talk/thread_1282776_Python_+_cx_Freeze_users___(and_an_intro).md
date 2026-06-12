---
title: "Python + cx_Freeze users ?  (and an intro)"
date: 2009-10-04
forum: Programming Talk
---

### Post by osgZach on 2009-10-04
First some side notes: Jump to "The Problem" in bold, to skip the boring stuff.

[SIZE=1](1)
I don't know if this goes in this forum more than a general support forum as I don't know if the problem is with my feezing process or an issue with my Kubuntu install.  So apologies if this needs to be moved somewhere more appropriate..[/SIZE]

[SIZE=1](2)
I'd rather not get into a protracted debate about why I want to freeze my work to produce executables, especially on a *Nix OS where 95% of installs come with Python,  or get into a debate about dependencies..   I just don't feel right telling people "if you want to try this out, you have to go find  X, Y & Z, oh and X needs A needs D, and Y needs B, C, D, & E packages too.  

That being said..  I am a new programmer (if you can call me that yet).  I have always wanted to learn but struggled with self-teaching,  did the whole blowing my parents money on books when I was in my teens deal, etc..   Never could pick up anything.   But the past few weeks I have slowly been learning to use Python (Activestate 2.6 on Vista).   I have made some pretty good progress,  although I hit a phase where I was looking to jump ship to another potentially easy to learn language  that was cross-platform and had an **easy** deployment process (unlike python it seems) or just going windows only and whatever else would make my life easier.   

I still don't understand  distutils, easy_install, etc..     Like a true  Windows "slave"  I'd rather compile  EXE's and distribute them so they can be put anywhere,  clicked and run.

Py2EXE works great for this.   cx_Freeze also worked great for producing Windows executables as well.     Problem is now trying to get  a  clickable EXE on  Linux.   Because I am **really** putting for an effort to be  cross-platform.
[/SIZE]   
**The Problem**
I got my Python env. all setup on a Virtualbox'd  Kubuntu 9.04 install.  Got all my dependencies I've been using in Windows, etc and its pretty much the same install.   Everything works great in that regard..  I can  "python  mygame.py"  and it will run just fine.

cx_Freeze gives me a nice  executable in my build directory.   **But I can only run my program from the *Terminal* ??**   I don't understand why this is.   My permissions appear to be set properly,  even when checking under my standard user  with  "ls"  I get an  **x** in every category.   But the program doesn't run..  I tried making a shortcut to it too,  no go..  Just get a generic listing in the taskbar until it times out.     

So far the application is only a console app,  but I plan to implement a GUI soon, either way I can run it fine by double-clicking with my Win32 executable,  but the  EXE produced under Kubuntu  does not run at all unless I open a Terminal and use  bash..


Is this a question of  cx_freeze needing some special indicators from me/my build script?    Or is it an issue with Kubuntu in particular ?

Hope someone can help out here..   I really don't want to go through the whole   "here are the bytecodes and data files,  good luck with the dependencies chumps!"    Its just not an option from my  viewpoint.

I want to build apps that a user can download a zipfile,  extract to an arbitrary directory, and click the EXE and it runs..   Just like if you clicked Firefox or any other application.  Do I need to make some kind of  bash/shell script,  or do a special packaging routine or, is it something else these other developers do to get  one-clickers ?

---

