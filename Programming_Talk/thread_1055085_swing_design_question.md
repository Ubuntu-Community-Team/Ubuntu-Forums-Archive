---
title: "swing design question"
date: 2009-01-30
forum: Programming Talk
---

### Post by badperson on 2009-01-30
Hi,
I'm writing an app that will run some transformations/reports/perl scripts on xml files, throughout the process files might be backed up, modified, new files might be created, reports run...

anyway, throughout the process I would like to have the gui update the user with status, and I would like to be able to use different fonts, layouts, colors etc. 

What's the best way to do this? I'm working through the sun tutorials, and JTextPane is interesting, but appending text to the pane and switching the fonts around appears to be a lot of work...

just wondering what the best solution for this might be. 
bp

---

### Post by Zugzwang on 2009-01-30
> **badperson said:**
> 
anyway, throughout the process I would like to have the gui update the user with status, and I would like to be able to use different fonts, layouts, colors etc. 


That doesn't look reasonable. Normally, a progress bar and some "Doing task <foo> at the moment" status text should suffice. 

If you really want to do it that way, you might want to consider the TextPane's HTML renderer. There, you can use (simple) HTML code which is easier to use if you know HTML.

---

