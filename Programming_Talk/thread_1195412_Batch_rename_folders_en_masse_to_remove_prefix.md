---
title: "Batch rename folders en masse to remove prefix"
date: 2009-06-23
forum: Programming Talk
---

### Post by davidmigl on 2009-06-23
Posting this here for reference in hopes that it will help someone someday... I couldn't find anything on the web exactly about this (there were a lot of things that were close) so I had to figure it out myself.

I wanted to batch rename folders to remove a prefix. There were other directories that didn't have the prefix. So my original folders for example were ```
Prefix - Folder One Name
Prefix - Another Folder
Prefix - Testing
Elements
```
and I wanted to rename these to```
Folder One Name
Another Folder
Testing
Elements
```

The final code I got working was```
for i in Prefix*;do mv "$i" "$(echo $i|cut -c9-)";done
```

The for loop runs on all files with the prefix. I needed the double quotes "" because some folders had spaces and that confused linux. $ for absolute references. bash executes any command in parenthesis () and returns the result as a string. cut -c#- cuts # of characters from the beginning and | pipes the filename to the cut command.

---

### Post by lloyd_b on 2009-06-24
Instead of```
$(echo $i|cut -c9-)
```you can do the same thing using bash's internal string handling:```
${i#Prefix - }
```This takes the variable "$i", and strips off any leading "Prefix - " from the string.

It does the same job, but to my mind is a bit easier to understand than the "cut"...

Lloyd B.

---

### Post by radioking on 2011-02-03
Rather old thread, but adding a working solution...


The proposed substitution

```
${i#Prefix - }
```did not work for me (bash, Ubuntu 10.04 lucid).

I used this command instead and it worked:

```
for i in **PREFIX***;do mv "$i" "${i/#'**PREFIX**'/}";done
```**PREFIX** has to be substituted by your prefix-string that you would like to remove from the filenames in that folder.

---

### Post by slavik on 2011-02-03
man rename

---

