---
title: "Title Case / Camel Case File Names"
date: 2009-07-24
forum: Programming Talk
---

### Post by switchrodeo720 on 2009-07-24
I'm trying to put together a one liner that will rename all files within a directory to title case. An example is:

```
sample.movie.file.avi
```

Renamed to...

```
Sample.Movie.File.avi
```

With the help of some other forums I'm using the following:

```
for i in /path/to/files/*; do mv "$i" "$(echo $i | sed -e "s/\([^\.]\+\)\./\u\1\./g")"; done
```

The problem is that it doesn't rename the first character of the file name. I get:

```
sample.Movie.File.avi
```

Anyone have any ideas?

---

### Post by lswb on 2009-07-24
Try using '\<.' to designate the first letter of a word, something like

echo capitalize these words|sed 's/\(\<.\)\.*/\u\1/g'

---

### Post by jpkotta on 2009-07-25
This is handy, I just renamed a directory by hand like this yesterday.  I like the rename command better though.

Title Case
```
rename 's/(^|[\s_-])([a-z])/$1\u$2/g' *
```

CamelCase
```
rename 's/(^|[\s_-])([a-z])/\u$2/g' *
```

---

### Post by ibuclaw on 2009-07-25
Actually, I think
```
rename 's/\b(\w+\.)/\u$1/g'
```
Would be better suited for Camel.Casing names whilst leaving the suffix in tact.

ie:
> 
iain@jstdio:~/Desktop$ touch foo.bar.txt
iain@jstdio:~/Desktop$ ls
**foo.bar.txt**
iain@jstdio:~/Desktop$ rename 's/\b(\w+\.)/\u$1/g' foo.bar.txt 
iain@jstdio:~/Desktop$ ls
**Foo.Bar.txt**
iain@jstdio:~/Desktop$ 


Regards
Iain

---

### Post by switchrodeo720 on 2009-07-25
tinivole, 

That worked perfectly. I'm using it to rename a whole directory of files like so.

```
rename 's/\b(\w+\.)/\u$1/g' ~/Desktop/sample_dir/*
```

I'm just learing bash scripting & regex's. It would be great if you could talk me through your regex so I can understand how it's working. I'm familiar with the rename function already.

Thanks again for the help.

---

### Post by switchrodeo720 on 2009-07-25
I had this question posted here as well.

[BashScripts.org]("http://www.bashscripts.org/forum/viewtopic.php?f=8&t=847&p=2885#p2885")

I let them know you helped me out and linked back to this thread.

---

### Post by ibuclaw on 2009-07-26
> **switchrodeo720 said:**
> tinivole, 

That worked perfectly. I'm using it to rename a whole directory of files like so.

```
rename 's/\b(\w+\.)/\u$1/g' ~/Desktop/sample_dir/*
```

I'm just learing bash scripting & regex's. It would be great if you could talk me through your regex so I can understand how it's working. I'm familiar with the rename function already.

Thanks again for the help.

's///' is the search and replace function in Perl, as a default it only finds the first match.

It works like so:
```
s/find pattern/replace/
```
The 'g' on the end means to match the find pattern as many times as possible.


To quickly run through the rest.

'\b' matches word boundaries (the beginning and end of words). ie:
```
split /\b/, "Hello World!"
```
would return
```
("Hello", " ", "World", "!")
```
'\w' matches all alphanumerics plus '_' and '.', (same as [0-9a-zA-Z_.])
The appended '+' tells the regexp engine to find at least 1 or more matches of those characters.

'\.' matches a literal full stop '.' character.


The '()' brackets, or parenthesis in the regular expression is treated as a subexpression, and gets assigned to the $1 or \1 and up values respectively. ie:
```
s/(Hello) and (World)/$1 $2/
```
$1 would contain "Hello", $2 "World", and so would return
```
Hello World
```
'\u' means set the first character as an Upper case character.


The only one case where the rename expression won't work is when there is a space in the filename.

ie:
```
this file.txt
```
would be renamed to 
```
this File.txt
```

Regards
Iain

---

### Post by switchrodeo720 on 2009-07-26
Again I'd like to say thanks for the help and the regex details. Any good regex resources that you could pass along would be great.

---

### Post by switchrodeo720 on 2009-07-26
Oh yeah, I got a couple 404s from your footer links.

---

### Post by ibuclaw on 2009-07-26
> **switchrodeo720 said:**
> Oh yeah, I got a couple 404s from your footer links.

Heh, thanks for pointing that out.

On the first account, the BT team I'm associated with has undergone a recent name change, hence the missing page in Launchpad.

On the second account, I've been meaning to sort out a VPS with a friend/affiliate so I can get some real hosting setup.


As for references, I have none. What I know just comes from experience and age. Although, if I were new to this and had to start somewhere, I'd suggest learn how to use sed first.

Regards
Iain

---

### Post by OwnSurname on 2009-10-10
Given I'm an absolute beginner with scripting, thanks to you guys I was able to work out how to massively rename my mp3s using the rename function. Titlecase as suggested in #3 was almost perfect, but still missing the first word inside parentheses. So I modified it adding also words after the opening parenthesis '\(', and not only after whitespaces '\s', '_' and '-'. It works quite well for my needs:

rename 's/(^|[\(\s_-])([a-z])/$1\u$2/g' *


user@user_desktop:/tmp/renameMp3z$ touch "song one.mp3" "song two (own mix).mp3" "artist name - song 3 a really really useless long name.mp3"
user@user_desktop:/tmp/renameMp3z$ ll
total 0
-rw-r--r-- 1 user user 0 2009-10-10 12:04 artist name - song 3 a really really useless long name.mp3
-rw-r--r-- 1 user user 0 2009-10-10 12:04 song one.mp3
-rw-r--r-- 1 user user 0 2009-10-10 12:04 song two (own mix).mp3
user@user_desktop:/tmp/renameMp3z$ rename 's/(^|[\(\s_-])([a-z])/$1\u$2/g' *
user@user_desktop:/tmp/renameMp3z$ ll
total 0
-rw-r--r-- 1 user user 0 2009-10-10 12:04 Artist Name - Song 3 A Really Really Useless Long Name.mp3
-rw-r--r-- 1 user user 0 2009-10-10 12:04 Song One.mp3
-rw-r--r-- 1 user user 0 2009-10-10 12:04 Song Two (Own Mix).mp3

---

