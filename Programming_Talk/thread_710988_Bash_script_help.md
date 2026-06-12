---
title: "Bash script help"
date: 2008-02-29
forum: Programming Talk
---

### Post by schickb on 2008-02-29
My goal is to delete all files in a directory based on two customizable lists. The first list is a space separated list of file-expressions to delete. The second is a space separated list of file-expressions to exclude from the delete list (it overrides the first list).

My attempt is below. I think the problem is the way I insert $nukenames and $excnames into the find statement. But if I just copy and paste the echoed find statement directly at the bash prompt it works.

```
#!/bin/bash

touch ./xyz
touch ./abc1
touch ./abc2
touch ./abc3
touch ./lmn

#First list: stuff to delete
nuke="ab* lmn"

#Second list: exclude from deletion
exc="abc2"

nukenames="-name '$(echo "$nuke" | sed "s/[ \t]\+/' -o -name '/g")'"
echo $nukenames

excnames="-name '$(echo "$exc" | sed "s/[ \t]\+/' -o -name '/g")'"
echo $excnames

#Simple test is failing (add -print0 later)
echo "find . -type f -maxdepth 1 \( $nukenames \) | xargs echo"
find . -type f -maxdepth 1 \( $nukenames \) | xargs echo

#Ultimate goal, also failing
echo "find . -type f -maxdepth 1 \( $nukenames \) -a -not \( $excnames \) | xargs echo"
find . -type f -maxdepth 1 \( $nukenames \) -a -not \( $excnames \) | xargs echo
```

If there is a better way, please let me know. But I'd still like to know why this doesn't work for my own knowledge.

---

### Post by Mr. C. on 2008-02-29
I get a find warning:

```
-name 'ab*' -o -name 'lmn'
-name 'abc2'
find . -type f -maxdepth 1 \( -name 'ab*' -o -name 'lmn' \) | xargs echo
find: warning: you have specified the -maxdepth option after a non-option argument -type, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

...
```

Try this variation instead, which fixes the error, and uses set -x to show you what the shell sees.  Run it, and carefully examine nukenames and excnames inside the finds.  This should push you along:

```
#!/bin/bash

touch ./xyz
touch ./abc1
touch ./abc2
touch ./abc3
touch ./lmn

#First list: stuff to delete
nuke="ab* lmn"

#Second list: exclude from deletion
exc="abc2"

set -x
nukenames="-name '$(echo "$nuke" | sed "s/[ \t]\+/' -o -name '/g")'"
excnames="-name '$(echo "$exc" | sed "s/[ \t]\+/' -o -name '/g")'"

#Simple test is failing (add -print0 later)
find . -maxdepth 1 -type f \( $nukenames \) | xargs echo

#Ultimate goal, also failing
find . -maxdepth 1 -type f \( $nukenames \) -a -not \( $excnames \) | xargs echo
```

MrC

---

### Post by ghostdog74 on 2008-02-29
> **schickb said:**
> 
#First list: stuff to delete
nuke="ab* lmn"

if you do a declaration like this, the variable "nuke" will expand to these values "abc1 abc2 abc3 lmn"
```

# ls
abc1  abc2  abc3 lmn  xyz
# nuke="ab* lmn"
# echo $nuke
abc1 abc2 abc3 lmn   

```

if you are only doing it at one directory level, 
```

nuke="ab* lmn"
for i in $nuke
do  
 case $i in 
   *abc2* ) continue ;;
   * ) rm $i ;;  
 esac
done

```

---

### Post by schickb on 2008-02-29
> **Mr. C. said:**
> and uses set -x to show you what the shell sees.  Run it, and carefully examine nukenames and excnames inside the finds.  This should push you along:
Thanks for the tip. I see that the quotes inside the find are escaped and end up like this:

```
find . -maxdepth 1 -type f '(' -name ''\''ab*'\''' -o -name ''\''lmn'\''' ')'
```

Why so many extra quotes? I'll keep digging, but I'm still not sure what is going on or how to prevent it.

---

### Post by Mr. C. on 2008-02-29
You should then have also seen that the extra quotes are added at your nukenames and excnames assignments, well before they are interpolated into the find command line.

Why are they there - you added them!

See Chapter 3, Quoting in Detail: [http://cis68b1.mikecappella.com/](http://cis68b1.mikecappella.com/)

MrC

---

### Post by schickb on 2008-02-29
> **Mr. C. said:**
> You should then have also seen that the extra quotes are added at your nukenames and excnames assignments, well before they are interpolated into the find command line.
Actually I don't see that. The creation and echoing of excnames, for example, looks like this:

+ excnames=-name 'abc2'
+ echo -name ''\''abc2'\'''

Just by looking at that, I can't really tell if the extra quotes are added when the variable is create or when it is used. Either way, the result seems equivalent.

> Why are they there - you added them!
In the code above, I added one level of single quotes around *abc2*. I can see that the shell escapes those so that the single quotes print. Then I'd assume it adds additional layers of quotes to prevent expansion? First the shell quotes each escaped quote, then quotes the entire thing? But if that is what is happening it seems strange since single quotes aren't allowed within single quotes (even escaped ones). Its also odd that the end result is leading and trailing no-op double single quotes.

> See Chapter 3, Quoting in Detail: [http://cis68b1.mikecappella.com/](http://cis68b1.mikecappella.com/)Unless I'm missing something, the notes didn't really help me figure out how to prevent/fix all this. Maybe I'll just give up on using nested quotes and go with **set -f** to prevent the globbing inside the finds.

---

### Post by Mr. C. on 2008-02-29
Don't get frustrated - quoting is one of the most challenging problems in shell programming.

Here's my modified version of the program.  See the output below. Its important to learn how bash outputs what it sees with -x before the results become meaningful.

```
$ cat doit.sh
#!/bin/bash

touch ./xyz
touch ./abc1
touch ./abc2
touch ./abc3
touch ./lmn

set -x
#First list: stuff to delete
nuke='ab\* lmn'

#Second list: exclude from deletion
exc="abc2"

nukenames="-name $(echo "$nuke" | sed 's/[ \t]\+/ -o -name /g')"
excnames="-name $(echo "$exc" | sed 's/[ \t]\+/ -o -name /g')"

#Simple test is failing (add -print0 later)
find . -maxdepth 1 -type f \( $nukenames \) | xargs echo

#Ultimate goal, also failing
find . -maxdepth 1 -type f \( $nukenames \) -a -not \( $excnames \) | xargs echo
```

Note below that bash does not add extraneous quotes around its set -x debugging output.  It is exactly as we specified it:
```

$ ls
abc1  abc2  abc3  doit.sh  lmn  xyz

$ bash doit.sh   
+ nuke='ab\* lmn'
+ exc=abc2
++ echo 'ab\* lmn'
++ sed 's/[ \t]\+/ -o -name /g'
+ nukenames='-name ab\* -o -name lmn'
++ echo abc2
++ sed 's/[ \t]\+/ -o -name /g'
+ excnames='-name abc2'
+ find . -maxdepth 1 -type f '(' -name 'ab\*' -o -name lmn ')'
+ xargs echo
./lmn
+ find . -maxdepth 1 -type f '(' -name 'ab\*' -o -name lmn ')' -a -not '(' -name abc2 ')'
+ xargs echo
./lmn
```

---

### Post by schickb on 2008-03-01
> **Mr. C. said:**
> Don't get frustrated - quoting is one of the most challenging problems in shell programming. I've noticed :) Thanks for the continued feedback.

> Here's my modified version of the program.  See the output below.Unfortunately, your version doesn't work correctly. The result of the last find should be:

abc1 abc3 lmn

Find is not matching the *ab** files because it is receiving *ab\** instead of *ab**. Notice in the find statement how just the *ab\** substring of nukenames is getting quoted. It looks like parts of the string that have meta-characters are single quoted (this happened in my original code also). I'd like to know exactly what's going on there. 

Another way to ask the question: Is it possible to get a shell globbing meta-character into a variable and then back out into another shell statement without globbing or extra quoting occurring? Maybe **set -f** is the only way?

Also this script will be used by others, and I don't want everyone who edit those lists locally to have to think about escaping.

Here is a solution using set -f
```
#!/bin/bash

touch ./xyz
touch ./abc1
touch ./abc2
touch ./abc3
touch ./lmn

#First list: stuff to delete
nuke="ab* lmn"

#Second list: exclude from deletion
exc="abc2"

nukenames="-name $(echo "$nuke" | sed "s/[ \t]\+/ -o -name /g")"
excnames="-name $(echo "$exc" | sed "s/[ \t]\+/ -o -name /g")"

set -f
#Simple test
find . -maxdepth 1 -type f \( $nukenames \) | xargs echo

#Ultimate goal
find . -maxdepth 1 -type f \( $nukenames \) -a -not \( $excnames \) | xargs echo
```

---

### Post by Mr. C. on 2008-03-01
Oops, I'd only tested with two files - very bad of me.

Absolutely use noglob if that's to your advantage.

I hadn't noticed I had double quotes inside double quotes (which doesn't work, as the second quote immediately disables quoting).  Se the nukenames and excnames assignments.  Here's my version:

```
#!/bin/bash

touch ./xyz
touch ./abc1
touch ./abc2
touch ./abc3
touch ./lmn

set -x
set -f
#First list: stuff to delete
nuke='ab* lmn'

#Second list: exclude from deletion
exc="abc2"

nukenames="-name $(echo $nuke | sed 's/[ \t]\+/ -o -name /g')"
excnames="-name $(echo $exc | sed 's/[ \t]\+/ -o -name /g')"


#Simple test is failing (add -print0 later)
find . -maxdepth 1 -type f \( $nukenames \) | xargs echo

#Ultimate goal, also failing

$ bash doit.sh
+ set -f
+ nuke='ab* lmn'
+ exc=abc2
++ echo 'ab*' lmn
++ sed 's/[ \t]\+/ -o -name /g'
+ nukenames='-name ab* -o -name lmn'
++ echo abc2
++ sed 's/[ \t]\+/ -o -name /g'
+ excnames='-name abc2'
+ find . -maxdepth 1 -type f '(' -name 'ab*' -o -name lmn ')'
+ xargs echo
./abc1 ./abc2 ./abc3 ./lmn
+ find . -maxdepth 1 -type f '(' -name 'ab*' -o -name lmn ')' -a -not '(' -name abc2 ')'
+ xargs echo
./abc1 ./abc3 ./lmn
```

> 
Also this script will be used by others, and I don't want everyone who edit those lists locally to have to think about escaping.

Well, if that's the goal, this may need some more thought.  What will you do if someone edits in a nuke pattern of "-o" or ";" or any other find predicate?  Like quoting in the shell, parameter passing from user input or unfamiliar programmers will invite trouble without you ensuring anything entered is handled.

---

### Post by Mr. C. on 2008-03-01
The first time I looked at this problem, I knew there was a better way.  I was distracted elsewhere, and then came back and just responded to questions without recalling what I'd thought earlier.

There's a better way to do this problem!  And that is to use existing tools for their purposes rather than try to create a language on the fly (w/the find predicates).  Consider instead an approach that uses find and egrep as they are intended to be used.  This allows your users to create egrep patterns and expect egrep patterns to work:

```
set -x
# filename patterns (egrep style) of files to include as deletion candiates
includepats='ab|lmn'

# filename patterns (egrep style) that will be excluded from deletion
excludepats="abc2"

find . -maxdepth 1 -type f -print \
        | egrep     "$includepats" \
        | egrep -v "$excludepats"


 bash doit.sh
+ includepats='ab|lmn'
+ excludepats=abc2
+ find . -maxdepth 1 -type f -print
+ egrep 'ab|lmn'
+ egrep -v abc2
./abc1
./abc3
./lmn
```

---

### Post by ghostdog74 on 2008-03-01
with GNU find only
```

# ls
abc1  abc2  abc3  lmn  xyz
# find . -regextype egrep -regex ".*abc.|.*lmn" -not -regex ".*abc2|.*abc1"
./abc3
./lmn

```

---

### Post by Mr. C. on 2008-03-01
Nice call. I've spent +27 years with *nix systems, and I'm still learning from smart people like ghostdog74. 

Now using *BSD for my main systems, I miss some of the crazy GNU options.

---

### Post by schickb on 2008-03-01
> **ghostdog74 said:**
> with GNU find only
```

# ls
abc1  abc2  abc3  lmn  xyz
# find . -regextype egrep -regex ".*abc.|.*lmn" -not -regex ".*abc2|.*abc1"
./abc3
./lmn

```
Yes I did have that at one point, but switched to using -name because the regular expressions are non-intuitive for people who haven't read the find man pages. 

From the man pages: *"-regex  File name matches regular expression pattern.  This is a match on the whole path,  not a  search.   For  example,  to  match a file named `./fubar3', you can use the regular expression `.*bar.' or `.*b.*3', but not `b.*r3'."*

A related issue applies to the previously suggested egrep solution: It will match against any part of the path output by find. I can make sure I always CD into the target directory before running the search to solve that however.

I'll have to ask a few people if they'd rather enter regular expressions or file glob patterns.

Thanks again everyone for the feedback.

---

### Post by Mr. C. on 2008-03-01
Right - I was aware of the anywhere-in-path issues, but since you had maxdepth 1, that wouldn't have been an issue for this problem.  That's easily fixable with a simple RE.

The nice thing about using REs is that they are well documented, and don't preclude full path names.  How otherwise would you allow your program to delete foo/abc.txt but not goo/abc.txt ?

You *really* do want to avoid trying to build a find expression like you were.  Use common, simple tools, that you can easily control and modify, and won't cause odd and unexpected results.

Best of luck!

---

### Post by lkrubner on 2010-12-06
I am new to bash programming. I am having trouble understanding the syntax. Could someone please explain this code?

> **Mr. C. said:**
> 
```

 bash doit.sh
+ includepats='ab|lmn'
+ excludepats=abc2
+ find . -maxdepth 1 -type f -print
+ egrep 'ab|lmn'
+ egrep -v abc2
./abc1
./abc3
./lmn
```

What do the plus signs mean?

---

