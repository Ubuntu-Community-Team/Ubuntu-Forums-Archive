---
title: "Searching files and manipulating them"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Belgatom on 2008-11-01
Been on Ubuntu for a while now and just figured out that I don't know how to do one of the basic actions. 

Situation: I have a folder. In this folder there are files but every file has been given it's own subfolder. I want to get all those files selected at once and moved somewhere else. 

In windows, I did a search in the main folder for files with specific extension and I could manipulate the files in the search result window. 

In Ubuntu, I can perform the search but I can't manipulate the search results other than deleting them. 

How would I go about getting the results I want without dealing with every file one at a time.

---

### Post by kidders on 2008-11-02
Hi there,

```

stuff
  |
  +- dir1
  |    |
  |    +- file1
  |
  +- dir2
  |    |
  |    +- file2
  |
```

It sounds like you want to move file1, file2, etc. someplace. The simplest way to do that is...```
mv -i /path/to/stuff/*/* /path/to/destination
```
The "-i" covers the possibility that two of the files being moved could have the same name.

If you don't want to move *all* of the files, you can give mv your search criteria in many cases. Let me know if you need to do that.

I hope that helps.

---

### Post by scorp123 on 2008-11-02
> **Belgatom said:**
> Situation: I have a folder. In this folder there are files but every file has been given it's own subfolder. I want to get all those files selected at once and moved somewhere else.  Something like this? ```
find /where/we/should/search -name 'pattern.of.file.name.*.txt' -exec mv {} /new/home/for/files \;
```

---

### Post by Belgatom on 2008-11-02
Thx, I should learn more to use the command line. Managed to do it in the end though. Problem was that in the search field I typed "*.ext" and it didn't find anything. when I put in just the extension, it did and I was able to do what I needed.

---

