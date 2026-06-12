---
title: "Subversion help needed!"
date: 2009-08-09
forum: Programming Talk
---

### Post by wesg on 2009-08-09
Hi,
I write Wordpress plugins, which use the Subversion platform for version control. Hopefully those on the forum can help me with the problem I'm having now.

The SVN client says my working copy is locked, but I can't figure out how to unlock it. I've tried ```
svn cleanup
``` but that fails, and ```
svn unlock
``` doesn't work either. I think the problem started when I added a file to the copy, then tried to rename it. 

Any suggestions? I can't make any updates to the plugins until this is fixed.

---

### Post by dentharg on 2009-08-09
Did you rename the file in the FS or using SVN move operation?

---

### Post by wesg on 2009-08-09
First I did FS, then when I realized the problem, I renamed it back, then tried SVN. Right now the trunk is behaving properly, but the tags folder is locked (still has the wrong file name).

When I issue the command ```
svn cleanup
```
this is the output
```
svn: In directory 'tags/2.6.1'
svn: Error processing command 'committed' in 'tags/2.6.1'
svn: Working copy 'tags' locked
svn: run 'svn cleanup' to remove locks (type 'svn help cleanup' for details)
```

---

### Post by wesg on 2009-08-09
I was able to unlock the directories (there is a file called "locked" inside a hidden svn directory) but now I have a problem in that a file in the trunk is a different name than the one in the tag directory. 

How can I remedy this situation?

---

### Post by dbd on 2009-08-10
Have you tried using ```
svn move
``` to rename the file with the wrong name?

---

### Post by hessiess on 2009-08-10
Re checkout the working copy, manually merge the differances and be sure to use SVN's copy/move/delete etc insted of the OS in the future.

---

