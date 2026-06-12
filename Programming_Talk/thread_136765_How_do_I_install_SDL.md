---
title: "How do I install SDL?"
date: 2006-02-26
forum: Programming Talk
---

### Post by arcanistherogue on 2006-02-26
Specifically, I want to install SDL 1.2.9 on the Code::Blocks C++ IDE.  Or, KDevelop, I really don't care.

How do I do this?  It seems different then when I installed it on windows, I just put the appropriate files from the SDL source .tar.gz into the appropriate files, but I can't seem to find a codeblocks folder.  I tried /usr/share/codeblocks, but none of the folders seem to be there.  

What is the best IDE to use SDL in on linux, and how do I set it up?

---

### Post by hod139 on 2006-02-27
To install the SDL headers you need: libsdl1.2-dev.  For the libraries libsdl1.2debian
```
sudo apt-get install libsdl1.2-dev libsdl1.2debian
```

I'm not sure what the codeblocks stuff you mentioned is about.

As for the IDE, I would suggest KDevelop or Anjuta.  See the [sticky post]("http://ubuntuforums.org/showthread.php?t=6762") for more.

---

