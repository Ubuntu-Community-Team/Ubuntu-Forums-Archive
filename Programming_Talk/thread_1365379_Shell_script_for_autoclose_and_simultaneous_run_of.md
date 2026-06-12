---
title: "Shell script for autoclose and simultaneous run of two programs"
date: 2009-12-27
forum: Programming Talk
---

### Post by Exonimus on 2009-12-27
Hi guys,

First of all, let me tell you that I'm very new to scripting. The situation is as follows: 

I recently installed ubuntu on a laptop for my parents. I got everything working smoothly, but on a cold boot, wine seems to load pretty slowly, giving NO indication of loading whatsoever.

I figured I might be able to show a 'loading' image(e.g. with gthumb) and autoclose it when the wine program loads. (with a shell script)
As a form of experiment, I tried something along the lines of this:

gthumb -f '/home/exonimus/Desktop/load-bar2.gif'
wine "C:\Program Files\Microsoft Office\OFFICE11\WINWORD.EXE"
pkill gthumb

Now. I could either wait for wine to send a certain signal when it's done loading, but that's probably way over my head at the moment. The other reasonable option seemed a 'sleep' command, but when I put a sleep command below the 'wine' command, I'm pretty sure it won't work. 

Without putting any command there, wine only loads AFTER I close gthumb myself. How would I go and run two processes simultaneously? Thanks for any help.

---

### Post by ksa618 on 2009-12-27
This may work. Adjust the sleep command to the apropriate number of seconds. The '&' character starts the preceding command in the background.
```
gthumb -f '/home/exonimus/Desktop/load-bar2.gif' &
wine "C:\Program Files\Microsoft Office\OFFICE11\WINWORD.EXE" &
sleep 10
pkill gthumb
```

---

### Post by Exonimus on 2009-12-27
That worked! Thanks a lot :)

---

