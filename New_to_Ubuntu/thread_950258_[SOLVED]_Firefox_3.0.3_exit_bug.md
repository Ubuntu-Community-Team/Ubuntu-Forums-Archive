---
title: "[SOLVED] Firefox 3.0.3 exit bug?"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by mingle on 2008-10-17
Hi,

When ever I exit Firefox 3.0.3 on Ubuntu 8.04, the program seems to freeze for about 4 seconds, then a system message requestor pops up saying the program is not responding and gives me the option to "Wait" or Force Quit". If I do nothing in about another 4 seconds firefox shuts down by iteslf.

It does the same thing whether I use the window close button, the window-menu close option, or quit from the file menu.

It doesn't matter if I'm on a web page, or blank screen, it always does the same thing.

Is there a log file I can check or a system monitor package I can use to see what's causing this, as it's bloody annoying! :-)

I've searched on the web for a solution/similar issue but can't find anything.

Cheers,

Mike.

---

### Post by oldsoundguy on 2008-10-17
no issues with FF 3.0.3 on 6 machines 3 Gutsy, 1 Linux Mint, 2 Windows XP.

But the new FF 3.1 (now in beta) may solve your problem, so hang in there for a few more days until they get the bugs out and get the plug-ins to work.  It really is a VERY NICE browser and it is FAST!!

---

### Post by Bakon Jarser on 2008-10-17
Run Firefox from the terminal and see if it has errors when closing.

---

### Post by biggyfred on 2008-10-17
Having the same issue with two different computers. One a 64bit 8.04 box, the other a 32bit 8.04 box. Both started showing the bug as soon as I upgraded. I posted a bug report with Firefox. Looks like we wait now.

I ran Opera for a couple of hours today with no problem. Reopened Firefox and got the bug within a minute. Definitely firefox.

---

### Post by mingle on 2008-10-20
Hi,

Running from the terminal gave me no luck, but I'm glad that someone else has come across the same issue - @biggyfred,sorry to hear it's giving you a hard time too! :-)

Cheers,

Mike.

---

### Post by mingle on 2008-11-05
Hi All,

I've managed to locate the cause of this annoying glitch (for me, anyway): GMail Manager!

I have around 20 Gmail accounts (don't ask!) set up in GMail manager, so I'm not sure if that's part of the problem - I haven't investigated any further.

But when I disable the GMail Manager plugin, Firefox closes just fine!

Cheers

Mike.

---

