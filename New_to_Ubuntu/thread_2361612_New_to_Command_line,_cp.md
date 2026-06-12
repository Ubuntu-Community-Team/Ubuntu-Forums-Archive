---
title: "New to Command line, cp"
date: 2017-05-18
forum: New to Ubuntu
---

### Post by Agencyman on 2017-05-18
Hi folks,

I am out of time, GUI copy keeps prompting and stopping. I need to use command line cp with force and recursive to copy about 60 Gb, in a file recovery operation, Windows can't deal with it, but I can see all the directories in Ubuntu .  

I can't even get Command to recognize the directory to be copied. What is the syntax?  it shows /dev/sdh4

 It is on a drive (called by the Files GUI only as Acer), and I want the entire subdir Users copied to a USB drive thus far UNTITLED, and in a new dir.  I could reformat the USB if necessary.

Any assistance would be appreciated, customer impatient, of course :) .

Apologies for coming crawling her for last minute help.

Bruce

---

### Post by TheFu on 2017-05-18
Use rsync, not cp.  rsync won't re-copy files that have been already completed.
```
$ rsync -avz {source} {target}
```

/dev/sdh4 is not a directory. It is a partition.  You probably want/need to mount it before use.  Probably is short for "almost certainly", for someone who isn't an expert at Linux.

USB drives might be formatted with a file system that only allows 2G files. Could that be the issue with the failures?  If you want the owner/group and permissions, then you'll need a Linux file system.

---

### Post by Agencyman on 2017-05-18
Thank you kind responder!

Now I will get back on the case.

---

### Post by Agencyman on 2017-05-18
Working fine so far.  I had to ask a friend, but found out an *amazing* truth, (like an infant discovering the bubbles can be popped as they drift by...), dragging the icon into the terminal instantly put in the proper path and I simply removed the quote marks.

Thx

---

### Post by TheFu on 2017-05-18
Ah - you weren't using *command completion*.  Really should look that up, dude.  It effectively prevents wrong answers.  If you are typing more than 3 characters at a time, then you are doing it wrong.

I still see youtube videos from linux experts where they type everything. Perhaps they are doing it for clarity, but it seems like a noob mistake.  Saw over an hour of Redhat training today and the instructor NEVER used *tab completion*. Not once. It was painful to watch, especially on long paths where is just isn't necessary to type.

BTW, don't assume every terminal works the same way.  And on a server without a GUI, you'd be toast.  By learning to be efficient without a mouse, you'll be better in all situations.

---

### Post by Agencyman on 2017-05-18
:shock:\\:D/:grin:

Thx again,
B.

---

