---
title: "How can I replace text in a file from the command line?"
date: 2006-04-09
forum: Programming Talk
---

### Post by rogeriovinhal on 2006-04-09
Hi, I want to know how can I change some text inside a file just from command line, precisely, from a script.

I want my script to change a Makefile to all entries inside it of "-O2" to "-O4".
How can I do that?

---

### Post by wylfing on 2006-04-09
The [FONT="Courier New"]sed[/FONT] tool is what you need. (You don't need to install it -- it's already there.) The syntax is something like:```
sed -e s/oldtext/newtext/ inputfile
```
My sed skillz are a little rusty, sorry. You might be better off reading the man pages.

Edit: OK, my memory is refreshed. I think this would work for you:
```
sed -e s/-O2/-O4/ Makefile > Makefile.new
```

---

### Post by rogeriovinhal on 2006-04-09
[QUOTE=NeTo]Blame Microsoft for that :p . Check [this thread](http://amsn.sourceforge.net/forums/viewtopic.php?t=742) on the aMSN forums for details on what happened.

You need to update to the last cvs snapshot. You can also modify the *protocol.tcl* file; find a line containing *MSNP13 MSNP12 CVR0*, delete *MSNP13*, save and recompile.[/QUOTE]

Thanks! That worked! :-D 

I guess I have to find a good guide to look for these commands when I need them.

---

### Post by golgotha64 on 2006-04-11
Just for future reference there's a tool called rpl which is capable of doing string replacement in a similar manner to the sed solution given above, but it can work on multiple files.

It has saved my a lot of time an effort in the past :-)

---

### Post by asimon on 2006-04-12
[QUOTE=golgotha64]Just for future reference there's a tool called rpl which is capable of doing string replacement in a similar manner to the sed solution given above, but it can work on multiple files.[/QUOTE]
sed can work on multiple input files too. ;-)

---

