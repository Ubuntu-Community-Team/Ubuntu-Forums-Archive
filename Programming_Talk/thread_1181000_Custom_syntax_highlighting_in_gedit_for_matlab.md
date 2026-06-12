---
title: "Custom syntax highlighting in gedit for matlab"
date: 2009-06-07
forum: Programming Talk
---

### Post by gsub on 2009-06-07
Hi, all.

I'm on Jaunty now, and gedit seems to recognize octave/matlab (*.m) files as Objective C files.

Following the instructions here: [http://ubuntuforums.org/showthread.php?t=368353](http://ubuntuforums.org/showthread.php?t=368353)
I managed to get gnomevfs-info to report the MIME type of all .m files as Matlab

However, gedit does not seem to play along, for some, not all .m files, which are still being highlighted as objective-c.

It sounds weird, but is there any other place where gedit obtains the MIME type of a file it is opening?

Thanks.

---

### Post by soltanis on 2009-06-07
I've noticed that when I told gedit to interpret a .lisp (Common Lisp) file as Scheme (they share at least some similarities in syntax), it would remember in the future, but only for that specific file.

This was in a git repository, and git add . never added new "visitor" files that gedit had made to store this information, so I have concluded its probably stored on a per-file basis somewhere in the .gnome2/gedit directory or something.

---

### Post by sg42 on 2009-06-08
you're right - some files on my system are recognized correctly as matlab, while others are not. 

all it takes for gedit to recognize a file correctly is open -> change highlighting to matlab (octave) -> save.

although i looked in the .gnome directory, but couldn't find anything.

---

