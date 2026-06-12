---
title: "unzip a file with a name containing a string"
date: 2012-11-04
forum: Programming Talk
---

### Post by Dabo Ross on 2012-11-04
Hello, this isn't exactly a problem as something I don't know how to do. 

I want to be able to make a .sh script that will take out the file "worldedit.jar" from a ziped folder which is named worldedit-<versionnumber>.

My problem is that I don't know how to do any of this. 
Basically there will be a zipped folder whose name will be worldedit with a few numbers after it in the /home/newlanders/server/update/ folder. 
I just want to get the file worldedit.jar out of the zipped folder, so I don't have to do it myself unzipping the whole thing and then deleting the files that I don't need that were in that folder. I am going to be including this in a crontab job script to be run automatically, right before it transfers all .jar files from the /home/newlanders/server/update/ folder. (most updates are just jars, only worldedit comes ina  zip and I need to get the jar out of it.)
I will be deleting the zip folder after I get worldedit.jar out of it.

Thanks in advance for anyone who can/will help.

---

### Post by spjackson on 2012-11-04
I'm not sure that I truly understand what you are asking for, but I'll take a guess.
```

cd /home/newlanders/server/update
unzip worldedit1234.zip worldedit.jar

```
Is that it?

---

### Post by Dabo Ross on 2012-11-04
That would work if it was named worldedit1234 every time, but it won't have the same numbers after its name every time... I need a way to unzip any zip file who's name contains worldedit, whether it be worldedit1234 or worldedit7398.

---

### Post by ssam on 2012-11-04
if there is 1 file with a name worldedit????.zip, then you can use
```
unzip worldedit*.zip worldedit.jar
```
bash will replace "worldedit*.zip" with a list of files that match the pattern.

if there are several files with a name that matches, then you can filter out the first (or last), with something like
```
unzip `ls worldedit*.zip | head -n1` worldedit.jar
```
the backticks (`) tell bash to run the command within them, and use their output as part of a command. "ls worldedit*.zip" gets all the files with a name that matches, and "| head -n1" acts as a filter that only allows the first answer though. use 'tail' instead to get the last.

---

### Post by Dabo Ross on 2012-11-04
> **ssam said:**
> if there is 1 file with a name worldedit????.zip, then you can use
```
unzip worldedit*.zip worldedit.jar
```
bash will replace "worldedit*.zip" with a list of files that match the pattern.

if there are several files with a name that matches, then you can filter out the first (or last), with something like
```
unzip `ls worldedit*.zip | head -n1` worldedit.jar
```
the backticks (`) tell bash to run the command within them, and use their output as part of a command. "ls worldedit*.zip" gets all the files with a name that matches, and "| head -n1" acts as a filter that only allows the first answer though. use 'tail' instead to get the last.

Thanks so much for this, It looks like it will work. I haven't tried it yet but it seems exactly what I need. I thought that the * character would only do that when I was using it like something.*.something but it will work with something*something? That is pretty cool, thanks. I will try it in a little bit and edit this post with my results.

---

### Post by Vaphell on 2012-11-04
> I thought that the * character would only do that when I was using it like something.*.something but it will work with something*something? 

depends on the context. In fullblown regexes used by *grep*, *sed*, *awk*, *perl*, etc ***** is a 0+ modifier to the symbol before it, eg
.* = *<any char>(0 or more times)*
while in case of shell patterns (globs) ***** is a standalone *<any sequence>*

```
unzip `ls worldedit*.zip | head -n1` worldedit.jar
```

unfortunately this line reinforces bad practices.
ls is for human eyes not for scripts. It should not be parsed.

---

### Post by Dabo Ross on 2012-11-04
Ok, thanks. This works now. I have taken all that and written this:
```
PATH=/opt/someApp/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
#!/bin/bash
cd /home/newlander/server/update/
if [ -a `ls worldedit*.zip | tail -n1` ]
then
    unzip `ls worldedit*.zip | tail -n1` WorldEdit.jar
    rm worldedit*.zip
fi
```
That works great!

---

### Post by Vaphell on 2012-11-04
a bit messy, hashbang line (#!/bin/bash) should be the very first line.
and i'd do that 'unzip the last found archive' like this to avoid parsing LS

```
for f in worldedit*.zip; do continue; done
[ -f "$f" ] && unzip "$f" WorldEdit.jar
```

---

### Post by Dabo Ross on 2012-11-05
> **Vaphell said:**
> a bit messy, hashbang line (#!/bin/bash) should be the very first line.
and i'd do that 'unzip the last found archive' like this to avoid parsing LS

```
for f in worldedit*.zip; do continue; done
[ -f "$f" ] && unzip "$f" WorldEdit.jar
```
```

#!/bin/bash
PATH=/opt/someApp/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

cd /home/newlander/server/update/
for f in worldedit*.zip; do continue; done
if [ -f "$f" ] 
then
     unzip "$f" WorldEdit.jar
     rm "$f"
fi

```
Like that?
I am pretty much a beginner in bash.

---

### Post by ssam on 2012-11-06
I am not sure that ls is any worse to parse than any other command, though globbing in the if statement could be faster.

both methods are going to give problems if any of the filenames have spaces in, or even worse if they contain characters like '*' or '\n'. see [http://unix.stackexchange.com/questions/9496/looping-through-files-with-spaces-in-the-names](http://unix.stackexchange.com/questions/9496/looping-through-files-with-spaces-in-the-names) for examples of getting around this.

---

### Post by Dabo Ross on 2012-11-06
> **ssam said:**
> I am not sure that ls is any worse to parse than any other command, though globbing in the if statement could be faster.

both methods are going to give problems if any of the filenames have spaces in, or even worse if they contain characters like '*' or '\n'. see [http://unix.stackexchange.com/questions/9496/looping-through-files-with-spaces-in-the-names](http://unix.stackexchange.com/questions/9496/looping-through-files-with-spaces-in-the-names) for examples of getting around this.

For my case, the file names should only contain a-z 1-9 and . and -. So I think it should be fine. Also the time it takes isn't really a problem, and there should be only 0-3 files to parse anyways. Thanks!

---

### Post by Vaphell on 2012-11-06
> **ssam said:**
> I am not sure that ls is any worse to parse than any other command, though globbing in the if statement could be faster.

ls doesn't necessarily show true representation of the filename and that affects later operations on the output, while directly called globs don't mangle data. Also globs are native while piping ls to get a subset of data means spawning processes and it has a cost.
```
$ time ( for f in *; do :; done; echo $f )
real	0m0.001s
user	0m0.010s
sys	0m0.000s
$ time ( ls | tail -n1 )
real	0m0.006s
user	0m0.030s
sys	0m0.000s
```
numbers may vary a bit, but the difference is visible.
In this case it may be negligible, but spawning short lived process to perform trivial task may add up to some serious time.
In general - to access set of files use native globs as often as possible. If that is not possible for whatever reason, look for the next best method that is still kosher and avoids filename problems completely (most likely using **find ... -print0**)
While it might look like an overkill, it will lead you to a deeper understanding how shell works.

> both methods are going to give problems if any of the filenames have spaces in, or even worse if they contain characters like '*' or '\n'. see [http://unix.stackexchange.com/questions/9496/looping-through-files-with-spaces-in-the-names](http://unix.stackexchange.com/questions/9496/looping-through-files-with-spaces-in-the-names) for examples of getting around this.

No, parsing ls output when there are file names with \n is broken beyond repair, because file1\nfile2 in its output is indistinguishable from file1part1\nfile1part2. with globs the problem doesn't exist at all.
When you use simple
```
for f in *; do something with "$f"; done
```
you can be sure that f will be filled with proper names, even chock full of newlines, spaces, tabs and whatnot - after all it's the shell that does it, not you by manual manipulation of string representations of names.
The only thing left to do to be safe in this case is to put $f in double quotes to prevent troublesome characters like *, space or \n to mess things up.


OP, from that *| tail -n1 * i assume you want to access only the 'latest' file in alphabetical order? If so, the code should work. What should happen with the rest of matching files?

---

### Post by Dabo Ross on 2012-11-07
I want to just take worldedit.jar from the latest one (ei worldedit1-3-4 is later than worldedit1-3-3) and then delete all the .zip's
But I do have a script that is working for what I need, so I don't really need any more help, thanks!

---

