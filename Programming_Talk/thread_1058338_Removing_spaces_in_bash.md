---
title: "Removing spaces in bash"
date: 2009-02-02
forum: Programming Talk
---

### Post by Benzaa on 2009-02-02
Hi,

I've been looking for a bash scrip to change a file name like this:

A file name.txt

to

AFileName.txt

I have seen some scripts that use sed, but those scripts just put the words together without capitalization.

mv "$1" `echo "$1" | sed 's/[ ]*//g'`

Another great idea is the use of variable expansion 
var="A file name.txt"
var=${var/ /}

But again, it just puts the words together.


Any idea for the capitalization part?

---

### Post by johnl on 2009-02-02
This seems to work for converting the text to proper case:

echo "This is my file.txt" | sed 's/\(^\|[[:space:]]\)./\U&/g'

You can from there run it through an expression to filter out the spaces.  It could probably be done in one pass, but I don't know how :)

---

### Post by Benzaa on 2009-02-03
Thanks for the help

I will try this code as soon as Im home.

btw, could you please tell me what does the sed command do?

sed 's/ \(^\|[[:space:]]\)./\U&/g'

why did you put an |??
and the U&, what is it for?

---

### Post by Tek-E on 2009-02-05
For figuring out about the sed command. I recommend.
```

man sed

```
and the | is a pipe that sends the text "This is my file.txt" through the sed command.

---

