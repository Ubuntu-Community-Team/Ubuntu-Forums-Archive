---
title: "[SOLVED] bash complete"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by gorgon on 2008-09-20
hi all,

Im trying to figure out how to use the 'complete' command. What I want is to get printed the completion of a directory name without using <Tab>.

Something along the lines of:
```

$ complete [unknown arguments] ~/my-direct

(would print:)

~/my-directory

```
cheers!

---

### Post by Mornedhel on 2008-09-20
The 'complete' utility is for specifying how Bash will try to complete on tabs.

Here is a link to the man page of complete : [http://linux.die.net/man/1/complete](http://linux.die.net/man/1/complete)

What are you trying to do exactly ?

---

### Post by gorgon on 2008-09-20
> The 'complete' utility is for specifying how Bash will try to complete on tabs.

ah, ok! What I want to do is to print/echo the completion, thus not using the tab key. kind of:

$ [complete utility] ~/my-directo
pushing enter would print..
~/my-directory

is there anything that would do this?

---

### Post by Mornedhel on 2008-09-20
I don't think there's a special utility for this. You could always edit Bash's behavior when autocompleting. The relevant files are /etc/bash_completion (system-wide) or your own .bash_completion (only modifies your user's configuration) if you want to try. Be warned : this is not noob-friendly.

If your needs are limited to displaying file names, you could use 'ls ~ | grep my-dir'. This will output all files and folders beginning with my-dir in your home directory. For more complex stuff, use find (not noob-friendly either). Obviously, this will not work for other types of completion (mplayer's arguments, for instance, can be autocompleted).

---

### Post by gorgon on 2008-09-20
> you could use 'ls ~ | grep my-dir'

yes, this is very close to what im looking for. Is there a way to only print the directories and not the files? And is there a way to only print that which *starts* with 'my-dir', and not that which only contains it?

Many thanks!

---

### Post by starcannon on 2008-09-20
I don't know how elegant this is, but it works:

```
ls --hide=*.*
```give that a shot and see if it does what your requesting.

GL and have fun

---

### Post by Mornedhel on 2008-09-20
ls | grep '^my-dir' will display only those that start with my-dir. The ^ means "start of the line". Regular expressions are cool :)

ls -d */ will display only the directories. Combine both :

ls -d */ | grep '^my-dir'

to get what you want. You will probably want to write an alias for that...

---

### Post by Mornedhel on 2008-09-20
> **starcannon said:**
> I don't know how elegant this is, but it works:

```
ls --hide=*.*
```give that a shot and see if it does what your requesting.

GL and have fun

Actually, that doesn't entirely work. It hides files that have a . in their names, which is always the case for directories, but also sometimes for regular files (typical example off the top of my head : Makefile). My way adds a trailing slash, but takes care of such files.

---

### Post by gorgon on 2008-09-20
thanks a lot! bash kicks a$$ :D

---

### Post by starcannon on 2008-09-20
I just got to dinking around with ls a bit and also noticed the -F flag is very handy:

```
ls ~ -a -F | grep /
```that should only list nothing but directories that occur in the /home directory, including .hidden directories, if I understand the output on my screen correctly.

GL have fun

---

