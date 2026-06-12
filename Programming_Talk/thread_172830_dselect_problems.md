---
title: "dselect problems"
date: 2006-05-09
forum: Programming Talk
---

### Post by Boyd on 2006-05-09
[FONT="Courier New"]Whenever I use dselect, and the help screens come up, I just see garbage on the whole terminal window.  If I press the space bar, it moves on to the menu, which looks normal.  This happens both in the Ubuntu terminal window, or even in a remote login from my Mac using iTerm.  I have tried various Character Encoding settings, to no avail.  Any ideas?

Here is a sample:

He&#9484;&#9472;:eI&#9532;&#9500;&#9472;&#9472;d&#9508;c&#9500;#&#9472;&#9532;e

Thanks.
Boyd[/FONT]

---

### Post by yaaarrrgg on 2006-05-10
When I run dselect, I don't see anything unusual.  I wonder if you may have installed another version (like a debian package)?  Maybe try removing and reinstalling, it from the standard ubuntu repositories?

---

### Post by Boyd on 2006-05-11
Thanks for the reply.  I don't think it is the dselect installation - an independent version on my Mac OS X does the same thing.  I think the Ubuntu one is the one that came with it.  I even tried bringing up a new xterm window on the Mac just now - same thing - the menu pages look/work fine, but information/help screens are "garbaged" - it has to do with the ascii graphic characters I think.  But I don't know how to get them interpreted correctly.  

OH.......!! found it - the TERM environmental variable was vt100.  When I set it to xterm, dselect works fine.  

Thanks for your help - I know you didn't help directly, but just explaining it to someone else helps me think of other things to try.

Boyd

---

