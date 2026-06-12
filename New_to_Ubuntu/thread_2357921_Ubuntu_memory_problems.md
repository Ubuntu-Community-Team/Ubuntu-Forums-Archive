---
title: "Ubuntu memory problems"
date: 2017-04-07
forum: New to Ubuntu
---

### Post by karobeiniki on 2017-04-07
Hi all,

My set of problems consists mostly of complains towards the way newly installed Ubuntu is behaving.

1) Ubuntu freezes whenever I launch too many applications. I was unable to confirm, but it looks the freezing happens when RAM is full (though I don't know what about swapped memory)

It wouldn't be surprising if not the fact, that I am not using demanding software at the moment (max 30 open tabs in Chrome + Skype + text editor simultaneously)
And freezing is not preceded by any warnings, just everything slows down suddenly to an unacceptable rate (nothing crashes)

2) volume control problem - I used for a while x-face desktop and it worked fine with sound. But I have multiple cases with pulse volume (contemporary it doesn't see analog audio output, it works with usb headphones though.


Additional question to the above are:

Is there a way to turn off system questions "are you sure?" It is quite useless that if I click x symbol for browser it won't close, but rather inform
 "browser doesn't respond, are you sure?"

Or ending session from terminal [COLOR=#111111][FONT=Consolas]gnome-session-quit
[/FONT][/COLOR]Only opens window informing there are open files that should be taken care of.

Thank you for all constructive answers.

---

### Post by RobGoss on 2017-04-07
I guess the question is what are the specs for your machine?
>  max 30 open tabs in Chrome + Skype + text editor simultaneously) 
You may have answered your own question as far as the browser problem. I would have to say having so many tabs open might be the issue

I don't really know why would one need so many tabs open at one time. Try to limit the tabs used I'm sure it will help

If the machine it self is slow it could be a Ram issue and might need to be increased. Not knowing what the specs are I'm  just guessing

---

### Post by karobeiniki on 2017-04-07
Thank you for the reply. Nevertheless question still stays. How to make OS take care of memory? When working ion Windows, I remember having several hundred tabs open (sic!), and they were successfully kept on the hard drive. So that is not a question about my browsing etiquette.

---

### Post by howefield on 2017-04-07
Are you capable of sharing your system specifications and operating system details ?

```
sudo lshw -short
```
```
cat /etc/*-release
```

---

### Post by TheFu on 2017-04-07
chrome is a memory hog. It will easily use 3-6G of RAM.
Can't speak about Skype. Haven't used it in about 10 yrs.

To check memory use, use **free -h** or top, atop, htop.  Make certain that both real and virtual memory do not run out by closing applications before that happens.

If you run out of real and virtual memory, then the system may crash. Just depends on how well those programs are written.

---

### Post by sp40140 on 2017-04-08
First, could you provide the hardware specifications for your computer? 
Second, please provide output of "free -m" command.

---

