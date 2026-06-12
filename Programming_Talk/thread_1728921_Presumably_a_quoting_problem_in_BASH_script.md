---
title: "Presumably a quoting problem in BASH script"
date: 2011-04-14
forum: Programming Talk
---

### Post by jamesisin on 2011-04-14
Hello.  I have a script for prepending album numbers in front of track numbers/names for FLAC files (use the bouble-bracket button to get a clean version of the script):

[http://jamesisin.com/a_high-tech_blech/index.php/2011/04/recursive-prepending-script/](http://jamesisin.com/a_high-tech_blech/index.php/2011/04/recursive-prepending-script/)

The problem is that if there is a parenthesis in the folder path I get an error.  It appears that, in spite of my having the variable quoted ( "$directory" ) in my find command, find is running into the opening parenthesis and stumbling.  (I get the same error using single-quotes.)

```
find: paths must precede expression: 02
```

I guess I need to use a different method of quoting the variable, I'm just not clear which that might be.

(Of course if you have other suggestions for improving my script, I'm always open to that as well.)

---

### Post by BkkBonanza on 2011-04-14
See **man find**, search for UNUSUAL FILENAMES.
The print output doesn't always work as expected and it may be that you need to explicitly use print0 instead.

---

### Post by Vaphell on 2011-04-14
can you provide an example that crashes find?

---

### Post by jamesisin on 2011-04-14
BkkBonanza - I'll look into what you say about print0.  Thanks.

Vaphell - Here is an example path that I crafted outside the script so I could see in detail what was happening inside the script:

```
$ directory="/home/[username]/Desktop/Status Quo/Pictures (40 Years of Hits)"
$ echo $directory
/home/[username]/Desktop/Status Quo/Pictures (40 Years of Hits)
$ find "$directory" -type d -name [0-9][0-9]
find: paths must precede expression: 02
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]
```

If I just run the quoted path I get the same thing:

```
$ find "/home/[username]/Desktop/Status Quo/Pictures (40 Years of Hits)" -type d -name [0-9][0-9]
find: paths must precede expression: 02
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]
```

And the same for escaped characters:

```
$ find /home/[username]/Desktop/Status\ Quo/Pictures\ \(40\ Years\ of\ Hits\)/ -type d -name [0-9][0-9]
find: paths must precede expression: 02
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]
```

(As an aside, find doesn't crash per se; it just throws an error.)

---

### Post by DaithiF on 2011-04-14
what version of find? ... works fine for me on 4.4.2:

$ find --version
find (GNU findutils) 4.4.2

---

### Post by Vaphell on 2011-04-14
strange
here is what it looks like on my box

```
$ dir="/home/me/test/test (test)/wtf (666 666)"
$ echo $dir
/home/me/test/test (test)/wtf (666 666)
$ find "$dir" -type d -name [0-9][0-9]
/home/me/test/test (test)/wtf (666 666)/00

```
can you cd to the dir first and run find in .?

---

### Post by BkkBonanza on 2011-04-14
Also working here on 4.4.2

```

find "/home/[username]/Desktop/Status Quo/Pictures (40 Years of Hits)" -type d -name [0-9][0-9]
find: `/home/[username]/Desktop/Status Quo/Pictures (40 Years of Hits)': No such file or directory

```

---

### Post by jamesisin on 2011-04-14
Thanks, Ubuites.  I tried running it while in that directory:

```
find . -type d -name [0-9][0-9]
find: paths must precede expression: 02
```

Could you add folders called 01 and 02 in your test directories and run find again as above?

(I'm also running find 4.4.2 incidentally.)

---

### Post by Vaphell on 2011-04-14
```
$ find "$dir" -type d -name [0-9][0-9]
/home/me/test/test (test)/Status Quo/Pictures (40 Years of Hits)/02
/home/me/test/test (test)/Status Quo/Pictures (40 Years of Hits)/00
/home/me/test/test (test)/Status Quo/Pictures (40 Years of Hits)/01

```

---

### Post by jamesisin on 2011-04-14
Sorry for this.  It looks like it might be a terminal bug in Ubuntu.

If I change a folder/file name (in this case adding the parentheses) which might effect a command or script execution, I have to close all open terminals which were opened prior to the change in order for the change to take effect within the execution of the command or script.

This in spite of the fact that tab-completion within all open terminals (new or prior) function as expected (in and out of scripts).

Odd enough?  Can anyone confirm this buggy behavior?  (I'm running 10.04 here.)

---

### Post by BkkBonanza on 2011-04-14
Here's what I get - it seems to indicate you need quotes on the expression,

```

$mkdir 01 02
$find . -type d -name [0-9][0-9]
find: paths must precede expression: 02
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]
$ find . -type d -name "[0-9][0-9]"
./01
./02

```

---

### Post by jamesisin on 2011-04-14
BkkBonanza - I bet if you close all your terminals and run the same command again it will work.  (See my last post on page 1.)

---

### Post by BkkBonanza on 2011-04-14
I thought it did work.
In my last post I ran it twice - the first time without quotes, the second time with quotes. Didn't the second time work? See output.
I should have put a blank line bewteen for clarity.

---

### Post by jamesisin on 2011-04-14
My script quotes the variable.  If you look back through what I was doing in the testing you will see that I ran it with and without quotes.  If I close out all the terminals the script succeeds (with no quoting of the regular expression).

When I run into this again, I'll test the quoting of the regular expression in my script without restarting all my terminals.

I'm still guessing that if you restart all your terminals you will get it to succeed without quoting the regular expression.

(Is quoting regular expressions a best practice?)

---

### Post by Arndt on 2011-04-14
> **jamesisin said:**
> My script quotes the variable.  If you look back through what I was doing in the testing you will see that I ran it with and without quotes.  If I close out all the terminals the script succeeds (with no quoting of the regular expression).

When I run into this again, I'll test the quoting of the regular expression in my script without restarting all my terminals.

I'm still guessing that if you restart all your terminals you will get it to succeed without quoting the regular expression.

(Is quoting regular expressions a best practice?)

I don't think the various terminals have anything to do with the problem. If you have files 01 and 02, for example, and issue the command

find . -name [0-9][0-9]

the shell will expand [0-9][0-9] into 01 02, and you will effectively be doing

find . -name 01 02

If you try that, you will see that error message "find: paths must precede expression: 02"

You don't want the shell to expand the expression, you want 'find' to do it, and then you must quote the expression:

find . -name '[0-9][0-9]'

It's not so much a matter of best practice, but a question of what you want to happen.

---

### Post by jamesisin on 2011-04-14
Arndt - Not to be contrary but my script works.  The only time I run into this problem is when I have changed a folder name (not clear on the exact rules for the break) in the path.  Without changing my script (which lacks quotes around the regular expression) I can run it, have it fail, close all terminals, reopen a terminal, and run it again and it will work.

---

### Post by jamesisin on 2011-04-14
Ok, I have sorted out one scenario in which you may repeat this.

```
$ cd Desktop/
$ mkdir animal
$ cd animal/
$ mkdir dog
$ cd dog
$ mkdir 01
$ mkdir 02

[While the terminal is in the dog directory open that folder in Nautilus and change the name dog to dog (not cat).  Then proceed.]

$ RecursiveAutoAddDiscNoToFlac.sh 


This script changes FLAC file names under a containing folder which you supply.
It assumes that your discs are separated into numbered sub-folders.
As such sub-folder names should be 01, 02, and so forth.

Example:  "01/01 &#8211; Track Name.flac" becomes "01.01 &#8211; Track Name.flac"

I will require the path to the containing folder: /home/[username]/Desktop/animal/dog\ \(not\ cat\)/


I have confirmed this is a directory.
Press <ENTER> to continue (ctrl-c will abort).

find: paths must precede expression: 02
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

[As you can see the script errors as per the thread.  Now if you change up one directory (to leave the changed directory) you will see something different.]

$ cd ../
$ ls
dog (not cat)
$ RecursiveAutoAddDiscNoToFlac.sh  

This script changes FLAC file names under a containing folder which you supply.
It assumes that your discs are separated into numbered sub-folders.
As such sub-folder names should be 01, 02, and so forth.

Example:  "01/01 &#8211; Track Name.flac" becomes "01.01 &#8211; Track Name.flac"

I will require the path to the containing folder: /home/[username]/Desktop/animal/dog\ \(not\ cat\)/


I have confirmed this is a directory.
Press <ENTER> to continue (ctrl-c will abort).


mv: cannot stat `/home/[username]/Desktop/animal/dog (not cat)/02/*.[Ff][Ll][Aa][Cc]': No such file or directory
*.[Ff][Ll][Aa][Cc] changed
mv: cannot stat `/home/[username]/Desktop/animal/dog (not cat)/01/*.[Ff][Ll][Aa][Cc]': No such file or directory
*.[Ff][Ll][Aa][Cc] changed

```

(The mv operation fails because find finds no flac files.  But the find command works the second run.  That's the point.)

---

### Post by Vaphell on 2011-04-14
so without quoting you script is not working, but sort-of-working which shouldn't be considered 'good enough'. Such glitches can be disastrous in case of potentially more destructive commands.
Quote that pattern to avoid expansions and it will always work, name changed,terminal restarted or not.

---

### Post by jamesisin on 2011-04-14
So, to hearken back to a question I asked earlier in this thread, quoting regular expressions *is* a best-practice?

---

### Post by Vaphell on 2011-04-14
quoting anything that can be misunderstood by the shell is the best practice. fixed strings - single quotes, strings with variable expansion - double quotes.
Bash does wildcards and simple regexes so you need hide them from it if you want to pass them as parameters.

my first thought was 'hey, he didn't quote the pattern' (i had my share of problems with bash expanding find parameters in the past) but given that this command worked somehow on my box i dismissed lack of quotes as a cause without much thought :) i must have been dreaming or something :)

---

### Post by jamesisin on 2011-04-15
Of course there is only a problem in the weird circumstance where the folder name is changed unbeknownst to the shell.  That can't be correct/expected behavior.

I'm still a bit dubious of quoting regular expressions.  If I do so in this operation it gets borked pretty badly:

```
for filename in */*.[Ff][Ll][Aa][Cc]
   do
      echo $filename
   done
```

That works great.  I can't get it to work with quotes.  If I quote the entire search term ( "*/*.[Ff][Ll][Aa][Cc]" ) I get one result instead of a per item result (an array of one element instead of an array with one element per flac returned).

---

### Post by Arndt on 2011-04-15
> **jamesisin said:**
> Of course there is only a problem in the weird circumstance where the folder name is changed unbeknownst to the shell.  That can't be correct/expected behavior.

I'm still a bit dubious of quoting regular expressions.  If I do so in this operation it gets borked pretty badly:

```
for filename in */*.[Ff][Ll][Aa][Cc]
   do
      echo $filename
   done
```

That works great.  I can't get it to work with quotes.  If I quote the entire search term ( "*/*.[Ff][Ll][Aa][Cc]" ) I get one result instead of a per item result (an array of one element instead of an array with one element per flac returned).

Here you should not quote, because it's not a different program that wants a file matching expression, it's all within the shell.

(These are not really regular expressions, but the name doesn't matter here.)

---

### Post by Vaphell on 2011-04-15
every time shell sees something that looks like a pattern it tries to evaluate it in place
so when you do
```
for file in *.flac
```
in reality you get
```
for file in 1.flac 2.flac 3.flac ...
```
this is desired
but when you want to run find or grep you don't really want your pattern to be substituted in place by a bunch of filenames that happen to match the pattern.
```
find -name *.flac
``` becomes ```
find -name 1.flac 2.flac 3.flac ...
``` and that leads to obvious problems with syntax and logic
In such scenarios you want to pass the untouched pattern to the command and to do that you need to use quotes. Single quoted strings are completely ignored by the shell.

try```
echo *
echo '*'
```

---

### Post by jamesisin on 2011-04-15
Yes, I knew about single-quotes creating a literal string (non-parsed).  I also recognize that since echo uses double-quotes echo "*" will not be parsed (as the shell might otherwise parse "*" under some other command).

Though the matter of quoting regex's seems a bit convoluted, I think I understand the general principle you are espousing: if the regex is to be handed over to another application/command it's probably time to quote it.  Is that about correct?

---

### Post by Vaphell on 2011-04-15
yes, that's correct - otherwise shell may helpfully expand it before the command has a chance to see it.

---

### Post by jamesisin on 2011-04-15
Perhaps I'm making a similar mistake in this other script:

[http://jamesisin.com/a_high-tech_blech/index.php/2011/04/malleable-renaming-script/](http://jamesisin.com/a_high-tech_blech/index.php/2011/04/malleable-renaming-script/)

It fails when what is to be replaced is a pattern in the containing folder (path) name when I use the look in sub folder pattern (*/*....).  Rather it tries to replace the space in the containing folder instead of the file name (when available).

Script:

```
#for filename in *
for filename in */*.[Ff][Ll][Aa][Cc]
#for filename in */*.[Mm][Pp]3
#for filename in */*.[Oo][Gg][Gg]
   do
   mv "$filename" "${filename/ / &#8211; }"
   echo $filename changed
done


exit
```

Results:

```
$ mkdir animal
$ cd animal/
$ mkdir dog
$ touch "dog/01 .flac"

$ pwd
/home/[username]/Desktop/animal

$ RemoveStringModifiable.sh
mv: cannot move `dog /01 .flac' to `dog &#8211; /01 .flac': No such file or directory
dog (not cat)/01 .flac changed

$ ls dog
01 .flac
```

It's trying to make the substitution in the first occurrence in the (relative) path instead of merely the file name.

Ideas?

---

### Post by kaibob on 2011-04-15
It's a bit confusing, but it appears that the dog directory contains a space at the end. If that's the case, then you have a few options. One is to change into the dog directory before renaming so that bash only returns the file name and not the path. Another is to assign the path and file names to separate variables with parameter expansion ; change the file name pretty much as done in your script; and then perform the move. An example of the latter approach is:

```
#!/bin/bash

for file in */*.flac ; do
  direc="${file%/*}"
  name="${file##*/}"
  mv "$file" "${direc}/${name/ / &#8211; }"
done
```

As an aside, the above issue has nothing to do with quoting. In your shell script, parameter expansion (search and replace) is working the way it's supposed to work.

---

### Post by Vaphell on 2011-04-15
edit: not directly related to current problem, more of general advice when handling spaces

start your script with
```
IFS=$'\n'
```
this will separate data by newlines, not by all whitespace characters, space included. Spaces will stay as parts of strings not separators between them so you can do something like for i in `find ...` and it will work without hassle

for i in <pattern> done by shell itself is resistant to that problem though, as long as you "" your loop variable (and all others)

---

