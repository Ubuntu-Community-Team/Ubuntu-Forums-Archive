---
title: "linux mint-firefox crashes segmentation fault"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by irish66 on 2008-11-30
Well one reason i decided to try Linux, was because my browser, no matter which one I used in Windows was always crashing. Unfortunately it does the same in Linux. Well at least firefox does with "segmentation fault" message.Does anybody have any ideas about that. I'm trying opera at the moment. But opera doesn't have plugins i run such as "no script" "tabs menu" "download hedlper" "down them all" and @session manager"
M

---

### Post by SunnyRabbiera on 2008-11-30
well you could try a reinstall of firefox, head down to your mint menu and go to system and then administration and go to sysnaptic package manager.
in that search for firefox, remove it by clicking the box next to the installed firefox package and selecting "mark for complete removal"
after that click apply and after firefox is removed also head to your home directory, hit control-h to unhide folders and delete your mozilla profiles folder listed as .mozilla

after all is taken care of resinstall firefox, see what happens.

---

### Post by irish66 on 2008-11-30
writing this in opera
Thank you. I've done that, We'll see how things go.
I see that Wine Linux has an option to run in safe mode.
Maybe i should try that with linux firefox,if i get crashes again, and see if i can find out exactly what is causing crashes. It must be something I install, because I know a chap who says his firefox never crashes. So the logical conclusion is that it's one of the add ons i use.
M

---

### Post by SunnyRabbiera on 2008-11-30
possibly, also try to run firefox in a terminal and see if it spits out any errors.

---

### Post by irish66 on 2008-11-30
will do-thank you.
M

---

### Post by irish66 on 2008-12-01
have decided to move over to opera for the moment. Firefox was crashing even without extensions. 
M

---

### Post by Dedoimedo on 2008-12-01
Hello,

Option 1: run Firefox from command line and see what errors comes up.
Option 2: use strace to hook the Firefox process and follow up the execution until it crashes, then post results here.

Did you recently install any plugins, a la flash?

Dedoimedo

---

### Post by irish66 on 2008-12-01
Hi, it was crashing even without any plugins.
What is strace? and what does hook the firefox process mean. By the way, I was starting firefox many times through the terminal. All i got after crash was "segmentation fault." 
M

---

### Post by Dedoimedo on 2008-12-02
Hello,

strace is a powerful tool for debugging applications (system calls). Hook process - to "catch" the process while it's running.

So, if firefox has process id (pid) of 2766, then you hook it like this:

```

sudo strace -f -p firefox -o strace.file

```

This whill trace all firefox events (including children (-f flag) and output them to a file (-o flag) and then you may try reading the output for interesting clues.

You may want to consider posting here, if you want.

More about strace, try "man strace" in terminal and in general, Google for it.

Dedoimedo

---

