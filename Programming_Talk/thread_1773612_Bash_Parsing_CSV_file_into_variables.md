---
title: "Bash: Parsing CSV file into variables"
date: 2011-06-02
forum: Programming Talk
---

### Post by jhonan on 2011-06-02
This is not so much 'how' to make this work, as 'why' should this work!

I need to read a comma delimited CSV file line by line, when I reach a certain line I want to read all the fields into variables. There are 6 fields in the CSV.

I've seen examples where the bash READ command reads the first field, and then lumps everything else into the second field. So you need to do a second pass to split out the second field. However, I wrote the following code which seems to work;

[FONT=Courier New]inputfile="./templates.csv"
SaveIFS=$IFS
IFS=","
while read f1 f2 f3 f4 f5 f6; do
  if [[ ${f1} == ${TEMPLATE_ID} ]]
  then
    export TEMPLATE_NAME=${f2}
    export TEMPLATE_PATH=${f3}
    export SOME_OTHER_FIELD=${f4}
  fi
done < "$inputfile"
IFS=$SaveIFS  [/FONT]

According to MAN READ, the line "read f1 f2 f3 f4 f5 f6;" should not work. Is this the correct usage of READ?

---

### Post by DaithiF on 2011-06-02
> **jhonan said:**
> 
According to MAN READ, the line "read f1 f2 f3 f4 f5 f6;" should not work. 

why not?
from man bash:
```
One line is read from the  standard  input,  <snip> and the
              first word is assigned to the first name, the second word to the
              second  name, and so on, with leftover words and their interven&#8208;
              ing separators assigned to the last name.  If  there  are  fewer
              words read from the input stream than names, the remaining names
              are assigned empty values. 
```

---

### Post by geirha on 2011-06-02
It's more or less correct, yes. I wouldn't change IFS globally though, you only need to change it for read.
```

while IFS=, read -r f1 f2 f3 f4 f5 f6; do
  ...
done < "$inputfile"

```
Now you don't have to remember the old IFS with saveIFS=$IFS.

On a side note, this will only work for simple csv-files, it will not work if any of the fields contain commas for instance; you'll need a csv-parser for a general approach.

man read does not explain the syntax for bash's builtin read. As a rule of thumb, if type says a command is a builtin or keyword, use help or check bash's man-page, otherwise, try man or info.

```
$ type read
read is a shell builtin
$ type [[
[[ is a shell keyword
$ type ls
ls is aliased to `ls --color=auto'
$ type -a ls
ls is aliased to `ls --color=auto'
ls is /bin/ls

# so, by the rule of thumb:
$ help read
$ help [[
$ man ls

```

---

### Post by jhonan on 2011-06-02
> **DaithiF said:**
> why not?
from man bash:
```
One line is read from the  standard  input,  <snip> and the
              first word is assigned to the first name, the second word to the
              second  name, and so on, with leftover words and their interven&#8208;
              ing separators assigned to the last name.  If  there  are  fewer
              words read from the input stream than names, the remaining names
              are assigned empty values. 
```
Ah! Line 2848 of an unrelated man doc... How did I miss it? :smile: - I was doing 'man read' which gives a different syntax;

```
NAME
       read - read from a file descriptor
SYNOPSIS
       #include <unistd.h>
       ssize_t read(int fd, void *buf, size_t count);

```> **geirha said:**
> man read does not explain the syntax for bash's builtin read. As a rule of thumb, if type says a command is a builtin or keyword, use help or check bash's man-page, otherwise, try man or info.

```
$ type read
read is a shell builtin
$ type [[
[[ is a shell keyword
$ type ls
ls is aliased to `ls --color=auto'
$ type -a ls
ls is aliased to `ls --color=auto'
ls is /bin/ls

# so, by the rule of thumb:
$ help read
$ help [[
$ man ls

```
I never realised this, I always thought HELP <command> gave the same entry as MAN <command> - Thanks!

---

### Post by DaithiF on 2011-06-02
> **jhonan said:**
> Ah! Line 2848 of an unrelated man doc... How did I miss it? :smile: - I was doing 'man read' which gives a different syntax;


sorry, i should have noticed you had mentioned **man read** -- thats documentation for the C read function rather than the bash builtin, as you now know.  For what its worth, those 2848 (and the following 2515) lines in man bash are well worth a read (no pun intended) :)  ... i find something new everytime i delve in there

---

### Post by jhonan on 2011-06-02
> **DaithiF said:**
>   For what its worth, those 2848 (and the  following 2515) lines in man bash are well worth a read (no pun  intended) :smile:  ... i find something new everytime i delve in there
Yeah, I never even realised man bash existed up until now.

> **geirha said:**
> It's more or less correct, yes. I wouldn't change IFS globally though, you only need to change it for read.
```

while IFS=, read -r f1 f2 f3 f4 f5 f6; do
  ...
done < "$inputfile"

```Now you don't have to remember the old IFS with saveIFS=$IFS.
Unfortunately the fields in the CSV have spaces in them, and this approach splits the fields out using the spaces. So "My Template Name" becomes f1=My, f2=Template, f3=Name

---

### Post by DaithiF on 2011-06-02
> **jhonan said:**
> Unfortunately the fields in the CSV have spaces in them, and this approach splits the fields out using the spaces. So "My Template Name" becomes f1=My, f2=Template, f3=Name
It shouldn't ... simplified example:
```
$ IFS=, read f1 f2 f3 < <(echo "my template,is,nice") && echo $f1
my template

```
can you double check your code?

---

### Post by jhonan on 2011-06-02
> **DaithiF said:**
> It shouldn't ... simplified example:
```
$ IFS=, read f1 f2 f3 < <(echo "my template,is,nice") && echo $f1
my template

```can you double check your code?
Ah! I'm breaking the field because I'm using printf and not echo;

```
IFS=, read f1 f2 f3 < <(echo "my template,is,nice") && printf "%-20s\n" $f1
my                  
template
```
Strange, the field doesn't break when I use my original method (storing IFS)

I'm always getting confused by this exact thing, spaces in variables/commands/parameters and how bash parses them.

---

### Post by jhonan on 2011-06-02
> **jhonan said:**
> Ah! I'm breaking the field because I'm using printf and not echo;

```
IFS=, read f1 f2 f3 < <(echo "my template,is,nice") && printf "%-20s\n" $f1
my                  
template
```
And here's the fix.... lol

```
IFS=, read f1 f2 f3 < <(echo "my template,is,nice") && printf "%-20s\n" [COLOR=Red]"$f1"[/COLOR]
my template
```

Seriously... quotes, double-quotes and spaces in bash are really hard for me to get my head around.

---

### Post by DaithiF on 2011-06-02
man bash to the rescue again:

```
man bash | less +"/^\s+printf"
printf [-v var] format [arguments]
    ...
    [B]The  format  is  reused as necessary to consume all of the argu-
    ments. [/B]

```

how many arguments do you have in these two cases?
1. printf "-20s\n" my template
2. printf "-20s\n" "my template"

1. 2 arguments, only 1 format, format gets reused ... giving you two lines
2. 1 argument, 1 format, success - hurrah!

> 
Seriously... quotes, double-quotes and spaces in bash are really hard for me to get my head around. 	

while waiting for the lightbulb to come on, quick rule of thumb ... when in doubt, quote!!  :)

Also, see here: [http://mywiki.wooledge.org/Quotes](http://mywiki.wooledge.org/Quotes)

---

### Post by geirha on 2011-06-02
Also consider giving [http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls) a read. It'll help avoid common bash-scripting bugs.

Also peak at the questions at [http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ). The first FAQ deals with your initial query.

---

