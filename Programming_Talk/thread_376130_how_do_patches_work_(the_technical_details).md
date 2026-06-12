---
title: "how do patches work? (the technical details)"
date: 2007-03-04
forum: Programming Talk
---

### Post by speedingbullet on 2007-03-04
I know that patches cover up security holes and make the program run better, but my question is: Say your making a patch written in Python, but the patch is for a program written in C++. How would you get them to be able to connect to each other? Infact, how can you get the patch to connect to the program, even if its in the same language as the program?


I'm a bit uninformed of how this works.

---

### Post by Tomosaur on 2007-03-04
Generally speaking, a patch is a comparison between a file and the newer version. Let's say you have a file installed on your system, which looks like this:

```

#include <stdio.h>
int main(){
  printf("Hello World!");
  return 0;
}

```

But a newer version is released:
```

#include <stdio.h>
int main(){
  printf("Hello World!");
  printf("Goodbye World!");
  return 0;
}

```

Well, the patch would compare the two files, and produce a patching file, which details the differences between the two:

```

insert "printf(\"Goodbye World!\");" @ line: 4 column 2

```

The 'patch installer' simply uses the comparison file to make the changes to the original file. Now, some patches are different - maybe you want to add extra files or whatever. The principle is still the same.

If you want to check this out for yourself, create two identical files, make some changes to one of them, then run 'diff' and 'patch' between the two.

The system is not the same for every patch, but that's a basic example.

---

### Post by studiesrule on 2007-03-04
Well, I may not be adequately knowledgable about this, but I do know about compile-time patching.

For example, look at this small patch. It comes from a great little program called FileLight (for the KDE desktop). It fixes a small memory crash.
```

[BEGIN PATCH - part.cpp.diff]
--- part.cpp 2004-11-23 23:58:51.000000000 +0300
+++ part.cpp.fixed 2006-06-22 23:52:17.000000000 +0400
@@ -170,8 +170,11 @@
KAboutData*
Part::createAboutData()
{
- static KAboutData about( APP_NAME, I18N_NOOP( APP_PRETTYNAME ), VERSION );
- return &about;
+ //static KAboutData about( APP_NAME, I18N_NOOP( APP_PRETTYNAME ), VERSION );
+ //return &about;
+
+ KAboutData* about = new KAboutData( APP_NAME, I18N_NOOP( APP_PRETTYNAME ), VERSION );
+ return about;
}

bool
[END PATCH - part.cpp.diff]

```

Well, as you can probably deduce, this patch will go and replace certain lines in a file. Now you don't have to go through the source and patch it manually, and all. I don't think i need to explain too much, the '+' is to add a line, and the '-' is to remove a line.

As far as patches after the program has been built, I have no clue. One idea i have is that the object code (output of foo.cpp as foo.o) is recompiled and added to the dynamic linker library (most often .so). Again, I'm not too sure about this.

---

### Post by Mr. C. on 2007-03-04
> **speedingbullet said:**
> I know that patches cover up security holes and make the program run better, but my question is: Say your making a patch written in Python, but the patch is for a program written in C++. How would you get them to be able to connect to each other? Infact, how can you get the patch to connect to the program, even if its in the same language as the program?

I'm a bit uninformed of how this works.

Part of the confusion comes from words being used in different ways.

A patch is simple a set of changes.

Patching is applying those set of changes to something.

What tools one uses to apply a patch depends on the tools selected by the patch creator.  A patch creator can select any tools that allows changing a set of files.  It could be as simple as a set of instructions given to a user, or as complex as a self-extracing, downloading, check-sum verifying application that requires minimal user input.

Make sense?
MrC

---

