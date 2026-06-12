---
title: "How to modify multiple file permissions recursively"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by pkadeel on 2012-11-10
Problem:
I have a folder containing around 1000+ files and subfolders for which I want to change file permissions (i.e. folders to 0755 and files to 0644).

Previously I was using ubuntu and nautilus could do that task but now I have switched to xubuntu and I am unable to find any such option in Thunar. I do not want to install nautilus just to accomplish this task because otherwise I like xubuntu and Thunar the way they are.

I have tried the chmod -R but it changes the permissions irrespective of file or folder difference.

Any ideas how to do this without installing anything new? I don't mind if the method requires terminal commands.

---

### Post by HiImTye on 2012-11-10
```
while read f; do sudo chmod 0755 $f; done < <(find . -type d 2>/dev/null); while read f; do sudo chmod 0644 $f; done < <(find . -type f 2>/dev/null)
```should do what you want. make sure you're in the first folder you want to set permissions in, or replace the period with the folder you want to start in

---

### Post by jerome1232 on 2012-11-10
You could use the find command, something like this might do the trick

Files, use with just -print to see what files it would modify, I'd suggest seting up a small test directory with a few files and folders in it to make sure it works as intended
```
find /path/to/the/place -type f -print -exec chmod 0644 {} \;
```and directories, the same but with d
```
find /path/to/the/place -type d -print -exec chmod 0755 {} \;
```

---

### Post by pkadeel on 2012-11-10
> **HiImTye said:**
> ```
while read f; do sudo chmod 0755 $f; done < <(find . -type d 2>/dev/null); while read f; do sudo chmod 0644 $f; done < <(find . -type f 2>/dev/null)
```should do what you want. make sure you're in the first folder you want to set permissions in, or replace the period with the folder you want to start in
Ok it does the job as expected. I tested it on a dummy folder tree. Now i understand what 
```
while read f; do sudo chmod 0755 $f; done
``` is doing here. I can also understand what
```

find . -type d

```is doing. What I could not understand is 
```
<<
``` after the done and ```
2>/dev/null
```Can you please explain the whole process for my knowledge sake.

---

### Post by HiImTye on 2012-11-10
> **pkadeel said:**
> What I could not understand is 
```
<<
``` after the done
< <() is process substitution. it tells *read* to iterate over whatever is in the () instead of a file
> and ```
2>/dev/null
```Can you please explain the whole process for my knowledge sake.it's also process substitution. that tells bash to redirect anything from pipe *2* (*stderr*) to output to */dev/null* instead of outputting to *read*. this saves cycles, by not having *read* try to do work on any errors that *find* produces (usually permission errors)
you can read about them both here: [http://tldp.org/LDP/abs/html/process-sub.html](http://tldp.org/LDP/abs/html/process-sub.html)

---

### Post by pkadeel on 2012-11-10
Thank you @HilmTye and @jerome1232 for your input and guidance.
Problem solved.

---

### Post by Lars Noodén on 2012-11-10
**<<** is is actually two things, there's a space in between them. **<** and **<()**

**<** redirects from a file, or something acting as a file.  So your loop will be reading data from a file.
 
**<()** redirects the output from the stuff running in the subshell between the parenthesis.  I'd like to read more about it myself. 

**2>/dev/null**  This redirects any error messages to /dev/null so you will never see them.  2 stands for stderr (1 is for stout). 

The concept involved is [redirection](http://wiki.bash-hackers.org/syntax/redirection).

Edit:  Oops.  Too slow. :)
Edit 2: Here is material on process substitution:
[http://tldp.org/LDP/abs/html/process-sub.html](http://tldp.org/LDP/abs/html/process-sub.html)

---

### Post by Morbius1 on 2012-11-10
Since you already did a "-R 755" you had to follow HiImTye's method but in the future you might want to start out with something like this:
```
chmod -R a+rwX,go-w /path/to/folder
```All folders will end up as 755 and all files will end up as 644 unless the file was marked executable to begin with. That's what the big "X" does.

Just a suggestion.

---

### Post by pkadeel on 2012-11-10
> **Morbius1 said:**
> Since you already did a "-R 755" you had to follow HiImTye's method but in the future you might want to start out with something like this:
```
chmod -R a+rwX,go-w /path/to/folder
```All folders will end up as 755 and all files will end up as 644 unless the file was marked executable to begin with. That's what the big "X" does.

Just a suggestion.
Frankly speaking, while reading about chmod in the man pages, I saw that X but could not visualize what it can do for me but now after your post, i can see that it could be done this way which is I guess the right way to do such a task.

Thank you for this tip.

---

