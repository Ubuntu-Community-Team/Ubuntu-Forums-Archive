---
title: "Eclipse + sshfs = slow?"
date: 2009-06-29
forum: Programming Talk
---

### Post by Mirge on 2009-06-29
Anybody else notice that Eclipse with sshfs is insanely slow? Any solution(s) for it?

---

### Post by Mirge on 2009-06-29
Trying to figure out RSE... am able to connect, etc. Then I made a PHP project (local) called TestProject1, and changed the default "newfile.php" to "index.php"..... now when I hit the Run button near debug..... it says can't find newfile.... it's trying to run newfile, when I renamed it to index.php. Any idea how to make it understand that the file has changed? heh.

EDIT: nevermind @ "newfile" issue.

---

### Post by Mirge on 2009-06-29
Is there a way to make it so Eclipse PDT runs php -l (lint) to check syntax... rather than actually run the script?

---

### Post by Mirge on 2009-06-29
Getting the Zend version of PDT seems to have solved a lot of issues I've been having with Eclipse PDT...

[http://www.youtube.com/watch?v=VRFZpk-YHl4](http://www.youtube.com/watch?v=VRFZpk-YHl4)
[http://www.youtube.com/watch?v=x8WnciHjXco&feature=channel](http://www.youtube.com/watch?v=x8WnciHjXco&feature=channel)

Both were pretty interesting video tutorials, in case anybody else needed some help.

---

### Post by soltanis on 2009-06-29
sshfs works over an encrypted network tunnel. I wouldn't exactly expect it to be fast.

---

### Post by Mirge on 2009-06-30
> **soltanis said:**
> sshfs works over an encrypted network tunnel. I wouldn't exactly expect it to be fast.

Well I know and understand that, but it was being VERY slow. Geany could save a file in under a second, not instantly as if it was actually on my local disk, but under a second easy. Eclipse was taking 10-15 seconds.

Decided to put that on the backburner for now and try to figure out RSE...

---

### Post by rocketflame on 2009-06-30
i've found eclipse + anything to be slow. i've used in my computers class for a bit but now prefer just using a txt editor.  And it takes FOREVER to load but enough of me complaining  :)

---

### Post by Mirge on 2009-06-30
hehe, I stopped using sshfs with Eclipse... just editing locally & exporting to RSE to upload the files. Real fast.

---

### Post by Mirge on 2009-06-30
Imported a big project...

 5387 mike      20   0 1243m 647m  36m S   93  8.5   7:19.49 java

java using 93% cpu, boooo :(

EDIT: Disabled automatic validation... nice & snappy again.

---

