---
title: "tree output"
date: 2012-10-01
forum: Programming Talk
---

### Post by IAMTubby on 2012-10-01
Hey,
Is it possible to get the tree output in pure text form(as in without all the ---'s in between).

I want to use the tree output as input for an application. The ---'s make it difficult to process.

Thanks.

---

### Post by Lars Noodén on 2012-10-01
I couldn't find anything in the [tree](http://manpages.ubuntu.com/manpages/precise/en/man1/tree.1.html) man page about removing the line graphic and replacing them with white space, but you could get that by piping the output through [tr](http://manpages.ubuntu.com/manpages/precise/en/man1/tr.1.html)

```

tree  /etc/ | tr '&#9492;&#9472;&#9500;&#9474;' '    '

```

tree can also do XML output, that might be easier to process depending on what you are doing.

---

### Post by IAMTubby on 2012-10-01
> **Lars Noodén said:**
> I couldn't find anything in the [tree](http://manpages.ubuntu.com/manpages/precise/en/man1/tree.1.html) man page about removing the line graphic and replacing them with white space, but you could get that by piping the output through [url0http://manpages.ubuntu.com/manpages/precise/en/man1/tr.1.html]tr[/url]

```

tree  /etc/ | tr '&#9492;&#9472;&#9500;&#9474;' '    '

```

tree can also do XML output, that might be easier to process depending on what you are doing.
Lars, that's very useful. But is it possible to get your output like
```

/home/xxx/yyy/1
/home/xxx/yyy/1/1.png

```
where every line is an absolute path.

---

### Post by Lars Noodén on 2012-10-01
> **IAMTubby said:**
> Lars, that's very useful. But is it possible to get your output like
```

/home/xxx/yyy/1
/home/xxx/yyy/1/1.png

```
where every line is an absolute path.

That would be [font=Courier new]tree -fi /home/xxx/yyy[/font]

---

### Post by IAMTubby on 2012-10-01
> **Lars Noodén said:**
> That would be [font=Courier new]tree -fi /home/xxx/yyy[/font]
Thanks a lot Lars, really useful reply. :)

---

### Post by trent.josephsen on 2012-10-01
Or perhaps just "find"?

---

### Post by IAMTubby on 2012-10-01
> **trent.josephsen said:**
> Or perhaps just "find"?
Trent, but I want to find a word(not a file) in the entire filesystem.
I am not comfortable with "grep". I write
```

$grep "hello"

```

it, never comes up with the result. I have lots of text documents that have the word "hello" in them. Is it just me ? or are there other arguments to add ?

Thanks.

---

### Post by IAMTubby on 2012-10-01
> **trent.josephsen said:**
> Or perhaps just "find"?
Okay, I am being lazy here. I should have had a look at the man page for grep.
Looked at it and saw that you have to mention as
```

$grep "hello" *

```

Thanks.

---

### Post by trent.josephsen on 2012-10-01
I'm not sure what you're saying about grep. I was observing that "find" and "tree -fi" do almost the same thing, except that tree omits dotfiles (which you can do with find's -prune option). I'd use "find" over "tree" in a script because (a) tree isn't always installed and (b) tree is meant for human eyes, which is why it has fancy line graphics in the first place. If you do use tree, you'll also want to account for the file count it outputs on the last line. find is better sorted for when you want to have precise control over the output.

---

### Post by IAMTubby on 2012-10-01
> **trent.josephsen said:**
> I'm not sure what you're saying about grep. I was observing that "find" and "tree -fi" do almost the same thing, except that tree omits dotfiles (which you can do with find's -prune option). I'd use "find" over "tree" in a script because (a) tree isn't always installed and (b) tree is meant for human eyes, which is why it has fancy line graphics in the first place. If you do use tree, you'll also want to account for the file count it outputs on the last line. find is better sorted for when you want to have precise control over the output.
Trent, sorry my bad!
Executed find! Yup, this is what I wanted.
Almost similar to $tree -fi except for the count at the end.

What is the best way to find a word from the entire filesystem, say I want to find all files which have the word "hello".
PS : I don't want to find files, which have the word "hello" in it's filename, I want contents to have the word "hello".

Thanks.

---

### Post by Vaphell on 2012-10-01
```
grep -r hello <dir>
```

---

### Post by Lars Noodén on 2012-10-01
> **IAMTubby said:**
>  I want to find all files which have the word "hello".

One way would be to use [grep](http://manpages.ubuntu.com/manpages/precise/en/man1/grep.1.html):

```

grep -r 'hello' ./*
grep -lr 'hello' ./*

```

---

### Post by IAMTubby on 2012-10-01
> **Vaphell said:**
> ```
grep -r hello <dir>
```
Thanks Vaphell

> **Lars Noodén said:**
> One way would be to use [grep](http://manpages.ubuntu.com/manpages/precise/en/man1/grep.1.html):

```

grep -r 'hello' ./*
grep -lr 'hello' ./*

```
Thanks Lars.

It almost works. But I have 2 doubts
1)Can you clarify if the search pattern is searched as 'hello' or "hello" or just hello
```

grep -r 'hello' ./* or
grep -r "hello" ./* or 
grep -r hello ./*
[code]

2)This is the output of my grep command
[code]
$ grep -r hello ./* ./hello.txt:This is a test for hello 
grep: ./versions/UnixSockets/echo_socket: No such device or address 
grep: ./versions/UnixSockets/StartingAllOverAgain/echo_socket: No such device or address 
grep: ./versions/UnixSockets/StartingAllOverAgain/CompilingServer/echo_socket: No such device or address 

```

Why is it so ?

---

### Post by Lars Noodén on 2012-10-01
> **IAMTubby said:**
> 1)Can you clarify if the search pattern is searched as 'hello' or "hello" or just hello
[code]
grep -r 'hello' ./* or
grep -r "hello" ./* or 
grep -r hello ./*
[code]


All three are the same.  They won't look for the quotes, just what's between them.  If you want to specify a pattern, you can use [egrep](http://manpages.ubuntu.com/manpages/precise/en/man1/egrep.1.html) instead.

---

### Post by IAMTubby on 2012-10-01
Ok answer for 2.

```

$ file echo_socket
echo_socket: socket

```

So is it because, it tries to search inside a file of type socket.
This should be reported as a bug ? 
Ideally it shouldn't check inside a file of type socket right ? because it's a special file.

---

### Post by Vaphell on 2012-10-01
error messages are harmless and you can filter them out by redirecting stderr to /dev/null

```
grep ... 2> /dev/null
```

then there is this
```
$ grep --help
...
-D, --devices=ACTION      how to handle devices, FIFOs and sockets;
                            ACTION is `read' or `skip'
...
```

---

### Post by IAMTubby on 2012-10-02
> **Vaphell said:**
> error messages are harmless and you can filter them out by redirecting stderr to /dev/null

```
grep ... 2> /dev/null
```

then there is this
```
$ grep --help
...
-D, --devices=ACTION      how to handle devices, FIFOs and sockets;
                            ACTION is `read' or `skip'
...
```
Thanks a lot Vaphell, shall try it out.

---

