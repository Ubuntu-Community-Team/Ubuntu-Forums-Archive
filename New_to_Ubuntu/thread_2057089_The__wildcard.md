---
title: "The * wildcard?"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by Cor. Dunn on 2012-09-12
Hi All,

I really don't understand the * wildcard's definition "will match against none or more characters in a filename" ? Wouldn't that just return everything in the directory?

Any explanation?
Thanks

---

### Post by Kopkins on 2012-09-13
So, the wildcard is not used by itself very often. It is used in combination with other things. You can use it to move several files at once for example.

A simple list of the current directory. From my terminal: ```
kyle@Kopkins:~/Pictures$ ls
2012            Dear_Elizabeth.jpg  GreenTree.jpg  ubuntu-carcoal-1440x900.jpg
3-21_16.JPG     DSC02745.JPG        images.jpeg    ubuntu-carcoal-glow.jpg
AirBalloon.jpg  Gold.jpg            Lightning.JPG
```Move anything with the ending .jpg to parent directory```
kyle@Kopkins:~/Pictures$ mv *.jpg ..
kyle@Kopkins:~/Pictures$ ls 
2012    3-21_16.JPG     DSC02745.JPG      images.jpeg     Lightning.JPG
```Notice that files without the extension as '.jpg' didn't go anywhere. But, the important thing is that ALL of the files with the .jpg extension are moved.

Or, remove several files. ```

$ls
file1         file2.py     file3.txt     picture1
document1     1file        2file

$rm file*

$ls
picture1     document1     1file     2file
```Notice that all the files that start with 'file' and end with anything else are removed, but the files that have 'file' in their name, but do not start with it are still here. If we change this to 'rm *file' then only the two names 1file and 2file would be removed, if we changed it to 'rm *file*' anything with the 'file' in the name would be removed.

Basically it's a space filler. It can be substituted for anything, or nothing. 

Hope that helps clear things up.

Kopkins

---

### Post by Cor. Dunn on 2012-09-13
Yes it did, thank you very much!

---

### Post by Kopkins on 2012-09-13
If you're satisfied with the answer don't forget to mark your thread as solved. From thread tools at the top. 

Glad to help.
Kopkins

---

### Post by Lars Noodén on 2012-09-13
If you want to see the full description look at the manual page for [glob](http://manpages.ubuntu.com/manpages/precise/en/man7/glob.7.html).  The standard it follows is POSIX.  

```

man glob

```

There is also Perl Compatible Regular Expression (PCRE) pattern matching, but that is something different.

---

### Post by nothingspecial on 2012-09-13
[[COLOR="Blue"]A good explanation[/COLOR]]("http://mywiki.wooledge.org/BashGuide/Patterns")

---

