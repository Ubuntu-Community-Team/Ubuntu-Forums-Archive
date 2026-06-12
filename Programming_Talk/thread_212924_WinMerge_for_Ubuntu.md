---
title: "WinMerge for Ubuntu"
date: 2006-07-10
forum: Programming Talk
---

### Post by Bunro on 2006-07-10
I used until now WinMerge as a tool to compare PHP and HTML file (for upgrading my web site).

What kind of a tool would you recommend with Ubuntu?

I installed TkDiff and gave it a test drive this weekend but it is not so user friendly? Or maybe some body can tell me how to transfer the updates and/or  my corrections from the one side to the other?

In general where can I find a overview (plus description) of different application that you can install in Ubuntu Linux.

Regards, Robert

---

### Post by fluffington on 2006-07-10
I haven't used it myself, but [Meld](http://meld.sourceforge.net/) looks nifty. It's also in the Ubuntu repos ([meld](http://packages.ubuntu.com/dapper/gnome/meld) in universe).

---

### Post by supirman on 2006-07-10
We use tkdiff in a cvs type environment at work so this is a bit different how I normally use it, but you can merge changes easily.  

Basically, you do tkdiff <file 1> <file 2>.  As you'll notice, a diff section will be highlighted.  You can go to the next diff section by pressing the down arrow.  To choose which section to accept in merging, click the left arrow, or the right arrow, depending on which side you want to be in the final file.  When you've  selected which side to use for each diff section, click Merge->show merge window, and it will show you the resulting file.  You can then save it as whatever file you'd like. 

I don't know if that's what you're intending.  The aforementioned arrows are highlighted in the attached picture.

---

### Post by anydoby on 2008-06-12
> **fluffington said:**
> I haven't used it myself, but [Meld](http://meld.sourceforge.net/) looks nifty. It's also in the Ubuntu repos ([meld](http://packages.ubuntu.com/dapper/gnome/meld) in universe).

I have just tried Meld with Gnome-Commander. It works excellent and the UI is very friendly, even better to me than the WinMerge's one. THank you for the hint.

---

### Post by KingTermite on 2008-06-12
It's not free, but its the best compare tool I've *EVER* used. I've used it in Windows at work for years, and recently found out a Linux version is about to be released.

Beyond Compare
[http://www.scootersoftware.com/beta3/download.php](http://www.scootersoftware.com/beta3/download.php)

Main site with screenshots (windows), etc...
[http://www.scootersoftware.com](http://www.scootersoftware.com)

---

### Post by evan70 on 2008-10-27
Yeah :) Meld is GREAT :) thnkz for tip :)

---

### Post by newbuntuxx on 2008-10-27
didn't even know such a tool existed! Meld is just great! thanks fluffington

---

### Post by vhof on 2009-03-14
In Krusader there's an absolutely amazing option in File >> Compare by content which uses **kdiff3**.
You can compare/diff/merge with it files and directories etc.
Just found it. n-joy!

---

