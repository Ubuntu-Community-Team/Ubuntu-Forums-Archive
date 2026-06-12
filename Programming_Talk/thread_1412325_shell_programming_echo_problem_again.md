---
title: "shell programming: echo problem again"
date: 2010-02-21
forum: Programming Talk
---

### Post by piyush.neo on 2010-02-21
```

piyush@piyush-machine:~$ echo \\\\\\\z
\\\z
piyush@piyush-machine:~$ echo \\\z
\z

```
but if i combine both of them

```

piyush@piyush-machine:~$ echo `echo \\\\\\\z`
\\z

```

As far as i know there can't be any substitution in the output of  command substitution..right??
the output of second segment should be 
\\\z
And if shell is doing substituion then output shoul be
\z

But how it is \\z??  
 :confused::confused:

---

### Post by piyush.neo on 2010-02-21
guys plz help me out with this...?? m stuck with echo

---

### Post by Barrucadu on 2010-02-21
The problem is you're, for some reason, running echo twice, which escapes stuff twice:

```
echo `echo \\\\\\\z`
```

Becomes:
```
echo \\\\z
```

Becomes:
```
\\z
```

---

### Post by piyush.neo on 2010-02-21
> **Barrucadu said:**
> The problem is you're, for some reason, running echo twice, which escapes stuff twice:

```
echo `echo \\\\\\\z`
```

Becomes:
```
echo \\\\z
```

Becomes:
```
\\z
```

If that is the case then why
```

piyush@piyush-machine:~$ echo \\\\\\\z
\\\z

```
It must be \\\\z

---

### Post by geirha on 2010-02-21
[http://mywiki.wooledge.org/BashFAQ/082](http://mywiki.wooledge.org/BashFAQ/082)

---

### Post by piyush.neo on 2010-02-21
After digging a bit about shell substitution behaviour i came to conclusion that during command line substitution:

if "\x"  (where x is any character) makes any sense to shell (i.e if it is \n or \t etc) then shell execute it like "\n" as a single entity else it is treated as it is
So in **echo `echo \\\\\\\z`**
the "z" in "\\\\\\\z" is not escaped by last "\" as it is not making any sense and taken as "\z".
therefore it reduces to echo \\\\z.
whereas```

$echo \z
z
$

```
z is escaped by "\"...
:P:P

---

### Post by Rany Albeg on 2010-02-21
If you want to echo a \ then echo \\ . So if you want to echo 4 slashes do echo with 8 slashes.

You typed 7 slashes, so the last one wasnt escaped.

---

### Post by piyush.neo on 2010-02-21
> **Rany Albeg said:**
> If you want to echo a \ then echo \\ . So if you want to echo 4 slashes do echo with 8 slashes.

You typed 7 slashes, so the last one wasnt escaped.

No..i don't have to echo 4 "\"..i am just concerned with the output...

---

### Post by falconindy on 2010-02-22
* A single backslash won't be printed.
* A backslash before a non-meaningful value won't be printed either.
* A backslash before a backslash will print a single backslash (because you're escaping the escape char)

Therefore, 7 backslashes followed by a non-meaningful value will result in 3 backslashes and the trailing value.

In other words, this is "working as intended."

---

### Post by piyush.neo on 2010-02-22
> **falconindy said:**
> * A single backslash won't be printed.
* A backslash before a non-meaningful value won't be printed either.
* A backslash before a backslash will print a single backslash (because you're escaping the escape char)

Therefore, 7 backslashes followed by a non-meaningful value will result in 3 backslashes and the trailing value.

In other words, this is "working as intended."

These are when you write commands directly on terminal but during command substitution this is not the case...
Read my above post....
OR see it urself
this is debugged version...
as u can see there are 4 slashes
```

piyush@piyush-machine:~$ cat try1
echo `echo \\\\\\\z`
piyush@piyush-machine:~$ bash -v try1
echo `echo \\\\\\\z`
echo \\\\z
\\z
piyush@piyush-machine:~$ 



```

---

### Post by geirha on 2010-02-22
It's because of ``'s backslash handling. Just quote it in single quotes and all the backslashes will be treated literally.

```
$ echo '\\\\\\\z'
\\\\\\\z

```

---

### Post by falconindy on 2010-02-22
> **piyush.neo said:**
> These are when you write commands directly on terminal but during command substitution this is not the case...
Read my above post....
OR see it urself
this is debugged version...
as u can see there are 4 slashes
```

piyush@piyush-machine:~$ cat try1
echo `echo \\\\\\\z`
piyush@piyush-machine:~$ bash -v try1
echo `echo \\\\\\\z`
echo \\\\z
\\z
piyush@piyush-machine:~$ 



```
And we arrive back at Barracadu's post explaining about how you're using echo twice, which is skewing your results.

This is where I proclaim you a troll. Good day.

---

### Post by piyush.neo on 2010-02-22
> **falconindy said:**
> And we arrive back at Barracadu's post explaining about how you're using echo twice, which is skewing your results.

This is where I proclaim you a troll. Good day.

How Barrucado is skewing my this explanation....?
> 
After digging a bit about shell substitution behaviour i came to conclusion that during command line substitution:

if "\x" (where x is any character) makes any sense to shell (i.e if it is \n or \t etc) then shell execute it like "\n" as a single entity else it is treated as it is
So in echo `echo \\\\\\\z`
the "z" in "\\\\\\\z" is not escaped by last "\" as it is not making any sense and taken as "\z".
therefore it reduces to echo \\\\z.
whereas
Code:
$echo \z
z
$
z is escaped by "\"...


Please point it so that i can rectify myself....:o

---

### Post by piyush.neo on 2010-02-22
> **geirha said:**
> It's because of ``'s backslash handling. Just quote it in single quotes and all the backslashes will be treated literally.

```
$ echo '\\\\\\\z'
\\\\\\\z

```

i know quoting will treat them literally.....but i am interested in how shell interpreted that double echo and why differently for two echo....

---

### Post by kaibob on 2010-02-22
> Quote:
After digging a bit about shell substitution behaviour i came to conclusion that during command line substitution:

if "\x" (where x is any character) makes any sense to shell (i.e if it is \n or \t etc) then shell execute it like "\n" as a single entity else it is treated as it is
So in echo `echo \\\\\\\z`
the "z" in "\\\\\\\z" is not escaped by last "\" as it is not making any sense and taken as "\z".
therefore it reduces to echo \\\\z.
whereas
Code:
$echo \z
z
$
z is escaped by "\"...

Please point it so that i can rectify myself....

piyush.neo

I'm not an expert on this, but I tend to agree with the above, although I would explain it differently. 

The Bash Reference Manual states:

> When the old-style backquote form of substitution is used, backslash retains its literal meaning except when followed by ‘$’, ‘`’, or ‘\’.

So, in the command shown below, the echo command within the backticks sees 3 escaped backslashes plus a literal backslash plus a z and therefore returns 4 backslashes and a z. The echo command outside of the backticks then sees two escaped backslashes plus a z and prints 2 backslashes and a z to the screen. 

```
$ echo `echo \\\\\\\z`
\\z
```

It appears that things are working correctly. 

kaibob

---

### Post by piyush.neo on 2010-03-08
Was not in touch with net for a long time....
Forget to thank u  guys....:D

---

