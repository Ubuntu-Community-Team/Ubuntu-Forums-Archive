---
title: "script to count files"
date: 2014-06-10
forum: Programming Talk
---

### Post by jimmyh1972 on 2014-06-10
Hi
I wrote this script:
==================
#!/bin/bash


cd ~/Documents
A=${ls ~/Documents/*.doc | wc -l}
if [ ${A} = 1 ] ; then
`zenity --file-selection`
fi
==================
but its not working
whats the problem?
I need to count a specific file in a directory and then to activate zenity.
thank's ahead
Jimmi

---

### Post by squakie on 2014-06-10
I'm not sure exactly what you are searching for, but I believe the following is happening:

via the ls, you are listing all file names that have the extenstion .doc.  This could be a multiple line file.  You are feeding the list to wc, which with the -l option is counting the newlines in the list. If you are only expecting a single file, perhaps the count would be 1, but I would suspect more than 1.  You then compare that count - $A to 1 (and wouldn't it just be $A??) - so if the count of newlines in the ls output is greater than 1 - quite possible - your zenity command would never execute.

Put an echo of $A ahead of the "if" - it will probably be greater than 1.  Unless you only expect to have no or only 1 file of .doc extension in the folder.  

Are you trying to run zenity against a single file name returned when there is only 1 file of .doc extension in the folder?

---

### Post by sudodus on 2014-06-10
Please ***describe in detail what you want to do***! Otherwise we can only guess, and the tips might be very wrong.

-o-

- If you want the output of **ls ~/Documents/*.doc | wc -l** you should have normal parentheses, not curly parentheses.

- Maybe you should use the same syntax, so $() instead of `` for the zenity line too. ***Do you really want to execute the file, that you select with zenity***? Is it executable, or can it be expected to be executable?

---

### Post by squakie on 2014-06-10
I've been trying that first set statement in a terminal window and it right away says "bad substitution".  Something the OP should have tried before ever making the script.  Executing the script also echoes that error, so obviously Sudodus is right on the button - how can we know what you want to do and what "but it' not working" mean without detail.  What do you want to do?  HOW does it currently "not work"?  What are your error messages?  The list just goes on.  It's very important to state the detail of what you want to do, what you've tried, the exact errors you are getting, etc..  Without that someone stupid like me replies without knowing that information and I give you bad information.  I should have let Sudodus post and waited for you to reply before I ever even made my first post.  So sorry for the bum information, and please do as Sudodus has asked.

---

### Post by jimmyh1972 on 2014-06-10
well its quit simple (or should be) I want to count the number of *.doc files inside the directory,  if there is only 1 file of *.doc inside the directory, if so to execute zenity.

---

### Post by sudodus on 2014-06-10
And what do you want zenity to do? How do you want to use the result of zenity?

---

### Post by Vaphell on 2014-06-10
ls | wc -l approach is unreliable because it ignores the possibility of a filename with newlines.

```
$ > $'file\name.doc'
$  ls | wc -l
2
```
oops.
```
$ find -maxdepth 1 -type f -iname '*.doc' -printf x | wc -c
1
```

---

### Post by squakie on 2014-06-11
Could be wrong here, but I think you also have to pipe stderr to /Dev/null so if no file is found it doesn't dump the error message to the screen as sometimes it confuses someone running the script.  The /Dev above should be a lower case "d" but for some reason my tablet seems to not let me enter itin that string.

---

### Post by steeldriver on 2014-06-11
I think I would do something like

```

#!/bin/bash

shopt -s nullglob
files=( *.doc )

if ((${#files[@]} == 1)); then
  zenity --file-selection
fi

```
or
```

#!/bin/bash

shopt -s nullglob
files=( *.doc )

((${#files[@]} == 1)) && zenity --file-selection


```

which should be safe for all "globbable" filenames and doesn't require any external programs to do the counting.

---

### Post by ofnuts on 2014-06-12
> **alex_deef said:**
> Why not use find command? 
To count all files (including subdirs):

find /home/vivek -type f -print| wc -l

[LIST=1]
[*]because the question here is to count some specific files in some specific directory.
[*]see Vaphell's post above about what happens with "wc -l" if there are LF characters in file names. Of course this is on the verge of pedantic if the script is for your own use, since such files are only created by professors for the final exam of Bash Scripting 101.
[/LIST]

---

### Post by sisco311 on 2014-06-14
> **Vaphell said:**
> 
```
$ find -maxdepth 1 -iname '*.doc' -type f -printf x | wc -c
1
```

Fixed. ;)

You should put the -iname test before the -type test in order to avoid having to call stat(2) on every file.

---

