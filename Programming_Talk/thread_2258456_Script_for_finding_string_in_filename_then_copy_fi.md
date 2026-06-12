---
title: "Script for finding string in filename then copy file"
date: 2014-12-27
forum: Programming Talk
---

### Post by mark bower on 2014-12-27
I need a script file which will look in a directory comprised of folders of .jpg files, one file name at a time, and search for a specified "string".  If the string is found in the file name, that file will be copied to another specified folder.  All of the file names have the form:  [year]_[name]_[activity or event]_[location].jpg.  So typical file examples are,

1984_Mark.Bower_swimming_[Arcadia,CA].jpg
or 1984_Mark.Bower_swimming at Oceanside_[Oceanside,CA].jpg

In the terminal, I goto the folder with the above files and issue ```
cp $(ls | grep Mark) ~/Desktop/catch
```
The code works for the first example, but not the second because of the spaces which "grep" does not tolerate.  The specified string is "Mark", but I also might have wanted to make it "swimming". I have looked at discussions on "xarg" which appears to handle the spaces issue, but I could not follow the complications of the code.

The purpose of the desired script is obvious.  Given a zillion stored images on a HD, one could select out  images of a specific individual from many folders and store them to a single folder which would only contain images of that individual.  So how might I do it?

mark

---

### Post by steeldriver on 2014-12-27
You don't need a script - you just need to use shell globs instead of (fragile) `ls` and `grep`

```

cp -t ~/Desktop/catch/ *Mark*

```

---

### Post by mark bower on 2014-12-27
Yep, that is sweet and works like a champ when implemented from a folder!  Could I trouble for modification of the code that will tell it to search all folders in a directory - I believe this involves a "recursive" function?  For instance, when @$ ~/Desktop the code would look in all folders on the Desktop for "Mark" and send them to catch.

thanks
mark

---

### Post by steeldriver on 2014-12-27
Well you could enable recursive shell globbing (`globstar`) but the more traditional approach would be to use the `find` command

```

find ***path/to/source/dir/*** -type f -name '*Mark*' -exec cp -t  ***path/to/target/dir/*** -- {} +

```

Before running it you should think about whether there's a possibility of conflicting file names and if so how you want to handle that (noclobber? numbered backups?)

---

### Post by mark bower on 2014-12-28
steeldriver

Wow.  You pulled it all together for me and I thank you v. much for your quick responses.

I will have to spend some time to understand what some of the code does, particularly the "-- {}  +" at the end.  Even if I had read the man on FIND and CP I would not have made it without your help.

happy new year
mark

---

### Post by Vaphell on 2014-12-28
-- is by convention a special parameter that says "here the -options block ends", treat everything after this point as a thing to process (eg file in case of file processing tools, like *mv* here), even if it looks like a switch. Many commands follow that convention. It's a safeguard against filenames starting with - and looking like switch which would confuse the hell out of the command. The command doesn't know if a param is an option or a thing to work on, all params are just a bunch of text passed by the shell.

{} is a placeholder where the names found by *find* are plugged into the* -exec*'ed command and the finishing \; or + declare if you want to run 1 command per file, or bunch them together in 1 big command.

lets say you have file1 file2 file3
find -exec mv -t dir -- {} \; is the equivalent of
mv -t dir -- file1
mv -t dir -- file2
mv -t dir -- file3

on the other hand
find -exec mv -t dir -- {} + is the equivalent of
mv -t dir -- file1 file2 file3

---

### Post by mark bower on 2014-12-28
Vaphell

Thanks for the further, detailed explanation.  I went to "man find" and believe after reading about the options used I fully understand them .  However, again, I never could have done it on my own.  What I did not see in "find"(I may have missed it) was a discussion on the use of "--" as explained by you.  I am guessing that it is explained elsewhere.  I am saving your "knowledge nuggets" along with steeldriver's in a doc for reference.

mark

---

### Post by schragge on 2014-12-29
"--" is not an option to find, it's an option to cp, ls, mv and other GNU tools from the package coreutils. It is described in the [GNU Coreutils Manual]("https://www.gnu.org/software/coreutils/manual/html_node/Common-options.html"). This page is also available locally on your system with
```
info -f coreutils -n 'Common options'
```

---

### Post by Vaphell on 2014-12-29
like schragge said, -- was related to *mv* spawned by *find*
long story short *find* doesn't care about anything between *-exec* and *+*/*\;* it just plugs the relevant stuff in where {} is and spawns the command as is. What the command does with provided params is none of *find*'s business.

```
find -some find_stuff **-exec** [COLOR="#0000FF"]this -is --some=command -- with its own parameters {}[/COLOR] **\;** -some more_find_stuff
find -some find_stuff **-exec** [COLOR="#0000FF"]this -is --some=command -- with its own parameters {}[/COLOR] **+** -some more_find_stuff
```

---

### Post by ofnuts on 2014-12-29
> **Vaphell said:**
> the finishing \; or + declare if you want to run 1 command per file, or bunch them together in 1 big command.

lets say you have file1 file2 file3
find -exec mv -t dir -- {} \; is the equivalent of
mv -t dir -- file1
mv -t dir -- file2
mv -t dir -- file3

on the other hand
find -exec mv -t dir -- {} + is the equivalent of
mv -t dir -- file1 file2 file3

Which leads to a question for which I have not yet found an answer:  omitting commands that have a (slightly) different behavior if passed a single file or multiple files (like grep), and given the assumed better performance when calling one single command on several files, are there cases where the '[SIZE=5]**;**[/SIZE]' is preferred over the '[SIZE=5]**+**[/SIZE]'? For instance are there commands that have a maximum number of input parameters or is there even a system limit (assuming we deal with under a million files...)?

---

### Post by Vaphell on 2014-12-29
my understanding is that + respects the limits enforced by the system and splits the bulk command if necessary.

In some cases, eg mv oldname newname + wouldn't even work, so i guess the rule of thumb would be "use + if your *find* supports it, unless it doesn't make sense". And if i have to do something remotely complicated on a per file basis i prefer to roll my own *while read* loop fed with *find -print0 *and not be restricted by a huge oneliner.

---

### Post by schragge on 2014-12-29
Yup, this is my understanding as well. Citing the [find manual]("http://www.gnu.org/software/findutils/manual/html_node/find_html/Multiple-Files.html"):
> This expansion is done in such a way as to avoid exceeding the maximum command line length available on the system.
 Different approaches are [discussed at some length]("http://www.gnu.org/software/findutils/manual/html_node/find_html/Deleting-Files.html") in the manual cited above (See *info -f find -n 'Deleting Files'*).

---

### Post by mark bower on 2014-12-29
Well thanks.  I went to "info -f coreutils . . ." and, well, got smothered.  I am going to settle for Vaphells explanation for now.

1)Now I have grown the code a bit to implement as a script file, but have trouble inputing the variable "string" (= a person's name).  It would seem the problem is related to the placement of "$" which I have placed before the first " ' ", and between " ' ", and " * "; neither position works.  Any suggestions regarding the syntax needed would be appreciated? (Inputing "source" and "catch" works just fine)

2)Also, the variables source and string are unhappy unless I input the explicit paths, eg /home/rocky/Desktop vs ~/Desktop.  I can easily live with that small discomfort - but maybe there is a way?

```
#!/bin/bash

read -p "Please enter full path to directory of image folders  : " source
echo ""
read -p "Please enter destination folder for copied image files  : " catch
echo ""
read -p "Please enter string to search for within file names  : " string


#SAVE LINE BELOW AS WORKING LINE
#find /home/rocky/Desktop/ -type f -name '*Dulcey*' -exec cp -t /home/rocky/Desktop/catch/ - {} +

#following line works - except for trying to introduce the variable for string
find $source -type f -name '$*string*' -exec cp -t $catch - {} +
```

Thanks
mark

---

### Post by Vaphell on 2014-12-29
quote your "$variables" ($source $catch) or any space inside will make it go boom due to word splitting

*"*$string*"*. ' ' are literal quotes, so even if you didn't put $ in the wrong place, it wouldn't work. Also i suggest using *-iname*, which is case insensitive, instead of case sensitive *-name*

-- not -

~: you might use something like ${source/#~/$HOME}

---

### Post by steeldriver on 2014-12-29
The single-quotes around $*string* prevent it from being expanded by the shell - you need to change those to double-quotes, and in any case it should be *$string*. You should also double-quote your other variables. The `-` should be two `--`

```

find [COLOR=#0000ff]**"**[/COLOR]$source[COLOR=#0000ff]**"**[/COLOR] -type f -name [COLOR=#0000ff]**"**[/COLOR]*$string*[COLOR=#0000ff]**"**[/COLOR] -exec cp -t [COLOR=#0000ff]**"**[/COLOR]$catch[COLOR=#0000ff]**"**[/COLOR] [COLOR=#0000ff]**--**[/COLOR] {} +

```

EDIT: oops beaten by Vaphell!

---

### Post by mark bower on 2014-12-29
Thank you both!

The "*$string*" syntax works just great, and I corrected the "-" to what it was supposed to be, "--".

Sorry, and again a very,very minor issue, but I did not understand how to shorten the path, eg, /home/rocky/Desktop/catch to ~/Desktop/catch?

Anyhow, you guys have been a big help and I have "piece of mind".

mark

---

### Post by Vaphell on 2014-12-30
instead of "$source" use "${source/#~\//$HOME/}". It will translate ~/some/dir to /home/you/some/dir so you don't have to type full path.

---

### Post by ofnuts on 2014-12-30
> **schragge said:**
> Yup, this is my understanding as well. Citing the [find manual]("http://www.gnu.org/software/findutils/manual/html_node/find_html/Multiple-Files.html"):

 Different approaches are [discussed at some length]("http://www.gnu.org/software/findutils/manual/html_node/find_html/Deleting-Files.html") in the manual cited above (See *info -f find -n 'Deleting Files'*).

Definitely sheds some light on the problem. Thx.

---

### Post by mark bower on 2014-12-30
Well, I couldn't get the abbreviated path ($source" use "${source/#~\//$HOME/}" to work? My understanding is that it is intended to "take care of ~/home" part of the path?

So I tried entries of "rocky/Desktop" and "/rocky/Desktop" for "source" with msg "Bad substitution".  Also tried ~/rocky/Desktop with msg "No such file or directory".  Getting it right is probably not worth more effort since it is such a minor issue.  At any rate, I am v. pleased with out the script executes.

Thanks
mark

---

### Post by steeldriver on 2014-12-30
The ~ is a synonym for your home directory (usually that would correspond to the absolute path /home/rocky - assuming your username is rocky) so your Downloads directory would simply be

```

~/Downloads

```

Vaphell's substitution would convert that to /home/rocky/Downloads e.g.

```

$ bash -c 'read -p "Enter source directory: " source; echo "${source/#~\//$HOME/}"'
Enter source directory: ~/Downloads
/home/steeldriver/Downloads

```

---

### Post by mark bower on 2014-12-31
@steeldriver 
The code fully works for me - thanks for the further explanation of Vaphell's code.  While I do not understand the substitution coding, I should have tried just "~/Desktop" vs "/rocky/Desktop" etc.  And I will apply that same code for the destination line.  

So for others that may be looking, I present the full code below which is my script file, made executable, and placed on the Desktop where the photo folders reside.  I remmed the original line where the full path must be entered for "source".
```
#!/bin/bash

#use:  copy selected files from any number of folders in a directory to a destination folder
#where selection is governed by a search of ea file name for a specified string

gnome-terminal -x bash -c '
echo "Copy Select Files From Many Folders to a Single Folder"
echo ""
read -p "Enter full path to <dir> with image folders: " source; 
read -p "Enter destination folder for copied image files: " catch;
read -p "Enter string to search for within file names: " string;
echo "$source"; echo "$catch"; echo "$string";

#find "$source" -type f -iname "*$string*" -exec cp -t "$catch" -- {} +;

find "${source/#~\//$HOME/}" -type f -iname "*$string*" -exec cp -t "$catch" -- {} +;

sleep 10 '
```

Thank you both for getting me through the syntax and coding issues.
mark

---

### Post by mark bower on 2015-04-08
I do not understand the behavior of acceptable paths for entry #2, ie "catch", in the script presented in my post #21(31 Dec 14).  The folder to receive the selected files (in response to an input for "catch", I name "catch-it" and it is located at /home/rocky/Desktop/catch-it.  The 1st and 3rd entries for "source" location and "string" to search for, cause me no grief.

The following are entries and results for inputs to catch, the 2nd entry required in the script:
**catch-it**    - this **works**.
**/home/rocky/Desktop/catch-it**    - this **works**.
**~/Desktop/catch-it**    - THIS DOES NOT WORK.

1) Why does  **catch-it**  alone work with no path information explicitly given?
2) Why doesn't  **~/Desktop/catch-it**  work vs fouling with "No such file or directory" msg?

mark

---

### Post by ofnuts on 2015-04-09
Because "~" is not replaced by /home/{your_id} when in quotes. You can use:
```

"$HOME/Desktop/Catch"

```
or the more contrived:
```

~/"Desktop/Catch"

```

---

### Post by mark bower on 2015-04-09
I modified my post #22 to eliminate quotes which were misleading; I used them for emphasis in my text, but not in the responses required for the script.  
So now I ask again with respect to the script in post #21:

1) Why does **catch-it** alone work with no path information explicitly given?
2) Why doesn't** ~/Desktop/catch-it** work vs fouling with "No such file or directory" msg?

---

### Post by Vaphell on 2015-04-09
Standalone "catch-it" is reachable from the dir you are running the script from so it works pretty much by accident.
Like ofnuts said, ~ cannot be quoted nor stored in variables, otherwise bash won't see it and expand it by default. Bash doesn't look inside strings/vars for ~.

If you want to be able to type in ~, store it in variables and have things work, you need to use the same trick that was applied to *find*'s root dir, ie expand the variable in question with substitution of ${var/#~\//$HOME/}. Once you do that, /home/username/... will be used.

the gist of it.

```
$ mkdir -p ~/test
$ test="~/test"
$ [[ -e $test ]] && echo true || echo false   # test if exists
false
$ [[ -e ${test/#~\//$HOME/} ]] && echo true || echo false    # test if exists
true


$ bash -c 'x="~/Desktop/some-dir"; echo "$x => ${x/#~\//$HOME/}"'
~/Desktop/some-dir => /home/vaphell/Desktop/some-dir
```

---

### Post by mark bower on 2015-04-10
o.k.  thank you both;  "~ cannot be quoted nor stored in variables" really makes sense for me.  Vaphell, based on my experience level I will have to spend some time on your further explanation to understand/get the gist of it.

The script works marvelously; my title for it is "copy_selected_files.sh".  I have about 1,800 35mm family slides scanned and stored in 3 major directories.  When I run the script using my daughter's name, all of the directories and sub-directories are accessed and shortly all the slides with her name in a file name are transfered to the catch folder.  I should say that each digital image has everyones name who is in the photo, included in the file name.  The script makes it very tidy to segregate the photos by person and prepare a DVD of photos including that person. 

I hope my satisfaction with this thread is more reward for you to continue to help others.

thanks
mark

---

### Post by Vaphell on 2015-04-10
```
$ x=~/abc
$ echo "$x"
/home/vaphell/abc
```

bash sees that naked ~ in the code, right off the bat substitutes it with full home dir before doing anything else with this code. Assignment never sees ~, gets  /home/user/abc instead and that's the value stored in $x here.

```
$ x="~/abc"
$ echo "$x"
~/abc
```

this is pretty much equivalent to your scenario. When you prompt user for input, stuff gets saved in the variable verbatim. If you typed in ~, it's going to be literally ~. There is no dir that is literally named '~' so you get errors. That means that you need to process that ~ alias by hand to the true value before trying to access the path.

You can do this with builtin **${x/[COLOR="#008000"]pattern[/COLOR]/[COLOR="#0000FF"]replacement[/COLOR]}** expansion.
pattern obviously is going to be ~ and the replacement is going to be $HOME=/home/username. If the pattern is prefixed with #, it forces the matching only at the start, ~'s in the middle/at the end are going to be ignored.


```
$ x="~/abc~"
$ echo "${x/[COLOR="#008000"]#~[/COLOR]/[COLOR="#0000FF"]====[/COLOR]}"
====/abc~
$ echo "${x/#[COLOR="#008000"]~[/COLOR]/[COLOR="#0000FF"]$HOME[/COLOR]}"
/home/vaphell/abc~
```

Note that my in my previous posts i replaced ~/ with $HOME/ because reasons (~user is a valid alias too so ~=$HOME is not always a rock solid assumption) but it won't work if you type ~ alone.


'~' -> $HOME might be just enough for your needs, but you could also write a tidy function that translates stuff and abstracts the gritty details away, eg

```
unroll()
{
  if [[ $1 = '~' ]]    # ~
  then
      echo "$HOME"
  elif [[ $1 = '~'/* ]]     # ~/stuff
  then
      echo "$HOME/${1#*/}"
  elif [[ $1 = '~'[[:alnum:]]* ]]    # ~user/stuff, looks in /etc/passwd for user's home dir
  then
      local id=${1#'~'}; id=${id%%/*}
      IFS=: read -r _ _ _ _ _ hdir _ < <( grep "^$id:" /etc/passwd )
      [[ -n "$hdir" ]] && echo "$hdir/${1#*/}" 
  else
      echo "$1"
  fi
}

unrolled_find_dir=$( unroll "$find_dir" )
unrolled_dest_dir=$( unroll "$dest_dir" )
```

that function in action:
```
$ unroll '~/abc~'
/home/vaphell/abc~
$ unroll '~pulse/x/~'
/var/run/pulse/x/~
$ unroll '~root/aaa'
/root/aaa
$ unroll '/usr/bin'
/usr/bin

```

---

### Post by mark bower on 2015-04-10
o.k. Vaphell - your creating more homework for me.  Thanks

---

