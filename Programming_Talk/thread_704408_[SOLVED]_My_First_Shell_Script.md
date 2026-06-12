---
title: "[SOLVED] My First Shell Script"
date: 2008-02-22
forum: Programming Talk
---

### Post by what4893 on 2008-02-22
Hi,

I'm writing a video converting script and I'm having trouble storing console output into a variable. This is my first shell script so I'm probably doing this completely wrong, and any help is greatly appreciated.

$frameSize = tcprobe -d 0 -i filename.avi | grep "frame size" | sed 's/^*-g //' | awk '{print $q}';

The command after the equals sign outputs the exact value I want to store in the console, but when I run this in a shell script I get an error stating that, "=: not found". What am I doing wrong? Thanks for your help.

Nick

---

### Post by dwhitney67 on 2008-02-22
Lose the $ sign in front of frameSize, and lose the spaces on either side of the = sign.  Also, add back-quote signs since you are executing a single statement.

It should look something like:

```
frameSize=`tcprobe -d 0 -i filename.avi | grep "frame size" | sed 's/^*-g //' | awk '{print $q}'`
```

---

