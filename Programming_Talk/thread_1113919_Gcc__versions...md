---
title: "Gcc  versions.."
date: 2009-04-02
forum: Programming Talk
---

### Post by redbrain on 2009-04-02
So hey i am just having wierd problems.

So i am writing some applications for work in ubuntu in C with gcc all works great. Then i transfer over to SLES 10 sp1.....

not so great i find that i cant do any memory mangment my free() calls all segfault so i turn on -Wall and -Werror -pedantic etc..

So i find i had some silly unisnged vs signed problems. So i fixed those on ubuntu works fine better mem mangement.. then still on SLES still free() problems so i jsut comment them out and it works ok.

Untill i get to this:

```

extern LinkedList* getKeys_Basic( const char* filepath)                                                                                                     
{      
                                                                                                                                                      
  FILE *cfg= fopen(filepath, "r");  
....
}

```

It seg faults as soon as fopen is called and i dont understand why it works fine on ubuntu and debian and fedora. But i cant understand this.

I am compiling a new version of gcc as SLES 10 has:

gcc (GCC) 4.1.2 20070115 (prerelease) (SUSE Linux)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


So compiling 4.3.3 :) so i am hoping this will fix it. But i cant believe its a standard glibc function causeing a segfault so it must be something to do with my code but ubuntu fixes it for me :S

Has anyone got any experience with older gcc versions and keeping apps working across all of them?

---

