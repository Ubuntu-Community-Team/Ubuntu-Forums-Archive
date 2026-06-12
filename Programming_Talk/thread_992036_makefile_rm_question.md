---
title: "makefile/ rm question"
date: 2008-11-24
forum: Programming Talk
---

### Post by bovus on 2008-11-24
I trying to write a makefile for a programming assignment.  In my main directory I have the makefile and a folders called src.  In the src directory I have two other directories with source code in both of them.  I want to be able to run the one makefile in the main directory and have it remove all temp files (*~, *.o, \#*, ...) in all of the sub-directories of the main directory while keeping the sub-directories in-tact. Is there a way to do this with the 'rm' command or a makefile trick?

---

### Post by Joe Beam on 2008-11-24
you could use find and rm together with xargs...

find . -type f -name "*~" -print0 | xargs -0 rm -v
find . -type f -name "*.o" -print0 | xargs -0 rm -v
find . -type f -name "#*" -print0 | xargs -0 rm -v

---

### Post by dwhitney67 on 2008-11-24
You could specify within your Makefile the directories which contain the source code.  Then iterate over each of these directories to remove the unwanted files.

If you plan to use a wildcard character (i.e. the '*') in your statements, I would make a backup of everything before you proceed.  It is not uncommon to hear that someone accidentally deleted their source code files as well because of a typo in their script (or Makefile).

Another alternative available to you is to create Makefiles in the source code directories.  These Makefiles can be called from your top-level Makefile.

---

### Post by bovus on 2008-11-24
> **dwhitney67 said:**
> Another alternative available to you is to create Makefiles in the source code directories.  These Makefiles can be called from your top-level Makefile.

I tried doing this (because I though it would be the easiest way). However I don't think I know how to properly do it. First I tried this:

In main makefile I have a section called "clean" which does this:

clean: src/cards/clean

(there is a clean section in src/cards/makefile that removes unwanted files)

But make give me this error:

make: *** No rule to make target `src/tests/clean', needed by `clean'.  Stop.


then I modified the main makefile's clean section to be

clean: src/cards/makefile

and in src/cards/makefile under the "all" section I call the "clean" section.  This did not throw an error but it also did not remove the unwanted files in the the src/cards directory

---

### Post by bovus on 2008-11-24
> **dwhitney67 said:**
> If you plan to use a wildcard character (i.e. the '*') in your statements, I would make a backup of everything before you proceed.  It is not uncommon to hear that someone accidentally deleted their source code files as well because of a typo in their script (or Makefile).

Yea, I made sure I did that:

backup: fclean
        tar -cvvf $(BACKUP_DIR)/$(PROJECT_NAME).tar . >$(BACKUP_DIR)/$(PROJECT_NAME)_backup.log
        gzip -c $(BACKUP_DIR)/$(PROJECT_NAME).tar >$(BACKUP_DIR)/$(PROJECT_NAME).tar.gz
        -rm -f $(BACKUP_DIR)/$(PROJECT_NAME).tar

---

### Post by dwhitney67 on 2008-11-24
> **bovus said:**
> I tried doing this (because I though it would be the easiest way). However I don't think I know how to properly do it. First I tried this:

In main makefile I have a section called "clean" which does this:

clean: src/cards/clean

(there is a clean section in src/cards/makefile that removes unwanted files)

But make give me this error:

make: *** No rule to make target `src/tests/clean', needed by `clean'.  Stop.


then I modified the main makefile's clean section to be

clean: src/cards/makefile

and in src/cards/makefile under the "all" section I call the "clean" section.  This did not throw an error but it also did not remove the unwanted files in the the src/cards directory

Top-Level Makefile could look something like:
```

SRC_DIR = src/dir1 src/dir2

...

clean:
        @for dir in $(SRC_DIR); do \
            make -C $$dir $@; \
        done

```

Your Makefile within the source-code directory (e.g. src/dir1):
```

SRCS = $(wildcard *.cpp)
OBJS = $(SRCS:.cpp=.o)
...

clean:
        $(RM) $(OBJS)

```

---

### Post by bovus on 2008-11-24
thanks, I was wondering could this task also be done with the *find* command and piping the results to the *rm* command?

---

### Post by dwhitney67 on 2008-11-24
> **bovus said:**
> thanks, I was wondering could this task also be done with the *find* command and piping the results to the *rm* command?
Yes, you can do it that way too.  There are also options with the 'find' command that could delete the file w/o the need for the 'rm'.

Examples:
```

find srcdir -type f -name '*.o' -delete
find srcdir -type f -name '*.o' | xargs -r rm

```

---

### Post by Joe Beam on 2008-11-25
> **dwhitney67 said:**
> You could specify within your Makefile It is not uncommon to hear that someone accidentally deleted their source code files as well because of a typo in their script (or Makefile).

I know I did that once in school...had to re-write entire program in one night. It actually turned out better.

Be really careful with the # character and shell expansion!

---

