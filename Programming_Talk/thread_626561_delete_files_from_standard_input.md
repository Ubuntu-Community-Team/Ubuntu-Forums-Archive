---
title: "delete files from standard input?"
date: 2007-11-29
forum: Programming Talk
---

### Post by cknight on 2007-11-29
I'm looking for a solution to the following bash-scripting problem.  Using the 'find' command I can generate a list of files and relative paths.  What I'd like to do is to store them temporarily, ask the user a question and then delete (or not) the list of files.  I know 'find' offers the ability to execute a bash command with the list, but I'd like to output the results of 'find' and ask the question ('Are you sure?') first.  (Essentially, 'rm -i' but ask the question once for the entire list of files to delete, rather than for each individual file)

So, I thought the best way was to output the 'find' command to a file and then use this file with 'rm' to delete the file names contained in the file output by 'find'.  But I can't get this last bit to work.  Any ideas or better solutions?

Thanks!

p.s. anyone know of a good tutorial on the web for using 'find'?  Searching for 'find' in google is proving challenging!

---

### Post by DMills on 2007-11-29
man xargs

Also consider the -print0 option to find and corresponding option to xargs....

Regards, Dan.

---

