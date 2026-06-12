---
title: "Copy to the bin directory"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by Excatter on 2012-08-20
Hello to everyone, im new in this exciting world; im from Argentina. I was folowing the tutorial for knowing the bash commands and i have experienced a problem when i was starting the chapter that teaches how to writte scripts. I can't copy any folder to the bin directory, it says that i don't have the permision. How can i solve this?
Thanks and best regards to the best community.

---

### Post by papibe on 2012-08-21
Moved to its on thread. You'll get better visibility and more chances of replies.

---

### Post by jemofthewest on 2012-08-21
Have you tried using sudo?

```
$sudo mv script.sh /usr/bin
```

You need root permissions to write pretty much anything not in your home folder, so use sudo to edit or move files there.  

BTW you'll probably want to move your scripts to /usr/bin instead of /bin (/bin is typically reserved for programs that only root should run).  For extra credit, you can do what I do and make a bin folder in my home folder and put my scripts there (so they don't get confused with installed programs).  You'll need to add /home/user/bin to your path though.  Check out this thread for info on that:

[http://ubuntuforums.org/showthread.php?t=1717636](http://ubuntuforums.org/showthread.php?t=1717636)

---

### Post by snip3r8 on 2012-08-21
> **jemofthewest said:**
> Have you tried using sudo?

```
$sudo mv script.sh /usr/bin
```

You need root permissions to write pretty much anything not in your home folder, so use sudo to edit or move files there.  

BTW you'll probably want to move your scripts to /usr/bin instead of /bin (/bin is typically reserved for programs that only root should run).  For extra credit, you can do what I do and make a bin folder in my home folder and put my scripts there (so they don't get confused with installed programs).  You'll need to add /home/user/bin to your path though.  Check out this thread for info on that:

[http://ubuntuforums.org/showthread.php?t=1717636](http://ubuntuforums.org/showthread.php?t=1717636)
You can put a /bin in your home folder? well well, you **do** learn something new every day.

---

