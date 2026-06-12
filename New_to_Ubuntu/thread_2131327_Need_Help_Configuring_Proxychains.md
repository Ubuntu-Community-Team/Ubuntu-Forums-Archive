---
title: "Need Help Configuring Proxychains"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by ctbuzzy on 2013-04-01
I've installed Proxychains-4.4 successfully. But now I'm unable to edit the config file. When I try to use nano, I get the following:

**                                  [ line 1/1 **(100%), col 1/1 (100%), char 0/0 (0%)]
^G Get Help     ^O WriteOut     ^R Read File     ^Y Prev Page     ^K Cut Text       ^C Cur Pos
^X Exit            ^J Justify         ^W Where Is     ^V Next Page     ^U UnCut Text   ^T To Spell

This is all I get. I do not get the menu/information that would allow me to edit the config file. Something is missing. I get this limited menu whether I apply nano to "config," "configuration" or "config.mak." It happens whether or not I use sudo.

Any help appreciated! I need answers that are not directed at a Ubuntu/Proxychains expert. Nothing I could find on Google made any sense to me. Thanks!

---

### Post by ctbuzzy on 2013-04-01
When I attempt to use gedit, it opens the .conf file, but there is nothing in it.

---

### Post by ViliX64 on 2013-04-01
Are you sure, you have rights to view&edit? Try to use sudo&root..

---

### Post by ctbuzzy on 2013-04-01
Yes, thanks, I've tried both nano & gedit using sudo & it still fails. It's successfully entering editing mode in nano & opening a file in gedit. The problem seems to be that the config file is unrecognized, doesn't exist, or contains no data. When I open the proxychains directory in GUI, there are two files that resemble "config," but no file that matches exactly: "config.mak" & "configuration." They both contain data. Am I missing the config file itself? If so, how do I get it back?

---

