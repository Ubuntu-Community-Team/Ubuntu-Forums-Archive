---
title: "How to keep linux script from over writing enviornmtent variables ?"
date: 2010-05-02
forum: Programming Talk
---

### Post by youralibaba on 2010-05-02
#! /bin/bash 
#SCRIPT FOR DISPLAYING INODE, FILE PERMISSIONS ETC OF COMMAND ARGUMENTS
for data in $@
do
          set `ls -l`
          echo "$1 $2 "$3"
done

echo "$@"

The sript above is executed:-
./script file1 file2 file3 file4 file 5...

The error is that instead of showing the inode etc, of the ALL FILES IN COMMAND LINE ARGUMENTS, THE SET COMMAND OF LINUX OVER WRITES THE $@, so only "ls -l' of 1st commadn argument(file1) is displayed. The script should display it for every file in linux directory. Plz specify the what is the thing done wrong in the script.

---

### Post by youralibaba on 2010-05-02
Plz help linux gurus.

---

### Post by trent.josephsen on 2010-05-02
I don't really know what you're trying to do, but perhaps you should be using $data in the body of your for-loop? e.g. `ls -l $data`

(p.s. USING ALL CAPITAL LETTERS IS SHOUTING.  Please use mixed case.)

---

### Post by soltanis on 2010-05-03
Why are you trying to write a bash script? You can just do this:

```

ls -l file1 file2 file3...

```

At least that's what it looks like you're trying to do.

---

### Post by detroit/zero on 2010-05-03
> **youralibaba said:**
> #! /bin/bash 
#SCRIPT FOR DISPLAYING INODE, FILE PERMISSIONS ETC OF COMMAND ARGUMENTS
for data in $@
do
          set `ls -l`
          **echo "$1 $2 [COLOR=Red]"[/COLOR]$3"**
done

echo "$@"

The sript above is executed:-
./script file1 file2 file3 file4 file 5...

The error is that instead of showing the inode etc, of the ALL FILES IN COMMAND LINE ARGUMENTS, THE SET COMMAND OF LINUX OVER WRITES THE $@, so only "ls -l' of 1st commadn argument(file1) is displayed. The script should display it for every file in linux directory. Plz specify the what is the thing done wrong in the script.
I'm not sure, but I think you have an extra quotation in the line I highlighted above.

If saving keystrokes is your aim, typing "./script" (8 chars) is more than just typing "ls -l" (5 chars). Since the script syntax is the exact same as the command being executed:
> ./script file1 file2 file3 file4 file 5...
you're not really gaining anything.

Also, I note that your script contains the line I highlighted above
```
           echo "$1 $2 "$3"
```
but, in the syntax you state
> ./script file1 file2 file3 file4 file 5...

There is no file4 and file5 in the echo, so the way things are, you can't run this on more than three files at a time.

As someone else pointed out, having a script for this is sort of  an exercise in futility.

---

