---
title: "Learning Commands - Help"
date: 2013-02-02
forum: New to Ubuntu
---

### Post by toad3000 on 2013-02-02
Hi. So I want to lists all files and directories in my home directory and then I Need to display all the files and directories that are in capital letters and if it's a directory it needs to have a "/" at the end of it

for example
FILE1
FILE2
DIR3/

I Have this command so far but I'm having trouble with the part where I Have to add the "/" at the end of the directory. Is there a way to do this by a single command or do I have to do something else. I am allowed to make scripts 

ls | more | grep [A-Z]

---

### Post by steeldriver on 2013-02-02
*n/m reread your post and realized I misunderstood what you were asking*

---

### Post by drunkenbrawler on 2013-02-02
`More' won't help because its not a stream processor.
You need to try control statements in bash or awk as you have conditional action.
Something like following:


```
[aniket @ aniket-XPS-15z : ~]$ ls -l  | awk '{ if($0 ~ /^d/) print toupper($NF)"/" ;else print toupper($NF)}'

```
output:
```

124
A.BMP
ANIKET/
A.OUT
DESKTOP/
DOCUMENTS/
DOWNLOADS/
DWHELPER/
FOO.C
MUSIC/
PICTURES/
PUBLIC/
SENT
TEMPLATES/
TEXPUT.LOG
ONE/
VIDEOS/
[aniket @ aniket-XPS-15z : ~]$

```

---

### Post by drunkenbrawler on 2013-02-02
Hi,

I think I misunderstood the question. The reply posted by steeldriver made me realize that. The snippet I posted will just capitalize your current directories.

You will need something like
```

[aniket  @ aniket-XPS-15z : ~]$ ls -l  | awk  '{ if($0 ~ /^d/ && $NF ~  /^[A-Z_]+$/) print $NF"/" ;else if ($NF ~ /^[A-Z_]+$/) print $NF}'
CAPITAL/
CAPITAL_FILE
[aniket @ aniket-XPS-15z : ~]$

```

---

### Post by steeldriver on 2013-02-02
there's also the -F switch to ls, which appends the trailing / on dirs, so possibly something like this will work?

```
$ ls
DIR  DiR  dir  FILE  fIlE  file
$ ls -F | grep -Ewo '[[:upper:]]*/?'
DIR/
FILE

```

---

### Post by sisco311 on 2013-02-02
Sounds like a homework question. Is this your homework?

From the [code of conduct](http://ubuntuforums.org/index.php?page=policy) that you agreed to when you created your account:

> 
While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.


---

### Post by toad3000 on 2013-02-02
Thank You! The -F command really works. I used it with the command I had previously. The full command I have is this. 

ls -F | more | grep [A-Z]

---

### Post by toad3000 on 2013-02-02
Do you know any good forums people can discuss commands and such? 
Thanks :)

---

### Post by sisco311 on 2013-02-02
If you check out the man page of ls you will find out that there is an option which you can use to print a `/' (slash) after each file name which is a directory. Once you are able to print the directory names in the format you want, you can pipe the output of ls to grep in order to list only the all uppercase file names. The pattern you use in grep depends on what do you mean by file names in capital letters...

---

### Post by sisco311 on 2013-02-02
> **toad3000 said:**
> Thank You! The -F command really works. 

-F will also append other indicators (*/=>@|) to the entries. If you scroll down a little bit the man page you will find the option which does exactly what you want. ;)

> **toad3000 said:**
> Do you know any good forums people can discuss commands and such? 
Thanks :)

This one. Just don't expect someone else to solve your homework for you.

---

