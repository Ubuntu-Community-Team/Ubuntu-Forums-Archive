---
title: "Google projects + subversion help needed"
date: 2007-07-23
forum: Programming Talk
---

### Post by maximinus_uk on 2007-07-23
Just wondering if anyone here who knows anything about subversion and or google projects could give me any information about using them together? Google's help pages on the subject are a little terse, to say the least - they more or less say 'use a gui - here's a list'. Personally I'd rather use the command line (and I did try a few gui's - none seemed to work).

I've never used subversion before but I have been programming for a good few years, but surely it can't be that hard to get up and running can it?

---

### Post by zanglang on 2007-07-23
Do you have experience with other revision-control software, like CVS? If you have subversion installed (package name 'subversion' on repository) you should be able to jump straight into it with the same commands, albeit with 'svn' instead of 'cvs'.

If not, basically you'll be using a handful of commands, checkout, update, commit, add, log, diff, info. You should definitely start off with reading chapter 1 of **The** SVN book first to get familiar with version control basics.
[http://svnbook.red-bean.com/en/1.2/index.html](http://svnbook.red-bean.com/en/1.2/index.html)

There are some GUIs for subversion, check out 'rapidsvn', 'subcommander' and 'esvn', but imho they're not quite as well integrated as TortoiseSVN on Windows, so it's a good thing you're comfy with the command line.

Once you decide to 'checkout' a Google project, check the 'Source' tab from the project page, there should be a line you can copy and paste in the terminal.

---

