---
title: "Bash: How do i &quot;Pipe&quot; into a command?"
date: 2009-10-13
forum: Programming Talk
---

### Post by rob86 on 2009-10-13
How do I pipe information into a command with Bash? I know about |, but...

For example, let's say I have a text file containing just file path names that are all over the file system.

How do I use that text file (or any output from another command) in a command like, cp (copy) ?

like 

/home/myuser/afilehere
/home/myuser/somedir/anotherfile


and I want to copy all the files in that text file into one main folder.

I thought it'd be something like "cp - /home/FinalDir" where - is the value of the line, but - doesn't seem to work?

---

### Post by doas777 on 2009-10-13
I believe you are looking for <, but the usage is not quite right for what you want. first off, to make that work, the cp command would have to be capable of taking multiple source arguments (which it is not). as it stands your second path would be treated as your destination.

you probably need to read the file and run the command programatically

---

### Post by -grubby on 2009-10-13
I'm not quite sure what you mean, but if we have ~/copynames and we want to copy every file specified in that file (seperated by, say, spaces) to ~/copied_files/, we could do:

```

cp `cat ~/copynames` ~/copied_files/

```

EDIT: This won't work, I just realized; as the above poster said, cp lacks the ability to read multiple source files
EDIT1: Though in this specific case, you might want to try:

```

for filen in `cat ~/copynames`
do
    cp filen ~/copied_files/
done

```

---

### Post by Pres-Gas on 2009-10-13
I would say you will want to look into xargs.  Read up on the man page and go to the Examples section.  It may spark some ideas for you.

[http://manpages.ubuntu.com/cgi-bin/search.py?title=xargs](http://manpages.ubuntu.com/cgi-bin/search.py?title=xargs)

---

### Post by DaithiF on 2009-10-13
actually, cp can take multiple arguments if you use the -t destination flag, so for the OPs original question, something like this would work:
```
cat listoffiles.txt  | xargs cp -t destdir

```
though it would be pretty fragile as it would break with spaces in the file names/paths, so better to do a while read line; do cp "$line" destdir; done < listoffiles.txt method instead.

---

### Post by Penguin Guy on 2009-10-13
Personally I would recomend using a for loop, something like:

**[BASH]**
[PHP]for file in `cat list.txt`     # For each line output by the command 'cat list.txt'
do
       cp "$file" "/path/to/destination"     # Copy that file it to the destination
done[/PHP]

Which can be put on one line using semicolons as so:
```
for file in `cat list.txt`; do cp "$file" "/path/to/destination"; done
```

---

### Post by DaithiF on 2009-10-13
> **Penguin Guy said:**
> Personally I would recomend using a for loop, something like:

**[BASH]**
[php]for file in `cat list.txt`     # For each line output by the command 'cat list.txt'
do
       cp "$file" "/path/to/destination"     # Copy that file it to the destination
done[/php]Which can be put on one line using semicolons as so:
```
for file in `cat list.txt`; do cp "$file" "/path/to/destination"; done
```

thats not a good way to do it though because it won't handle spaces correctly (despite putting quotes around $file.  Each line in list.txt will get split according to the current IFS (whitespace by default), so paths with spaces will get split. Better to use while read variable; do blah $variable blah; done < list.txt which stores each line into the variable in its entirety.

---

### Post by doas777 on 2009-10-13
this is why I hate spaces in filenames. spend 5 minutes writing the script, and 2 hours figuring out how to deal with that one fricken file....

---

### Post by kaibob on 2009-10-13
This one works with files that contains spaces. 

```
#!/bin/bash

while read line ; do
   cp "$line" /target/directory
done < file
```

EDIT: I just noticed that DaithiF had already suggested the above in the text of his post. Sorry for the repetition.

---

