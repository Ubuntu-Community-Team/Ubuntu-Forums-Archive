---
title: "Recursively looks for text files"
date: 2013-09-23
forum: Programming Talk
---

### Post by Langstracht on 2013-09-23
I have been trying to cobble together a script that does the following:

asks me to input 2 separate strings (2 single words if that's the technical limit)

recursively looks for text files (purposely excluding binaries) that contain both the words

displays each file that contains the words consecutively 

and

keeps each file on the screen until I do something (hit "Enter" perhaps or TAB)

I have played around with grep, -egrep, cat etc. and basically gotten nowhere.

Can anyone help?  Please,

Thanks in advance.

---

### Post by steeldriver on 2013-09-23
AFAIK there's no easy way to logically AND matches in grep - you basically need to grep each file that contains pattern1 again to see if it contains pattern2, e.g. something like

```

while read -rd $'\0' file; do grep -qIw 'pattern1' "$file" && grep -qIw 'pattern2' "$file" && echo "$file"; done < <(find . -type f -print0)

```

Note that the bash && logical operator is a 'short-circuit' evaluator i.e. it only executes the second grep if the first one returns true - so it's not as inefficient as all that (and it only echos the filename if both greps return true, which completes the test)

---

### Post by Langstracht on 2013-09-23
Thanks so much for your very complete and very prompt response.

I guess what I wrote may have not been as precise as it should have been,

What I want the script to do is show me (the content of) the file.  The code you have so kindly provided lists the filename(s).

That said, I think it "does the job" but it would be much easier to verify that if I saw the file(s).

And that said, I really wanted an interrogative ... or perhaps you're saying that's not possible.

Finally the complexity of the code fully explains why my pea brain wasn't able to get anywhere.

Thanks again.

---

### Post by steeldriver on 2013-09-23
You can replace the echo "$file" command with any other command you want to perform on the matching "$file" e.g. to cat the contents

```

while read -rd $'\0' file; do grep -qIw 'pattern1' "$file"  && grep -qIw 'pattern2' "$file" && [COLOR=#0000ff]**cat  "$file"**[/COLOR]; done < <(find . -type f -print0)

```

or to echo the name and then cat the contents - note the use of a subshell ( ... ) 

```

while read -rd $'\0' file; do grep -qIw 'pattern1' "$file" && grep -qIw 'pattern2' "$file" && [COLOR=#0000ff]**(echo "$file: "; cat "$file")**[/COLOR]; done < <(find . -type f -print0)

```

If your pattern1 and pattern2 are variables you will need to use double quotes not single quotes, like "$pattern1", "$pattern2" for example

```

read -p "Please enter the first pattern: " pattern1

read -p "Please enter the second pattern: " pattern2

while read -rd $'\0' file; do 
    grep -qIw "$pattern1" "$file" && grep -qIw "$pattern2" "$file" && (echo "$file: "; cat "$file")
done < <(find . -type f -print0)

```

---

### Post by Vaphell on 2013-09-23
you can skip the *find* part entirely as *grep* is able to perform recursive searches and generate list files
```
while read -rd $'\0' file
do
  grep -qIw "$pattern2" "$file" && (echo "$file: "; cat "$file")
done < <( grep -ZlrIw "$pattern1" . )
```

---

### Post by Langstracht on 2013-09-23
steeldriver - I have tried all 3 of  your suggestions and I think they ALL display all the files that they are supposed to.

Thank you so VERY much. 

Why do I "think" they do?  Well, because there is no pause/freeze between files - just one continuous outpouring.

Is this fixable do you think?

---

### Post by Vaphell on 2013-09-23
few changes:
```
while read -r [COLOR="#0000FF"]-u 3[/COLOR] -d $'\0' file
do
  ...
  read -p "Press Enter to continue..."
done [COLOR="#0000FF"]3[/COLOR]< <( ... ) 
```

---

### Post by Langstracht on 2013-09-23
Vaphell - I tried your code.

Dunno why but I get the following error:

```
emailfind2.sh: 6: Syntax error: redirection unexpected
```

---

### Post by Vaphell on 2013-09-23
```
$ echo $pattern1 $pattern2
echo bash
$ while read -r -u 3 -d $'\0' file; do   echo "=== $file ========================" && grep -P "$pattern1|$pattern2|$" "$file"; read -p "Press Enter to continue..."; done 3< <( grep -ZlrIw "$pattern1" . 2>/dev/null | xargs -0 grep -Zlw "$pattern2" )
=== ./syntax.sh ========================
#!/bin/[COLOR="#FF0000"]bash[/COLOR]

if [ -f file ]
then
  [COLOR="#FF0000"]echo[/COLOR] line1
  [COLOR="#FF0000"]echo[/COLOR] line2
else
  [COLOR="#FF0000"]echo[/COLOR] line3
fi
Press Enter to continue...
```
grep -P inside the loop is only used to colorize the output

---

### Post by Langstracht on 2013-09-23
Well I still don't know why I got that error.  But I DO know how to get rid of it.

I did some playing around and found that using

```
bash emailfind2.sh
```
works just fine.  It seems to me I've been "caught" with that before.  Sorry about that.

Just missing that elusive "in between" pause and we're good to go.

---

### Post by Vaphell on 2013-09-23
probably your script was run with sh not bash
set up the hashbang line (#!/bin/bash), chmod +x your script and use it like this
```
./script # this uses the interpreter shown in the hashbang line
```
not like this
```
<shell_name> script # this overrides the hashbang line
```

and no, we are not missing anything :) The pause is already there, in versions of code with **read -u 3** and **done 3< <( ... )**. Just look at the output of my version of code from post #9, there is a 'Press enter' message at the end of file and it waits for enter before moving to the next file.
it's pretty version goes like this
```
while read -r -u 3 -d $'\0' file
do
  echo "=== $file ========================"
  grep -P "$pattern1|$pattern2|$" "$file"
  read -p "Press Enter to continue..."
done 3< <( grep -ZlrIw "$pattern1" . 2>/dev/null | xargs -0 grep -Zlw "$pattern2" )
```

---

### Post by 1clue on 2013-09-23
I use something similar to this for a single string, you could easily change it by adding another xargs grep on.

> #!/bin/bash
$EDITOR `find . -name '*.txt' -print | sort | xargs grep -l "$1" | xargs grep -l  "$2"`

This edits all files that contain the two text strings, all entered on the command line.

Based on your assignment, you could change it to find the two strings immediately adjacent to each other or possibly separated by some amount of whitespace.

If you just want to list the files that match, remove the $EDITOR `` wrapper.

---

### Post by Vaphell on 2013-09-24
this code will fail spectacularly on whitespaced paths/filenames, *xargs -d $'\n'* is required as a bare minimum (though the only rock solid way to handle filenames is null as delimiter)


just for kicks general solution working with any number of parameters
```
#!/bin/bash

results=( . )

for w in "$@"
do
  i=0
  while read -rd $'\0' r
  do
    (( i++ )) || results=()
    results+=( "$r" )
  done < <( grep -rIiwlZ "$w" "${results[@]}" 2>/dev/null )
done

for f in "${results[@]}"
do
  printf "\n___ %s ______________________________________\n" "$f"
  grep -Pwi --color=always "$( printf "%s|" "$@" )$" "$f"
  read -p "Press Enter to continue..."
done
```

words are iterated over in a loop. Each iteration works with a fileset returned by the previous iteration to minimize grind. What's left in the array after the loop finishes is the final set of results, the only thing left to do is printing them.

```
$ ./grep_words.sh bin bash echo if

___ ./syntax.sh ______________________________________
#!/[COLOR="#FF0000"]**bin**[/COLOR]/[COLOR="#FF0000"]**bash**[/COLOR]

[COLOR="#FF0000"]**if**[/COLOR] [ -f file ]
then
  [COLOR="#FF0000"]**echo**[/COLOR] line1
  [COLOR="#FF0000"]**echo**[/COLOR] line2
else
  [COLOR="#FF0000"]**echo**[/COLOR] line3
fi
Press Enter to continue...
```

---

### Post by ofnuts on 2013-09-24
For the sake of completeness, the various filters in 'find' are and'ed by default, so you can use several '-exec grep' filters:
```

find -type f -name '*.txt' -exec grep - q pattern1 {} \;  -exec grep -q pattern2 {} \;  -print

```
And of course since these are and'ed, the second grep only runs if the first one is successful.

---

### Post by Langstracht on 2013-09-24
If only for my one benefit I thought it might be useful to list some of the suggestions for dealing with this matter and the results I got.



```

while read -rd $'\0' file; do grep -qIw 'pattern1' "$file" && grep -qIw 'pattern2' "$file" && echo "$file"; done < <(find . -type f -print0)

```

works ... but only outputs filenames


```

while read -rd $'\0' file; do grep -qIw 'pattern1' "$file"  && grep -qIw 'pattern2' "$file" && cat  "$file"; done < <(find . -type f -print0)

```

does not work returns error bash: syntax error near unexpected token `do'


```

while read -rd $'\0' file; do grep -qIw 'pattern1' "$file" && grep -qIw 'pattern2' "$file" && (echo "$file: "; cat "$file"); done < <(find . -type f -print0)

```

works - outputs both filename AND contents ... does not pause between files


```

read -p "Please enter the first pattern: " pattern1

read -p "Please enter the second pattern: " pattern2

while read -rd $'\0' file; do 
    grep -qIw "$pattern1" "$file" && grep -qIw "$pattern2" "$file" && (echo "$file: "; cat "$file")
done < <(find . -type f -print0)

```

works - outputs filename AND content ... does NOT pause between files


```

while read -rd $'\0' file
do
  grep -qIw "$pattern2" "$file" && (echo "$file: "; cat "$file")
done < <( grep -ZlrIw "$pattern1" . )

```

outputs the filename followed by the content - does NOT pause, displays content of .sh file at beginning of output


```

while read -r -u 3 -d $'\0' file
do
  ...
  read -p "Press Enter to continue..."
done 3< <( ... )

```

which I interpreted, perhaps wrongly, as 

```

while read -r -u 3 -d $'\0' file
do
  grep -qIw "$pattern2" "$file" && (echo "$file: "; cat "$file")
  read -p "Press Enter to continue..."
done 3< <( grep -ZlrIw "$pattern1" . )

```

endlessly prints the contents of the .sh file, pausing after each


```

while read -r -u 3 -d $'\0' file; do   echo "=== $file ========================" && grep -P "$pattern1|$pattern2|$" "$file"; read -p "Press Enter to continue..."; done 3<
[/CODE}

does not work - returns error bash: syntax error near unexpected token `newline'


[CODE]
while read -r -u 3 -d $'\0' file
do
  echo "=== $file ========================"
  grep -P "$pattern1|$pattern2|$" "$file"
  read -p "Press Enter to continue..."
done 3< <( grep -ZlrIw "$pattern1" . 2>/dev/null | xargs -0 grep -Zlw "$pattern2" )

```

shows content of .sh file, does pause, shows correct file names and contents ... then goes on to show the filenames and contents for all the other files ...


14
```

find -type f -name '*.txt' -exec grep - q pattern1 {} \;  -exec grep -q pattern2 {} \;  -print

```

does not produce any screen output

So, sorry to say while 

```

read -p "Please enter the first pattern: " pattern1

read -p "Please enter the second pattern: " pattern2

while read -rd $'\0' file; do 
    grep -qIw "$pattern1" "$file" && grep -qIw "$pattern2" "$file" && (echo "$file: "; cat "$file")
done < <(find . -type f -print0)

```

is the best fit to what I was looking for, it doesn't pause between files.

---

### Post by steeldriver on 2013-09-24
combined soultion

```

#!/bin/bash

read -p "Please enter the first pattern: " pattern1
read -p "Please enter the second pattern: " pattern2

while read -rd $'\0' [COLOR=#0000ff]**-u3**[/COLOR] file; do 
  grep -qIw "$pattern1" "$file" && grep -qIw "$pattern2" "$file" \
  && (echo "$file: "; cat "$file"; [COLOR=#0000ff]**read -p "Press Enter to continue..."**[/COLOR])
done [COLOR=#0000ff]**3<**[/COLOR] <(find . -type f -print0)

```

or

```

#!/bin/bash

read -p "Please enter the first pattern: " pattern1
read -p "Please enter the second pattern: " pattern2

while read -rd $'\0' [COLOR=#0000ff]**-u3**[/COLOR] file; do 
  grep -qIw "$pattern1" "$file" && grep -qIw "$pattern2" "$file" \
  && (echo "$file: "; [COLOR=#00ff00]**grep -w "$pattern1\|pattern2" "$file"**[/COLOR]; [COLOR=#0000ff]**read -p "Press Enter to continue..."**[/COLOR])
done [COLOR=#0000ff]**3<**[/COLOR] <(find . -type f -print0)

```

FWIW I checked the one you says has a syntax error near unexpected token 'do' - it looks OK to me, perhaps you executed it in a non-bash shell?

---

### Post by Langstracht on 2013-09-24
I am happy, delighted actually, to be able to tell that your latest codes works PERFECTLY.  Thank you SO much.

As for your comment on the non-operational/'do' error.  I know what you mean.  But really I don't.  I ran the code on the command line ... and I have no idea what the O/S did with it ... or what I might/could do to change.

In any event since, thanks to  your code my problem is solved, it's a bit academic.

Thanks again SO MUCH.

---

### Post by Vaphell on 2013-09-24
> does not work - returns error bash: syntax error near unexpected token `newline'

obviously it's ended prematurely there should be more stuff after 3


> shows content of .sh file, does pause, shows correct file names and contents ... then goes on to show the filenames and contents for all the other files ...

care to elaborate what happens exactly? I am not getting any other files, only the ones that have all the required words and there is nothing more.

---

### Post by steeldriver on 2013-09-24
If you are making an effort to learn this stuff, then you should try to understand all the other good suggestions from Vaphell et al. - here's a version using ofnuts' suggestion (which I like) but adding the printout / pause

```

#!/bin/bash

read -p "Please enter the first pattern: " pattern1
read -p "Please enter the second pattern: " pattern2

find . -exec grep -qIw "$pattern1" {} \; -exec grep -qIw "$pattern2" {} \; -exec bash -c \
    'echo "$0"; grep -w "$1\|$2" "$0"; read -p "Press ENTER to continue..." ' {} "$pattern1" "$pattern2" \;

```

---

### Post by ofnuts on 2013-09-24
> **Langstracht said:**
> 
```

find -type f -name '*.txt' -exec grep - q pattern1 {} \;  -exec grep -q pattern2 {} \;  -print

```

does not produce any screen output

.
Of course because it's merely  expounding a possible technique, so as  written here it searches for the strings "pattern1" and "pattern2". Adapting  this to a real-life script is "left as an exercise to the reader" (a trivial one at that)..

---

### Post by Langstracht on 2013-09-26
Vaphell, given your comment that it "works" for you, I tried it again.  And this time it did work.  Guess I must have gotten screwed up in the sh/bash thing again the first time.  ??  Sorry about that.

I was not aware that some folks intentionally post code that doesn't work and then express gleeful disdain when that is reported back.  Bit of an eye opener that.

I'll try to avoid responding to such posts in future.

That said, thanks to almost all for your prompt and helpful responses.

---

### Post by ofnuts on 2013-09-26
> 
I was not aware that some folks intentionally post code that doesn't work


If anyone here does that, s/he should be reported to the mods, and hopefully banned.

---

### Post by Vaphell on 2013-09-26
i think OP might be talking about your rough hint about *find -exec -exec*, insightful nonetheless, and the remark of "left as an exercise to the reader" :-)

---

### Post by ofnuts on 2013-09-26
That can't be, I did not post code, but coding suggestions... 

Putting a warning in my sig to avoid future misunderstandings..

---

### Post by 1clue on 2013-09-27
FWIW this whole thread as originally posted sounded like a class assignment.  I never post working, finished-for-the-purpose code in those cases.  It's called cheating, and it can get you kicked out of pretty much any university.

What I posted started as working-for-another-purpose code that I actually use, with a modification to illustrate the two inputs.

I seriously doubt you could get banned over not participating in cheating.

---

