---
title: "bashed and loopy"
date: 2014-03-11
forum: Programming Talk
---

### Post by maclenin on 2014-03-11
I am trying, for example, to rename (mv?) the following files...
```
test_342.jpg
test_234.jpg
test_432.jpg
test_423.jpg
test_243.jpg
test_324.jpg
```
...to...
```
test_0000.jpg
test_0001.jpg
test_0002.jpg
test_0003.jpg
test_0004.jpg
test_0005.jpg
```
...using the following bash script:
```
#!/bin/bash
i=0
for file in *.jpg
do
printf -v j "%04d" $i
mv "$file" "$j.jpg"
((i+=1))
done
```
However, my results are:
```
0000.jpg
0001.jpg
...
0005.jpg
```
How can I preserve the "test_" prefix? I assume using regex in some fashion - but I am not quite certain how to deploy.

Thanks for any guidance - and to any good references re: bash usage!

---

### Post by Vaphell on 2014-03-11
```
#!/bin/bash

i=0
for file in *.jpg
do
    [[ ${prfx+x} ]] || prfx=${file%%[0-9]*}
    printf -v f '%s%04d.jpg' "$prfx" "$i"
    mv "$file" "$f"
    ((i++))
done
```

i assume the prefix is the same for all files, so i check if the prfx variable is unset and use the current $file value to extract the relevant part, here with %% (strip longest possible rightside [0-9]*).
In fact you can skip the conditional part and run extraction on each pass, it's not like there are significant savings to be made.

---

### Post by maclenin on 2014-03-13
Vaphell!

Thank you - your script worked as advertised!

However, I strive to understand what I use! With this in mind, can you explain to me the difference between "%" vs. "#" (when "#" isn't flagging a comment)?

Using the file: **test_234.jpg**

what would: ${file**%**[0-9]*} extract? "**4.jpg**" ? Why? Because there are at least 1 numbers on the back (right) end file? But there is also a "test_" and why is the .jpg also extracted?
what would: ${file**%%**[0-9]*} extract? "**234.jpg**" ? Why? Because there are 3 numbers on the back (right) end of file? But there is also a "test_" and why is the .jpg also extracted?

what would: ${file**#**[0-9]*} extract? "**nothing**" ? Why? Because there are no numbers on the front (left) end of "file"?
what would: ${file**##**[0-9]*} extract? "**nothing**" ? Why? Because there are no numbers on the front (left) end of "file"?

also - does [0-9]* mean, in this case, all occurrences of numbers before .jpg?

can you explain what %s%04d does, with particular reference to %s?

Thanks for your guidance - as always!

---

### Post by Vaphell on 2014-03-14
read about bash parameter expansion, these operators and many others will be described.
[http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion](http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion)

in short # trims minimal fragment matching the pattern on the left, % on the right
## and %% are the greedy versions of these concepts (eat as much as possible)

```
$ x=a.b.c.d.e.f
$ echo ${x%.*}/${x%%.*}
a.b.c.d.e/a
$ echo ${x#*.}/${x##*.}
b.c.d.e.f/f

$ f=test_234.jpg
$ echo ${f%[0-9]*}  # non-greedy, matches (last_digit->end)
test_23
$ echo ${f%%[0-9]*} # greedy, matches (first_digit->end)
test_
$ echo ${f#*[0-9]}  # non-greedy, matches (start->first_digit)
34.jpg
$ echo ${f##*[0-9]} # greedy, matches (start->last_digit)
.jpg
```
notice how * changes position depending on the operator for the expression to make sense. Expression used with % is almost always similar to **['border' char][COLOR="#0000FF"]*[/COLOR]** (=find particular char, go to the right), with # almost always **[COLOR="#0000FF"]*[/COLOR]['border' char]** (=find particular char, go to the left)

in the context of file management % is often used to remove extensions (%.*) and ## is often used to remove dirs from full paths to get the filename (##*/)

> what would: ${file#[0-9]*} extract? "nothing" ? Why? Because there are no numbers on the front (left) end of "file"?
what would: ${file##[0-9]*} extract? "nothing" ? Why? Because there are no numbers on the front (left) end of "file"?

If you mean extract = return value, then no, it would be the whole string. The pattern doesn't extract, it deletes. Here without the initial digit on the very left, the expression can't match anything so it does nothing (unchanged value). Even if it matched in case there was a digit, it would remove everything because * would match everything to the right end, returning empty value.
TL;DR: the expression tailored for % used with # doesn't do anything interesting, it can only return all or nothing.

> [0-9]* mean, in this case, all occurrences of numbers before .jpg?
not exactly, this expression works according to the glob rules and * means any sequence of characters. It says find a fragment matching the pattern 'digit+anything'
% requires shortest possible, %% wants the longest one.

> can you explain what %s%04d does, with particular reference to %s?

printf is a classic C function that exists in multiple languages and works pretty much the same in all of them, with minor differences. Once you know it in one language, you know it in all.

%X are placeholders in a formatting string where parameters are plugged in in order, and the actual char defines the type of data.
%s = string
%d = number
%04d is an 'upgrade' of the basic %d that says 0-padded 4-digits wide

```
printf '[COLOR="#0000FF"]%s[/COLOR][COLOR="#006400"]%04d[/COLOR].jpg' [COLOR="#0000FF"]"$prfx"[/COLOR] [COLOR="#006400"]"$i"[/COLOR]
```

---

### Post by maclenin on 2014-08-09
**Vaphell!**

First, a belated thank you for your earlier guidance!

I am revisiting our bashed and loopy discussion and wondering how one would go about renaming ONLY THE NUMBERED files (i.e. if the prefix for the files were different)?

For example, rename only...

```
test_345.jpg
test_123.jpg
test_678.jpg
```

...and NOT:

```
test_red.jpg
test_green.jpg
test_blue.jpg
```

Thanks, again - and for the references!

---

### Post by Vaphell on 2014-08-10
you could narrow down the glob, eg test*[0-9]*.jpg to make sure it includes at least 1 digit

---

### Post by DaveNelson on 2014-08-10
Regarding:
```
Thanks for any guidance - and to any good references re: bash usage
```
I have found the Advanced Bash Scripting Guide at the Linux Documentation Project to be a good reference as well:
[http://www.tldp.org/guides.html#abs](http://www.tldp.org/guides.html#abs)

---

### Post by Vaphell on 2014-08-10
tldp is meh, in their examples there is much garbage like this

```
for file in $( find $directory -type f -name '*' | sort )
```

---

### Post by rhss6-2011 on 2014-08-13
have you tried using a combination of find/grep and sed?

You can use find or grep to find the files you're looking for, then you can use sed to rename them.

I.E.
```

find -iname 'z_*' | while read file;
do
target=`echo "$file" | sed 's/z_//g'`;
echo "Renaming '$file' to '$target'";
mv -f "$file" "$target"
done ;

```

What that does, is it finds ANY file I have that reads z_whateverfileIwant and renames it to whateverfileIwant

---

### Post by maclenin on 2014-09-02
...another log on the fire - thanks all, for your comments.

Relatedly, I would like to preserve this sort order, while renaming (mv) the files... 
```
test_0000.jpg
test_**0000a**.jpg
test_0001.jpg
test_**0001a**.jpg
test_0002.jpg
```
...using a variation of this [COLOR="#FF8C00"]**script**[/COLOR] - if feasible...
```
#!/bin/bash
pfx="test_"
i=0
sfx=".jpg"
**ls | sort -V** | [COLOR="#008000"]**for**[/COLOR] old in *.jpg **<--- this portion (ls | sort -V) of this line seems to sort the filenames in the manner I require, however, I am (seemingly) unable to pipe the sorted output to the [COLOR="#008000"]for[/COLOR] loop...** 
do
printf -v new '%s%04d%s' "$pfx" "$i" "$sfx"
echo mv "$old" "$new"
((i+=1))
done
```
...to yield:
```
mv test_0000.jpg test_0000.jpg
mv test_**0000a**.jpg test_0001.jpg
mv test_0001.jpg test_0002.jpg
mv test_**0001a**.jpg test_0003.jpg
mv test_0002.jpg test_0004.jpg
```
**HOWEVER,** when I run the [COLOR="#FF8C00"]**script**[/COLOR], as shown, the "default" sort order (upon which [COLOR="#008000"]**for**[/COLOR] seems to operate) yields, the following...which I do **NOT** want: 
```
mv test_**0000a**.jpg test_0000.jpg
mv test_0000.jpg test_0001.jpg
mv test_**0001a**.jpg test_0002.jpg
mv test_0001.jpg test_0003.jpg
mv test_0002.jpg test_0004.jpg
```
Thanks, again, for any guidance!

---

### Post by Vaphell on 2014-09-02
using ls for scripting is a big nono, it's only for human eyes and it cannot be depended upon to preserve original names in case they contain some nasty but legit characters like newline.

```

files=()
while IFS= read -rd $'\0' f
do
    files+=( "$f" )
done < <( find -maxdepth 1 -iname '*.jpg' -print0 | sort -zV )

i=0
for old in "${files[@]}"
do
    [[ ${prfx+x} ]] || prfx=${old%%[0-9]*}
    printf -v new '%s%04d.jpg' "$prfx" "$i"
    echo "mv: '$old' => '$new'"
    mv -- "$old" "$new"
    ((i++))
done
```

edit: gotta work on it a bit, because in your example there is a namespace collision between old and new so there is high risk of overwriting files with higher numbers before processing them.

0000->0000
0000a->0001 # this destroys original 0001 before processing it/pushing its index higher.

I think additional step is required, where temporary names with proper indices are given, and then the proper name format is restored.

edit 2: this thing should be good
```
#!/bin/bash

echo "--- temporary filenames ---"
i=0
while IFS= read -rd $'\0' old
do
   [[ ${prfx+x} ]] || prfx=${old%%[0-9]*}
    printf -v tmp '%s%04d.jpg.tmp' "$prfx" "$i"
    echo "mv: '$old' => '$tmp'"
    mv -- "$old" "$tmp"
    ((i++)) 
done < <( find -maxdepth 1 -iname '*.jpg' -print0 | sort -zV )

echo "--- end result ---"
for f in *.jpg.tmp
do
    echo "mv: '$f' => '${f%.tmp}'"
    mv -- "$f" "${f%.tmp}"
done
```

```
$ ./ren_seq.bash 
--- temporary filenames ---
mv: './test_0000.jpg' => './test_0000.jpg.tmp'
mv: './test_0000a.jpg' => './test_0001.jpg.tmp'
mv: './test_0001.jpg' => './test_0002.jpg.tmp'
mv: './test_0001a.jpg' => './test_0003.jpg.tmp'
mv: './test_0002.jpg' => './test_0004.jpg.tmp'
mv: './test_0002a.jpg' => './test_0005.jpg.tmp'
--- end result ---
mv: 'test_0000.jpg.tmp' => 'test_0000.jpg'
mv: 'test_0001.jpg.tmp' => 'test_0001.jpg'
mv: 'test_0002.jpg.tmp' => 'test_0002.jpg'
mv: 'test_0003.jpg.tmp' => 'test_0003.jpg'
mv: 'test_0004.jpg.tmp' => 'test_0004.jpg'
mv: 'test_0005.jpg.tmp' => 'test_0005.jpg'
```

---

### Post by maclenin on 2014-09-06
**Vaphell!**

Thank you! I have a few more (learning-related) questions, which I will post, in due course. In the meantime, I am trying to figure out how to run the script in a "test" / "dry-run" mode?

For example, if I comment out (of the first and second loop)...
```
#mv -- "$old" "$tmp"
```
```
#mv -- "$f" "${f%.tmp}"
```
...and run the modified script, it yields the following...
```
--- temporary filenames ---
mv: './test_0000.txt' => './test_0000.txt.tmp'
mv: './test_0000a.txt' => './test_0001.txt.tmp'
mv: './test_0001.txt' => './test_0002.txt.tmp'
mv: './test_0001a.txt' => './test_0003.txt.tmp'
mv: './test_0002.txt' => './test_0004.txt.tmp'
mv: './test_0002a.txt' => './test_0005.txt.tmp'
[B]--- end result ---
mv: '*.txt.tmp' => '*.txt'[/B]
```
...rather than:
```
--- temporary filenames ---
mv: './test_0000.jpg' => './test_0000.jpg.tmp'
mv: './test_0000a.jpg' => './test_0001.jpg.tmp'
mv: './test_0001.jpg' => './test_0002.jpg.tmp'
mv: './test_0001a.jpg' => './test_0003.jpg.tmp'
mv: './test_0002.jpg' => './test_0004.jpg.tmp'
mv: './test_0002a.jpg' => './test_0005.jpg.tmp'
[B]--- end result ---
mv: 'test_0000.jpg.tmp' => 'test_0000.jpg'
mv: 'test_0001.jpg.tmp' => 'test_0001.jpg'
mv: 'test_0002.jpg.tmp' => 'test_0002.jpg'
mv: 'test_0003.jpg.tmp' => 'test_0003.jpg'
mv: 'test_0004.jpg.tmp' => 'test_0004.jpg'
mv: 'test_0005.jpg.tmp' => 'test_0005.jpg'[/B]
```
My sense is - for "dry-run" purposes - I would need to somehow re-direct or pipe the "echoed" temporary filenames from the first loop to the second - as the second is expecting to find renamed files, which it will not, given **#mv -- "$old" "$tmp"**.

As my "test" script is currently written, the first loop (still) has real files to work with - the second loop finds nothing....

Thanks, as always, for any suggestions!

---

### Post by Vaphell on 2014-09-06
```
#!/bin/bash

[[ $1 == -n ]] && dryrun=true || dryrun=false

old=()
tmp=()
new=()

i=0

while IFS= read -rd $'\0' f
do
    old+=( "$f" )
    [[ ${prfx+x} ]] || prfx=${old%%[0-9]*}
    printf -v t '%s%04d.jpg.tmp' "$prfx" "$i"
    tmp+=( "$t" )
    n=${t%.*}
    new+=( "$n" )
    ((i++)) 
done < <( find -maxdepth 1 -iname '*.jpg' -print0 | sort -zV )

echo "--- step 1 ---"
for(( i=0; i<${#old[@]}; i++ ))
do
    printf -- "%s => %s\n" "${old[i]}" "${tmp[i]}"
    "$dryrun" || mv -- "${old[i]}" "${tmp[i]}"
done

echo "--- step 2 ---"
for(( i=0; i<${#tmp[@]}; i++ ))
do
    printf -- "%s => %s\n" "${tmp[i]}" "${new[i]}"
    "$dryrun" || mv -- "${tmp[i]}" "${new[i]}"
done
```

i used arrays to store names for each step in the workflow (old/tmp/new) which makes mv entirely optional. mv is guarded by $dryrun var, which is dependent on the lame arg support for **-n** param you can see in the first line.

---

### Post by maclenin on 2014-09-07
**Vaphell!**

Thanks, again, for the on-going guidance. I've created a "test" script to help me understand various elements of yours.

In this case, I am looking at evaluations of the **dryrun** variable...
```
#!/bin/bash
set -x
[[ $1 == -n ]] && dryrun=true || dryrun=false
**[COLOR="#008000"]"$dryrun"[/COLOR]** || printf '%s\n' **[COLOR="#008000"]$?[/COLOR]** "dryrun is set to false"
**[COLOR="#008000"]"$dryrun" $?[/COLOR]**
$dryrun $?
```
...with the -n paramater set:
```
$ ./test.sh -n
+ [[ -n == -n ]]
+ dryrun=true
+ **[COLOR="#008000"]true[/COLOR]**
+ **[COLOR="#008000"]true 0[/COLOR]**
+ true 0
```
...with the -n parameter unset:
```
$ ./test.sh
+ [[ '' == -n ]]
+ dryrun=false
+ **[COLOR="#008000"]false[/COLOR]**
+ printf '%s\n' **[COLOR="#008000"]1[/COLOR]** 'dryrun is set to false'
1
dryrun is set to false
+ **[COLOR="#008000"]false 0[/COLOR]**
+ false 1
```

Why, especially with -n unset, the seemingly different evaluation of **"$dryrun"** (as highlighted in **[COLOR="#008000"]green[/COLOR]**)?

Thanks for any clarification!

---

### Post by Vaphell on 2014-09-07
it all makes sense when you know that true and false are ordinary commands, that *true* always succeeds (0) and *false* always fails (1) and that $? is a status of a previous command. A || B is boolean logic that translates here to *run B if A fails.*

```
#!/bin/bash
set -x
[[ $1 == -n ]] && dryrun=true || dryrun=false
[COLOR="#000080"]"$dryrun"[/COLOR] || [COLOR="#006400"]printf[/COLOR] '%s\n' [COLOR="#000080"]$?[/COLOR] "dryrun is set to false"
[COLOR="#B22222"]"$dryrun"[/COLOR] [COLOR="#006400"]$?[/COLOR]
$dryrun [COLOR="#B22222"]$?[/COLOR]
```
colors show the path in the false case. True case is just 3x true in order (printf is not executed)

the condition could be written this way
```
[[ $1 == -n ]] && dryrun=1 || dryrun=0 # using integers
...
(( dryrun )) || mv
(( dryrun == 0 )) && mv
[[ $dryrun -eq 0 ]] && mv
```
or 
```
[[ $1 == -n ]] && dryrun=yes || dryrun=no  # using strings
...
[[ $dryrun == yes ]] || mv
```

---

### Post by maclenin on 2014-09-11
**Vaphell!**

Thanks.

Can one assign $? to explicitly monitor / return the exit status of a specific command / process - other than the way deployed in the sample scripts?
```
#!/bin/bash
set -x
[[ $1 == -n ]] && dryrun=true || dryrun=false
"$dryrun" || printf '%s\n' $? "dryrun is set to false"
"$dryrun" $?
$dryrun $?
```
Also, it seems $? / exit status juggle a dual role?

1. failure / success - "process"
```
$ x
x: command not found
$ echo $?
127 **< --- failure - the process did not complete successfully**
$ 
```
```
$ x=clear
$ "$x"
$ echo $?
0 **< --- success - the process completed successfully**
$ 
```
2. false / true - "boolean(?)"
```
$ x=false
$ "$x"
$ echo $?
1 **< --- false - however, the process also completed successfully - begging an additional "process" exit status 0?**
$
```
```
$ x=true
$ "$x"
$ echo $?
0 **< --- true - however, the process also completed successfully - begging an additional "proccess" exit status 0?**
$
```
Thanks, again, for any comments!

---

### Post by Vaphell on 2014-09-11
you are overthinking it
It doesn't matter if a given command crashes or ends peacefully, what matters is what the exit status is.
0 is success, period. Non-0 is failure, period.
Command can return a bunch of exit codes depending on the type of failure no problem and many commands do that.

example:
```
$ p=
$ bash -c 'echo p: $0; [[ -z $0 ]] && exit 1; [[ $0 =~ ^[0-9]+$ ]] || exit 2; exit 0' "$p"; echo "status: $?"
p:
status: 1
$ p=abc123
$ bash -c 'echo p: $0; [[ -z $0 ]] && exit 1; [[ $0 =~ ^[0-9]+$ ]] || exit 2; exit 0' "$p"; echo "status: $?"
p: abc123
status: 2
$ p=123
$ bash -c 'echo p: $0; [[ -z $0 ]] && exit 1; [[ $0 =~ ^[0-9]+$ ]] || exit 2; exit 0' "$p"; echo "status: $?"
p: 123
status: 0
```

0 => integer is provided
1 => no param/null value
2 => non-integer string

even in your example missing command is 127 but "normal" failure mode of *false* is 1

*true* command is pretty much equivalent to *exit 0* and *false* to *exit 1*

---

### Post by maclenin on 2014-09-14
Thanks, **Vaphell!**

Every answer begs another question - thanks for your thorough explanations...I'll catch up, at some point....

In your example...
```
$ bash -c 'echo p: $0; [[ -z $0 ]] && exit 1; [[ $0 =~ ^[0-9]+$ ]] || exit 2; exit 0' "$p"; echo "status: $?"
```
...you assign exit values 1 and 2 to the conditional statements and 0 to "else". The exit codes you assign are familiar - though, with "reserved" use, it seems...as discussed: success (0), failure - vanilla (1), failure - syntax error (2). Your choice of "reserved" exit values won't cause any mischief? Could you have chosen 10, 11 and 12 (or any other numbers from 0 to 255) as exit values? Is there a published list of (all 255?) bash exit values / meanings? I received a "status: 231", for example, when I tried to assign an "exit 999" to one of the conditionals.

What role does the "$p" play (just after the -c 'string')?

As for my ongoing battle with exit status: commands / expressions experience either success / true (0) or failure / false (1 - 255).... From a debugging standpoint, with p=123 and changing the exit status of your regex conditional to 5...
```
[[ $0 =~ ^[COLOR="#FF0000"][0-9[/COLOR]+$ ]] || exit 5;
```
...if there is a [COLOR="#FF0000"]syntax error[/COLOR] on the left side of the || statement, the statement still completes - and with an ambiguous "status: 5", which tells us nothing about the syntax error while trying to convince us that 123 is a non-integer string? Or, differently, because it's telling us that 123 is a non-integer string we should smell a syntax error?

Thanks, again, for the help!

---

### Post by Vaphell on 2014-09-14
> Every answer **raises **another question

FTFY, begging the question is a logical fallacy based on circular reasoning where unproven assumption is asked to be accepted at face value and the whole argument is built upon it, also confirming the assumption ;-)

> Your choice of "reserved" exit values won't cause any mischief? Could you have chosen 10, 11 and 12 (or any other numbers from 0 to 255) as exit values? Is there a published list of (all 255?) bash exit values / meanings? I received a "status: 231", for example, when I tried to assign an "exit 999" to one of the conditionals.

i can assign whatever i want from the 0-255 range though there is a convention with some values having a clearly defined meaning.

[http://www.tldp.org/LDP/abs/html/exitcodes.html](http://www.tldp.org/LDP/abs/html/exitcodes.html)

Bash won't complain if you use them though, a lot of stuff in cli is based on gentlemen's agreements.
If you write something that is going to be used by others, document the modes of failure your code supports.

> What role does the "$p" play (just after the -c 'string')?

it is simply passed as a param
bash -c '<inlined script>' "param #0" "param #1"
When you use inline "scripts" with -c, params start from $0. In case of fullblown scripts $0 is taken by the program name itself and the user params are from $1 up, but here there is no standalone program, so params are shifted.
I used $p to pass values indirectly to abstract the code away. That allowed me to have exact same line used to showcase all 3 possibilities.


> ```
[[ $0 =~ ^[0-9+$ ]] || exit 5
```

in this case the syntax error itself returns 2 (according to the linked website about exit codes bash uses 2 for syntax error stuff) and if it was the very last thing executed in the script, it would be the status of the whole thing too. *|| exit 5 *overrides it as would any other chained command.
If you had* '<syntax error> || echo'* you'd get 0 out of that because echo is successful. I think the best advice here would be to avoid syntax errors in the first place ;-)

---

