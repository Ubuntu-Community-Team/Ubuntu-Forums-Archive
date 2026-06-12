---
title: "Creating or finding a file"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by rhichi on 2008-05-19
Hey, so I've been trying to make Skype work on Hardy Heron via the advice about PulseAudio given here:

[http://ubuntuforums.org/showthread.php?t=686911&page=1](http://ubuntuforums.org/showthread.php?t=686911&page=1)

However, being the absolute newb I am, I don't know how to create or find the file ~/.asoundrc. I tried simply inputting ~/.asoundrc into a terminal window but it said the directory does not exist.

Edit: That problem is solved, read 3rd and 5th post please.

---

### Post by Inxsible on 2008-05-19
> **rhichi said:**
> Hey, so I've been trying to make Skype work on Hardy Heron via the advice about PulseAudio given here:

[http://ubuntuforums.org/showthread.php?t=686911&page=1](http://ubuntuforums.org/showthread.php?t=686911&page=1)

However, being the absolute newb I am, I don't know how to create or find the file ~/.asoundrc. I tried simply inputting ~/.asoundrc into a terminal window but it said the directory does not exist.
The easiest way is to type this command in a terminal. If you have a file of that name, it will open that file. If you don't it will create a file and open a blank file for you to edit.```
gksudo gedit ~/.asoundrc
```There are other ways to create files too, but those are best described later once you are more familiar with Linux and the command line.

---

### Post by rhichi on 2008-05-19
Well that solves that problem, but now it won't let me save default.pa, claiming I don't have permission. If I try to save as over it, I'm told it's a read-only file and I can't replace it.

---

### Post by Inxsible on 2008-05-19
> **rhichi said:**
> Well that solves that problem, but now it won't let me save default.pa, claiming I don't have permission. If I try to save as over it, I'm told it's a read-only file and I can't replace it.Where are you trying to save it?

You can save anything in your home drive. For everywhere else, you need to have root privs to be able to write to files.

---

### Post by rhichi on 2008-05-19
I tried saving it in the same place it came from. If I just save it in home, won't that mean that I now have duplicate files? How will the comp know which one to use? And besides, since this is my comp, shouldn't I be able to get access? It doesn't even prompt me for root password.

---

### Post by rhichi on 2008-05-19
Never mind. I put my balls on and just tried it; now it works. Thanks so much oh ye who does not hate on the younglings.

---

