---
title: "Creating a WordPad doc with Bash"
date: 2010-03-18
forum: Programming Talk
---

### Post by iMisspell on 2010-03-18
I have a plan text file which i would like make a copy of, take certon parts of the copyed file and make them bold, then send the second file to a windows machine to print out... 

So im looking for a way to create a file using Bash (or Perl) that can have some text Bold and for that file to be read on a windows machine for printing. 

I can not install any new programs to the windows machine, MS Office (dont know the version) is installed along with the default programs.


The original text file can not be changed, so a second file will be used for "formatting", then that second file will be printed. 

All the "work" will be done on a laptop with Ubuntu, the second file will then be transfured to a windows machine via a thumbdrive to be printed.

This is a little project im doing for work; the laptop can-not be hooked to the work-network so the laptop can not print.

As far as installing programs (or perl modules) to the laptop, its my own personal laptop so i can do what ever i want.

Thanks for any guidance.

_

---

### Post by wmcbrine on 2010-03-18
You probably want Rich Text Format. Not that it's especially easy to work with, but I can't think of anything simpler that will both do what you need, and be readable by WordPad.

On the other hand, how automated does this process need to be? You could just use OpenOffice to make a .doc file. Then again, do you really need it to be read by WordPad, or just printable by Windows? A PDF might work -- there are all kinds of tools in Linux to work with PostScript, which you can then convert to PDF.

P.S. Your sig makes the browser window really wide, requiring sideways scrolling to read your post.

---

### Post by roccivic on 2010-03-18
It sounds like it would be much easier to save your file as HTML and slap some <b>, <i>, <u>, etc, tags around required text.

Then set up PDF as your default printer and print to file using "lp" or "lpr".

Peace

---

### Post by Shpongle on 2010-03-18
the simplest way would be open office , i use it for college all the time and it works great

---

### Post by iMisspell on 2010-03-19
> **wmcbrine said:**
> P.S. Your sig makes the browser window really wide, requiring sideways scrolling to read your post.Thanks, didnt realize that.
Not sure if they have Acrobat on the computer which i would be using.
Not sure how many files i will be doing this to, but im tring to make it as automated as possible.
The script that will be doing all the work will be saved the 'nautilus-scripts' dir, so i can right-click on one file or many files and do what needs to be done.
This is aillte something which im making for myself to make my life alittle easyer at work, not sure how keen the "bossess" will be if i spend alot of time doing it, my job has nothing to do with PC computers ;)



> **roccivic said:**
> It sounds like it would be much easier to save your file as HTML and slap some <b>, <i>, <u>, etc, tags around required text.Bingo; nice and simple, thanks for the idea.



> **DillByrne said:**
> the simplest way would be open office , i use it for college all the time and it works greatCant do that, my laptop does not have access to printing while at work.

_

---

