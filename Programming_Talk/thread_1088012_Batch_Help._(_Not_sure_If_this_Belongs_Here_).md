---
title: "Batch Help. ( Not sure If this Belongs Here )"
date: 2009-03-05
forum: Programming Talk
---

### Post by Tek-E on 2009-03-05
First off, Im sorry If I have posted this thread in the wrong section.

But here is my question.
Lately due to my "dumb" friends they have created batch Files that make my computer (Running windows XP) go through a continously loop.  They put
```

shutdown.exe -r -f -t 00

```
in my startup folder.  So to prevent them I wrote a batch file to shutdown without having to worry about this issue.
here it is
```

cd C:\DOCUME~1\ALLUSE~1\STARTM~1\Programs\Startup
xcopy *.* C:\STARTUP_FILES\*.*
del *.*
shutdown.exe -s -f -t 5

```
The only problem is that there are some files that I need to run on start up so I thought I would change the attributes of the files I need/want to run on start up to being hidden that way they are not deleted on shutdown.
```

attrib +h file.exe

```
The file doesnt get deleted but it also doesnt run on start up....
:(

Any ideas on how to fix this?
Thank you very much guys! :D

---

### Post by Can+~ on 2009-03-05
So... why don't just delete the offending batch file?

---

### Post by Tek-E on 2009-03-05
I have.
But with such a thing being such a common occurance why would I want to daily go and manually delete the file(s) from my startup folder when I can have it done for me whenever I shut down.


Why should I do what I can make my computer do for me?

---

### Post by Can+~ on 2009-03-05
I think you can lock the screen with Super (Windows key) + L.

That should prevent dumb users messing with your files.

---

### Post by Tek-E on 2009-03-05
Yes, and that is helpful information.
but not exactley what I am looking for.

---

