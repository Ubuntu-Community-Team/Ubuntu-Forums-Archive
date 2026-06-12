---
title: "Small Script Task"
date: 2010-06-28
forum: Programming Talk
---

### Post by GreenPanda on 2010-06-28
Hello All, I'm not a very experienced programmer but I'm starting to change that fact. I wanted to do a little scripting project that will hopefully make me more familiar with the linux system.

Just to make it clear, I'm not sure if this is a good idea or even possible as it would perhaps violate linux permissions or something of that caliber. There might be other programs that already do this, but I want make one myself; just for the practice.

Is it possible to have a script checking the /tmp folder for any files that are downloaded (e.g. flash files), and move them into a separate folder as soon as they are finished downloading?

If it isn't, I thank you anyway. If it is, can anyone suggest a language to use, and how I might go about starting this?

---

### Post by unter on 2010-06-28
since noone answer you i bumb yr thread :)

i know only that you could move file with .flv extension from temp to other folder but how can you script to known when .flv has finished? .flv only stays in /tmp until browser is refreshed. how to capture this? maybe programmer answer :D

---

### Post by hannaman on 2010-06-28
Yes, it is possible.  The difficult task is to determine when the file has completely finished downloading.
One way could be to check and see if the process that is downloading the file - such as wget - is complete before moving it.
Another way is to check the file size, wait and then check it again.  If the file has stopped growing, move it, if not wait some more and check again.  This method may be unreliable when getting files from the internet, though.

---

### Post by Some Penguin on 2010-06-29
If you're 'moving' them within the same filesystem, you should be able to create a hard link in the new place and then unlink the original, even while the download continues.

---

### Post by soltanis on 2010-06-29
I always wondered what hard links were for. Guess that answered my question.

By the way, all browsers don't store files with their extension. Google Chrome doesn't, for example, when I examine my cache all I see is a bunch of randomly numbered files and an "index" file which is some kind of binary format. Firefox, though, I think does.

---

