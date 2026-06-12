---
title: "&quot;export: command not found error in four places"
date: 2015-07-30
forum: New to Ubuntu
---

### Post by Dubem on 2015-07-30
Dear Experienced People,

Please help me solve this problem. If I open my command terminal,

“export: command not found
“export: command not found
“export: command not found
“export: command not found

will appear in 4 places.

I have also try francis@francis-SATELLITE-C660:~$ grep export .bashrc -n

and got the following output;

88:#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'
118:“export PYTHONPATH=/home/francis/workdir/lib/python2.7/site-packages/:”
119:“export PYTHONPATH=/home/francis/workdir/lib/python2.7/site-packages/:”
120:“export PYTHONPATH=/home/francis/workdir/lib/python2.7/site-packages/:”
121:“export PYTHONPATH=/home/francis/workdir/lib/python2.7/site-packages/:”

Please assume zero knowledge and guide me on how to remove this problem.

Thank you.

---

### Post by dino99 on 2015-07-30
export is a bash internal (builtin) command.

do "sudo -i" and then run the export command.

---

### Post by steeldriver on 2015-07-30
Huh?

All that's happened is that you have added some malformed lines to your ~/.bashrc file - in particular, the double-quotes are misplaced, and appear to be non-ascii characters (possibly copy-pasted from a web site?). You need to open ~/.bashrc in a text editor e.g.

```

nano ~/.bashrc

```

or 

```

gedit ~/.bashrc

```

and replace lines 118-121 with

```

export PYTHONPATH="/home/francis/workdir/lib/python2.7/site-packages/:$PYTHONPATH"

```

making sure you use ordinary " characters from the keyboard

NOTE: I have assumed that the dangling colon characters are also unintended: it won't actually make a difference if you don't have an existing PYTHONPATH definition

---

### Post by Dubem on 2015-07-30
Thank you so much, Steeldriver.
It is ok now.

Once again, thanks alot

---

