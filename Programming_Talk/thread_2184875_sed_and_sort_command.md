---
title: "sed and sort command"
date: 2013-10-30
forum: Programming Talk
---

### Post by stinkeye on 2013-10-30
I can remove blank lines and sort a file with...
```
cat file.txt | sed '/^\s*$/d' | sort -d > file2.txt
```
What's the right format so as not to use the cat command
and can I edit the file in place?
Thanks.

---

### Post by papibe on 2013-10-30
Hi stinkeye.

To avoid cat you can use 'file.txt' as a parameter:
```
sed '/^\s*$/d' file.txt | sort -d > file2.txt
```
You can also remove the blanks directly from the file using the 'inplace' (-i) option:
```
sed '/^\s*$/d' -i file.txt
```
Hope it helps.
Regards.

---

### Post by stinkeye on 2013-10-30
> **papibe said:**
> Hi stinkeye.

To avoid cat you can use 'file.txt' as a parameter:
```
sed '/^\s*$/d' file.txt | sort -d > file2.txt
```
You can also remove the blanks directly from the file using the 'inplace' (-i) option:
```
sed '/^\s*$/d' -i file.txt
```
Hope it helps.
Regards.

Hi papibe,
thanks.
Can both the sed and sort command run inplace.

---

### Post by papibe on 2013-10-30
> **stinkeye said:**
> Can both the sed and sort command run inplace.
Not exactly, but yes (there's no inplace option but there's sort of a trick).

Using the --ouput=FILE option, you can redirect the output to a file, even the same file:
```
sort file.txt -o file.txt
```
Regards.

---

### Post by stinkeye on 2013-10-30
OK, thank you.

---

### Post by vasa1 on 2013-10-31
What does "in place" mean? Does it just mean replacing the existing file with the modified one retaining the original name?

>       -i[SUFFIX], --in-place[=SUFFIX]

              edit files in place (makes backup if SUFFIX supplied)



---

### Post by papibe on 2013-10-31
> **vasa1 said:**
> What does "in place" mean? Does it just mean replacing the existing file with the modified one retaining the original name?
Not exactly. That is what 'sort -o' does, which is not proper 'in place', but two steps: read the source file until is finished, closed the source file, and then opening as 'w' a new file with the same name (if exists use the same inode), write the sorted content and finally close the newly opened file.

In place means, opening the source file, as 'rw' and making modifications on the fly using the same file descriptor as the original file. The command rsync also has an in-place option which is very useful to backup big (huge) files, like VM disks (vdi) for instance.

Does that help?
Regards.

---

### Post by vasa1 on 2013-10-31
> **papibe said:**
> Not exactly. That is what 'sort -o' does, which is not proper 'in place', but two steps: read the source file until is finished, closed the source file, and then opening as 'w' a new file with the same name (if exists use the same inode), write the sorted content and finally close the newly opened file.

In place means, opening the source file, as 'rw' and making modifications on the fly using the same file descriptor as the original file. The command rsync also has an in-place option which is very useful to backup big (huge) files, like VM disks (vdi) for instance.

Does that help?
Regards.
Yes, it does :)
So, as a simple way of looking at it, "in place" is useful for large files if disk space is a concern?

---

### Post by drmrgd on 2013-10-31
> **vasa1 said:**
> Yes, it does :)
So, as a simple way of looking at it, "in place" is useful for large files if disk space is a concern?

I guess you could look at it that way too.  I usually think of it as a quick way to make permanent changes to a file if I'm sure that they're correct in one step.  Take this simple text file for example:

```

$ cat output.txt 
There are many tees on the golf course that really hurt my game

```

I probably meant to write 'trees' not 'tees' (tees should be helpful in golf!).  I can fix it with sed:

```

$ sed 's/tees/trees/' output.txt 
There are many trees on the golf course that really hurt my game

```

But, the only place that's taken effect is in the terminal as the change is only make to what's printed to the screen and not to the file.  I can save the change to a temp file and then overwrite the original in two steps, or I can use the **-i** option to change the file in place.  

Also, you can provide arguments to '-i' and actually create a backup file if you wish:

```



$ sed -i.bak 's/tees/trees/' output.txt
$ ls -l output*
-rw-rw-r-- 1 dave dave 65 Oct 31 06:30 output.txt
-rw-rw-r-- 1 dave dave 64 Oct 31 06:29 output.txt.bak
$ more output.txt*
::::::::::::::
output.txt
::::::::::::::
There are many trees on the golf course that really hurt my game
::::::::::::::
output.txt.bak
::::::::::::::
There are many tees on the golf course that really hurt my game

```

Now there are two files, the original renamed 'output.txt.bak' and the new, fixed version called 'output.txt'.

---

### Post by vasa1 on 2013-10-31
I felt a little silly asking about "in place" but I have company: 
[http://backreference.org/2011/01/29/in-place-editing-of-files/](http://backreference.org/2011/01/29/in-place-editing-of-files/)

---

### Post by drmrgd on 2013-10-31
Not silly at all!  Thanks for posting that link; I think it's quite informative!

---

### Post by vasa1 on 2013-10-31
I found this one also informative: [http://www.unix.com/showthread.php?t=202403](http://www.unix.com/showthread.php?t=202403). I got the impression the author wasn't too keen on in place editing.

---

### Post by drmrgd on 2013-10-31
> **vasa1 said:**
> I found this one also informative: [http://www.unix.com/showthread.php?t=202403](http://www.unix.com/showthread.php?t=202403). I got the impression the author wasn't too keen on in place editing.

To me personally, it all depends on what you're doing, how valuable your data is, and what are the resources available to you.  For me, when I have very small text files that will experience very fast I/O and not a lot of system resources are necessary, I have no problem editing in place.  The less amount of time the file is in the buffer, the less likely it is to be a victim of something like a system crash or something along those lines, which would destroy my file (note: the probability is never 0!).  If the file is very large and / or has critical data that's difficult to regenerate, then I would always use a temp file to hold my work while I do the edits.  

Along those lines, if I'm working from a server, now I have the possibility of a system malfunction **along with** the possibility of a network failure.  In those cases I'm more likely to keep a temp file around just to mitigate tragic circumstances, again, depending on how large / critical the data I'm editing is.  

Of course, the safest bet is to always use a temp file and never edit in place.

---

