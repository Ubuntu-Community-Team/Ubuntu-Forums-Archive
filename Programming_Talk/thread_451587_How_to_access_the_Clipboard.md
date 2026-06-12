---
title: "How to access the Clipboard?"
date: 2007-05-22
forum: Programming Talk
---

### Post by ADT on 2007-05-22
I have no idea how to do this;

I want to code a program that does the following;

When I copy a piece of text in an X windows application (eg firefox) I want my program to be able to take the text from the clipboard and put it into a text file.

I can't do this because I don't know how to get at this 'piece of text' in the clipboard.

Any help would be appreciated.

---

### Post by Jussi Kukkonen on 2007-05-22
In python you'd do this:
```
import os
s = popen('xsel').read()
```
More info on X clipboard should be here [www.freedesktop.org/standards/clipboards.txt](www.freedesktop.org/standards/clipboards.txt), but freedesktop.org has some server problems at the moment...

---

### Post by ADT on 2007-05-22
Thanks, I never tried python before but I'll give it a shot.

---

### Post by WW on 2007-05-22
That should be
```

import os
s = os.popen('xsel').read()

```
Also xsel is not installed by default.  You'll have to install it first, e.g.
```

sudo apt-get install xsel

```
(or use Synaptic).  You will have to enable the universe repository, if you haven't already.

---

### Post by crfaldu1 on 2009-10-27
xsel >> file.txt

This will append the current selection to file.txt.  One can even assign short cut (keyboard binding) to run this command.  I use it all the time to same notes on things I read

---

### Post by arunkumar413 on 2011-07-11
how to assign the shortcut key?

---

### Post by yuler on 2011-08-26
There are multiple ways to accomplish this.  Running a Bash script is one way.  Bash is the default shell program in Ubuntu.  A shell interprets command line input.

[The Bash Reference Manual]("http://www.gnu.org/software/bash/manual/bashref.html")
[Advanced Bash-Scripting Guide]("http://tldp.org/LDP/abs/html/index.html")
[Greg's Wiki]("http://mywiki.wooledge.org/")  [Chet Ramey's Bash Page]("http://tiswww.case.edu/php/chet/bash/bashtop.html")
[Bash Hackers Wiki]("http://wiki.bash-hackers.org/start")
[List of Bash online-tutorials]("http://wiki.bash-hackers.org/scripting/tutoriallist")
[[Bash Hackers Wiki]]("http://wiki.bash-hackers.org/scripting/tutoriallist")

With a Bash script, you can use the xclip command line utility to redirect clipboard data to a file.  Xclip is in the Software Center.

xclip -o -sel clip > filename

If you want to automatically increment the filename, put the routine inside a loop.  

The script can also avoid overwriting files, or assign the name to a formula that will never create a duplicate filename, such as according to the date and time (e.g. filename2011-08-24-122308). You can assign this Bash script to a hotkey, icon, activate upon startup, start/stop under certain conditions, etc.

---

### Post by hakermania on 2011-08-26
For anyone following:
In c++ you can see qclipboard lib for info

---

### Post by majedaly on 2011-11-10
you can also try xclip.
you can use `xclip -o` inside of a command as well

---

### Post by ofnuts on 2011-11-10
Just wondering, is there also a way to set the clipboard from a script?

(I haven't ready any of the aforementioned docs yet).

---

