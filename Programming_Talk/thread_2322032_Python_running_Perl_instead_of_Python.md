---
title: "Python running Perl instead of Python?"
date: 2016-04-25
forum: Programming Talk
---

### Post by scoutchorton on 2016-04-25
So I have a Python file (test.py to be specific), and if I have the code:

```
print "Hallo"
```

Save it, open file browser and double click it (yes, I allowed it to be executed), it brings up this weird cursor I've never seen, and brings up this error:

 [ATTACH=CONFIG]268630[/ATTACH]

I went to investigate this /usr/bin/print and I found a Perl file. Am I missing something because Python uses C, not Perl (last I knew).

If I use Terminal to do 

```
python ~/Desktop/(path to file)/test.py
```

it works fine.

I'm going to restart my computer, and if that doesn't fix it, purge python and install it again.

I'm on Ubuntu 16.04 LTS, Python 2.7.11, and if you need more details, just let me know!

I'll report with results when I restart and reinstall!

---

### Post by steeldriver on 2016-04-25
Does your file contain a "shebang" to indicate that it should be run using the python interpreter?

```

#!/usr/bin/python

print "Hallo"

```

Otherwise, the system will try to run it using the default shell, I think - which will treat `print` as the system command /usr/bin/print

[Remember that - unlike some other OSes - the file extension has no particular significance on *nix]

---

### Post by scoutchorton on 2016-04-25
No, I'll have to try it. I've used it without it for so long, so I just asumed because it was a .py it would run python scripts...

---

### Post by scoutchorton on 2016-04-25
I restarted, didn't work. I did sudo apt-get pruge python2.7, and trying to repair damage now. I tried the shebang, and it worked!!

---

