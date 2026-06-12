---
title: "pipes-bash and output handling"
date: 2008-09-10
forum: Programming Talk
---

### Post by sag47 on 2008-09-10
Hello all,
I'm currently writing automated bash scripts for a linux box and wish to handle the output from the pipes...

To further explain what I'm trying to accomplish here is an example:

```
# cd ~
# ls -a | grep '^.m'
.macromedia/
.madedit/
.maltego/
.mcop/
.mcoprc/
.mozilla/
.msf3/
# 
```

I want to handle each directory above as an input for another set of commands as it goes down the hierarchy of all the folders that start with ".m".  This process needs to be automated since the amount and names of ".m" folders changes and increases as more are created.

So basically the solution I need is to echo text and folder into a file.

I'm basically want the automation to look like this:
```
# echo "#! /bin/bash" >> myfile.sh
# echo "sh .macromedia/configure.sh" >> myfile.sh
# echo "sh .madedit/configure.sh" >> myfile.sh
# echo "sh .maltego/configure.sh" >> myfile.sh
# echo "sh .mcop/configure.sh" >> myfile.sh
# echo "sh .mcoprc/configure.sh" >> myfile.sh
# echo "sh .mozilla/configure.sh" >> myfile.sh
# echo "sh .msf3/configure.sh" >> myfile.sh
```
That way I can call myfile.sh and have it run in sequence.  Later I'll need it to run multiple commands on each of those directories but I want to keep it simple and take it one step at a time.

I've already tried stuff like
ls -a | grep '^.m' | echo "sh " >> myfile.sh
echo "sh `ls -a | grep '^.m'`/configure" >> myfile.sh

Is there an argument for each line output?  Such as $1 where I can include it in the commands and make it look like (this also does not work btw but I'm looking for something similar)...
ls -a | grep '^.m' | echo "sh $1/configure.sh" >> myfile.sh

SAM

---

### Post by mssever on 2008-09-10
```
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]'#!/bin/bash'[/COLOR] > outfile
[COLOR=#008000]**for **[/COLOR]directory in .m*; [COLOR=#008000]**do**[/COLOR]
  [COLOR=#666666][[[/COLOR] -d [COLOR=#ba2121]"$directory"[/COLOR] [COLOR=#666666]]][/COLOR] [COLOR=#666666]||[/COLOR] [COLOR=#008000][B]continue
  [/B][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"bash \"$directory\"/configure.sh"[/COLOR] >> outfile
[COLOR=#008000]**done**[/COLOR]

```

EDIT: Notice that I called bash, not sh. To make your script more robust, make sure all your configure scripts are executable, then drop the bash altogether (i.e., just call "$directory/configure.sh").

---

### Post by sag47 on 2008-09-10
> **mssever said:**
> ```
[COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]'#!/bin/bash'[/COLOR] > outfile
[COLOR=#008000]**for **[/COLOR]directory in .m*; [COLOR=#008000]**do**[/COLOR]
  [COLOR=#666666][[[/COLOR] -d [COLOR=#ba2121]"$directory"[/COLOR] [COLOR=#666666]]][/COLOR] [COLOR=#666666]||[/COLOR] [COLOR=#008000][B]continue
  [/B][/COLOR][COLOR=#008000]echo[/COLOR] [COLOR=#ba2121]"bash \"$directory\"/configure.sh"[/COLOR] >> outfile
[COLOR=#008000]**done**[/COLOR]

```

EDIT: Notice that I called bash, not sh. To make your script more robust, make sure all your configure scripts are executable, then drop the bash altogether (i.e., just call "$directory/configure.sh").

Thanks alot for your reply, your post jogged a spark of thought for me and I came up with this:
```
# ls -a | grep '^.m' | while read line;do echo "sh $line";done
sh .macromedia/
sh .madedit/
sh .maltego/
sh .mcop/
sh .mcoprc/
sh .mozilla/
sh .msf3/
```

For anyone else reading this I further went on to modify it as:
```
# echo "#! /bin/bash" >> myfile.sh
# ls -a | grep '^.m' | while read line;do echo sh "$line"configure.sh;done >> myfile.sh
```
So I know how to handle it from here!
Thanks alot.
SAM

---

### Post by mssever on 2008-09-10
> **sag47 said:**
> For anyone else reading this I further went on to modify it as:
```
# echo "#! /bin/bash" >> myfile.sh
# ls -a | grep '^.m' | while read line;do echo sh "$line"configure.sh;done >> myfile.sh
```So I know how to handle it from here! That approach will fail if any interesting directory contains spaces or other special characters. You'd have to do ```
ls -A1 --quoting-style=shell
``` But that's the hard way to do things. Why not eliminate the ls, grep, and while statement and replace it with a for loop like I used above? It's guaranteed to work in all cases, and it's a whole lot easier.

---

### Post by ghostdog74 on 2008-09-10
> **sag47 said:**
> Thanks alot for your reply, your post jogged a spark of thought for me and I came up with this:
```
# ls -a | grep '^.m' | while read line;do echo "sh $line";done
sh .macromedia/
sh .madedit/
sh .maltego/
sh .mcop/
sh .mcoprc/
sh .mozilla/
sh .msf3/
```

For anyone else reading this I further went on to modify it as:
```
# echo "#! /bin/bash" >> myfile.sh
# ls -a | grep '^.m' | while read line;do echo sh "$line"configure.sh;done >> myfile.sh
```
So I know how to handle it from here!
Thanks alot.
SAM
the find command encompass 
1) searching for files/directories according to you wish
2) internal "while loop" to display files for you
3) execute stuffs for you as it iterates the files/directories
therefore , your code can be simplified to this
```

find /fullpath -type d -name ".m*" | while read dir
do
  find $dir -type f .....
done 

```

---

### Post by sag47 on 2008-09-10
Awesome, well I think anyone who is looking for a similar solution has a ton of options with all these posts.  Thanks to all who replied, I modified my script accordingly and it works well/efficiently.  +thanks to all

SAM

---

