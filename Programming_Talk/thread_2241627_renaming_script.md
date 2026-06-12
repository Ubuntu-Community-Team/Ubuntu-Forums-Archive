---
title: "renaming script"
date: 2014-08-27
forum: Programming Talk
---

### Post by MrWestwood on 2014-08-27
Good day. I have a folder with lots of .jpg files in subfolders.
The structure is WestonIN7pm/YYYY-MM-DD/WestonIN.jpg

There are lots of jpg but each has the string WestonIN in the name.

What I want to do is change the WestonIN in each file name to WestonIN7pm.

I've tried to do a command like this:
find /home/lanein1/WestonIN7pm/2014-08-*/* -name "*.jpg" | rename "s/WestonIN/WestonIN7pm/" *.jpg

I was hoping it would go through each folder and rename the files it finds but it doesn't. However, if I run the commands seperately they work.

Any advice?

Thanks

---

### Post by TheFu on 2014-08-27
Try:```

find /home/lanein1/WestonIN7pm/2014-08-*/* -iname "*.jpg" \
    -exec rename "s/WestonIN/WestonIN7pm/og" {} \; 
```
Although I think that will not do what you want - the directory will be renamed too.

```

find /home/lanein1/WestonIN7pm/2014-08-*/* -iname "*.jpg" \
    -execdir rename "s/WestonIN/WestonIN7pm/og" {} \; 
```
should be better.

---

### Post by MrWestwood on 2014-08-29
Hi. Sorry for the delay. Many thanks for this I will give it a try.

Kind regards

---

### Post by greg59 on 2014-09-02
Another suggestion:

for i in `ls *.jpg`; do mv $i $(echo $i | sed 's/WestonIN/WestonIN7pm/'); done

this will loop through all .jpg files and for each one it renames that file to the result of passing in the file name to sed.

---

### Post by TheFu on 2014-09-02
> **greg59 said:**
> Another suggestion:

for i in `ls *.jpg`; do mv $i $(echo $i | sed 's/WestonIN/WestonIN7pm/'); done

this will loop through all .jpg files and for each one it renames that file to the result of passing in the file name to sed.

Nice, but that doesn't handle recursive directories.  Might work with an ls -R ...  nope, don't think it will.  I get the feeling there are more than a few directories to handle.

---

### Post by Vaphell on 2014-09-02
> ```
for i in `ls *.jpg`; do mv $i $(echo $i | sed 's/WestonIN/WestonIN7pm/'); done
```

so many nopes.

for i in `ls *.jpg` - why can't you use the glob directly? for i in *.jpg works just fine and unlike the ls hack, is always going to work correctly.
NEVER use ls for scripting

mv $i $(...) is going to blow up on filenames with whitespace, always quote your variables and $() if you want to preserve their format.

invoking sed to do a trivial replacement is an overkill because bash can do such things natively
mv "$i" "${i/WestonIn/WestonIN7pm}"

---

### Post by greg59 on 2014-09-03
I am grateful for the analysis there Vaphell. It wasn't entirely obvious to me why ls is so frowned upon but with a bit of googling I am now more than a little wary of it (especially for any files with '*'s in them). As for globbing in general, it is a feature I haven't really exploited as much as I should have. Some of my own scripts may have to change.

Thanks :]

---

### Post by Vaphell on 2014-09-03
the chief reason is that there are all kinds of characters that are let's say unprintable, but otherwise completely legal in filenames because in linux filesystems everything but / and null char \0 are allowed in names. Ls will do something with these chars for printing purposes, eg will put ?? there, and as a result the name presented is not the name the file actually has.
Another problem is with cutting the output to proper names. Newline is legit and then, even ignoring funky chars, you are unable to solve the ambiguity
Let's say you have output:
```
a
b
c
```
such output is produced in 4 cases
```
1. a, b, c
2. a, b\nc
3. a\nb, c
4. a\nb\nc
```
and you have no way of telling which scenario you are dealing with. This is inherent problem of transforming filenames to plain text, because the crucial information about the boundaries is lost.

And if you are saying you will never have filenames with funky chars or newlines - never say never, eg it's rather easy to create weird filenames by mistake in scripts, let's say by assuming that some command will always return a filename friendly, single line but getting multiline value. *ls* based janitor script would be hard pressed to mop such files up.


 
There are only 2 way to support filenames in a rock solid way
- native globs which create array-like structure with original names and no boundary problems
- *find *and other tools that support \0 char as a separator, usually combined with *while read -d $'\0'* - null char is disallowed in names, so it never collides with the legit chars and there is no ambiguosity
Every other approach can be tricked.

---

