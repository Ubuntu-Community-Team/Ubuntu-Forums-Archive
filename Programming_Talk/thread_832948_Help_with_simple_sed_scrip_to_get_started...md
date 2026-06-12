---
title: "Help with simple sed scrip to get started.."
date: 2008-06-18
forum: Programming Talk
---

### Post by hopelessone on 2008-06-18
Hi,

I want to mass edit .html file names..

1. I want to add three zero's infront of a file
2. I want to delete some part of the file..

Can someone give me an example to get me started?

Thanks..

---

### Post by sisco311 on 2008-06-18
1.) ```
rename -n 's/()/000$1/' *.html
```2.) ```
rename -n 's/foo//' *.html
```use the -v option after you tested the command with the -n (no action)

EDIT:

**EXAMPLES**

  **i.) Remove file extention:**

```
rename -n 's/\.tmp$//' *.tmp
```  **ii.) Change file extension:**

```
rename -n 's/\.htm$/\.html/' *.htm
rename -n 's/\.PNG$/\.png/' *.PNG
``````
rename -n 's/\.html$/\.htm/' *.html
rename -n 's/\.png$/\.PNG/' *.png
``` ** iii.) Special characters in filename:**

    a.) Delete leading whitespace(space):

```
rename -n 's/^[ \t\r\n\f]*//' *
rename -n 's/^ *//' *
```    b.) Delete/Replace all whitespaces(spaces):

```
rename -n 's/[ \t\r\n\f]//' *
rename -n 's/ //g' *
``````
rename -n 's/[ \t\r\n\f]/_/g' *
rename -n 's/ /_/g' *
```    c.) Remove/Replace non-visible characters:

```
rename -n 's/[^\x20-\x7E]//g' *
rename -n 's/[^\x20-\x7E]/_/g' *
```   **iv.) Translate uppercase(lowercase) names to lower(upper):**

```
rename -n 'y/A-Z/a-z/' *
rename -n 'y/a-z/A-Z/' *
```  [B]v.) Insert/Overwrite 
[/B] 
    a.) Insert new prefix(suffix):

```
rename -n 's//Foo Fighters - /' *
rename -n 's/$/.ogg/' *
```    b.) Insert text after n-th character:

```
rename -n 's/(^.{n})(.*$)/$1-text-$2/' *
``` c.) Overwrite/Delete the first n characters:

```
rename -n 's/^.{n}/text/' *
rename -n 's/^.{n}//' *
``` d.) Overwrite/Delete the last n characters:    

```
rename -n 's/.{n}$/text/' *
rename -n 's/.{n}$//' *
```**  vi.) Insert date:**

    a.) Old name - Date:

```
rename -n 's/$/-'`date +%d-%m-%y`'/' *
```    b.) Old name - Date - Extension:

```
rename -n 's/(\.ext)$/-'`date +%d-%m-%y`'$1/' *.ext
rename -n 's/(\....)$/-'`date +%d-%m-%y`'$1/' *
```    c.) Date - Old name:

```
rename -n 's//'`date +%d-%m-%y`'-/' *
```  **vii.) Search and Replace/Delete:**

    a.) Replace/Delete first:

```
rename -n 's/foo/bar/' *
rename -n 's/foo//' *
```    b.) Replace/Delete all:

```
rename -n 's/foo/bar/g' *
rename -n 's/foo//g' *
```    c.) Replace/Delete last:

```
rename -n 's/foo*$/bar/g' *
rename -n 's/foo*$/bar/g' *
```

---

### Post by hopelessone on 2008-06-18
Than-Q Very muchly... !!

---

### Post by ghostdog74 on 2008-06-18
> **hopelessone said:**
> Hi,

I want to mass edit .html file names..

1. I want to add three zero's infront of a file
2. I want to delete some part of the file..

Can someone give me an example to get me started?

Thanks..

bash:
```

#!/bin/bash
for files in *.html
do
 newfile="000"${files/string_to_replace/}
 mv "${files}" $newfile
done

```

---

### Post by Hubi17 on 2008-06-18
Thank you soooooo much. I been looking for something like this for a while now.

---

### Post by Jozza The Wick on 2008-07-26
Thanks. A litte confusing - it would nice to have rename accept simple wildcards to allow people to do these things without having to learn regexp, though!

---

