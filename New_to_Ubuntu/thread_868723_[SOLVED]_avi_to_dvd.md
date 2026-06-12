---
title: "[SOLVED] avi to dvd"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by expatCM on 2008-07-24
I have been using ManDVD to convert avi to dvd.  It often works.  There are some times when it just skips through the process though.

Since the identified home page of ManDVD does not exist and since there is no FAQ or forum I was wondering if anyone can suggest another program to use?

---

### Post by rockstarrem on 2008-07-24
If you're looking for a dvd encoder I just looked through the repository and found "DVD Encoder OGMRip", is that what you're looking for?

---

### Post by brian_p on 2008-07-24
> **expatCM said:**
> I have been using ManDVD to convert avi to dvd.  It often works.  There are some times when it just skips through the process though.

Since the identified home page of ManDVD does not exist and since there is no FAQ or forum I was wondering if anyone can suggest another program to use?

If you want simplicity - devede.

---

### Post by didac on 2008-07-24
If you are not afraid of terminals, you can use Mplayer-Mencoder.

If you do, devede will do everything for you. 

```
sudo apt-get install devede
```

or

[http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)
[http://www.getdeb.net/search.php?keywords=devede](http://www.getdeb.net/search.php?keywords=devede)

---

### Post by chronographer on 2008-07-24
DeVeDe works fine, just remember to test it before you start it running, you may need to deinterlace the video or something...

---

### Post by Hospadar on 2008-07-24
Qdvdauthor is more similar to mandvd in that it will do menus, etc.  I've had success with it but you do need to pay attention to what it's doing because it's just a frontend for command-line tools, and if those are not installed/fail qdvdauthor won't work.  but don't worry, it's not hard to use, just keep your eyes open.

---

### Post by halitech on 2008-07-24
+1 for Devede

if you have just a single file (or mulitple parts of the same movie), Devede will work fine, just make sure your output is not above 110% (it over compensates a little) and it should be fine. If you have multiple files and they arent part of the same movie, you could also try Tovid. I've used it in the past and it worked okay.

another option, if you want to use ManDVD and it fails on a single file, install Devede and use it to convert that file to an mpg and then redo the dvd.

---

### Post by expatCM on 2008-07-24
This is a VERY GOOD forum.  A wide range of relevant advice in super quick time.  That is really great :)   I can see that I have some exploring to do ...  many thanks to everyone for taking the time to respond ... I appreciate it ..  :)

---

