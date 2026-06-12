---
title: "rename files and folders  because of different character set"
date: 2016-10-11
forum: New to Ubuntu
---

### Post by okr-l on 2016-10-11
Hi

I'd like to rename the incompatible characters (mainly germen Umlaute) from my files and folders used in windows change to the suitable characters in Linux (Kubuntu).

A bulk rename, sounds simple, but I haven't succeeded yet.

---

### Post by TheFu on 2016-10-12
Welcome to the forums.

I use 'rename' for stuff like that.  In theory, the default character set is UTF8 on Linux file systems, so an umlaut shouldn't be any issue.
rename is a tiny perl program that uses regex to match. No GUI.  rename handles an entire directory alone, but needs something like 'find -exec' for recursive renaming.  I bet there is a batch renamer GUI somewhere, if that is the question?

Always, always, always test the rename before letting it run. The larger the area/number of files to be renamed, the greater the risk of mistakes.
Some examples: [https://stackoverflow.com/questions/16541582/finding-multiple-files-recursively-and-renaming-in-linux](https://stackoverflow.com/questions/16541582/finding-multiple-files-recursively-and-renaming-in-linux)

---

