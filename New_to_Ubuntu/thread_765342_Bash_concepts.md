---
title: "Bash concepts"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by schickb on 2008-04-24
Having come from years of Windows work, I wanted to clarify a few things. When bash (or similar shell) gets an unquoted glob expression it expands it, correct? So when I type "rm *.o" (without the quotes), what rm really gets is a list of files that bash found matching *.o correct? The difference from Windows isn't very noticeable here.

What throws me is that the -R recursive flag for commands like rm behave very different from Windows because of shell expansion of globs.

For example, on Windows the following would recursively delete all files matching the glob pattern "del /s *.o" since it is del that expands the glob recursively . Under bash, however, the shell doesn't know to be recursive so I believe "rm -R *.o" just deletes files in the current directly that match along with recursively deleting any directories in the current directory that match. Correct?

To recursively delete all matching files,  I need to do something like "rm $(find . -name *.o)" or "find . -name *.o | xargs rm". 

Did I get all that right? Is there a simpler way to recursively delete files match a glob pattern? Is there any such thing as a "recursive glob" pattern?

---

### Post by markd on 2008-04-25
I think you've got that about right.  The expansion happens before the command execution.  The find command is the way to go.  There's also the -exec param:

find . -name *.o -exec rm -i {} \;

---

