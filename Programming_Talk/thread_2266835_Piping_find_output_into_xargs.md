---
title: "Piping find output into xargs"
date: 2015-02-25
forum: Programming Talk
---

### Post by cogset on 2015-02-25
I apologize if this isn't so much of a programming question but  rather a general question about using find and xargs, if this needs to be moved please do so.

Having said that, I'm after a combination of commands that will allow me to find all *jpeg files in a directory, rename them to *jpeg and then immediately link those renamed files in another directory where I keep an index of recent files.

So far I've come up with this ```
find . -mindepth 1 -exec rename  's/\.jpeg$/\.jpg/'   '{}' ';'
```which works, what I'd like to do next is to link the resulting *jpg files to another directory using one command.
To that extent I've tried ```
find . -mindepth 1 -exec rename  's/\.jpeg$/\.jpg/'   '{}' '; |xargs -I {} cp -s {} /tmp 
``` but to no avail, I really don't know this stuff and xargs in particular, so is there any way to make this work?
Should I use something else altogether?

I've also tried this```
 find . -mindepth 1 -exec rename  's/\.jpg$/\.jpeg/'   '{}' ';'  && for F in '*jpeg' ; do find $F -cmin -1 -exec cp -s '{}' /tmp/ ';'  ; done
``` but it doesn't work either, refusing to create the links.

---

### Post by Vaphell on 2015-02-25
oneliners are overrated, if you want to cram non-trivial logic in there you are better off with a script that is more readable and maintainable.

```
#!/bin/bash

while read -rd $'\0' jpg
do
    jpeg=${jpg%.*}.jpeg
    mv "$jpg" "$jpeg"
    cp -s "$jpeg" /tmp
done < <( find -iname '*.jpg' -print0 )
```

---

### Post by cogset on 2015-02-27
Thanks, both for the script and for pointing out that "oneliners" are not necessarily the best solution.

Having said that, I'm still curious about to why in the second line that I've posted, xargs doesn't seem to work at all: is that a trivial syntax error on my part, or is it  just not supposed to work at all in that case?

Whilst  for the last line I've posted, **cp -s** fails to create the links at all, printing the message > can make relative symbolic links only in current directoryand** ln -s** creates broken symlinks.

---

### Post by Vaphell on 2015-03-01
it doesn't work because there is no (viable) input for xargs to work with. The pipe redirects output to input of another command, if the preceding command spits out nothing the following command chain has nothing to do.

I just ran *find -exec rename* and despite 53 matching files the command was completely silent. No wonder xargs does nothing.
Find prints out found items by default, but whenever you do something else on the fly with -exec or whatever that behavior is overriden and stuff on stdout is not a given.

---

