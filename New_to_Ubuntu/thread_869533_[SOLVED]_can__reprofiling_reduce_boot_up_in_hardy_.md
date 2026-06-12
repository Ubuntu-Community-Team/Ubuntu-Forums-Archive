---
title: "[SOLVED] can  reprofiling reduce boot up in hardy heron ??????"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by imgkg on 2008-07-24
can reprofiling reduce boot up time in hardy heron and how to do it ? 
[http://ubuntuforums.org/showthread.php?t=254263]("http://ubuntuforums.org/showthread.php?t=254263") <-----------this post is outdated i guess or i have a problem 

> How do I do it?

(1) At the bootup menu (GRUB), select your default kernel. You may need to press ESC to see this menu.

(2) Press e for edit.

(3) Choose the first line (it should start with "kernel"). Press e again.

(4) Move to the end of the line, then add the word profile. Press enter.

(5) Press b to boot.


as mentioned in (3) point Choose the first line (it should start with "kernel") i dont have first line that starts with "kernel", first line starts with a "root"

---

### Post by sdennie on 2008-07-25
It's fine if the "kernel" line isn't the first line, just scroll down to whatever line it's on and continue the instructions.  You may or may not notice a difference after profiling the boot like this.

Also, another related thread for doing something similar for login time can be found here: [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)

---

