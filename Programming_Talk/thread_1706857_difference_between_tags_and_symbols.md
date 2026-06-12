---
title: "difference between tags and symbols"
date: 2011-03-14
forum: Programming Talk
---

### Post by cybo on 2011-03-14
i am using vim an linux for some time now but i never really became a power user so i decided to be one. right now i have a question about tags and symbols. i know what html tags are but it i don't know what tags are in linux. i also can't figure out what symbols are. i know that they are somehow tied to searching through code (an the ability to search through code using vim) but i can't figure out how. i'm using exVim (it is very much like ide) which has a search feature. i would really appreciate if someone could explain what tags and symbols are?

any help is appreciated

---

### Post by MadCow108 on 2011-03-14
it depends on the context.
I guess you are speaking about tags created by [exubertant ctags](http://ctags.sourceforge.net) used to index source code.
well and thats what they are, a search index for sourcecode. its more efficient than brute force greping.
many tools use this type of index for all kinds of stuff, e.g. there are a bunch of plugins for vim using it for keyword competition and displaying function signatures in the editor.

when you usually speak of symbols in the unix world the chances are high that symbols in object files are meant.
These are basically string values representing some chunk of compiled code in an object file, like a function or a variable.
the nm tool displays symbols defined in ELF files. They are used during the linking process to combine several objects to running executables.
```

$cat test.c
int a;
int test()
{
    fasf();
    return 0;
}
$gcc test.c -c
$nm test.o
0000000000000004 C a
                 U fsaf
0000000000000000 T test

```

a and test are symbols defined in test.o, fasf is undefined, the linker will need another object file defining it to do something useful.
the meaning of the letters is described in the manpage

---

