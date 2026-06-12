---
title: "Scripting Question - diff/compare or bash shell script"
date: 2022-08-29
forum: New to Ubuntu
---

### Post by zane786 on 2022-08-29
Hi 

I could not quite find the correct forum for this question I have.
Its related to file editing/bash scripting or the diff/compare commands found on Ubuntu

My scenario:
Looking to find 2 files with "almost exact content" out of a list of 150 files.

Fileset_A* has 75 files and Fileset_B* has 75 files
eg. Fileset_A_025.txt and Fileset_B_149.txt have almost the same content/data.
I just need at least 10 consecutive words to match in both, then I need to flag this diff/compare as a hit( they are similar) and record the 2 file names.
How do I diff or compare each file to each other file to get the hit.
All files have a single paragraph in them, with a max. of 220 words (max. 1300 characters) in the biggest file. 


Can anyone assist please?
or guide me to correct forum too

---

### Post by TheFu on 2022-08-30
> **zane786 said:**
> Hi 

I could not quite find the correct forum for this question I have.
Its related to file editing/bash scripting or the diff/compare commands found on Ubuntu

My scenario:
Looking to find 2 files with "almost exact content" out of a list of 150 files.

Fileset_A* has 75 files and Fileset_B* has 75 files
eg. Fileset_A_025.txt and Fileset_B_149.txt have almost the same content/data.
I just need at least 10 consecutive words to match in both, then I need to flag this diff/compare as a hit( they are similar) and record the 2 file names.
How do I diff or compare each file to each other file to get the hit.
All files have a single paragraph in them, with a max. of 220 words (max. 1300 characters) in the biggest file. 


Can anyone assist please?
or guide me to correct forum too

Reads like a homework problem.  

BTW, Ubuntu text processing tools are the same as for all Unix systems. Nothing is ubuntu specific.
There are hundreds of different ways to solve the problem. That's normal.  What the class wants is for you to figure out your own way and go to the effort to make it work.  This is more about learning to think in the Unix way, than anything else.  [https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed) is my attempt to explain the difference.

There are a few diff tools - diff, sdiff, are the text versions.  You could use awk, perl, python, ruby, to code something up yourself, probably in about 20 lines.  A GUI diff tool is meld.  It is the best diff tool on any platform anywhere. It isn't installed by default, so it may not be what the class seeks.  I'd be surprised if an efficient solution wasn't already posted on stackexchange.

Good luck.

All these programs (those in /usr/bin/) have manpages installed, so to learn all the options a program supports, use the manpages. That's a very important skill to learn.  Took me about 6 months before the manpage layout was clearly genius to me.  Now, it is even more clear why they are setup the way they are.  To learn more about manpages, run 'man man'

As for basic knowledge like this, I can recommend [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) or any of the O'Reilly books - *UNIX Power Tools* should be available used for USD $0.50 at a used bookstore. Don't worry if it is 25 yrs old.  The many things all these commands do hasn't changed much in all that time.  That book shows how to solve problems using the existing tools on a Unix system - applies to Linux too.

---

