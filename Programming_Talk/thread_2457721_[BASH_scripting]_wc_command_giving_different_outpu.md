---
title: "[BASH scripting] wc command giving different output when executed by script"
date: 2021-02-07
forum: Programming Talk
---

### Post by pupscout on 2021-02-07
Hi there, I'm brand new to Linux programming and I'm attempting to build a Bash shell script which will let me specify a directory containing an album of lossless WAV files, and use ffmpeg to compress and convert each file in the directory into an MP3. My overall plan is to build a for loop to iterate over each file and run ffmpeg on it. But before I climb that hill, I need to count how many files are in a given directory. I ran my first "hello world" script today, then I figured out how to accept a positional parameter and echo that. It's the next step that I'm getting tripped up on: actually doing something useful with that parameter.

I'm familiar enough with the ls and wc commands to understand that I can pipe the output of ls to wc, and use the -l to count the newline characters and thereby count how many files are in a directory. I've put together this command, outside the context of my script, to make sure I'm using the right syntax:
```
ls ~/Desktop/1 | wc -l
```

Cool. Now I try to put the pieces together, and run the wc command from my script:

```

#!/bin/bash
numFiles=ls -l $1 | wc -l
echo "Hi! I found $numFiles files there."

```

Using the ~/Desktop/1 directory as an example, when I run the wc command above directly from the command line, the output is:
**12**
and this is correct.

However, when I run the script above, the output is:
[B]/home/scout/audio_convert.sh: line 8: -l: command not found
0
Hi! I found some  files there.[/B]

The manpage for wc makes me think I'm not missing anything about how to use the command, so I'm probably missing something about how to dynamically compose a command within a script, using a positional parameter. I've read some beginner's tutorials about bash scripting, but I haven't found anything that's quite clicked, that seems to cover what I'm trying to accomplish. I also ran this my a sysdamin friend of mine who lives and breaths the Linux terminal and he didn't see anything obvious that I was doing wrong.

Can someone help me understand why the output from my wc command is different when I run it from my script?

---

### Post by TheFu on 2021-02-07
tl;dr sorry.


$ more  2mp3-default
```
#!/bin/bash

for filename in "$@"; do
   NEW="${filename%.*}".mp3
   nice ffmpeg -i "$filename"   "$NEW"
done
```

Don't make it too hard.  Filenames cannot have spaces in the names. A space is a delimiter.

Run by passing in a list of input globbed filenames. For example:
```
$ 2mp3-default   *wav
```
or
```
$ 2mp3-default   song*
```

Never use 'ls' to generate inputs for scripts. Many reasons.
Google "advanced bash scripting guide" for help with aspects of bash scripting. I suspect the $1 handling is incorrect.

---

### Post by spjackson on 2021-02-08
TheFu's sensible and extensive advice notwithstanding, the reason your script is failing is because
> 
```
numFiles=ls -l $1 | wc -l
```

doesn't do what you think it does. It assigns ls to the variable numFiles then tries to execute
```
-l $1 | wc -l
```
In order to run the full command and get the output assigned to numFiles, what you need is:
```
numFiles=$(ls -l "$1" | wc -l)
```

---

### Post by pupscout on 2021-02-13
Sweet, thank you both for your help! I now see that the way I wanted to build the script, while theoretically feasible, was probably far too advanced for my first script. I understand a bit better now how to handle commands that include spaces, and that's super cool that you can loop through all the positional params without needing to know how many there are.

I extended the script above to create a new folder for the MP3s, and move each file into the folder after it's created. I made sure to test this script in a folder that includes copies of my WAVs, just in case...

```
#!/bin/bash

mkdir -p ./MP3
chmod 777 ./MP3
for filename in "$@"; do
   NEW="${filename%.*}".mp3
   nice ffmpeg -i "$filename" "$NEW"
   mv "$NEW" ./MP3
done
```

Pretty sure we can close this thread.

---

### Post by TheFu on 2021-02-13
Maybe it is just me, but I like to clearly denote directories. It would really suck if you moved every newly made file into a single file named "MP3", right? Adding the trailing / to the target directory completely changes the likelihood of that error.  May want to **mkdir -p** on the target, just be be certain. Also, check the return code from that mkdir to ensure it worked.  Or ... 

Also, whenever paths are going to be hardcoded, I'd set a variable at the top of the script and try to ensure the fill path is used, not a relative path.  Just safer that way.

```

if [ -d "$TARGET" ] ; then
   echo "WARNING: Target directory doesn't exist: $TARGET 
   Trying to create it."
   mkdir -p "$TARGET"
fi 
   mv "$NEW"  "$TARGET/"

```

```
for filename in "$@"; do
   # do something pattern is great.
done
```

We can pass in a list of files generated using other commands, like 'find'.
If you really want bulletproof scripts, always specify the full path to all commands, all directories, and don't assume any environment variables set by a session exist.  For example, $HOME may not be set when running from cron.
mv should be /usr/bin/mv
mkdir should be /usr/bin/mkdir
ffmpeg should be /usr/bin/ffmpeg ... or point to a different version if you need. Sometimes a project will need new features that aren't in the repo version.

Only you can mark a thread **SOLVED**.  Use the _Thread Tools button_ near the top. This really helps the community.

---

### Post by TheFu on 2021-02-13
And chmod 777 is for lazy people.  Don't do that.   E-V-E-R!

---

