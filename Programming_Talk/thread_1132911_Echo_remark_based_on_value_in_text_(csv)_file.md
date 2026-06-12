---
title: "Echo remark based on value in text (csv) file"
date: 2009-04-22
forum: Programming Talk
---

### Post by Mbengi Bongi on 2009-04-22
How do I get a shell script to check a CSV file and echo a statement based on the value of the 2nd column?

---

### Post by Arndt on 2009-04-22
> **Mbengi Bongi said:**
> How do I get a shell script to check a CSV file and echo a statement based on the value of the 2nd column?

If you care about the full syntax of CSV, including double quotes to enclose troublesome characters, this won't help you, but if you just have simple things separated by commas, this may work:

```
$ echo "frog,duck,cat" | awk -F , '{printf "my %s is cute\n", $2;}'
my duck is cute

```

Otherwise, there seem to be CSV libraries in both Perl and Python. I would use one of them rather than roll my own.

---

### Post by Mbengi Bongi on 2009-04-22
Thanks for your help Arndt.

Basically my script accepts user input, scans the file and prints back information about the city the user has inputted.  Column 2 in the file is the country.

If I wanted to introduce an 'if' statement, is it just a case of doing:

```
if $2="SCOTLAND" then
awk -F , '{printf "%s is in Scotland\n", $2;}'
else
awk -F , '{printf "%s is in England\n", $2;}'
fi

```

Sample of the file:

```
Edinburgh, SCOTLAND,Midlothian,EH,0131
Liverpool, ENGLAND,Merseyside,L,0151
```

Apologies for not making this clear :oops:

---

### Post by ghostdog74 on 2009-04-22
> **Mbengi Bongi said:**
> How do I get a shell script to check a CSV file and echo a statement based on the value of the 2nd column?

in your previous threads such as [this](http://ubuntuforums.org/showthread.php?t=988515), you are already exposed to how to get data from csv. you even know how to use cut (or not already?). what's going on?

---

### Post by Mbengi Bongi on 2009-04-23
> **ghostdog74 said:**
> in your previous threads such as [this](http://ubuntuforums.org/showthread.php?t=988515), you are already exposed to how to get data from csv. you even know how to use cut (or not already?). what's going on?

Sorry for being a pest :(, I have a disability that leaves me with a very poor memory and very short attention span and I totally forgot about my previous posts.

After having re-read all my previous entries which everyone has kindly answered, I've probably got all that I need.  Thanks very much!

---

