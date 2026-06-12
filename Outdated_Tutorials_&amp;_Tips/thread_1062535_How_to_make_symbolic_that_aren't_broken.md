---
title: "How to make symbolic that aren't broken"
date: 2009-02-07
forum: Outdated Tutorials &amp; Tips
---

### Post by johnraff on 2009-02-07
This is a Tip rather than a Tutorial, but it's something that had been bothering me for a long time. About half the symbolic links I made turned out broken, and searching the web brought up no help.

The problem seems to be because the "ln" command looks like "cp" or "mv", but it doesn't work the same way, and the manual doesn't really spell  it out. Let's take a concrete example. Say you're trawling around your file system, and in /usr/share/doc/aptitude/ you find a file README that you'd like another look at later. You can copy it to your desktop no problem with:
"cp README ~/Desktop/aptitude-readme.txt"
and there's a file aptitude-readme.txt on your desktop, because the shell adds the current working directory's path to README automatically before copying it. However: 
"ln -s README ~/Desktop/aptitude-readme.txt"
 results in a broken link. The problem is that you've made a link to README on your desktop, and there's no such file in your Desktop folder. The "file" command will tell you what's going on. Here's how it looks in my terminal:```

john@box:/usr/share/doc/aptitude$ ln -s README ~/Desktop/aptitude-readme.txt
john@box:/usr/share/doc/aptitude$ file ~/Desktop/aptitude-readme.txt
/home/john/Desktop/aptitude-readme.txt: broken symbolic link to `README'
john@box:/usr/share/doc/aptitude$ rm ~/Desktop/aptitude-readme.txt
john@box:/usr/share/doc/aptitude$ ln -s "$PWD"/README ~/Desktop/aptitude-readme.txt
john@box:/usr/share/doc/aptitude$ file ~/Desktop/aptitude-readme.txt
/home/john/Desktop/aptitude-readme.txt: symbolic link to `/usr/share/doc/aptitude/README'
```
If you give the full path to the file you're linking to, it works. "$PWD" will give you the path to the current working directory without having to type it all out.

**relative links**
You can also make links with a relative path instead of the full, absolute, path but it must be relative to the *directory where you're making the link* not the directory you are working in. For example, if you want a link to your .xsession-errors file (still working in that aptitude folder):```

john@box:/usr/share/doc/aptitude$ ln -s ../.xsession-errors  ~/Desktop/xsession-errors
john@box:/usr/share/doc/aptitude$ file ~/Desktop/xsession-errors
/home/john/Desktop/xsession-errors: symbolic link to `../.xsession-errors'
```

As long as you remember that the first path you give to the "ln" command is what's going to be written in the link you should be OK. :)

---

### Post by chenlin on 2011-02-23
:)Thanks a lot

---

### Post by johnraff on 2011-02-23
Glad it helped!


**To moderators:** If the thread title could be edited to read "How to make symbolic links that aren't broken" it would be appreciated :)

---

### Post by clockworkpc on 2011-03-03
> **johnraff said:**
> This is a Tip rather than a Tutorial, but it's something that had been bothering me for a long time. About half the symbolic links I made turned out broken, and searching the web brought up no help.

The problem seems to be because the "ln" command looks like "cp" or "mv", but it doesn't work the same way, and the manual doesn't really spell  it out. Let's take a concrete example. Say you're trawling around your file system, and in /usr/share/doc/aptitude/ you find a file README that you'd like another look at later. You can copy it to your desktop no problem with:
"cp README ~/Desktop/aptitude-readme.txt"
and there's a file aptitude-readme.txt on your desktop, because the shell adds the current working directory's path to README automatically before copying it. However: 
"ln -s README ~/Desktop/aptitude-readme.txt"
 results in a broken link. The problem is that you've made a link to README on your desktop, and there's no such file in your Desktop folder. The "file" command will tell you what's going on. Here's how it looks in my terminal:```

john@box:/usr/share/doc/aptitude$ ln -s README ~/Desktop/aptitude-readme.txt
john@box:/usr/share/doc/aptitude$ file ~/Desktop/aptitude-readme.txt
/home/john/Desktop/aptitude-readme.txt: broken symbolic link to `README'
john@box:/usr/share/doc/aptitude$ rm ~/Desktop/aptitude-readme.txt
john@box:/usr/share/doc/aptitude$ ln -s "$PWD"/README ~/Desktop/aptitude-readme.txt
john@box:/usr/share/doc/aptitude$ file ~/Desktop/aptitude-readme.txt
/home/john/Desktop/aptitude-readme.txt: symbolic link to `/usr/share/doc/aptitude/README'
```
If you give the full path to the file you're linking to, it works. "$PWD" will give you the path to the current working directory without having to type it all out.

**relative links**
You can also make links with a relative path instead of the full, absolute, path but it must be relative to the *directory where you're making the link* not the directory you are working in. For example, if you want a link to your .xsession-errors file (still working in that aptitude folder):```

john@box:/usr/share/doc/aptitude$ ln -s ../.xsession-errors  ~/Desktop/xsession-errors
john@box:/usr/share/doc/aptitude$ file ~/Desktop/xsession-errors
/home/john/Desktop/xsession-errors: symbolic link to `../.xsession-errors'
```

As long as you remember that the first path you give to the "ln" command is what's going to be written in the link you should be OK. :)

I always wondered about that.  In the past I had always used Nautilus: now I can script this!  Thank you :)

---

### Post by nan-tze on 2011-03-22
Ideal!! Thanks for the tip, johnraff!

---

