---
title: "Bash script help: unquoting a string"
date: 2006-12-04
forum: Programming Talk
---

### Post by duff on 2006-12-04
I'm a little lost here.  Here's an abstraction of what I'm trying to do:

```
print() {
	echo $1
	echo $3
}
A="foo \"bar baz\" bing"
print $A
```

So basically, I have a string that may have quoted parameters all in one string.  The above code will print: ```
foo
"bar
```
but I would like```
foo
bing
```
printed out.  Meaning $2 = bar baz (no quotes). Is this possible?

---

### Post by thomasaaron on 2006-12-04
Well, I know of two ways to accomplish something similar.

Use array variables:

print(){
echo ${A[1]}
echo ${A[3]}
}

A[1]=foo
A[2]="bar baz"
A[3]=bing

print $A


The other way I could figure out in python (and I'm sure BASH has an equivalent methodolgy) is to take your string, analyze it slice by slice until you come to the middle two quotation marks and delete everything in between them, the piecemeal it back together into a new string.

Hope that helps.
If not, you stumped me!

Best,
Tom

---

### Post by duff on 2006-12-04
> **thomasaaron said:**
> Well, I know of two ways to accomplish something similar.

Use array variables:

print(){
echo ${A[1]}
echo ${A[3]}
}

A[1]=foo
A[2]="bar baz"
A[3]=bing

print $A


It's actually coming to me from another process with the quotes escaped, so I can't store the parameters in an array myself.

> 

The other way I could figure out in python (and I'm sure BASH has an equivalent methodolgy) is to take your string, analyze it slice by slice until you come to the middle two quotation marks and delete everything in between them, the piecemeal it back together into a new string.

I was hoping for a one-liner to do the job :p

---

### Post by thomasaaron on 2006-12-04
The problem seems to be the space between bar and baz is throwing everything off. Darn, I hate getting stumped! I'll look through some books tomorrow for an answer. Dang it! ;)

---

### Post by ghostdog74 on 2006-12-04
There might be a better solution, but meantime here's a "one liner".

```

A="foo \"bar baz\" bing"
echo $A | /usr/bin/python -c "print ' '.join ([i for i in raw_input().split() if not i[0] =='\"' and not i[-1] == '\"']) "

```

---

### Post by Arndt on 2006-12-05
> **duff said:**
> I'm a little lost here.  Here's an abstraction of what I'm trying to do:

```
print() {
	echo $1
	echo $3
}
A="foo \"bar baz\" bing"
print $A
```

So basically, I have a string that may have quoted parameters all in one string.  The above code will print: ```
foo
"bar
```
but I would like```
foo
bing
```
printed out.  Meaning $2 = bar baz (no quotes). Is this possible?

It seems you want to do with regard to quoting what the shells usually do when they process a command line. The command to use then is 'eval'.

```
$ cat /tmp/showargs
#! /bin/bash

echo arg 1 = $1
echo arg 2 = $2
echo arg 3 = $3
```


```
$ cat /tmp/use-a
#! /bin/bash

A="foo \"bar baz\" bing"

/tmp/showargs $A

/tmp/showargs "$A"

eval "/tmp/showargs $A"
```

```
$ /tmp/use-a
$ /tmp/use-a
arg 1 = foo
arg 2 = "bar
arg 3 = baz"
arg 1 = foo "bar baz" bing
arg 2 =
arg 3 =
arg 1 = foo
arg 2 = bar baz
arg 3 = bing

```

---

### Post by duff on 2006-12-05
> **Arndt said:**
> It seems you want to do with regard to quoting what the shells usually do when they process a command line. The command to use then is 'eval'.


That's the one!  I had tried (something similar to) ```
showargs eval $A
```
but hadn't tried the eval before the function.  Thank you!!

---

