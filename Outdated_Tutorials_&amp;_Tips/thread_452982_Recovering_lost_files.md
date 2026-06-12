---
title: "Recovering lost files"
date: 2007-05-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Keith_Beef on 2007-05-23
I just did a stupid thing...

Copying some files from one disc to another, turned ym back for a moment, blinked, got distracted, and then went to delete the fisrt set of files, thinking that all had gone well.

For some reason, all had not gone as expected, so I was missing two or three subdirectories of a directory, each of which should have contained something in the order of a hundred or so photographs.

I started searching Ubuntuforums for a discussion on undeleting, and found a few wry comments "learn to not carelessly delete files", and helpful hints like sudo cd /#undel:hdaX

Well, I found a good program in the repositories called magicrescue, which has recovered lots of images, including plenty that I really didn't need to recover...

Like twenty or thirty copies of a JPEG resized to various dimensions at various qualities and various degrees of smoothing.

I also found a good toolkit called sleuthkit, along with its GUI.

So, keywords again:

undelete
recover deleted files
magicrescue
sleuthkit


Beef.

---

### Post by kidders on 2007-05-24
Nice one!

> **Keith_Beef said:**
> "learn to not carelessly delete files"It's a little disappointing that someone here would say something like that to you.

Provided you stop writing to the affected filesystem immediately, images are generally quite easily recovered, because the files tend to have such a rigid internal structure. Lots of other things (like certain archive formats) are also good candidates for undeletion ... they can even be recovered after the filesystem that contained them has been repeatedly formatted.

Glad to hear you managed to undo your mistake. :-) Hopefully others in the same situation will benefit from your experience.

Those keywords again:

undelete
recover deleted files
magicrescue
sleuthkit

[SIZE=1](I wonder if that'll bump your thread up the search rankings hehe!!)

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by ryanVickers on 2007-05-24
I know how you feel.  I had thought I had lost everything once for a while, but then I realized the problem (don't mind it, it's irrelevent, not anyones fault, and not even really a problem).  Well, I hope others with this problem find a way to recover their data, and everyone else is very careful.

> "learn to not carelessly delete files"

that is mean in this kind of situation, but true.  Everyone, be careful, and if you have this problem, hope everything goes well.  That's all good advice here so far!

---

### Post by Keith_Beef on 2007-05-26
> **Keith_Beef said:**
> "learn to not carelessly delete files"

> **kidders said:**
> Nice one!

It's a little disappointing that someone here would say something like that to you.



Nobody directed that advice at me, but it was something that I found in other threads.

I don't find it particularly mean, if said in the right spirit, which is why I referred to it as being "wry".

Once bitten, twice shy.


Beef.

---

### Post by BuffaloX on 2007-05-29
Cool this may come in handy. :popcorn::popcorn:

I looked both up, just to see if they would work.
I just did a bit of cleaning up on my drives, a perfect opportunity for a test.
But they are far from  just click and go, a bit too much to figure out, when I'm not exactly desperate.
But nice to know the tools exist. Just in case.

---

### Post by robheus on 2008-05-31
Painfull!!

Where are the good tools when you need them???

I just accidentally deleted some source files when reconfiguring my sources.
At that precise moment I could need some unremove utility.
Unless you write to the disk/parition, the file data is not realy lost, just the blocks have been 'freed' for use by any new file.
Unless you allocate those blocks, the can be restored, and if no file writes occur before you restore them, in principle they can be restored 100%.

But then, I didn't find any tool to quickly resolve this, at least they weren't there in the standard (hardy) linux installation.
So I browsed the internet for some remedy.
Installing those tools was actually worsening the problem, since they could overwrite the lost files (I removed some large files that could be missed in advance to free some more space, hoping that the filesystem would use those blocks instead of the datablocks of the lost files) , and apart from that, none of the tools was actual fit to tackle the problem.

Anyone know of a well-suited tool to handle this situation??

On an old Dos/windows system I used to have a very handy tool that would simply create one bigfile consisting of all the free blocks of the filesystem. Simply copy that file to another drive for further inspection, and delete the original file, and at least your data itself is stored somewhere and could in principle be retrieved and recovered using other tools.

Such a tool would have been handy, since now I can't possible retrieve those files.

---

### Post by finomeno on 2009-09-03
Thank you! (=

---

