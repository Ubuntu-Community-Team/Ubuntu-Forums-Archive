---
title: "making anti-spyware..."
date: 2007-08-31
forum: Programming Talk
---

### Post by hockey97 on 2007-08-31
Hi I want to know how people make anti-virus software and anti-spyware.

are their Libaries?? like I want to make a software that's free and won't take much time, I just wanted to make a program just to pratice my skills in c++, and want to give a free service just so I could pick up some experience.

any suggestions??

---

### Post by Mirrorball on 2007-08-31
There is no spyware for Linux, so you might want to ask this question at some other place.

---

### Post by PaulFr on 2007-08-31
One requirement for an anti-virus software would be to be able to detect executables (especially inside other objects, like emails, zip files).

One way to recognize a virus is to have a dictionary of virus signatures and apply a pattern matching algorithm once you have identified the executable code you need to process.

Another way is to monitor suspicious behavior (like connecting to the net, or scanning lots of files, or trying to replace/load DLLs in other process spaces on Windows). This is more a heuristic for unknown virii and will also work for spyware.

Then again, you could look at open source virus software like ClamAV (**[http://www.clamav.net](http://www.clamav.net)**) - download the source and educate yourself :-)

---

### Post by ryno519 on 2007-09-01
Yeah, I'm not sure there's much of a market for an anti-spyware application on GNU/Linux. If you want to hone your C++ skills the best way would be to get involved with an opensource project and fix bugs.

---

### Post by pmasiar on 2007-09-01
Join any project using C++ ... Why it has to be anti-spyware?

---

### Post by peabody on 2007-09-01
> **hockey97 said:**
> Hi I want to know how people make anti-virus software and anti-spyware.

are their Libaries?? like I want to make a software that's free and won't take much time, I just wanted to make a program just to pratice my skills in c++, and want to give a free service just so I could pick up some experience.

any suggestions??

To my knowledge, virus software auto-protect features periodically scan system memory for positive matches in a database of known virus signatures.  Spyware monitors works similarly.  These products also allow the user to exhaustively scan the harddrive for positive virus signatures.

The hard part isn't writing the code, it's maintaining your own database of known viruses.

If you're simply looking for a project to test your C++ skills on, why don't you try writing a simple game like rock, paper, scissors or hangman.  I guarantee it'll be a lot more fun :).

---

### Post by slavik on 2007-09-02
here's another interestingpiece of info:

way back when, when files had to be small and computers were slow, when someone posted a file somewhere, they would post the length of the file, not an md5 digest.

what a virus would have to do is compress the entire file within itself and decompress it when run. AV was supposed to be able to catch the decompression.

---

