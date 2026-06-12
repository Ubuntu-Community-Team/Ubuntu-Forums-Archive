---
title: "[SOLVED] Is there a way, from the command line, to know the Nth character of a file?"
date: 2007-12-21
forum: Programming Talk
---

### Post by Fixman on 2007-12-21
The title says it all

---

### Post by Fixman on 2007-12-21
Well, I found the command head that its pretty useful.

---

### Post by hod139 on 2007-12-21
```
cut -cN
```
will return the Nth character.

---

### Post by stylishpants on 2007-12-21
> **hod139 said:**
> ```
cut -cN
```
will return the Nth character.

Actually, that's not quite right.

Cut will process every line.  For each line, it will print the Nth character.

If you do 'cut -c100 file' and your file has 1000 lines of 50 chars each, you will get 1000 empty lines of output, not the 100th char in the file.

Here is one way to do it:

```

ruby -e 'n=100; puts File.open(ARGV[0]).read.slice(n,1)' file

```

Change the value of n to print a different char. Or read n from the cmd line too if you prefer:

```
 ruby -e 'n,file = ARGV[0,2]; puts File.open(file).read.slice(n.to_i,1)' 4 file

```

Note that n starts from 0 in this example.  Easy to change that though if you like.

Change 'puts' to 'print' if you don't want a newline printed after the character.


Perl version: (n starts at 1)
```

 perl -le '$n=4; undef $/; print(substr(<>,$n-1,1));' file
```

---

### Post by stroyan on 2007-12-21
head and tail can do a pretty good job showing a particular byte.
head -c 42 filename | tail -c 1

The dd command can skip a given number of bytes into a file.
It may be faster on big files because it can seek in and read one byte.
To see the first byte use
```
dd if=filename bs=1 count=1 skip=0 2>/dev/null
```
To see the 42nd byte use
```
dd if=filename bs=1 count=1 skip=41 2>/dev/null
```

A byte offset into a file is not always the same as the character
offset into the file.  That depends on the locale and the content of the file.
Some locales use multiple bytes per character.  Some encodings use a
variable number of bytes per character.  You would need to go to extra
effort to get most scripting languages to handle a locale with a character
encoding like utf8 correctly.

---

### Post by hod139 on 2007-12-22
If you want to use cut, you can do
```

cat foo.txt | xargs echo | cut -cN

```
This will count newlines as a character though.  If you don't want that, you will have to do more work.

---

