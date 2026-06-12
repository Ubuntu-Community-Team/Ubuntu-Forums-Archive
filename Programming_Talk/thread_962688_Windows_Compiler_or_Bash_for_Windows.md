---
title: "Windows Compiler or Bash for Windows"
date: 2008-10-29
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-10-29
I boot fully on linux, but I also am forced to use windows at certian places. I was wondering if their is a compiler to compile Open Source Source Code into windows binary, or a windows version of bash, or both.

I realize that to compile source for windows, that it must be written for windows but I have no compiler for Windows on the windows machines

---

### Post by LaRoza on 2008-10-29
[http://www.cygwin.com/](http://www.cygwin.com/)

[http://win-bash.sourceforge.net/](http://win-bash.sourceforge.net/)

On Windows, use gcc.

---

### Post by stevescripts on 2008-10-29
I have better results with mingw/MSYS, than cygwin ...(your results may vary ;) ) 
[http://www.mingw.org/](http://www.mingw.org/)

Steve

---

### Post by LaRoza on 2008-10-29
> **stevescripts said:**
> I have better results with mingw/MSYS, than cygwin ...(your results may vary ;) ) 
[http://www.mingw.org/](http://www.mingw.org/)

Steve

I was too lazy to google for it, and copied the cygwin from the first google search.

---

### Post by Majorix on 2008-10-29
> **LaRoza said:**
> On Windows, use gcc.

Are we sure there is a vanilla gcc for Windows? I thought that was why there is a MinGW :confused:

---

### Post by slavik on 2008-10-29
mingw == gcc on windows

---

### Post by Majorix on 2008-10-29
^ My thoughts exactly :)

---

### Post by Mr.Macdonald on 2008-10-29
without revealing any secrets, lets just say that I am not allowed to install anything on the windows machine. I need a pre-built binary or a way to compile win-bash on a linux machine

I am not doing anything wrong in my eyes and probably yours unless, you feel that running putty and pscp on a communist schools computers as wrong

---

### Post by ghostdog74 on 2008-10-29
you are not allowed to install anything, so are you sure you can bring your compiled binary and "install" into your windows machine?

---

### Post by Mr.Macdonald on 2008-10-30
I will have the binary on a CD and execute it from there, that what I have been doing with Firefox and putty

Might i mention that I probably need a version with a premade GUI, not one that uses the systems console

---

### Post by WW on 2008-10-30
You can cross-compile on Linux; here's one on many threads about cross-compiling in Linux for Windows: [http://ubuntuforums.org/showthread.php?t=724495](http://ubuntuforums.org/showthread.php?t=724495)

EDIT: I wrote a more detailed response about cross-compiling in post #11 of [this thread](http://ubuntuforums.org/showthread.php?t=473174).

---

