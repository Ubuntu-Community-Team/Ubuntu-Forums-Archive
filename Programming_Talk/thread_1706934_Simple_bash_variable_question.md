---
title: "Simple bash variable question"
date: 2011-03-14
forum: Programming Talk
---

### Post by jmg158 on 2011-03-14
Okay, so essentially, I'm writing a program, and early on, I have letters assigned strings (which are names of .wav's). Then I read in a one character response, and pass that to a function which I would like to play the song that is represented by that letter. Here is roughly what I have right now...

a="sound1.wav"
b="sound2.wav"

read -n 1 in

....

anyway, what should my aplay function look like?
aplay "$in" ----> is wrong because it tells it to play "a" or "b"

aplay $"$in" -----> just looks foolish

This is probably a really foolish situation. I could always set up a switch case, however, I'd like to avoid it if at all possible.

does anyone understand what I'm attempting to ask?

---

### Post by sisco311 on 2011-03-14
In bash >=4 you can use associative arrays:
```

declare -A files
files=( [a]="sound 1.wav"
[b]="sound 2.wav"
[c]="sound 3.wav"
...
)

read -rsn1 in
[ -f "${files[${in}]}" ] && aplay "${files[${in}]}"

```

See:
[http://mywiki.wooledge.org/BashFAQ/006](http://mywiki.wooledge.org/BashFAQ/006)

---

### Post by Arndt on 2011-03-14
> **jmg158 said:**
> Okay, so essentially, I'm writing a program, and early on, I have letters assigned strings (which are names of .wav's). Then I read in a one character response, and pass that to a function which I would like to play the song that is represented by that letter. Here is roughly what I have right now...

a="sound1.wav"
b="sound2.wav"

read -n 1 in

....

anyway, what should my aplay function look like?
aplay "$in" ----> is wrong because it tells it to play "a" or "b"

aplay $"$in" -----> just looks foolish

This is probably a really foolish situation. I could always set up a switch case, however, I'd like to avoid it if at all possible.

does anyone understand what I'm attempting to ask?

Have you looked at 'eval' (a bash builtin)?

How many files do you have? Just a and b, or all the way to z?

---

### Post by jmg158 on 2011-03-14
well, this is ambitious beyond my expertise, but the goal was to make like a simpler sampler type deal. so maybe the top row would be associated with clips (qwerty...). put the whole thing in a while loop... etc. I'll have to look that stuff up. Thanks for the help guys

---

### Post by SeijiSensei on 2011-03-14
Try this:

```

#!/bin/bash
MYSONGS="/home/me/mysongs/"

FILES="file1.wav file2.wav ... fileN.wav"

for f in $FILES
do
   aplay "$MYSONGS$f"
done

exit 0

```

Replace "/home/me/mysongs/" with the full path to the directory in which the .wav files are located  You can type the list of files as a continuous string without any carriage returns, or use the backslash character to denote a continuation like this:

```

FILES="file1.wav file2.wav ... fileN.wav \
fileNN.wav etc."

```

A better approach is to put the filenames in another file (a "playlist" as it were) with each filename on a separate line.  Suppose that list is stored in /home/me/mysongs/playlist.  Then you could use

```

#!/bin/bash
MYSONGS="/home/me/mysongs/"
PLAYLIST="/home/me/mysongs/playlist"

FILES=$(cat $PLAYLIST)

for f in $FILES
do
   aplay "$MYSONGS$f"
done

exit 0

```

The $(cat $PLAYLIST) command uses the "cat" command to list the playlist file and passes the output of the command to the environment variable FILES.  That lets you change the order of songs simply by editing the file.  

"As an exercise," see if you can figure out how to use the "$1" environment variable to let you choose from among a set of playlists with different names.  You could just edit the PLAYLIST variable each time, but you could also pass the name of a playlist file at the command line.  If you stored the code above in an executable file called, say, "playsongs", you might like be able to run "playsongs jazz" or "playsongs inthemood" to select from among your playlists.

---

### Post by jmg158 on 2011-03-14
wow man. 

put me to shame. spent a lot of time thinking about it and you just owned it in about 13 minutes haha. I'm not that clever. I'll try it out and post how it works. thanks!

---

### Post by sisco311 on 2011-03-14
> **SeijiSensei said:**
> Try this:

```

#!/bin/bash
MYSONGS="/home/me/mysongs/"

FILES="file1.wav file2.wav ... fileN.wav"

for f in $FILES
do
   aplay "$MYSONGS$f"
done

exit 0

```



+1 try it with files with (not so) `special characters' in their names. ;)

> **SeijiSensei said:**
> 
A better approach is to put the filenames in another file (a "playlist" as it were) with each filename on a separate line.


Newline is a valid character in a filename. One should use the null character to separate filenames in a `playlist'.

> **SeijiSensei said:**
> 
The $(cat $PLAYLIST) command uses the "cat" command to list the playlist file and passes the output of the command to the environment variable FILES.  That lets you change the order of songs simply by editing the file.  


BASH programmers don't like cat(s). :)

For example, < is faster, see:
```
man bash | less +/" +Command Substitution"
```

Please check out:
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

---

### Post by SeijiSensei on 2011-03-15
> **sisco311 said:**
> BASH programmers don't like cat(s).

I know about redirection, but I reject the ideological stance that one should never use cat.  This is a case where it's appropriate.  How would you propose placing the contents of a file into an environment variable using redirection?  

I've iterated over lists separated by newlines in many scripts, and it works as advertised.  As for newlines in file names, how many files do you have with one in them?  I don't believe I have any in the thousands of files I have scattered across a dozen machines or so.

You want to propose a different solution to the OP?  Then show the code.

---

### Post by sisco311 on 2011-03-15
cat is a very useful command. It can be used for many things, but in this case it's not the right tool for the job. 

Spaces are quiet common in filenames. So if you want to use cat, you have to reset the IFS to a newline:
```

OIFS="$IFS"
IFS=$'\n'
set -f
for file in $(cat list)
do  
  ...
done
IFS="$OIFS"
```

The man page also says that $(cat file) can be replaced by the equivalent but faster $(< file).


The same thing with redirection:
```
while read -r file
do
 ...
done < list

```

Once again, please check out the BashFAQ:
[http://mywiki.wooledge.org/BashFAQ/001](http://mywiki.wooledge.org/BashFAQ/001)

IMO the best solution to the OP's question is an associative array, but bash also allows you to expand a parameter indirectly:
```

a="sound 1.wav"
in="a"

aplay "${!in}"

```

As a last resort one could use **eval**:
```

a="sound 1.wav"
in="a"

eval aplay \"'$'${in}\"

```

From the first link I posted:
> The good news is that if you can sanitize the right hand side correctly, this trick is fully portable, has no variable scope issues, and allows all content including newlines. The bad news is that if you fail to sanitize the right hand side correctly, you have a massive security hole. Use eval at your own risk.

---

