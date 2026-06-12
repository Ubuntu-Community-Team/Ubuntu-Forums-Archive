---
title: "cron and cp -l question"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by tmbg002 on 2008-09-12
I have two questions that I have not been able to resolve through reading the man pages or searching the forums. They are:

1)
When I setup cron to run a script is there anything that I need to put in the file name or in the script that tells it to run or will it just run all non comment lines like they are commands?

2) 
If I use cp -al I have read that -l will just create links instead of copying the whole file, but if the original file is deleted then is the copied link lose its target? Or is none of what i just said correct?

Thanks in advanced!

---

### Post by mrsteveman1 on 2008-09-12
1) If you are just putting a script in one of the premade cron.hourly or cron.daily directories they are just bash scripts, so as long as you keep the interpreter line at the top they should be executed by the shell

2) I assume it does symlinks (never done that before with cp), so if you delete the original file the symlink will remain but will be broken. By default on some linux systems a broken symlink shows up red i believe.

---

### Post by KIAaze on 2008-09-12
> **tmbg002 said:**
> 1)
When I setup cron to run a script is there anything that I need to put in the file name or in the script that tells it to run or will it just run all non comment lines like they are commands?

I think that commands in the crontab file are run by "sh" (shell) by default.
If you are writing scripts, you should **always** put a "shebang line" on the first line to tell the shell which "interpreter" to use.
This is valid not only for bash scripting, but also for python, ruby, perl, etc.
Here's more info on this: [http://en.wikipedia.org/wiki/Shebang_(Unix](http://en.wikipedia.org/wiki/Shebang_(Unix))

> **tmbg002 said:**
> 2) 
If I use cp -al I have read that -l will just create links instead of copying the whole file, but if the original file is deleted then is the copied link lose its target? Or is none of what i just said correct?

Thanks in advanced!

Since you already read the manual, there's no point in me quoting it here.
I'm _[COLOR="Red"]not 100% sure[/COLOR]_, but I made some tests and here's what I think:

**If applied to a file, "cp -al" is equivalent to "ln" (hard link).**
This means that if the "original file" is deleted the "copied link" does not lose its target.
ex:
```
touch file1
cp -al file1 file2
```

To really delete the file, you have to delete file1 and file2.

**If applied to a directory, "cp -al" creates hard links (equivalent to "ln") recursively for all files inside the directory.**
This means that if the "original directory" is deleted the "copied link" does not lose its target.
Unlike a symbolic link however, if a new file is added into one of those directories after "cp -al", it won't appear in the other one!
And when the original directory is deleted, all files that have been added to it after the operation will therefore be lost.

_More info about soft&hard links and inodes:_
[http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-inodes.html](http://www.cyberciti.biz/tips/understanding-unixlinux-filesystem-inodes.html)
[http://en.wikipedia.org/wiki/Hard_link](http://en.wikipedia.org/wiki/Hard_link)
[http://en.wikipedia.org/wiki/Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link)
[http://en.wikipedia.org/wiki/Inode](http://en.wikipedia.org/wiki/Inode)

[B]Just play around in a temporary testing folder.
Also, check out the output of "ls -l". You can see the number of links there. ;)
Once it reaches 0, the file is "lost".[/B]

> Hard links cannot links directories 
Cannot cross file system boundaries

Soft or symbolic links are just like hard links. It allows to associate multiple filenames with a single file. However, symbolic links allows:
To create links between directories
Can cross file system boundaries

These links behave differently when the source of the link is moved or removed. 
Symbolic links are not updated 
Hard links always refer to the source, even if moved or removed

[http://www.cyberciti.biz/tips/understanding-unixlinux-symbolic-soft-and-hard-links.html](http://www.cyberciti.biz/tips/understanding-unixlinux-symbolic-soft-and-hard-links.html)

---

