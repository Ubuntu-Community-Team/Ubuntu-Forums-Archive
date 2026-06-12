---
title: "[SOLVED] Bash Script to rucurrsively create directories"
date: 2007-11-08
forum: Programming Talk
---

### Post by habtish on 2007-11-08
Since I have to use a windows machine at work, I am using Cygwin to emulate the *nix environment and am asking for your help in creating a bash script to do the following...

I have 20+ directories in a drive 'N' (/cygdrive/n). I want to scan all these directories for the presence of a sub-directory 'abc*' and if it doesn't exist, to create an empty directory with the name 'abc'. 

How can I achieve this?

Thanks!

---

### Post by geirha on 2007-11-08
Something like this perhaps?
```
find -type d -not -name abc -exec install -v -d "{}/abc" \;
```

---

### Post by ThinkBuntu on 2007-11-08
Random, but nice user pic. Does this make you the Conquering Lion of Judah?

---

### Post by habtish on 2007-11-08
> **geirha said:**
> Something like this perhaps?
```
find -type d -not -name abc -exec install -v -d "{}/abc" \;
```

OK, so what I am trying to do is look for a folder that starts with UPC, it could be named 'UPC List' or UPC Lists. If the folder exists, skip, if not create a folder named 'UPC List' as a sub-directory in all of the 20 directories I have.

```

htb@TIMS20050822B /cygdrive/p
$ find -type d -not -name UPC* -exec install -v -d "{}/UPC\List" \;
install: creating directory `./UPC'
install: creating directory `./UPC/List'
install: creating directory `./Dls/UPC'
install: creating directory `./Dls/UPC/List'
install: creating directory `./Dls/ftp%3a%2f%2fmirrors.kernel.org%2fsourceware%2
fcygwin/UPC'
install: creating directory `./Dls/ftp%3a%2f%2fmirrors.kernel.org%2fsourceware%2
fcygwin/UPC/List'
install: creating directory `./Dls/ftp%3a%2f%2fmirrors.kernel.org%2fsourceware%2
fcygwin/release/UPC'
install: creating directory `./Dls/ftp%3a%2f%2fmirrors.kernel.org%2fsourceware%2
fcygwin/release/UPC/List'
install: creating directory `./Dls/ftp%3a%2f%2fmirrors.kernel.org%2fsourceware%2
fcygwin/release/a2ps/UPC'
install: creating directory `./Dls/ftp%3a%2f%2fmirrors.kernel.org%2fsourceware%2
fcygwin/release/a2ps/UPC/List'
install: creating directory `./Dls/ftp%3a%2f%2fmirrors.kernel.org%2fsourceware%2
fcygwin/release/a2ps/UPC/List/UPC'
install: creating directory `./Dls/ftp%3a%2f%2fmirrors.kernel.org%2fsourceware%2
fcygwin/release/a2ps/UPC/List/UPC/List'
install: creating directory `./Dls/ftp%3a%2f%2fmirrors.kernel.org%2fsourceware%2
fcygwin/release/a2ps/UPC/List/UPC/List/UPC'
install: creating directory `./Dls/ftp%3a%2f%2fmirrors.kernel.org%2fsourceware%2
fcygwin/release/a2ps/UPC/List/UPC/List/UPC/List'
install: creating directory `./Dls/ftp%3a%2f%2fmirrors.kernel.org%2fsourceware%2
fcygwin/release/a2ps/UPC/List/UPC/List/UPC/List/UPC'
install: creating directory `./Dls/ftp%3a%2f%2fmirrors.kernel.org%2fsourceware%2

```In the above example, I tested the command you gave me on a network drive P:\ [cygdrive/p] and under a directory called 'Dls', I created a folder 'UPC_list' and in another folder on the P:\ drive called 'Pics', I created another folder called 'UPC List'.

So I wanted to see if the command quoted above was going to skip the P:\Pics folder as well as the P:\Dls folder and make a directory called "UPC List" in the other directories....

What it did was, it created a directory UPC on P:\, on P:\Dls, P:\Pics, P:\Dls\ftp ... at this point I stopped the command since it was not doing what I had wanted it to do... any suggestions?

---

### Post by habtish on 2007-11-08
> **ThinkBuntu said:**
> Random, but nice user pic. Does this make you the Conquering Lion of Judah?

It used to be the official seal of my country back when we had a king who claimed to have a direct linage to King Solomon;'His Imperial Majesty King H/Selassie Conquering Lion of Judah' or something like that... I just use it to identify myself as an Ethiopian :)

---

### Post by geirha on 2007-11-08
Sorry, I missed the * in "abc*" there. That makes it a bit more complex.
I believe this should work.
```

for dir in `find -type d -not -name "UPC*"`; do 
    if ! ls "$dir/UPC"* &>/dev/null; then 
        install -v -d "$dir/UPC List" 
    fi
done

```

---

### Post by habtish on 2007-11-09
> **geirha said:**
> Sorry, I missed the * in "abc*" there. That makes it a bit more complex.
I believe this should work.
```

for dir in `find -type d -not -name "UPC*"`; do 
    if ! ls "$dir/UPC"* &>/dev/null; then 
        install -v -d "$dir/UPC List" 
    fi
done

```
geirha, I really appreciate your help in this. The script above resulted in making a directory in the P:\ called 'dir' and the under that 'dir' directory it made another folder called 'UPC List"... hmmm what are we missing?
```

htb@TIMS20050822B /cygdrive/p
$         for dir in `find -type d -not -name "UPC*"`; do
>                 if !ls "$dir/UPC"* &>/dev/null; then
                if ls "$dir/UPC"* &>/dev/null; then
>                         install -v -d "dir /UPC List"
>                 fi
>         done
install: creating directory `dir '
install: creating directory `dir /UPC List'

```

---

### Post by geirha on 2007-11-09
you've misspelled the install-line there. Try copy/pasting the whole thing.

edit: and also, there's a rogue if-line there as well

---

### Post by habtish on 2007-11-09
Bah, I missed the $ in the $dir, my apologies... part of it worked. Here's what I had in the P:\ drive. ```

htb@TIMS20050822B /cygdrive/p
$ ls
 Pics             another one                synopsis.pdf
Dls                  Space  Stuff                  generate.sh   test

```In the directory "Space", I created a "UPC Lists" folder to see if the script would skip it since it starts with UPC*.
The script ran fine and created a directory "UPC List" in the parent /, all the subfolders including /Space, which it should have skipped....

Edit: Also for folders that have spaces > "another one" in my example above, it created new folders, "another" and "one" and populated those with "UPC List", how can we account for spaces in directory names?

---

### Post by geirha on 2007-11-09
```
install -v -d "dir /UPC List"
``` you also have a space which should not be there.
```
install -v -d "$dir/UPC List"
``` no space between "$dir" and "/UPC List"

---

### Post by geirha on 2007-11-09
We're not handling directories with spaces properly. Better make it a script like this: ```
#!/bin/bash

IFS=$'\n'
for dir in `find -type d -not -name "UPC*"`; do 
    if ! ls "$dir/UPC"* &>/dev/null; then 
        install -v -d "$dir/UPC List" 
    fi
done
```

the $IFS (Internal Field Seperator) by default seperates on any whitespace, By setting it to only seperate on newline, we avoid splitting on spaces in directory-names.

---

### Post by habtish on 2007-11-09
Worked like a charm. You are a life saver!!!

Thanks a bunch for following up on this and helping me through it.....Thank You!!

---

