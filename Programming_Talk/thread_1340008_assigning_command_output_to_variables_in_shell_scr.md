---
title: "assigning command output to variables in shell scripts"
date: 2009-11-28
forum: Programming Talk
---

### Post by giraffe32 on 2009-11-28
Hi, 

I'm teaching myself shell scripting.

I am embarrassed to admit that i've been struggling with some of the following concepts for a couple of days:

When I attempt to use 'sort', 'uniq' commands in a shell script, I can't figure out the syntax
to write the output of commands like 'sort' and 'uniq' to local shell script variables (as opposed to sending the output to existing/new files in the filesystem.

eg



var1="this is a simple text variable"
var2=""
var2=`cat $var1 | sort | uniq`

produces debug output:

cat: this
cat:  is 
cat: a 
cat: simple 
cat: text 
cat: variable

var2=

I understand that these commands require file input but man pages state that they accept input from stdin and pipes.

Appreciate any help.

Could anybody provide any links to good online unix training resources.

Thanks.

---

### Post by Arndt on 2009-11-28
> **giraffe32 said:**
> Hi, 

I'm teaching myself shell scripting.

I am embarrassed to admit that i've been struggling with some of the following concepts for a couple of days:

When I attempt to use 'sort', 'uniq' commands in a shell script, I can't figure out the syntax
to write the output of commands like 'sort' and 'uniq' to local shell script variables (as opposed to sending the output to existing/new files in the filesystem.

eg



var1="this is a simple text variable"
var2=""
var2=`cat $var1 | sort | uniq`

produces debug output:

cat: this
cat:  is 
cat: a 
cat: simple 
cat: text 
cat: variable

var2=

I understand that these commands require file input but man pages state that they accept input from stdin and pipes.

Appreciate any help.

Could anybody provide any links to good online unix training resources.

Thanks.

When I do the same, I get

```
cat: this: No such file or directory
cat: is: No such file or directory
cat: a: No such file or directory
cat: simple: No such file or directory
cat: text: No such file or directory
cat: variable: No such file or directory
```

What is it you want sorted?

---

### Post by carl.davis on 2009-11-28
I think you would want an echo to replace the cat. However, there are also other problems. I don't think you can use sort or uniq in that manner. They are both designed to process on lines of files, not an array of words.

sort - sort lines of text files
uniq - report or omit repeated lines

Try doing it this way:

Create a file named word.list and containing:

```
this 
is 
a 
simple 
text 
variable
```


Change your script to be:

```
var2=""
var2=`cat word.list | sort | uniq`
echo $var2
```

Then execute the script.

---

### Post by giraffe32 on 2009-11-28
carl.davis: 
You hit the nail on the head.
I didn't read the 1st line of the man sort page.

I was trying to sort multiple words on one line ..

Thanks both for taking the time to reply.

---

