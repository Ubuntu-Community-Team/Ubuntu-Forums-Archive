---
title: "I wrote an AutoHotKey-like script"
date: 2008-01-23
forum: Programming Talk
---

### Post by peabody on 2008-01-23
Posted it in general (since autohotkey like programs are asked about there), but I figured I'd link to it from here as well because the script is far from finished and I could use help:

[http://ubuntuforums.org/showthread.php?p=4189647](http://ubuntuforums.org/showthread.php?p=4189647)

---

### Post by peabody on 2008-01-24
Sorry for the double post, but I felt like bumping the thread.

I am making some really decent progress.

I have actually discovered a way to get hotstring behavior without the requirement of a shortcut key!

It's a bit hacky, and it requires the script to be run as root, but it works, and it doesn't require patching the kernel!

Basically, I discovered a keylogger on the Internet that worked by reading from the /dev/input/event* file mapped to the keyboard.  It was a C program that could decode the input into the actual text.

I modified that program so it would only output the key sequences.  Then I ran that from within a test script as a readable pipe.  Everytime a character key was pressed, my script would receive the output from the program.  I would build a string of characters typed and try to match it against a list of abbreviations.  If a match happened, I would send a number of backspaces equal to the length of the abbreviation, then send the text expansion.

It works!  Typing btw, ianal and their ilk expands in any program in X11.  There are some rough edges...namely, I need a way to detect keyboard layouts and perform translations.  But for now what's important is that it is actually possible to replicate this functionality in Linux without hacking the kernel.

Is anybody interested in this?  I haven't received any feedback on this yet.

---

