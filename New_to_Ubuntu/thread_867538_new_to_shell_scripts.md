---
title: "new to shell scripts"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by karasuman on 2008-07-23
I'd like to convert a bunch of avi files to .mp4 files.  I know how to do this one at a time:

```
mp4ize "file"
```

I know how to make an executable like

```
mp4ize "file1"
mp4ize "file2"
...
```

to do all of them without me having to constantly check in.

Is there a way to just tell it to mp4ize all of the files of a certain type in a directory?

I'm really a beginner at this stuff, but I'd like very much to understand what I'm doing so I can expand what I'm capable of.  I'd appreciate any help.  :)

---

### Post by jordanmthomas on 2008-07-23
```
for i in $(ls | grep .mp4); do mp4ize "$i"; done
```
will run mp4ize on all the .mp4 files in the current directory

If you need help understanding just ask.

---

### Post by RequinB4 on 2008-07-23
You can use * as a symbol for "anything" (Gets more technical, but that's it)

So you wanted to mp4ize three files that are all in a directory: a.avi; b.avi; and c.avi
You can do this:
```

mp4ize a.avi
mp4ize b.avi
mp4ize c.avi

```

Or this, which will do the same for any file with ending .avi:
```

mp4ize *.avi

```

Alternatively, you can use a  for command to search for every .mpg file and do the command on each one, as demonstrated above


Hope it helps

---

### Post by Cappy on 2008-07-23
```

while [ $# -gt 0 ]; do
    if [ "$1" != "--" ]; then
        parameters="$parameters $1"
    fi
    shift
done

```

And then running with
```
mp4ize *.avi
```
or something. I forget if it's * or .* in bash.

---

### Post by Locutus_of_Borg on 2008-07-23
Theres an app called Bulk Rename that does this for any file and with a nice GUI

---

### Post by karasuman on 2008-07-23
> **Cappy said:**
> ```

while [ $# -gt 0 ]; do
    if [ "$1" != "--" ]; then
        parameters="$parameters $1"
    fi
    shift
done

```

And then running with
```
mp4ize *.avi
```
or something. I forget if it's * or .* in bash.

Could you explain the syntax in the first part?

I really appreciate everybody's help.  :)  I know there are applications that can just do this FOR me, but this seems like something that should totally be within my reach without an app, and I'd really like to learn.

---

### Post by karasuman on 2008-07-23
> **jordanmthomas said:**
> ```
for i in $(ls | grep .mp4); do mp4ize "$i"; done
```
will run mp4ize on all the .mp4 files in the current directory

If you need help understanding just ask.

is i just a placeholder?

what exactly does 'grep' mean/do?  I see that popping up a lot in places.

---

### Post by jordanmthomas on 2008-07-23
> **karasuman said:**
> is i just a placeholder?

what exactly does 'grep' mean/do?  I see that popping up a lot in places.

grep searches for patterns in the input it's given.  In my example I pipe (|) the output of ls to it and search for any line with ".mp4" in it.


The i is not really just a placeholder, but a variable that holds the name of each thing grep finds.  for each i means "hey take this and set i to be each line in it."  Then, the body of the for (between the do and the done) says what we want to do with each i (file that is a .mp4)

Hope this helps some.  I'm honestly not a great teacher. :)

---

### Post by scorp123 on 2008-07-23
> **Locutus_of_Borg said:**
> Theres an app called Bulk Rename that does this for any file and with a nice GUI Renaming a file and converting one video format into another are NOT the same thing!

---

