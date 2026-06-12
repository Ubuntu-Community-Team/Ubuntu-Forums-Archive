---
title: "Help using (more repacing) system commands in Linux&amp;C++"
date: 2009-02-03
forum: Programming Talk
---

### Post by christian8807 on 2009-02-03
I know that system commands, like system("clear") is bad programming practice, but how should i replace this? Is there also one for the pause command? I'm using a cin >> char for now, but I was just wondering if there was a better one that I could use.

Thanks :popcorn:

---

### Post by lensman3 on 2009-02-03
system("clear") could be replaced with a curses output string.  I think the command window has a ESP xx xx sequence that will replace the clear.  The  earliest terminals just output 20 (or the number lines on the screen) newlines to the screen to move all the text off.  See the manual page->"man ncurses" for details.

As for pause, take a look at the stty terminal command.  It controls the raw device so that you can wait at the device level for a character. Also ncurses will do terminal reads and writes with getch.  The curses system has been around for years and is found on ALL Unixes there are even Window ports.

---

