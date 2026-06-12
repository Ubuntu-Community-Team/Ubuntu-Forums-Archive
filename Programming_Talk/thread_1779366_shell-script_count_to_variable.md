---
title: "shell-script count to variable"
date: 2011-06-10
forum: Programming Talk
---

### Post by d32l4 on 2011-06-10
```

#!/bin/bash

TEST=$'count *.avi *.AVI *.mpeg *.MPEG *.divx *.DIVX *.mkv *.MKV *.mpg *.MPG *.mp4 *.MP4'

echo $TEST

```

why do i get a STRING result ( the echo command prints every filename )

if i use the terminal command:

```
count *.avi *.AVI *.mpeg *.MPEG *.divx *.DIVX *.mkv *.MKV *.mpg *.MPG *.mp4 *.MP4
```

i get an integer.

I need an integer. Please help.

---

### Post by gmargo on 2011-06-10
Use the $() form:
```

TEST=$(count *.avi *.AVI *.mpeg *.MPEG *.divx *.DIVX *.mkv *.MKV *.mpg *.MPG *.mp4 *.MP4)

```or, with backticks instead:
```

TEST=`count *.avi *.AVI *.mpeg *.MPEG *.divx *.DIVX *.mkv *.MKV *.mpg *.MPG *.mp4 *.MP4`

```

See the "Command Substitution" section in the **dash(1)** or **bash(1)** man pages for more info.

---

### Post by DaithiF on 2011-06-10
as gmargo says, $( ...) or ` ... ` for running commands and capturing their output.  $' ... ' is a different construct in bash.
from man bash:
```
       Words of the form $'string' are treated specially.  The word expands
       to string, with backslash-escaped characters replaced  as  specified
       by the ANSI C standard.  Backslash escape sequences, if present, are
       decoded as follows:
              \a     alert (bell)
              \b     backspace
              \e
              \E     an escape character
              \f     form feed
              \n     new line
              \r     carriage return
              \t     horizontal tab
              \v     vertical tab
              \\     backslash
              \'     single quote
              \"     double quote
              \nnn   the eight-bit character whose value is the octal value
                     nnn (one to three digits)
              \xHH   the eight-bit character whose value is the hexadecimal
                     value HH (one or two hex digits)
              \cx    a control-x character

```

---

### Post by d32l4 on 2011-06-10
thanks for the answers.
I tried both ways to solve my problem, but now i get:

```

/home/josanna/Documents/scripts/mv2d.sh: 17: count: not found

```

but in the folder I run this script, **are** *.avi - files :(

iam using:
ubuntu 11.04 natty
gnome terminal && fish

is there an other way to count files from the same data type?

---

### Post by DaithiF on 2011-06-10
its not telling you that its not finding avi files, its telling you that it can't find the 'count' command :)

I've never heard of a count command like this either actually.  you say it works from the command line for you, what is the result of the commands:
```
type count

```and
```
which count
```

personally i would count files like:
```
i=$(ls *.avi *.mpg *.etc | wc -l)

```

---

### Post by GrantStoner on 2011-06-10
Remove the quotes? From what I understand, something such as
```
[ "$" -ne "1"]
```would be read as a string, while something like
```
[ $ != 1 ]
```would be read as an integer.
Yeah?

---

### Post by Petrolea on 2011-06-10
Use 'wc' instead of count, I've never heard of it either.

---

### Post by d32l4 on 2011-06-10
Thanks for your answers.
First of all i think I have to apologize for my english :P

 @DaithiF i made a Screenshot:

[myTERMINAL]("http://dl.dropbox.com/u/12434512/Screenshot-1.png")

here you can see the count - command [line 3+4], and what it should do [result printed in line 5]

then i typed in the commands you asked.

The command "mv2d" executed my shell script with: 

```

i=$(ls *.avi *.mpg *.etc | wc -l)

```

i could save an Integer Value in "i", but i got the errors[line 11+12]. Is there a way to hide these errors?

---

### Post by DaithiF on 2011-06-10
interesting.  I think I understand now.  you're running **fish** as your interactive shell.  It has a builtin count command, the only shell I know that does.

your script however has a shebang of #!/bin/bash, so gets run by bash rather than fish, and so the fish-specific count command is not available.

Since i don't know much about fish I'm going to stick with bash -- to suppress the 'cannot access *.mpg' etc type warnings, set the nullglob option in your script with the line:

```
shopt -s nullglob

```
anywhere before the line where you count the files.

---

### Post by d32l4 on 2011-06-10
thanks again for your fast reply...

I take another screenshot...
[Terminal]("http://dl.dropbox.com/u/12434512/Screenshot.png")

i still got an error, the command shopt is not guilty =(
do I have to download an additional package?

---

### Post by DaithiF on 2011-06-10
ah yes, you're running ls within a subshell so the fact that you are setting shopt -s nullglob in the parent has no effect unfortunately.

so plan B :) , throw away the ls error output:
```
i=$(ls *.avi *.mpeg 2>/dev/null | wc -l)

```

---

### Post by kaibob on 2011-06-10
You my want to consider using an array to count files in a directory. This will work with bash only.

[http://mywiki.wooledge.org/BashFAQ/004](http://mywiki.wooledge.org/BashFAQ/004)

---

### Post by sisco311 on 2011-06-10
> **kaibob said:**
> You my want to consider using an array to count files in a directory. This will work with bash only.

[http://mywiki.wooledge.org/BashFAQ/004](http://mywiki.wooledge.org/BashFAQ/004)

+1

```

[sisco@acme xtmp]$ ls -1
file 1
file 2
file 3
file?4
file 5
file 6
[sisco@acme xtmp]$ ls -1 | wc -l
7
[sisco@acme xtmp]$ echo oops
oops
[sisco@acme xtmp]$ files=(*)
[sisco@acme xtmp]$ echo "${#files[@]}"
6

```

---

### Post by Jose Catre-Vandis on 2011-06-10
So how to use:
```
$ IFS= files=(*)
$ echo ${#files[@]}
```
to count multiple file types? Say count all *.avi,*.mkv,*.mpg in a folder where other file types may reside?

---

### Post by sisco311 on 2011-06-10
> **Jose Catre-Vandis said:**
> So how to use:
```
$ IFS= files=(*)
$ echo ${#files[@]}
```
to count multiple file types? Say count all *.avi,*.mkv,*.mpg in a folder where other file types may reside?

```
$ files=(*.avi *.mkv *.mpg)
$ echo "${#files[@]}"
```

or if you are lazy to type so much (like me :P), you can use [Brace Expansion]("http://mywiki.wooledge.org/BashGuide/Patterns?highlight=%28Brace+Expansion%29"):
```
$ files=(*.{avi,mkv,mpg})
$ echo "${#files[@]}"
```

---

### Post by kaibob on 2011-06-10
deleted

---

### Post by d32l4 on 2011-06-11
thy a lot... its finally working now =)

---

### Post by Jose Catre-Vandis on 2011-06-11
Thanks sisco311 (I tried a few variations on that before posting, none of which worked, but now it does)

---

### Post by geirha on 2011-06-11
> **sisco311 said:**
> ```
$ IFS= files=(*.avi *.mkv *.mpg)
$ echo ${#files[@]}
```

or if you are lazy to type so much (like me :P), you can use [Brace Expansion]("http://mywiki.wooledge.org/BashGuide/Patterns?highlight=%28Brace+Expansion%29"):
```
$ IFS= files=(*.{avi,mkv,mpg})
$ echo ${#files[@]}
```

Avoid changing IFS globally, it may cause problems for later commands, and in that code snippet it does absolutely nothing useful.

You may want to enable nullglob, and possibly dotglob.

```
(
    shopt -s nullglob
    files=(*.avi *.mkv *.mpg)
    echo "There are ${#files[@]} avi and mpg files."
)
```

Setting nullglob globally may cause issues later in the script if you're not careful about quoting all the right places, so for safety I put the parenthesis (which starts a subshell) around it.

---

### Post by sisco311 on 2011-06-11
> **geirha said:**
> Avoid changing IFS globally, it may cause problems for later commands, and in that code snippet it does absolutely nothing useful.



D'oh! You are absolutely right.

I was playing with a file with a newline in its name & I forget to quote the array variable. Of course, without the quotes, echo did not print the newline...

:redface:

---

### Post by Jose Catre-Vandis on 2011-06-11
so what's wrong with just:
```
files=(*.avi *.mkv); echo "There are ${#files[@]} avi and mkv files"
```

why would you need the "globs" ?

---

### Post by kaibob on 2011-06-11
> **Jose Catre-Vandis said:**
> so what's wrong with just:
```
files=(*.avi *.mkv); echo "There are ${#files[@]} avi and mkv files"
```

why would you need the "globs" ?

By globs, I assume you are referring to the nullglob and dotglob shell options. 

Nullglob is needed because the "files" array variable will otherwise contain *.avi and *.mkv if no matching files are found. Thus, as presently written, your command will show 2 matching files when run in an empty directory.  

The Bash Reference Manual explains this as follows:

> nullglob. If set, Bash allows filename patterns which match no files to expand to a null string, rather than themselves.

The Bash Reference Manual defines dotglob as follows:

> dotglob. If set, Bash includes filenames beginning with a `.' in the results of filename expansion.

In this instance, dotglob determines whether hidden files are included in the file count.

---

### Post by Jose Catre-Vandis on 2011-06-11
Thanks **kaibob** that's very useful to know and understand :)

---

