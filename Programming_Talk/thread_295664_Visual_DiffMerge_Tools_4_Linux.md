---
title: "Visual Diff/Merge Tools 4 Linux?"
date: 2006-11-08
forum: Programming Talk
---

### Post by pwhite on 2006-11-08
I made the complete switch from Windows to Ubuntu (no longer dual-booting) a couple of months ago and my only real complaint so far is that I haven't been able to find a good stand-alone visual diff/merge tool.

This was one of the reasons I was hesitant to switch in the first place, but I figured Eclipse's diff capability was good enough to take the plunge. However, I'd really like to be able to diff/merge files that are not part of an existing Eclipse project and a visual directory diff would be nice too. Are there any tools comparable to Araxis Merge (hands-down best merge tool I've ever used) or Exam Diff Pro available for Linux? I'm open to commercial products as well as long as the pricing is fairly reasonable.

Thanks!
Peter

---

### Post by [woodstock] on 2006-11-08
Hi!

I actually don't know any of the software you mentioned. However you could take a look at "meld". Maybe it will suit your needs.

HTH
Peter

---

### Post by cwaldbieser on 2006-11-08
> **pwhite said:**
> I made the complete switch from Windows to Ubuntu (no longer dual-booting) a couple of months ago and my only real complaint so far is that I haven't been able to find a good stand-alone visual diff/merge tool.

This was one of the reasons I was hesitant to switch in the first place, but I figured Eclipse's diff capability was good enough to take the plunge. However, I'd really like to be able to diff/merge files that are not part of an existing Eclipse project and a visual directory diff would be nice too. Are there any tools comparable to Araxis Merge (hands-down best merge tool I've ever used) or Exam Diff Pro available for Linux? I'm open to commercial products as well as long as the pricing is fairly reasonable.

Thanks!
Peter

I like kompare.

---

### Post by pwhite on 2006-11-09
Thanks for the response guys! I've installed both apps and they both look pretty good although I haven't tried any real nasty diffs yet. I'll probably alternate between them until one grows on me more than the other. :) 

As a side note, you can see some scaled down screenshots of Araxis Merge [here]("http://www.araxis.com/merge/index.html") if you're curious.

-Peter

---

### Post by MondoTofu on 2008-03-03
**meld's **other cool tricks include 

[LIST=1]
[*]diffing two directories,
[*] tabbed folders allow several diffs to take place at once
[*] diff file against CVS repository  (no need to fire up eclipse for that one).
[*] extensible text filters that help you specify with regex what sort of changes to ignore
[/LIST]

I used to be stuck on WinMerge, except that it would lose its mind on files larger than 64K and the diffs moderately complex.

---

### Post by jii on 2008-04-13
I'm still looking for a usable diff tool in Ubuntu. I grade programming assignments. After an instructor's script provides report files for each student (in their own directory), I need to visually compare each student's output against the instructor's master output to decide how many points to deduct. The problem I have with both Kompare and Meld is that they make it very difficult to switch to the next student file. 

In Meld, there is a "browse..." button above each file. When I click it and choose a different file, the comparison doesn't change. If I click refresh, nothing happens. If I click reload, it reloads the original two files. I'm not sure what purpose the browse buttons even serve, but I have to quit and reopen Meld each time I want to compare different files, which renders it unusable for me. 

In Kompare, if I swap out either the "Source" or "Destination" file, then the other gets automatically changed to the path of the new file. For example, if I have the source and destination filled in as "/grades/master_output.txt" and "/grades/student1/output.txt", and then I change the destination by browsing to "/grades/student2/output.txt", the source will change to "/grades/student2/", forcing me to then click on the source and change it back to "/grades/output_master.txt". This happens in either direction. While incredibly annoying, Kompare is still usable, except for the occasional error messages like "not a valid diff file" that pop up when trying to compare a couple of .txt files that gedit opens just fine. I would also be nice if I could configure Kompare to not open a new window each time I compare different files.

It seems like I need less features, but features that actually work. I don't know if it matters, but I'm using Gutsy Gibbon with Gnome. If anyone can suggest their favorite file comparison tool that can do what I need (be able to change which files I'm comparing, in real-time) I'll be happy to check them out.

---

### Post by nanotube on 2008-04-14
> **jii said:**
> 
In Meld, there is a "browse..." button above each file. When I click it and choose a different file, the comparison doesn't change. If I click refresh, nothing happens. If I click reload, it reloads the original two files. I'm not sure what purpose the browse buttons even serve, but I have to quit and reopen Meld each time I want to compare different files, which renders it unusable for me. 


i haven't used kompare, so i'll just give you my suggestion about meld
you can start meld from the cli with the file arguments. so, you start with:
```
meld /grades/master_output.txt /grades/student1/output.txt
```
when you're done, close, go back to terminal, hit arrow up and replace 1 with 2, open meld again.

you could even write a shell script that will automatically open the next one when you close the one you are done with (loop over the studentN directories in /grades, and keep opening meld)

which would be even better than manually swapping the files with a mouse.

hope that helps. :)

---

### Post by ghostdog74 on 2008-04-14
have you tried the usual suspects, diff or sdiff?

---

### Post by apoth on 2008-04-14
gvimdiff

---

### Post by nsche on 2008-04-15
I use the diff mode in emacs.  You can operate on as many buffers/files as you want 2 or 3 at a time.  It lets you just look at them or change either direction.  It uses colors to highlight the diffs.  It is about all I use emacs for.

---

### Post by unutbu on 2008-04-15
If you use emacs you can compare 2 files (or 2 directiories)  using M-x ediff (or M-x ediff-directories).
You don't have to understand diff output to use ediff.

---

### Post by SuperMike on 2009-06-16
I just installed meld on Ubuntu 8.04.2. Man, that's a really nice program. I'd prefer this over any command-line tool for this on any day!

---

### Post by Mirge on 2009-06-17
Your response is a tad late :).

---

### Post by nanotube on 2009-06-17
> **Mirge said:**
> Your response is a tad late :).

never too late for a little meld praise :)

---

### Post by castudil on 2009-07-06
Hi, I tried Meld and seems to work fine as a front-end for diff. Thanks for the sharing.


For plagiarism detection, e.g. in a programming course, i would recommend to take a look at

[http://theory.stanford.edu/~aiken/moss/](http://theory.stanford.edu/~aiken/moss/)

---

### Post by webtechquery on 2010-05-05
Hi there.

I want you to check out DiffMerge as well.
Check out the following website for details, regarding Free Diff Tools for Ubuntu:

[http://www.webtechquery.com/index.php/2010/05/free-diff-tools-ubuntu-linux-windows/](http://www.webtechquery.com/index.php/2010/05/free-diff-tools-ubuntu-linux-windows/)

Thanks

---

### Post by fattmox on 2010-11-19
I use GVim to "Split Diff with..." another file - has a great visual comparison plus another menu for cut and put blocks.

---

### Post by pmj005 on 2011-12-25
Not sure why nobody mentioned kdiff3. It is a very nice KDE application and I have been using it.

---

### Post by The Cog on 2011-12-25
Closed for necromancy.

---

