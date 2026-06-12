---
title: "C Function prototypes and ctags"
date: 2011-01-30
forum: Programming Talk
---

### Post by benjiisnotcool on 2011-01-30
Hi all,

Ive started some programming for a uni project and as part of it I want to use a pseudo terminal.  I'm not too experienced with this sort of programming so I thought I'd use a tags file to give me stuff like parameter info while I'm coding (I use Vim).

All the reading I've done points me to use
```
ctags -R --c-kinds=+p
```and I've also tried
```
ctags -R --c++-kinds=+p --fields=+iaS --extra=+q
```However I don't seem to get any tags relating to functions.  This is the output I get from pty.h

!_TAG_FILE_FORMAT    2    /extended format; --format=1 will not append ;" to lines/
!_TAG_FILE_SORTED    1    /0=unsorted, 1=sorted, 2=foldcase/
!_TAG_PROGRAM_AUTHOR    Darren Hiebert    /dhiebert@users.sourceforge.net/
!_TAG_PROGRAM_NAME    Exuberant Ctags    //
!_TAG_PROGRAM_URL    [http://ctags.sourceforge.net](http://ctags.sourceforge.net)    /official site/
!_TAG_PROGRAM_VERSION    5.8    //
_PTY_H    /usr/include/pty.h    21;"    d

I can't seem to get any more than that and it's driving me mental!  I've used ctags before with plenty of success but this was on gtk+ library and C++ stuff, never C.
Any ideas would be brill.

Cheers

---

### Post by benjiisnotcool on 2011-01-31
Sorted.  Downloaded the c lib source and ran ctags on that to get everything I need.
D'oh.

---

