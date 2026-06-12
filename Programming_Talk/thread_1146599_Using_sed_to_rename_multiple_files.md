---
title: "Using sed to rename multiple files"
date: 2009-05-02
forum: Programming Talk
---

### Post by smithjb on 2009-05-02
Hello,

I have a lot of files that have '+' in the middle of the filename and I need to remove them.  Here is what I've tried so far:

```
sed 's/+//g'
```This however returns nothing and is like it's waiting for another command.

If I enter:

```
echo word++++word | sed 's/+//g'
```The results are correct.

What am I missing?

Thanks,

---

### Post by Arndt on 2009-05-02
> **smithjb said:**
> Hello,

I have a lot of files that have '+' in the middle of the filename and I need to remove them.  Here is what I've tried so far:

```
sed 's/+//g'
```This however returns nothing and is like it's waiting for another command.

If I enter:

```
echo word++++word | sed 's/+//g'
```The results are correct.

What am I missing?

Thanks,

It's not waiting for another command; it's waiting for input. In the second example, you're giving it the output from the 'echo' command as input.

To solve your problem, you need to produce a list of file you wish to rename, then for each name, construct the new name using your 'sed' command, and perform the required 'mv' command. You can do all that in a 'sh' script.

You can also use the 'mmv' command. I don't remember if it comes with Ubuntu, or if you need to fetch it.

---

### Post by kaibob on 2009-05-02
A simple alternative that you may want to consider is the rename command:

```
rename -n 's/\+//g' *
```

The -n option shows files that will be renamed. Substitute -v for -n to actually rename the files.

---

### Post by smithjb on 2009-05-02
That worked.  Thanks So much!

One more quick question.  Also in some of these file names are dates in this format 'MM-DD-YY'.  I would like to enclose the date with parentheses.  Would I also be able to use the rename command since I would be required to include the pattern returned in the new file name?

Thanks!

---

### Post by _Purple_ on 2009-05-02
Does the filename only have date or there are other characters too?

---

### Post by smithjb on 2009-05-02
Yes it contains other characters.  Here's an example file name:

"BEGINNING 11-27-93.DOC"

Ideally, I would like:

"BEGINNING (11-27-93).DOC"

Thanks!

---

### Post by _Purple_ on 2009-05-02
```
rename -n 's/(.*) (.*)-(.*)-(.*)\.(.*)/$1 ($2-$3-$4).$5/'  *
```

```
rename -v 's/(.*) (.*)-(.*)-(.*)\.(.*)/$1 ($2-$3-$4).$5/'  *
```

---

### Post by kaibob on 2009-05-02
I'm new to perlexpr but came up with the following:

```
rename -n 's/([\d][\d]-[\d][\d]-[\d][\d])/($1)/' *
```

---

### Post by sujoy on 2009-05-03
is the rename in ubuntu different?
cause i tried ```
rename -n 's/\+//' *
```

but  nothing happened :confused:
rename (util-linux-ng 2.14.2) in arch linux

---

### Post by ghostdog74 on 2009-05-03
in bash, don't have to use outside tools like sed
```

for file in *++*; do echo mv "$file" ${file//+/}; done

```

---

### Post by geirha on 2009-05-03
> **sujoy said:**
> is the rename in ubuntu different?
cause i tried ```
rename -n 's/\+//' *
```

but  nothing happened :confused:
rename (util-linux-ng 2.14.2) in arch linux

In ubuntu, rename is a symbolic link to prename, which is installed by the perl package. See if you have a prename command.

---

### Post by smithjb on 2009-05-03
Thanks everyone for their help!!!  All appears to be good!!

---

### Post by sujoy on 2009-05-04
> **geirha said:**
> In ubuntu, rename is a symbolic link to prename, which is installed by the perl package. See if you have a prename command.

aha, right you are. looks like ubuntu inherits its rename from debian. 
lucky for me its in AUR

thanks a lot.

---

