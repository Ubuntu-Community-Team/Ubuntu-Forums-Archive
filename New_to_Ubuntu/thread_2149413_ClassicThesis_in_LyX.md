---
title: "ClassicThesis in LyX"
date: 2013-05-28
forum: New to Ubuntu
---

### Post by edub on 2013-05-28
Hi,

I just made the switch to Ubuntu 12.04 64 bit from Windows and am trying (in vain) to get ClassicThesis 4.1 ([http://code.google.com/p/classicthesis/](http://code.google.com/p/classicthesis/)) to work with LyX 2.0.2. LyX works properly with other documents, but even with the ClassicThesis example, I get the following LyX error:[INDENT]
Error:
[/INDENT]
[INDENT=2]Undefined control sequence.
LaTeX Error: Missing \being{document}
Undefined control sequence.
[/INDENT]
[INDENT]
Description:
[/INDENT]
[INDENT=2]}

       
 The control sequence at the end of the top line
 of your error message was never \def'ed. If you have
 misspelled it (e.g., `\hobx'), type `I' and the correct
 spelling (e.g., `I\hbox'). Otherwise just continue,
 and I'll forget about whatever was undefined.

 
 }
[/INDENT]
[INDENT=3]
[/INDENT]
[INDENT=2]You're in trouble here.  Try typing  <return>  to proceed.
 If that doesn't work, type  X <return>  to quit.[/INDENT]
 

Any ideas on how I can solve this.  

Thanks in advance!

---

### Post by Irihapeti on 2013-05-28
Welcome to the forums.

It's been a few years since I used LyX. From memory, it was a bit of an awkward beast when it came to using non-standard templates.

My guess would be that something isn't installed properly. Have you had it working correctly on Windows? How did you install or setup the classicthesis package on Ubuntu?

---

### Post by edub on 2013-05-29
Thank you for the fast response. 

To your questions: In  windows it works fine using pdflatex for the compiling. In Ubuntu I  installed the Tex Live packages, LyX, and tried to use the ClassicThesis  LyX files from [http://code.google.com/p/classicthesis/downloads/list](http://code.google.com/p/classicthesis/downloads/list).   

Any ideas on what I am missing or what could be improperly installed?

---

### Post by Irihapeti on 2013-05-29
Unfortunately, no. You might do better to ask on a forum devoted to LaTeX/LyX - there are a few of them around the internet - or even the developers of the package.

I may get a chance to play with the package tomorrow. If I find out anything useful, I'll post back. 

Incidentally, Ubuntu 12.04 uses the 2009 version of Texlive. There's a PPA for Texlive 2012 at [https://launchpad.net/~texlive-backports/+archive/ppa](https://launchpad.net/~texlive-backports/+archive/ppa). I'm not sure if this is partly causing the problem, but it's worth being aware of.

---

### Post by edub on 2013-05-29
Solved! 

I updated to the new Tex Live and all systems go!  Thanks for the tip.

---

### Post by Irihapeti on 2013-05-29
You're welcome.

Please could you mark this thread "solved". Instructions for this are here: [http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730](http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730)

---

### Post by markMDW on 2013-06-18
I was also looking into using LyX with 12.04.  It seemed to be exactly what I needed, except that I couldn't get any of the templates to work without warning messages instantly letting me know that something needed wasn't installed... and I thought those were default packages.  And I didn't see the Book class, which was what I wanted, btw.

The problem with LyX seems to be that its intended to be used by non-expert LaTeX users, but to use it, you nevertheless have to be an expert in LaTeX to get it configured so that it's useable.  And so, I would only recommend it to those are are advanced LaTeX users.  Perhaps try Kile instead.

---

