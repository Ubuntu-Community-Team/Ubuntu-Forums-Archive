---
title: "Sort Directory size"
date: 2011-12-21
forum: New to Ubuntu
---

### Post by lile001 on 2011-12-21
This should be a simple question. 

I am pruning some old files from my system.  I'd like to be able to list files and directories by size to find the largest ones.  When I use ls -l, it lists all directories as 4096 bytes.  is there a way to inquire as to the size of stuff WITHIN the directory?

Then I'd like to sort the list by size, to identify the largest files/folders first.  usually I can eliminate a big portion of the wasted space on my system by getting rid of the five largest files.  usually these are things I downloaded a long time ago, maybe to install a program or something, that I don't need anymore.  But how to find them in all these files without searching folder by folder?

---

### Post by Lars Noodén on 2011-12-21
Did you mean sorting like this?

```

ls -l | sort -k 5 -rn

```

You can also look at the size of a directory with [du](http://manpages.ubuntu.com/manpages/oneiric/en/man1/du.1posix.html)

---

### Post by sudodus on 2011-12-21
or use the Disk Usage Analyzer BaoBab to get an overview
```
baobab directory 
```
All can be seen by
```
baobab / 
```
and the home directories by
```
baobab /home 
```
and the 'other mounted partitions' by
```
baobab /media 
```

---

### Post by mcduck on 2011-12-21
I'd use *du* instead of *ls*:

```
du -hs * | sort -hr
```

---

### Post by lile001 on 2011-12-21
> **sudodus said:**
> or use the Disk Usage Analyzer BaoBab to get an overview
```
baobab directory 
```All can be seen by
```
baobab / 
```and the home directories by
```
baobab /home 
```and the 'other mounted partitions' by
```
baobab /media 
```

baobab rocks!  I had no idea this tool was available.  A nice simple graphical tool that even a Homer like me can understand.

---

