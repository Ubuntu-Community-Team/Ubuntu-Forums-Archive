---
title: "Bash command help"
date: 2009-06-29
forum: Programming Talk
---

### Post by Levo on 2009-06-29
I want to make a Bash script to handle mounting and unmounting of ISO files. I double click the .iso file and the script starts.
I use $* to "catch" the image file directory. Is there a similar variable to catch only the file name? E.g. with $* I get /media/data/image.iso but for some other reason I want image.iso only. Is it possible?

---

### Post by unutbu on 2009-06-29
Try 

```
iso=$(basename "$*")
echo "$iso"

```

---

### Post by pytheas22 on 2009-06-29
I don't know if you're writing this script for your own educational purposes, but if you're just interested in a script that will easily mount and unmount ISO images and don't want to write it yourself, try [this page]("http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html").

---

### Post by Levo on 2009-06-29
> **pytheas22 said:**
> I don't know if you're writing this script for your own educational purposes, but if you're just interested in a script that will easily mount and unmount ISO images and don't want to write it yourself, try [this page]("http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html").

Yes I have tested it, but I make something more complicated. I'll post
it later in the howtos section.

---

### Post by Levo on 2009-06-29
> **unutbu said:**
> Try 

```
iso=$(basename "$*")
echo "$iso"

```

Thanks! This is exactly what I want.

---

### Post by ghostdog74 on 2009-06-29
no need to use basename
```

echo "${*##*/}"

```

---

### Post by unutbu on 2009-06-29
Neat. Thanks for this, ghostdog74.

---

### Post by Levo on 2009-06-30
> **ghostdog74 said:**
> no need to use basename
```

echo "${*##*/}"

```


No this doesn't work for me.
The script looks like this (and it works fine):

```

ISO=$(basename "$*")
DIR=$*
```

How can this be rewritten with "${*##*/}"?

---

### Post by unutbu on 2009-06-30
That's odd, it works for me:
 
test.sh:
```
#!/bin/sh
ISO="${*##*/}"
DIR="$*"
echo "$DIR"
echo "$ISO"
```
```

% test.sh /media/data/image.iso 
/media/data/image.iso
image.iso

% test.sh /media/data/image with spaces.iso 
/media/data/image with spaces.iso
image with spaces.iso
```

---

### Post by Levo on 2009-06-30
> **unutbu said:**
> That's odd, it works for me:
 
test.sh:
```
#!/bin/sh
ISO="${*##*/}"
DIR="$*"
echo "$DIR"
echo "$ISO"
```
```

% test.sh /media/data/image.iso 
/media/data/image.iso
image.iso

% test.sh /media/data/image with spaces.iso 
/media/data/image with spaces.iso
image with spaces.iso
```

OK, my fault. This works.
Later in the script I used: ISO=$(basename "$DIR") instead of ISO=$(basename "$*"). How can this be rewritten using ${*##*/}?

---

### Post by Levo on 2009-06-30
I tried ${DIR##*/} and it worked!

But what is the difference between these two command?
```

$(basename "$*")
${*##*/}

```
And why is the second one better?

---

### Post by unutbu on 2009-06-30
$(basename "$*") spawns a subprocess to run /usr/bin/basename on $*. 
(Anything inside of $(...) is run in a subprocess.)
Spawning subprocesses take more system resources (in terms of both memory and CPU)
than using built-in shell commands.

${*##*/} is a built-in shell string operation. See
[http://tldp.org/LDP/abs/html/refcards.html#AEN21244](http://tldp.org/LDP/abs/html/refcards.html#AEN21244) 
Table B-5. String Operations

Note however, that making a script use less system resources might not be your highest priority. Maybe readability is more important to you than speed. If you don't use stuff like ${*##*/} often, there will come a day when you look at your script and say, "what the heck is that!?". In that case, you might want to stick with basename, or use comments.

---

### Post by Levo on 2009-06-30
> **unutbu said:**
> $(basename "$*") spawns a subprocess to run /usr/bin/basename on $*. 
(Anything inside of $(...) is run in a subprocess.)
Spawning subprocesses take more system resources (in terms of both memory and CPU)
than using built-in shell commands.

${*##*/} is built-in shell string operation. See
[http://tldp.org/LDP/abs/html/refcards.html#AEN21244](http://tldp.org/LDP/abs/html/refcards.html#AEN21244) 
Table B-5. String Operations

Note however, that making a script use less system resources might not be your highest priority. Maybe readability is more important to you than speed. If you don't use stuff like ${*##*/} often, there will come a day when you look at your script and say, "what the heck is that!?". In that case, you might want to stick with basename, or use comments.

I have no problem understanding it! I used ${*##*/}. It works fine. Thank you all for helping!

---

### Post by kaibob on 2009-06-30
> **unutbu said:**
> ...Note however, that making a script use less system resources might not be your highest priority. Maybe readability is more important to you than speed. If you don't use stuff like ${*##*/} often, there will come a day when you look at your script and say, "what the heck is that!?". In that case, you might want to stick with basename, or use comments.

I've wondered on occasion if the use of commands such as basename really slows things down much with very simple shell scripts. I'm sure advanced users want to use shell expansion just because it's a better way of doing things, but for beginner's like myself I think readability is a legitimate issue.

---

### Post by ghostdog74 on 2009-06-30
> **kaibob said:**
> I've wondered on occasion if the use of commands such as basename really slows things down much with very simple shell scripts. 
it will be true when you have to do basename for a lot of files inside loops.

---

