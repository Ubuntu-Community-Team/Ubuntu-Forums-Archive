---
title: "Problem with spaces in filenames"
date: 2008-03-18
forum: Programming Talk
---

### Post by Sciamano on 2008-03-18
Ehm... I know this is stupid but in making this script (which should break long audiobook mp3s in 8 minutes chunks) I'm encountering a problem when the names of the source files include spaces.

My script is basically the execution of a command (mp3splt) for each file in the specified directory:

```
#!/bin/sh

for file in `ls *.mp3`; do
   mp3splt -a -t 8.00 $1/$file
done
```

But, as I said, if the source filename contains spaces it won't work.
Here is an example of the errors:

```
Mp3Splt 2.1 (2004/Sep/28) by Matteo Trotta <matteo.trotta@lib.unimib.it>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
./01.: No such file or directory
Mp3Splt 2.1 (2004/Sep/28) by Matteo Trotta <matteo.trotta@lib.unimib.it>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
./John: No such file or directory
Mp3Splt 2.1 (2004/Sep/28) by Matteo Trotta <matteo.trotta@lib.unimib.it>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
./Grisham: No such file or directory
Mp3Splt 2.1 (2004/Sep/28) by Matteo Trotta <matteo.trotta@lib.unimib.it>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
./-: No such file or directory
Mp3Splt 2.1 (2004/Sep/28) by Matteo Trotta <matteo.trotta@lib.unimib.it>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
./The: No such file or directory
Mp3Splt 2.1 (2004/Sep/28) by Matteo Trotta <matteo.trotta@lib.unimib.it>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
./Appeal.mp3: No such file or directory
```

How can I solve? I've tried putting quotes almost everywhere (I thought quoting $file would work but it does not) but I did not succeed! :(
Thanks!

---

### Post by MonctonJohn on 2008-03-18
Did you try quotations?

```
#!/bin/sh

for file in `ls *.mp3`; do
   mp3splt -a -t 8.00 $1/"$file"
done
```

I see that you did... I'll play with the command at home... I know if done stuff like that before.

---

### Post by Sciamano on 2008-03-18
I know the solution probably is very simple but... I can't see it! :(

---

### Post by Cybergod on 2008-03-18
I'm not any good with regular expressions but it looks like that's what you need.

---

### Post by Sciamano on 2008-03-18
> **Cybergod said:**
> I'm not any good with regular expressions but it looks like that's what you need.

I don't understand what you mean.

---

### Post by slavik on 2008-03-18
my horrible shell scripting skill ...

```

ls *.mp3 | for i in readline; do
//stuff to do
done

```

---

### Post by Sciamano on 2008-03-18
> **slavik said:**
> my horrible shell scripting skill ...

```

ls *.mp3 | for i in readline; do
//stuff to do
done

```

I can't try right now, but I don't think this will solve the 'spaces' problem!

---

### Post by jobsonandrew on 2008-03-18
you can change the internal field separator in bash with:
```
IFS=$'\n'
```
this should stop it from thinking a new filename starts where there is a space if you put it at the top of your code

---

### Post by LaRoza on 2008-03-18
The above solutions will most likely help, but I can't test them because there are no spaces in my file names, which brings me to my next point...

It is easier to use underscores and camel case than spaces.

---

### Post by stylishpants on 2008-03-18
You don't need the backticked 'ls' command.  If you use that, then your for loop splits on whitespace and screws you up.

Your for loop can iterate over *.mp3 directly, in which case it just goes filename by filename and the whitespace problem goes away.

You need to double quote every place where you use the variable you create.

```


for file in *.mp3; do
    mp3splt -a -t 8.00 "$1/$file"
end

```

The "$1" does nothing here, presumably you've got that covered already.

Also, use bash instead of sh, it has more useful functionality and is more standard these days.
#!/bin/bash


For more info:
[http://wooledge.org:8000/BashPitfalls](http://wooledge.org:8000/BashPitfalls)

---

### Post by Sciamano on 2008-03-18
Both the IFS solution and the one proposed by stylishpants work.
I've chosen the second because it's cleaner, but still I want to thank jobsonandrew, because I learned something new from his proposed solution too.

Regarding the $1.. I've put it there because I want to be able to use the script in any directory. Therefore the script (which I called "booksplit") should work like this:

> booksplit . *(if I want to split files in the same directory)*
booksplit /directory/where/mp3/files/are *(to split files in a different directory)*

Is this not correct?

Thanks
Luca

P.S.: I've just checked the BashPitfalls link... nice to see my question represents the #1mistake bash programmers make. I feel less lonely now :)

---

### Post by Sciamano on 2008-03-18
For anyone interested... here is my "final" version:

```
#!/bin/bash
if [[ $# -lt 3 ]]; then echo "Usage: booksplit <source dir> <destination dir> <length of chunks in minutes>"; exit 1; fi

for file in "$1"*.mp3; do
    mp3splt -a -t "$3".00 "$file" -d "$2"
done
```

If you see something wrong, please let me know.
Thanks

---

### Post by kaens on 2008-03-18
This site, linked off of reddit the other day, is really helpful for writing BASH scripts,  it's got a lot of common mistakes people make that seem like they should work but don't (or don't work to well):

[http://wooledge.org:8000/BashPitfalls]("http://wooledge.org:8000/BashPitfalls")

---

