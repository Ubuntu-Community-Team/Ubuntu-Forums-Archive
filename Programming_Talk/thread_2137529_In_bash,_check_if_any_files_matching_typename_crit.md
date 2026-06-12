---
title: "In bash, check if any files matching type/name criteria exist in a directory"
date: 2013-04-21
forum: Programming Talk
---

### Post by Dreamer Fithp Apprentice on 2013-04-21
I need to determine whether any files matching certain criteria are present in a specified directory.

If it matters the criteria are:

directories, the name of which ends in "_files"
"regular" files, the name of which ends in ".html"
"regular" files, the name of which ends in ".htm"

I don't need to know how many there are or which types. I just need a simple binary logic response:

yes, one or more files of one or more of these types of files is present in the directory specified.
  or
no, no such files are present in the directory specified.

The  path/filename of the directory will be passed to the script in a  variable and stuff I've already done will have established that the  variable contains a valid directory path/filename.

I am trying  doing this with ls commands and putting the output in a variable,  planning to somehow extract the first 50 characters or so of the variable to  establish a new variable (I know, I am the spiritual descendant of Rube  Goldberg) and checking if this matches the expected output in the event  no such files are found but so far I've had no success. Right now I'm  bogging down at the point of establishing a variable containing the  output of an ls command. I've tried a lot of different nomenclatures  with `s, (s, $s, "s, and 's in a remarkably large number of  permutations, but so far it  hasn't worked. I wonder if maybe the size  of the output exceeds the permissable size of variables. Is there some way to send only the first 50 characters of so to the variable and ignore the rest? I've even started to tinker with the idea of sending the output of the command to a temporary text file, getting the variable from it, and deleting the file. I'm also wondering if I'm on the wrong track all together in trying to use the output of ls to do this. Any suggestions?

---

### Post by Lampi on 2013-04-21
try the find command (man find) in conjunction with "-regex"

example:
find ~/MyDocuments -type f -regex .*_files$
find ~/MyDocuments -type f -regex .*\.html$
find ~/MyDocuments -type f -regex .*\.htm$

... and put this in a for loop:

for file in $(find ~/MyDocuments -type f -regex .*_files$) ; do
  echo "file=[$file]" # this will just list the files it found
done

If the files contain whitespaces, you'll need to change $IFS or protect them with ""

---

### Post by sisco311 on 2013-04-21
Check out BashFAQ 004 (link in my signature). ;)

@ Lampi
Please  check out BashPitfalls 001 and BashFAQ 001.

---

### Post by prodigy_ on 2013-04-21
Here's binary logic:
```
#!/bin/bash

for pattern in ^d.*_files$ ^-.*\.html?$; do
	# replace /path/to/folder with actual path and folder name 
	ls -al /path/to/folder | grep -E $pattern >/dev/null && exit 1
done

exit 0
```

Exit code ($?) will be 1 if anything is found or 0 otherwise. If you need output, convert to function (replace exit with return) and add some conditional echo.

---

### Post by schragge on 2013-04-21
@**prodigy_**
Why not just
```
/bin/ls -Alq /path/to/folder | egrep -q '^d.*_files$|^-.*\.html?$' && echo yep || echo nope
```
or even (provided that none of the regular file names ends in [COLOR=blue]_files/[/COLOR]): ```
/bin/ls -Apq /path/to/folder | egrep -q '_files/$|\.html?$' && echo yep || echo nope
```
:?:

@**Lampi**
For binary logic you probably do not need the loop at all, just testing if the output of *find* is not empty should be enough:
```

[[
  -n $(
    find path/to/folder \( -type d -name \*_files -o -type f -regex '.*\.html?$' \) -printf found -quit
    )
]] && echo yep || echo nope

```

---

### Post by prodigy_ on 2013-04-22
> **schragge said:**
> @**prodigy_**
Why not just
TBH, I just suggested an example solution w/o giving it much thought. But great job here, **schragge**! You actually made me remember a thing or two from find/ls manpages.

---

### Post by Dreamer Fithp Apprentice on 2013-04-22
Thanks, guys. Talk about embarassment of riches. I'll study all of this, even if I get another one to work first.

---

### Post by Dreamer Fithp Apprentice on 2013-04-22
> **schragge said:**
> 
@**Lampi**
For binary logic you probably do not need the loop at all, just testing if the output of *find* is not empty should be enough:
```

[[
  -n $(
    find path/to/folder \( -type d -name \*_files -o -type f -regex '.*\.html?$' \) -printf found -quit
    )
]] && echo yep || echo nope

```

I tried this first. The relevant portion of my script, including some tests and comments is:```
# A test to make double sure of how $1 is set followed by Schragge's last method in post 5:
echo "Dollar-mark1 expands to $1 on line 49 just before last method of Schragge in post 5." >> /media/wdsm3/script_testing/test.sh.output.txt
[[
  -n $(
    find \"$1\" -maxdepth 1 \( -type d -name \*_files -o -type f -regex '.*\.html?$' \) -printf found -quit
    )
]] && echo "yep, some html components are present in $1."  >> /media/wdsm3/script_testing/test.sh.output.txt || echo "nope, no html components are present in $1."  >> /media/wdsm3/script_testing/test.sh.output.txt
```
But, note presence of "folder_files" directory in ls output:```
me@precise:~$ ls "/media/wdsm3/script_testing/test_  folder"
file .txt              html_components                subdirectory
folder_files           ordinary_file.txt              subdirectory with spaces
folder_files,hacksaws  ordinary file with spaces.txt

```When I run the script against the same "test_ folder", I get this in test.sh.output.txt, the last two lines of which are the point:```
test.sh begins processing another file here -----------------------
/media/wdsm3/script_testing/test_  folder is dollar one.
_variable_filename_end is set to folder
Dollar-mark1 expands to /media/wdsm3/script_testing/test_  folder on line 49 just before last method of Schragge in post 5.
nope, no html components are present in /media/wdsm3/script_testing/test_  folder.

```So, it isn't responding to "folder_files" as something that should elicit the "yep . . ." response. I tried removing the escape character prior to the *. Seperately, I tried replacing ```
-name \*_files
``` with something modeled on the later part ```
-regex '.*\.html?$'
``` I failed to save it but I think it was ```
-regex '.*_files?$'
```Still the same result. I have a lot of tinkering still to do and other expressions to try, but I thought, rather than one massive post, it would be clearer if I posted progress as I made it.

---

### Post by schragge on 2013-04-22
This ```
find \"$1\"
``` should be ```
find "$1"
``` Your folder contains spaces in its name. With your excessive quoting find sees it as two separate directories:
```
find '"/media/wdsm3/script_testing/test_' 'folder"'
``` Since those directories don't exist, find ends with non-zero exit status.

---

### Post by Dreamer Fithp Apprentice on 2013-04-22
> **schragge said:**
> This ```
find \"$1\"
``` should be ```
find "$1"
``` Your folder contains spaces in its name. With your excessive quoting find sees it as two separate directories:
```
find '"/media/wdsm3/script_testing/test_' 'folder"'
``` Since those directories don't exist, find ends with non-zero exit status.Thanks, Schragge. I made that change and it works.

I added the escaped quotes when plain $1 with no quotes didn't work. I need to study the effects of quotes. They trip me up more than anything. I thought I'd tried "$1" too but, unless I changed something else significant in the meantime, apparently not.

But about the "unless", a strange thing happened to me on the way to the forum . . .
I was trying your first and more general modification of Prodigy's suggestion
```
/bin/ls -Alq /path/to/folder | egrep -q '^d.*_files$|^-.*\.html?$' && echo yep || echo nope
```using an explicit path for testing, as I was suspecting problems with expansion of $1. In other words:```
/bin/ls -Alq "/media/wdsm3/script_testing/test_  folder" | egrep -q '^d.*_files$|^-.*\.html?$' && echo "yep, probable html components are present in $1." >> /media/wdsm3/script_testing/test.sh.output.txt || echo "nope, nothing looking like an html component or associated file is present in $1" >> /media/wdsm3/script_testing/test.sh.output.txt
```and it worked correctly with 26 of the 27 test cases I had prepared but failed in the same way, reporting a false negative, with the same test file, a subdirectory named (at least apparently) "folder_files". So I made and tried "word_files" but that worked correctly, i.e., a positive yep response. So I looked real carefully at the name of the folder giving the problem and it sure looked like "folder_files" but I tried renaming it anyway, thinking maybe there is a character in there that looks like an underline but isn't, so I renamed it to "folder" and then renamed that back to "folder_files" and that fixed it. Now I wish I had moved the file and created a new test case from scratch because I can't reproduce the error. I tried " folder_files" (with a leading space) but that worked correctly. I don't think I CAN create a file with a trailing space. I don't know of any character that closely resembles any of those of "folder_files" but that is the only explanation I can think of. I don't think it can have been any attribute of the file other than name because I didn't replace the file, I renamed it. Anyway, both approaches are working for me now. And perhaps it is easier to believe that a dilettante scripter could get confused than that a "_" should fall from heaven, or something like that.

Thanks, all. I'll mark this solved it the board will cooperate.

---

### Post by trent.josephsen on 2013-04-22
I don't know what problem you might have been having, but...
> **Dreamer Fithp Apprentice said:**
> I don't think I CAN create a file with a trailing space.
```
$ mkdir "folder_files "
OR
$ mkdir folder_files\ 
```
(with a space after the backslash on the second example) would both do it, and that would plausibly explain the behavior you saw. Trailing spaces are a lot easier to type by accident than leading spaces anyway, especially if you created the directory from a GUI file manager.

---

### Post by schragge on 2013-04-23
```
ls -Q
``` will help you spot leading/trailing spaces in file names.

---

### Post by Dreamer Fithp Apprentice on 2013-04-23
> **trent.josephsen said:**
> I don't know what problem you might have been having, but...

```
$ mkdir "folder_files "
OR
$ mkdir folder_files\ 
```
(with a space after the backslash on the second example) would both do it, and that would plausibly explain the behavior you saw. Trailing spaces are a lot easier to type by accident than leading spaces anyway, especially if you created the directory from a GUI file manager.

Thank you. That was a substantial untrue "factoid" I was unreasonably certain of. I see in fact most of the ordinary ways can create such a file, including the GUI way in Caja (and presumably Nautilus) or even saving from Firefox.  I think I probably picked up that misconception trying to save files to a FAT but I don't have a FAT handy to test atm. 

Hmmm . . . I see this means I need some more test files and I'll have to come up with a way to deal with this in a script. Looks easy enough now that I know there are such files.

> **schragge said:**
> ```
ls -Q
``` will help you to spot leading/trailing spaces in file names.Cool! I never noticed that option. Thanks.

---

