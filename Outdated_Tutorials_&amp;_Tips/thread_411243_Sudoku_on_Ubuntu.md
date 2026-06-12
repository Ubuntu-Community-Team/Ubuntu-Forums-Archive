---
title: "Sudoku on Ubuntu"
date: 2007-04-16
forum: Outdated Tutorials &amp; Tips
---

### Post by DouglasK on 2007-04-16
I, as do many others, enjoy playing Sudoku.

**_The native, GPL solution:_**
There are two main games available for Ubuntu:
[gnome-sudoku]("http://gnome-sudoku.sourceforge.net/") and [ksudoku]("http://ksudoku.sourceforge.net/") 

The limitation of both these clients is very limited (if any) support for pencil marks.  That said, here's how to install them:

```

$  # if you have the kdesktop installed:
$ sudo aptitude install ksudoku
$  # if you have the default ubuntu desktop:
$ sudo aptitude install gnome-sudoku
```

**_The Non-GPL, yet still FREE solution which offers better functionality:_**
My problem is that I like more advanced puzzles that require full pencil marking support to solve.

My solution was to install a free windows Sudoku program, "Simple Sudoku" ([COLOR="RoyalBlue"][http://angusj.com/sudoku/](http://angusj.com/sudoku/)[/COLOR]).  

Here's how I got it going:  I downloaded Simple Sudoku from the above site to my home folder.  The file name was "sudoku-setup.exe"

I followed the [COLOR="RoyalBlue"][directions to install wine]("https://help.ubuntu.com/community/Wine")[/COLOR] located on the [COLOR="RoyalBlue"][ubuntu wiki]("https://help.ubuntu.com/community/")[/COLOR].

Here are the commands I needed to get it up and running.  It was seriously easy:
```

$ cd                          # Gets us to our home dir where we have write permissions.
$ sudo aptitude install wine  # install wine
$ wine sudoku_setup.exe       # Install Simple Soduku.  :-)
```

Myself, I run the K Desktop environment and Wine created a menu item for Simple Sudoku automatically.

**_Conclusion_**
This article gives three options for people who want to play Sudoku on Ubuntu.  I hope this helps people out there who play way too much Sudoku.  :D

---

### Post by LazyBoy on 2007-07-05
FWIW, ksudoku has the best support for pencil marks I'd found (2nd button).  I do like to set up the short cuts though (1=1,2=2, etc.).  Once I do that and turn off the tracker option, I find the UI very fast.  

I've done the inverse of you, install vmware & kubuntu on windows boxes primarily to play ksudoku :)

I'll check out Simple Sudoku next time I boot windows.  I'm not sure if that's one of the ones I tried previously or not.

LB

---

