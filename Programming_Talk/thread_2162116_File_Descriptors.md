---
title: "File Descriptors"
date: 2013-07-13
forum: Programming Talk
---

### Post by HiImTye on 2013-07-13
I'm trying to output stdout and stderr to a file, after filtering stderr, but I'm having issues. if I do```
clamscan /any/path/* --max-filesize=1 --max-scansize=1 --debug 3>&1 1>&2 2>&3 3>&- | grep 'size exceeded'
```the data is displayed properly, in order. if I try to redirect the output to a file, however, such as```
clamscan /path/ -opts redirects>&here | grep 'here' &>out
```then I only receive the filtered data in the file, the data originally in stdout is only printed to the console. if I do one of```
clamscan /path/ -opts 2> >(grep 'size exceeded' >> out) >> out
--- or ---
clamscan /path/ -opts 1>out 2>&1 | grep 'size exceeded' >> out
```then I receive a file with information out of order, such as```
* clamscan output
* clamscan output
* clamscan output
...
* debug info
* debug info
...
```
at this point I'm stumped.




[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by ajgreeny on 2013-07-13
Are you sure you need the ampersand in "**&>out**" at the end of your command?

Normally,if you wish to make terminal output into a file, you simply just add "**> filename**" with no ampersand (the space does not seem to matter, but I always use one for clarity.
I have no idea if this will make any difference to your problem, and I have never used & in this situation, but it must be worth trying.

EDIT:  Ok I think you can forget this.  I've just tried using  command &>out and it produces the file as expected, with or without the &.
Sorry, I should have checked first.

---

### Post by HiImTye on 2013-07-13
```
1>file # redirect stdout to file
>file  # same as above
2>file # redirect stderr to file
&>file # redirect stdout and stderr to file
```;)


[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by sisco311 on 2013-07-13
> **HiImTye said:**
> if I try to redirect the output to a file, however, such as```
clamscan /path/ -opts redirects>&here | grep 'here' &>out
```then I only receive the filtered data in the file, the data originally in stdout is only printed to the console.
 Because you redirect only the stdout and stderr of the grep command. You have to create a compound command in order to redirect the output of clamscan as well:
```
{clamscan /any/path/* --max-filesize=1 --max-scansize=1 --debug 3>&1 1>&2 2>&3 3>&- | grep 'size exceeded';} > file 2>&1
```

NOTE: **&>word** is a bashism. It's useful in interactive bash shells, but in scripts the POSIX form is preferred: [B]>word 2>&1
[/B]

---

### Post by HiImTye on 2013-07-13
I was hopeful that this was going to be the solution, but again it outputs one and then the other instead of them mixed, although at least now it's capturing both stdout and stderr in one go

---

### Post by sisco311 on 2013-07-13
Oh, I see. A practical solution would be to grep both the stdout and stderr of the command. It's unlikely that the stdout and stderr of the command are similar.

I've moved your thread to the Programming Talk forum. ;)

---

### Post by HiImTye on 2013-07-13
yeah, I think I'll have to just output them together into a file then filter the file afterwards, or maybe use Sed to filter out anything from the debug that doesn't contain 'size exceeded'

I ended up just using a series of grep commands
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

